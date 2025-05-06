

Primero se guardan todos los archivos en una carpeta, de manera ordenadataly como estn en las instrucciones. 

```
(venv) C:\Users\Bianca\Documents\repositorio\Desarrollo-de-Software>pytest --cov=models
============================================== test session starts ==============================================
platform win32 -- Python 3.11.0, pytest-7.1.2, pluggy-1.5.0
rootdir: C:\Users\Bianca\Documents\repositorio\Desarrollo-de-Software
plugins: Faker-37.1.0, cov-3.0.0
collected 8 items

tests/test_account.py ........                                   [100%]

---------- coverage: platform win32, python 3.11.0-final-0 -----------
Name                                         Stmts   Miss  Cover
----------------------------------------------------------------
Actividades\actividad12\models\__init__.py       7      0   100%
Actividades\actividad12\models\account.py       44      0   100%
----------------------------------------------------------------
TOTAL                                           51      0   100%

============================================ 8 passed in 0.5s ============================================ 

```















```
(venv) C:\Users\Bianca\Documents\repositorio\Desarrollo-de-Software\Actividades>pytest actividad12/tests/test_account_model.py
============================================== test session starts ==============================================
platform win32 -- Python 3.11.0, pytest-7.1.2, pluggy-1.5.0
rootdir: C:\Users\Bianca\Documents\repositorio\Desarrollo-de-Software\Actividades
plugins: Faker-37.1.0, cov-3.0.0
---------- coverage: platform win32, python 3.11.0-final-0 -----------
Name                             Stmts   Miss  Cover
----------------------------------------------------
actividad12\models\__init__.py       7      0   100%
actividad12\models\account.py       44      0   100%
----------------------------------------------------
TOTAL                               51     0    100%

===================================== 8 pasaron en 0.5s =====================================


```
