Primero cree el archivo adapter.py dentro de iac_patterns 

```python 

adapter.py 

class MockBucketAdapter: def init(self, null_block: dict): self.null = null_block 

def to_bucket(self) -> dict: 
    # Mapear triggers a parámetros de bucket simulado 
    name = list(self.null["resource"]["null_resource"].keys())[0] 
    return { 
        "resource": { 
            "mock_cloud_bucket": { 
                name: {"name": name, **self.null["resource"]["null_resource"][name]["triggers"]} 
            } 
        } 
    } 

``` 

 

 

La clase MockBucketAdapter toma un bloque de configuración de Terraform que usa null_resource y lo convierte en un recurso simulado llamado mock_cloud_bucket. 

En concreto: 

Extrae el nombre del recurso null_resource. 

Copia los valores definidos en triggers. 

Crea un nuevo diccionario con formato de bucket simulado, incluyendo el nombre y esos valores. 

  

Hize cambios en builder.py : 

 

```python 

from iac_patterns.adapter import MockBucketAdapter 

``` 

 

 

Cree la clase Builder dentreo de Builder.py : 

 

```python 

class Builder: 

    def __init__(self): 

        self.infra = {} 

 

    def add_null(self, name, triggers=None): 

        null_factory = NullFactory(name, triggers) 

        resource = null_factory.create() 

        self.infra.update(resource) 

 

    def add_mock_bucket(self, name, triggers=None): 

         

        null_factory = NullFactory(name, triggers) 

        null_resource = null_factory.create() 

 

         

        adapter = MockBucketAdapter(null_resource) 

        mock_bucket_resource = adapter.to_bucket() 

 

         

        self.infra.update(mock_bucket_resource) 

 

    def generate(self): 

        return self.infra  

 

 

 

 

``` 

 

 

La clase Builder sirve para crear y almacenar diferentes recursos de infraestructura en un diccionario llamado infra. 

add_null(name, triggers=None): 
 Crea un recurso "null" usando una fábrica (NullFactory), y lo añade al diccionario infra. 

add_mock_bucket(name, triggers=None): 
 Primero crea un recurso "null" con NullFactory. Luego, usa un adaptador (MockBucketAdapter) para convertir ese recurso "null" en un recurso tipo "mock bucket". Finalmente, añade este recurso transformado al diccionario infra. 

generate(): 
 Devuelve la infraestructura completa que se ha ido construyendo (el diccionario infra). 

  

 

Luego ejecute, todo salio exitosamente: 
