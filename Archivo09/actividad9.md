Paso 1 (Rojo): Primera prueba 

En el archivo tests/test_user_manager.py,copie este codigo,q que da error porque le falta su implementacion 

 

``` 

 

import pytest 
from user_manager import UserManager, UserAlreadyExistsError 
 
def test_agregar_usuario_exitoso(): 
    # Arrange 
    manager = UserManager() 
    username = "kapu" 
    password = "securepassword" 
 
    # Act 
    manager.add_user(username, password) 
 
    # Assert 
    assert manager.user_exists(username), "El usuario debería existir después de ser agregado." 

 

``` 

C:\Users\Bianca\Documents\repositorio\user_management>pytest =========================================== test session starts =========================================== platform win32 -- Python 3.11.0, pytest-8.3.5, pluggy-1.5.0 rootdir: C:\Users\Bianca\Documents\repositorio\user_management plugins: anyio-4.6.2.post1, Faker-37.1.0, cov-6.1.1 collected 0 items / 1 error  

================================================= ERRORS ================================================== _______________________________ ERROR collecting tests/test_user_manager.py _______________________________ ImportError while importing test module 'C:\Users\Bianca\Documents\repositorio\user_management\tests\test_user_manager.py'. Hint: make sure your test modules/packages have valid Python names. Traceback: ......\AppData\Local\Programs\Python\Python311\Lib\importlib_init_.py:126: in import_module return _bootstrap._gcd_import(name[level:], package, level) tests\test_user_manager.py:2: in from user_manager import UserManager, UserAlreadyExistsError E ModuleNotFoundError: No module named 'user_manager' ========================================= short test summary info ========================================= ERROR tests/test_user_manager.py !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! Interrupted: 1 error during collection !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! ============================================ 1 error in 0.41s ============================================= 

``` 

  

 

 

Paso 2 (Verde): Implementamos lo mínimo: 

 

 

``` 

 

C:\Users\Bianca\Documents\repositorio\user_management>pytest 

=========================================== test session starts =========================================== 

platform win32 -- Python 3.11.0, pytest-8.3.5, pluggy-1.5.0 

rootdir: C:\Users\Bianca\Documents\repositorio\user_management 

plugins: anyio-4.6.2.post1, Faker-37.1.0, cov-6.1.1 

collected 1 item 

``` 

 

Ahora pasa la prueba 

 

Paso 3 (Refactorización) 

 

Iteración 2 

 

 Paso 1 (Rojo): Nueva prueba 

 

 

``` 

class FakeHashService: """ Servicio 'fake' que devuelve un hash simplificado con un prefijo, y lo verifica. """ def hash(self, plain_text: str) -> str: return f"fakehash:{plain_text}" 

def verify(self, plain_text: str, hashed_text: str) -> bool: 
    return hashed_text == f"fakehash:{plain_text}" 
  

def test_autenticar_usuario_exitoso_con_hash(): # Arrange hash_service = FakeHashService() manager = UserManager(hash_service=hash_service) 

username = "usuario1" 
password = "mypassword123" 
manager.add_user(username, password) 
 
# Act 
autenticado = manager.authenticate_user(username, password) 
 
# Assert 
assert autenticado, "El usuario debería autenticarse correctamente con la contraseña correcta." 

 
Aca se agrega esto y la prueba da señal color rojo  porque aun no se utiliza un servidor importante de hash ni un metodo authenticate_user.. 

 

Paso 2 (Verde): Implementación con inyección de hash_service 

En el archivo de Python agregue: user_manager.py,  

 

C:\Users\Bianca\Documents\repositorio\user_management>pytest 

=========================================== test session starts =========================================== 

platform win32 -- Python 3.11.0, pytest-8.3.5, pluggy-1.5.0 

rootdir: C:\Users\Bianca\Documents\repositorio\user_management 

plugins: anyio-4.6.2.post1, Faker-37.1.0, cov-6.1.1 

collected 1 item  

 

Aca la prueba da color verde porque ahora se agrego authenticate_user. 

 

Paso 3 (Refactorización) 

 

``` 

C:\Users\Bianca\Documents\repositorio\user_management>pytest 

=========================================== test session starts =========================================== 

platform win32 -- Python 3.11.0, pytest-8.3.5, pluggy-1.5.0 

rootdir: C:\Users\Bianca\Documents\repositorio\user_management 

plugins: anyio-4.6.2.post1, Faker-37.1.0, cov-6.1.1 

collected 0 items / 1 error                                                                                 

  

================================================= ERRORS ================================================== 

 

``` 

 

Paso 2 (Verde): Implementación 

 

En user_manager.py se le añaden métodos y se modifica el contructor.Todo esto hace que funcione bien la prueba. Luego se refactoriza y todo se ve razonable. 

 

 

 

 

 

 
