

Primero se guardan todos los archivos en una carpeta, de manera ordenada taly como estan en las instrucciones. 
Despues nos aseguramos de  que cuando corran los tests todo tenga 100 porciento.


![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo12/img/c1.png)


# Paso 1: Ejecutar pytest
Ejecuto pytest mediante el comando importante : pytest --cov=models.


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

# Paso 2: Crear una claseAccountFactory 

Abri el archivo account.py para poder ver y analizar la clase, las librerias entre otras cosas que me serviran 

 

![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo12/img/c2.png)


Se tienen los proveedores y los atributos Fuzzy:

![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo12/img/c3.png)



# Paso 3: Actualizar los casos de prueba 

  

Abro el archivo tests/test_account.py.  Hago unos cambios para que se pueda importar la nueva clase AccountFactory desde la ubicacion del módulo Factories 


![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo12/img/c4.png)


Empiezo con la prueba test_crear_todas_las_cuentas(), para borrar referencias a ACCOUNT_DATA  y Account. Luego las reemplazo con AccountFactory. 


![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo12/img/c5.png)


Se ve que se cambio el codigo, para crear 10 cuentas. 

 
# Paso 4: Actualizar test_crear_una_cuenta() 

![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo12/img/c6.png)


Se hicieron cambios en el código para que se pueda crear una cuenta , usando datos desconocidos. No se hizo mucho, solose cambio el 1 o por el 10 y el nombre de la funcion. 

# Paso 5: Actualizar test_to_dict()


![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo12/img/c7.png)

Se hicieron los cambios respectivos de borrar los rastros de ACCOUNT_DATA Y Account. 

# Paso 6: Actualizar test_from_dict() 

![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo12/img/c8.png)


# Paso 7: Actualizar test_actualizar_una_cuenta() 


![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo12/img/c9.png)


# Paso 8: Actualizar test_id_invalido_al_actualizar()



![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo12/img/c10.png)


# Paso 9: Actualizar test_eliminar_una_cuenta() 



![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo12/img/c11.png)



# Paso 10: Eliminar referencias a ACCOUNT_DATA 

# 10a: 

Nos vamos a Account.py para arreglar este problema de reemplazar instancias. 

Me fui a la carpeta account.py y luego agregue la funcion setUp, que es muy util para borrar carga de muchos archivos de tipo JSON. 

 

![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo12/img/c12.png)
 

10b: 

Agrego un nuevo metodo de clase, para crear trablas SQLAlchemy 


![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo12/img/c13.png)

La ejecucion final de todos los tests:


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
