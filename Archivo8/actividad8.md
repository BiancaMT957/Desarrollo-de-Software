## Ejercicio 1: Método para vaciar el carrito


Agregue el método vaciaren src/carrito.pyque realiza self.items = [].
Crea pruebas en tests/test_carrito.pyque agreguen varios productos, invoquen vaciar()y verifiquen que obtener_items()regresen una lista vacía y calcular_total()regresen 0.


![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/codi1.png)

Se creo la funcion test_vaciar_carrito(), para vaciar el carrito, luego se va a averificar si la lista de productos este vacio y el total de cosas sea 0.
## Ejercicio 2: Descuento por compra mínima

Agregue un nuevo método, por ejemplo, aplicar_descuento_condicional(porcentaje, minimo)en la clase Carritoque primero verifique si calcular_total() >= minimo.
Si se cumple la condición, aplica el descuento; De lo contrario, retorna el total sin descuento.
Escribe pruebas para ambos escenarios (condición cumplida y no cumplida).

![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/1md.png)

![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/2.png)
Se creo un nuevo metodo "aplicar_descuento_condicional(porcentaje, minimo).
Luego de eso se procedio a hacer pruebas para los escenarios(se creo la funcion aplicar_descuento_condicional).
Al final se ejecuto el test, teniendo previamente instalado el comando "pytest" dentro de Visual Studio Code y al final y se obtuvo el resultado de arriba.
## Ejercicio 3: Manejo de stock en producto

Modifica Productoen src/carrito.pyagregando self.stock = stocken el constructor y actualiza la fábrica en src/factories.pypara que genere un stock (por ejemplo, entre 1 y 100).
En Carrito.agregar_producto, antes de agregar o incrementar la cantidad, verifique que la suma de cantidades en el carrito no supere el stockproducto.
Escribe pruebas que verifiquen:
Se puede agregar un producto dentro del límite de stock.
Se lanza una excepción al intentar agregar más unidades de las disponibles.



Se creo la funcion agregar_ producto(), que permite que funciones bien el trabajo. Despues procedimos  a hacer 
![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/2m.png)


![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/3.png)
Al final se ejectura todo.



## Ejercicio 4: Ordenar artículos del carrito
Crea un método obtener_items_ordenados(criterio: str)donde criteriopuedas ser "precio"o "nombre".
Utiliza la función sorted()con una función lambda para ordenar según el criterio.
Escriba pruebas que verifiquen que, al agregar varios productos, la lista de vuelta esté ordenada correctamente según el criterio solicitado.


![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/3m.png)
Se procedio a crear la funcion "obtener_items_ordenados", con la intencion de devolver los items de los carritos ordenados por precio o nombre,
Sino cumple ninguna de ls criterios(ya sean preio o nombre),  entonces se devuelve un error.


![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/4.png)

Al final se tuvo esta ejecucion

## Ejercicio 5: Uso de accesorios de Pytest

En el archivo tests/conftest.py, crea un accesorio para un carrito vacío:
import pytest
from src.carrito import Carrito

@pytest.fixture
def carrito():
    return Carrito()

    
Crea también un accesorio para un producto genérico, usando la fábrica:
import pytest
from src.factories import ProductoFactory

@pytest.fixture
def producto_generico():
    return ProductoFactory(nombre="Genérico", precio=100.0)


    
Actualiza las pruebas existentes para usar estos dispositivos en lugar de instanciar los objetos directamente en cada prueba.


![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/5.png)
## Ejercicio 6: Pruebas parametrizadas

Por ejemplo, parametriza pruebas para aplicar_descuentousar distintos porcentajes y totales esperados.

De igual forma, para actualizar cantidades: pruebe con diferentes valores (válidos e inválidos) y verifique que se lanza la excepción en los casos correspondientes.


Se creo la funcion para parametrizar descuentos : 

![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/6md.png)

Tambien se procedieron a hacer cambios.

![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/6.png)
Al final se tiene el resultado en verde de la ejecucion, lo cual significa que esta bien todo lo trabajado.

## Ejercicio 7: Calcular impuestos en el carrito

![ee](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo8/img/7a.png)
Se procede a ver el error a la hora de ejecutar "pytest".

