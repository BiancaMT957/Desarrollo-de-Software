Paso 1: Inicializar la base de datos
Aca en test/test_account.py se crea el metodo setup_database(), tiene mucho que ver con la base de datos, se encarga de crear tablas.
Se corre por primera vez el test.
Paso 2: Cargar datos de prueba
Se cargan los datos json.
Se carga la funcion TestAccoundModel, que utiliza un metodo para cargar datos de prueba.
```
C:\Users\Bianca\Documents\pruebas pytest\actividad12>pytest
============================================================= test session starts =============================================================
platform win32 -- Python 3.11.0, pytest-8.3.5, pluggy-1.5.0
rootdir: C:\Users\Bianca\Documents\pruebas pytest\actividad12
plugins: anyio-4.6.2.post1, Faker-37.1.0, cov-6.1.1
collected 0 items
``` Paso 3: Escribir un caso de prueba para crear una cuenta
```
def test_create_an_account(self): """Probar la creación de una sola cuenta""" data = ACCOUNT_DATA[0] # obtener la primera cuenta account = Account(**data) account.create() assert len(Account.all()) == 1
```
C:\Users\Bianca\Documents\pruebas pytest\actividad12>pytest
============================================================= test session starts =============================================================
platform win32 -- Python 3.11.0, pytest-8.3.5, pluggy-1.5.0
rootdir: C:\Users\Bianca\Documents\pruebas pytest\actividad12
plugins: anyio-4.6.2.post1, Faker-37.1.0, cov-6.1.1
collected 1 item
Test/test_account.py .
============================================================== 2 passed in 0.29s ==============================================================
```
Paso 4: Escribir un caso de prueba para crear todas las cuentas
```
def test_create_all_accounts(self): """Probar la creación de múltiples cuentas""" for data in ACCOUNT_DATA: account = Account(**data) account.create() assert len(Account.all()) == len(ACCOUNT_DATA)
```
```
C:\Users\Bianca\Documents\pruebas pytest\actividad12>pytest
============================================================= test session starts =============================================================
platform win32 -- Python 3.11.0, pytest-8.3.5, pluggy-1.5.0
rootdir: C:\Users\Bianca\Documents\pruebas pytest\actividad12
plugins: anyio-4.6.2.post1, Faker-37.1.0, cov-6.1.1
collected 2 item
Test/test_account.py .
============================================================== 2 passed in 0.60 s ==============================================================
```
Paso 5: Limpiar las tablas antes y después de cada prueba
```
def setup_method(self): """Truncar las tablas antes de cada prueba""" db.session.query(Account).delete() db.session.commit() def teardown_method(self): """Eliminar la sesión después de cada prueba""" db.session.remove()
```
Al final se crearon los metodos setup_method y teardown_method para mantener limpia la base de datos
