# Indicaciones 
Se clona la raiz del proyecto. 


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b1.png)


Todo se tiene bien documentado 


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b2.png)



Desde visual Studio decido abrir el archivo clonado. 



![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b3.png)


Despues se instala todo lo necesario : 


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b4.png)



![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b5.png)



Ejecute flake.8: 



![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b6.png)


# Ejercicio 1: Análisis y evaluación de la cobertura actual

Corro los test despues y todo esta bien , por el 100 porciento.


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b7.png)


Voy a ejectuar : 


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b8.png)


Al final hago un reporte en html. 


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b9.png)


Busque el archivo en mi cmputadora y lo abri  



![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b10.png)



![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b11.png)


Procedo a  ejecutar las pruebas


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b12.png)


Noto que : 

Todas las funciones y líneas del archivo stack.py están actualmente cubiertas por pruebas.  Esto incluye métodos básicos como push, pop y peek, según los nombres de los tests que vimos (test_push, test_pop, test_peek). Dado que no hay líneas faltantes, no se identifican por ahora métodos con condicionales que requieran casos adicionales. 

 Breve informe: Informe de cobertura de código 

Resumen general: 

Proyecto: Desarrollado en Python. 

Módulo revisado: Actividades\actividad10\stack.py. 

Cobertura total: 100%. 

Líneas cubiertas: 12. 

Líneas no cubiertas: 0. 

Detalles del análisis: 

Todos los métodos en stack.py están cubiertos: 

push: Cubierto. 

pop: Cubierto. 

peek: Cubierto. 

Observaciones: 

No hay código no cubierto en el archivo. Las pruebas parecen manejar correctamente los tres métodos principales de la pila (push, pop, peek). Se recomienda mantener esta cobertura al añadir nuevas funcionalidades. 

Recomendaciones: Agregar pruebas adicionales si se añaden más condiciones, como manejo de errores o cambios en el comportamiento de los métodos existentes. 


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b13.png)



Descargue DB Browser para SQLite pa poder abrir el archivo test.db 


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b14.png)



![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b15.png)



# Ejercicio 2: Ampliar las pruebas para mejorar la cobertura 

a) 
Verificar que es un diccionario 

# Verificar valores específicos 

Chequear que 'id' y 'date_joined' existan en el dict 

Verificar tipos de datos esperados 


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b16.png)


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b17.png)


B ) Caso 1: el diccionario esta incompleto, falta email, phone_number, disabled


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b18.png)


Caso2:

![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b19.png)


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b20.png)



NUEVO: Verificar que se genera un ID . NUEVO: El ID debe ser entero 




![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b21.png)



Cambiamos varios atributos.Verificamos que se guardaron en la BD.


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b22.png)


penultima linea:ya no debe estar .Utima linea:  # find() debe devolver None 



![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b23.png)



![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b24.png)


Aseguramos que sea exactamente del formato <Account 'nombre'> 

 

# Ejercicio 3: Ampliación y optimización del Makefile 
 

Cree un nuevo objetivo en elarchivo Makefile ,con la finaidad de combinar todos los informes individuales en uno solo.



![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b25.png)


Ejecute flake.8: 


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b26.png)


Ejecuto todas las pruebas  



![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b27.png)


Ejecuto tmb con coverage report para tener un reporte de todas las lineas, aca me sale lo que tiene una cobertura de 100 porciento, lo cual esta bien. 


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b28.png)



Despues de usar “make clean” pa borrar los archivos cache y otros inservibles 


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b29.png)


 

# Ejercicio 4: Integración y pruebas con una base de datos temporales

Configurar una base de datos temporales para pruebas: se condiciona la configuración de la base de datos para que, en modo de prueba, se utilice una base de datos en memoria o un archivo temporal 



![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b30.png)


Modificar el accesorio de la base de datos en test_account.py: 



![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b31.png)



Ejecuto las pruebas 

![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b32.png)

Aca puedo agregar o crear el metodo validatepara verificar que el correo electrónico tenga un formato válido y que el nombre no esté vacío. 


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b33.png)


Procedo a crear 3 pruebas 

![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b34.png)


1ra prueba: 

Crea una cuenta con name="". Espera DataValidationError y verifica en el mensaje que la clave hable de “nombre vacío”. 

2da prueba: 

Crea una cuenta con un email sin @ ni dominio. Espera la misma excepción y busca en su texto algo como “formato de email inválido”. 


![e](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo11/img/b35.png)


Crea una cuenta con datos correctos. 


Comprueba que no hay excepción y que account.id se ha asignado correctamente. 

