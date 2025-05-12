
## Factory y fakes

#### Paso 1: Ejecutar pytest
Corri el test y me salieron errores: “corriendo fuera del contexto  de aplicacion”. 
Faltaba que toda la cobertura de ambos sea  100 porciento. 

```
============================================================ tests coverage ============================================================= 
____________________________________________ coverage: platform win32, python 3.11.0-final-0 ____________________________________________ 

Name                 Stmts   Miss  Cover
----------------------------------------
models\__init__.py       6      0   100%
models\account.py       43     19    56%
----------------------------------------
TOTAL                   49     19    61%
======================================================== short test summary info ======================================================== 
ERROR tests/test_account.py::TestAccountModel::test_crear_todas_las_cuentas - RuntimeError: Working outside of application context.       
ERROR tests/test_account.py::TestAccountModel::test_crear_una_cuenta - RuntimeError: Working outside of application context.
ERROR tests/test_account.py::TestAccountModel::test_repr - RuntimeError: Working outside of application context.
ERROR tests/test_account.py::TestAccountModel::test_to_dict - RuntimeError: Working outside of application context.
ERROR tests/test_account.py::TestAccountModel::test_from_dict - RuntimeError: Working outside of application context.
ERROR tests/test_account.py::TestAccountModel::test_actualizar_una_cuenta - RuntimeError: Working outside of application context.
ERROR tests/test_account.py::TestAccountModel::test_id_invalido_al_actualizar - RuntimeError: Working outside of application context.     
ERROR tests/test_account.py::TestAccountModel::test_eliminar_una_cuenta - RuntimeError: Working outside of application context.
=========================================================== 8 errors in 2.53s =========================================================== 
```

Luego instale  Flask mediante el comando : pip install flask-sqlalchemy factory-boy faker pytest pytest-cov 

```

```

 

Trate de solucionar el error haciendo arreglos en el codigo , agregandole el contexto de 

```
“ with app.app_context():”
```

dentro de cada metodo, ademas agregue : 


``` python
from flask import Flask   

from typing import Any    
```
 

 

Para que se importata la app Flask y Any  tambien y funciones bien el codigo. 

Se crearon estos dos nuevos fixtures, para el contexto de aplicacion. 

 
```python
@pytest.fixture(scope="session")
def app():
    """Crea una aplicación Flask para las pruebas"""
    app = Flask(__name__)
    app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///:memory:'
    app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False
    db.init_app(app)

    with app.app_context():
        db.create_all()
        yield app
        db.drop_all()

@pytest.fixture(scope="function", autouse=True)
def session(app: Any):
    """Crea una sesión nueva para cada prueba"""
    with app.app_context():
        db.session.query(Account).delete()
        db.session.commit()
        yield db.session
        db.session.close()
```
 

 

#### Paso 2: Crear una clase `AccountFactory` 

 

Se creo la clase Account Factory con elementos Fuzzy que podrian ser importantes. 

Los proveedores de Faker y los atributos Fuzzy son necesarios en este caso para crear datos falsos en campos como id, etc. 


```python
import factory 
from datetime import date 
from factory.fuzzy import FuzzyChoice, FuzzyDate 
from models.account import Account 
 
class AccountFactory(factory.Factory): 
    """Crea cuentas falsas""" 
 
    class Meta: 
        model = Account 
 
    id = factory.Sequence(lambda n: n) 
    name = factory.Faker("name") 
    email = factory.Faker("email") 
    phone_number = factory.Faker("phone_number") 
    disabled = FuzzyChoice(choices=[True, False]) 
    date_joined = FuzzyDate(date(2008, 1, 1)) 
``` 

 

#### Paso 3: Actualizar los casos de prueba 

Se agrego una nueva linea de texto para importar factories, se crea la prueba test_crear_todas_las_cuentas() para eliminar referencias a ACCOUNT_DATA y Account, ademas se hizo cambio para que ahora sean 10 cuentas lasque se puedan crear. 

 

```python 
def test_crear_todas_las_cuentas(self): 
    """Prueba la creación de múltiples Cuentas""" 
    for _ in range(10): 
        account = AccountFactory() 
        account.create() 
    assert len(Account.all()) == 10 
``` 

 

 

#### Paso 4: Actualizar test_crear_una_cuenta() 

A la prueba test_crear_una_cuenta() se le modifica eliminar las referencias a ACCOUNT_DATA y Account. 

 

```python
def test_crear_una_cuenta(self): 
    """Prueba la creación de una Cuenta usando datos conocidos""" 
    account = AccountFactory() 
    account.create() 
    assert len(Account.all()) == 1 
``` 

 

 

#### Paso 5: Actualizar test_to_dict() 

Se modifico la prueba test_to_dict(), para actualizarla y quitar todo rastro de CCOUNT_DATA y Account, cambiandolas por AccountFactory. 

 
```python 
def test_to_dict(self): 
    """Prueba la serialización de una cuenta a un diccionario""" 
    account = AccountFactory() 
    result = account.to_dict() 
    assert account.name == result["name"] 
    assert account.email == result["email"] 
    assert account.phone_number == result["phone_number"] 
    assert account.disabled == result["disabled"] 
    assert account.date_joined == result["date_joined"] 

``` 

Luego se hicieron de manera parecidad los pasos 6,7,8 y 9.

Por ultimo se corren todos los tests con el comando pytest –cov=models . 

 
