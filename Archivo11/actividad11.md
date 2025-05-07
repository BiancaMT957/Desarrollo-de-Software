

# Actividad 11
Cree las carpetas y archivos en Visual Studio Code, segun las instrucciones de la actividad 10.




## Paso 1: Instalación de pytest y pytest-cov:
Use el comando python3 -m pip install pytest pytest-cov para instalar pytest y pytest-cov
Paso 1: Instalación de pytest y pytest-cov:


![fg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/ñ8.png)



## Paso 2: Archivos de prueba
Abro el archivo test_pila:


![fg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/a3.png)



Abro el archivo : pila.py y e¿mde doy cuenta que estan los metodos pop, push, peek , is_empty


![fg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/a4.png)


Ejecuto el comando pytest-v para poder correr las pruebas


![fg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/a5.png)


## Paso 3:





Modifique el metodo test_is_empty para el test_stack(te devuelve “True” si la pila esta vacia, devuelve “False” lo contrario).



![fg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/a7.png)


Tambien test_pop, que es un metodo de pila para borrar elementos.
## Paso 4: Ejecuta pytest para verificaris_empty()
Corri el test y me sale esto, significa que esta todo bien, que todos los metodos passaron.




![fg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/a8.png)



## Paso 5: Escribiendo aserciones para el método peek():
Este método test_peek lo modifico


![fg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/a9.png)


Esta es la modificacion del metodo test_peek:




## Paso 6: Escribiendo aserciones para el método pop():

Se puede apreciar el metodo pop() de pila

![fg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/a11.png)


le agrego aserciones al metodo pop.


![fg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/a12.png)



## Paso 7: Escribiendo aserciones para elmétodo push()

Se puede apreciar el metodo push() de pila

![fg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/a13.png)


le agrego aserciones al metodo push.


![fg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/a14.png)



## Paso 8: Ejecuta pytest para verificar todas las pruebas

Ejecuto el comando"pytest" en la terminal de Visual Studio Code, esperando que se ejecuten los tests trabajados.
se ve la eejcucuion de los 4 tests, ademas de su porcentaje para cada uno.

![fg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/ñ8.png)



## Paso 9: Agregando cobertura de pruebas con pytest-cov

Aca se puede apreciar de una manera mas elegante y con porcentajes adecuados 

![fg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/ñ9.png)
