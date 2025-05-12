## Cree el entorno virtual 


C:\Users\Bianca\Documents\repositorio\actividad13>python -m venv venv 

 

## Procedi a activar el entorno virtual 


C:\Users\Bianca\Documents\repositorio\actividad13>venv\Scripts\activate 

(venv) 



 Cree el archivo .gitignore para poner cosas que no deben estar ahi, para que no las lea Visual Studio Code, sino muy pesado. 

 

 

## Paso 1: Probar búsqueda por título 

Se agrego este método que i implementa la búsqueda por título sin ningún patching o mocking. 

Este código instancia un objeto IMDbinicializándolo con una clave de API. Luego llama a imdb.search_titles()la película "Bambi" y afirma que los resultados no son None. También verifica que el mensaje de error esté vacío y que el id retornado sea tt1375666. 

 

``` 

import json
import pytest from unittest.mock
import patch, Mock from models.imdb
import IMDb 

Fixture para cargar los datos de IMDb desde un archivo JSON 

@pytest.fixture(scope="session") def imdb_data(): """Carga las respuestas de IMDb necesarias para las pruebas""" with open('tests/fixtures/imdb_responses.json') as json_data: return json.load(json_data) 

class TestIMDbDatabase: """Casos de prueba para la base de datos de IMDb""" 

@pytest.fixture(autouse=True) 
def setup_class(self, imdb_data): 
    """Configuración inicial para cargar los datos de IMDb""" 
    self.imdb_data = imdb_data 
 
###################################################################### 
#  Casos de prueba 
###################################################################### 
 
@patch('test_imdb.IMDb.search_titles') 
def test_search_by_title(self, imdb_mock): 
    """Prueba de búsqueda por título""" 
    imdb_mock.return_value = self.imdb_data["GOOD_SEARCH"] 
    imdb = IMDb("k_12345678") 
    resultados = imdb.search_titles("Bambi") 
    assert resultados is not None 
    assert resultados.get("errorMessage") is None 
    assert resultados.get("results") is not None 
    assert resultados["results"][0]["id"] == "tt1375666" 
  

``` 

 

## Paso 2: Búsqueda sin resultados 

Aca se implemento cosas para la “prueba triste”,  se parcheo la biblioteca de terceros “requests”, tambien se parcheo la funcion “get”, porque se sabe que IMDb.search_titles() eventualmente llamará al método requests.get() para la llamada a la API. 

 

``` 

def test_search_with_no_results(self, imdb_mock): 
    """Prueba de búsqueda sin resultados""" 
    imdb_mock.return_value = Mock(status_code=404) 
    imdb = IMDb("k_12345678") 
    resultados = imdb.search_titles("Titulo inexistente") 
    assert resultados == {} 
  

``` 

## Paso 3: Búsqueda por título fallida 

Aca se construyo un caso de prueba, se necesito un MOCK que se porta como objeto Response . Se retorno un codigo de 200.  

Luego se agrego una linea de codigo antes del metodo test_search_by_title_failed(), y se agrego un parametro para el simulacro de tipo mock. 

Esto genero un parcheo a una llamada requests.get, esto permitio controlar lo que regresa la variable imdb_mock. 

 

``` 

   """Prueba de búsqueda por título fallida""" 
    imdb_mock.return_value = Mock( 
        spec=Response, 
        status_code=200,  
        json=Mock(return_value=self.imdb_data["INVALID_API"]) 
    ) 
    imdb = IMDb("bad-key") 
    resultados = imdb.search_titles("Bambi") 
    assert resultados is not None 
    assert resultados["errorMessage"] == "Invalid API Key" 
  

``` 

## Paso 4: Probar calificaciones de películas 

A el metodo de calificaciones de peliculas, se le agrego una linea de codigo un poco antes del metodo y luego se agreg un parámetro para un nuevo simulacro , lo cual parcha a request.gets() y permite controlar la cosas que rertorna usando la variable imdb_mock. 

 

 

 

 

``` 

@patch('models.imdb.requests.get') 
    def test_movie_ratings(self, imdb_mock): 
        """Prueba de calificaciones de películas""" 
        imdb_mock.return_value = Mock( 

       spec=Response, 
        status_code=200,  
        json=Mock(return_value=self.imdb_data["GOOD_RATING"]) 
    ) 
    imdb = IMDb("k12345678") 
    resultados = imdb.movie_ratings("tt1375666") 
    assert resultados is not None 
    assert resultados["title"] == "Bambi" 
    assert resultados["filmAffinity"] == 3 
    assert resultados["rottenTomatoes"] == 5 
  

  

``` 

 

Al ultimo se tiene la solucion de todas las implementaciones  hechas. 


![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo13/img/13.png) 

 

Despues se corren los tests, luego verificamos que todo esta correctamente implementado.


  
