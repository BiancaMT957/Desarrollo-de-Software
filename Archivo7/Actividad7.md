## Ejercicio 1: Añadir soporte para minutos y segundos en tiempos de espera
Objetivo

Ampliar la funcionalidad para reconocer tiempos de espera expresados ​​en horas, minutos y segundos.
Instrucciones

Modifica la función que maneja el tiempo de espera en steps.py(o donde analiza el tiempo) para que acepte:
"1 hora y 30 minutos"
"90 minutos"
"3600 segundos"
Variaciones que incluyen segundos (por ejemplo, "1 hora, 30 minutos y 45 segundos").
Implemente un escenario de prueba en Gherkin ( belly.feature) que valide que el estómago gruñe o no según estas variaciones de tiempo.
Considere también crear pruebas unitarias con Pytest para la lógica de análisis (función que convierte el texto de tiempo en horas decimales).
En un entorno DevOps :
Agrega la ejecución de behavey pytesten tu tubería de CI/CD, de modo que al hacer push de los cambios se ejecutarán automáticamente las pruebas.
Ejemplo de pepinillo :

Escenario: Comer pepinos y esperar en minutos y segundos
  Dado que he comido 35 pepinos
  Cuando espero "1 hora y 30 minutos y 45 segundos"
  Entonces mi estómago debería gruñir


![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/ejer1.png)
![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/act72.png)
Primero abrimos visual studio y vamos abriendo los codigos dados, para luego seguir trabajando.
## Ejercicio 2: Manejo de cantidades fraccionarias de pepinos
Objetivo

Permitir que el sistema acepte cantidades fraccionarias de pepinos (decimales).
Instrucciones

Modifica el sistema (la clase Bellyy los pasos en Behave) para que acepte entradas como "0.5", "2.75".
Implementa un nuevo escenario en Gherkin donde se ingiera una cantidad fraccionaria y verifica el comportamiento.
Valida que el sistema lanza una excepción o error si se ingresa una cantidad negativa de pepinos.
Pruebas unitarias :
Cubre el caso de pepinos fraccionarios en test_belly.py.
Cubre también el caso de pepinos negativos (se espera un error).
Ejemplo de pepinillo :

Escenario: Comer una cantidad fraccionaria de pepinos
  Dado que he comido 0.5 pepinos
  Cuando espero 2 horas
  Entonces mi estómago no debería gruñir
En un entorno DevOps :

Asegúrese de que la falla (excepción por valor negativo) sea reportada como falla de construcción si ocurre.
Configura notificaciones (por correo/Slack/Teams) si alguna de las pruebas falla.
![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/ee.png)


![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/ff.png)


![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/gg.png)


![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/ejer2.png)
## Ejercicio 3: Soporte para idiomas múltiples (Español e Inglés)
Objetivo

Aceptar descripciones de tiempo en distintos idiomas (español e inglés).
Instrucciones

Modifica el parsing de tiempo para que reconozca palabras clave en inglés, además de español (por ejemplo, "two hours", "thirty minutes").
Escribe al menos dos escenarios de prueba en Gherkin que usan tiempos en inglés.
Implementa una función que convierte las palabras en inglés a valores numéricos (similar a la que se usa para el español).
En un pipeline DevOps , podrías:
Dividir los escenarios en distintas etiquetas ( @spanish, @english) y ejecutar cada conjunto en etapas diferentes, o en paralelo.
Ejemplo de pepinillo :

Escenario: Esperar usando horas en inglés
  Dado que he comido 20 pepinos
  Cuando espero "two hours and thirty minutes"
  Entonces mi estómago debería gruñir
![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/ejer3.png)


![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/4.png)
## Ejercicio 4: Manejo de tiempos aleatorios
Objetivo

Permitir ingresar rangos de tiempo (por ejemplo, "entre 1 y 3 horas") y elegir un tiempo aleatorio dentro de ese rango.
Instrucciones

Crea una función que, dada una expresión como "entre 1 y 3 horas", devuelva un valor aleatorio entre 1 y 3 horas.
Implementa un escenario en Gherkin que verifique que, tras comer pepinos y esperar un tiempo aleatorio, el estómago puede gruñir.
Imprime (en consola o registros) el tiempo aleatorio elegido para que el resultado sea rastreable en tu tubería.
En una canalización de DevOps :
Considere utilizar una semilla de aleatoriedad fija para evitar descamación (pruebas intermitentes).
O, si manejas aleatoriedad real, acepta el riesgo de pruebas no deterministas y monitorea cuidadosamente.
Ejemplo de pepinillo :

Escenario: Comer pepinos y esperar un tiempo aleatorio
  Dado que he comido 25 pepinos
  Cuando espero un tiempo aleatorio entre 1 y 3 horas
  Entonces mi estómago debería gruñir

![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/ejer4.png)


![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/44.png)

![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/5.png)
## Ejercicio 5: Validación de cantidades no válidas
Objetivo

Manejar y reportar adecuadamente errores al ingresar cantidades no válidas.
Instrucciones

Agregue validaciones para evitar que el usuario ingrese < 0 pepinos o > 100 pepinos.
Modifica la lógica para arrojar un error (excepción) si la cantidad no es válida.
Implemente un escenario de prueba que verifique el comportamiento de error.
En tu tubería , verifica que la excepción se maneje y la prueba falle de manera controlada si el sistema no lanza la excepción esperada.
Ejemplo de pepinillo :

Escenario: Manejar una cantidad no válida de pepinos
  Dado que he comido -5 pepinos
  Entonces debería ocurrir un error de cantidad negativa.
![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/ejer5.png)


![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/6.png) 
Se hicieron cambios en los codigos(funciones), para poder cambiar lo pedido. Finalmente nos da 
## Ejercicio 6: Escalabilidad con grandes cantidades de pepinos
Objetivo

Asegurar que el sistema no falle ni se ponga lento con cantidades y tiempos muy grandes.
Instrucciones

Agregue soporte para manejar cantidades de pepinos como 1000 (más allá del límite de validación anterior, o ajusta ese límite para pruebas internas).
Implementa un escenario en Gherkin para comer 1000 pepinos y esperar 10 horas.
Verifique que el sistema sigue comportándose correctamente (sin tiempos de espera ni errores de rendimiento).
En una canalización de DevOps :
Ejecuta pruebas de estrés o de larga duración (puedes simular) para garantizar la robustez.
Mide el tiempo de ejecución para asegurarte de que no aumenten excesivamente.
Ejemplo de pepinillo :

Escenario: Comer 1000 pepinos y esperar 10 horas
  Dado que he comido 1000 pepinos
  Cuando espero 10 horas
  Entonces mi estómago debería gruñir

Hicimos cambios en la funcion gerkhin(agregamos cosas) , depues de eso procedimos a cambiar cosas en el codigo.
![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/ejer6.png)

![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/66.png)


![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/7.png)

## Ejercicio 7: Descripciones de tiempos complejos
Objetivo

Ampliar la lógica para manejar descripciones avanzadas tipo "1 hora, 30 minutos y 45 segundos".
Instrucciones

Refuerza la expresión regular y parsing para que soporte múltiples separadores (comas, "y", espacios, etc.).
Implementa escenarios que cubran al menos 2-3 variaciones complejas en Gherkin.
Valida que el total en horas sea exacto (suma de horas, minutos, segundos).
En un pipeline :
Puedes analizar la cobertura de pruebas (coverage) para asegurarte de que la nueva lógica de parsing está completamente testeada.
Ejemplo de pepinillo :

Escenario: Manejar tiempos complejos
  Dado que he comido 50 pepinos
  Cuando espero "1 hora, 30 minutos y 45 segundos"
  Entonces mi estómago debería gruñir

![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/ejer7.png)


![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/77.png)

![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/8.png)
## Ejercicio 8: De TDD a BDD – Convertir requisitos técnicos a pruebas en Gherkin
Objetivo

Practicar el paso de una prueba unitaria técnica a un escenario BDD comprensible para el negocio.
Instrucciones

Escribe un test unitario básico con Pytest que valide que si se han comido más de 10 pepinos y se espera 2 horas, el estómago gruñe.
Convierte este test unitario en un escenario Gherkin, con la misma lógica, pero más orientado al usuario.
Implementa los pasos en Behave (si no existen).
En una canalización de DevOps :
Ejecuta primero los tests unitarios (rápidos) y luego los tests de Behave (que pueden ser más lentos y de nivel de integración).
Ejemplo de prueba unitaria (TDD):

def test_gruñir_si_comido_muchos_pepinos():
    belly = Belly()
    belly.comer(15)
    belly.esperar(2)
    assert belly.esta_gruñendo() == True
Ejemplo de Gherkin (BDD):

Escenario: Comer muchos pepinos y esperar el tiempo suficiente
  Dado que he comido 15 pepinos
  Cuando espero 2 horas
  Entonces mi estómago debería gruñir
![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/ejer8.png)

![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/88.png)


![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/9.png)
## Ejercicio 9: Identificación de criterios de aceptación para historias de usuario
Objetivo

Traducir una historia de usuario en criterios de aceptación claros y escenarios BDD.
Instrucciones

Toma la historia del usuario:
"Como usuario que ha comido pepinos, quiero saber si mi estómago va a gruñir después de esperar un tiempo suficiente, para poder tomar una acción".

Identifique los criterios de aceptación (por ejemplo, cuántos pepinos y cuánto tiempo se debe esperar).
Escribe escenarios Gherkin que reflejan esos criterios.
Implementa los pasos en Behave.
En un pipeline :
Asegúrate de vincular (por ejemplo, en GitLab Issues o GitHub Issues) los escenarios con la historia de usuario para tener trazabilidad (rastreabilidad).
Ejemplo de escenarios Gherkin :

Escenario: Comer suficientes pepinos y esperar el tiempo adecuado
  Dado que he comido 20 pepinos
  Cuando espero 2 horas
  Entonces mi estómago debería gruñir

Escenario: Comer pocos pepinos y no esperar suficiente tiempo
  Dado que he comido 5 pepinos
  Cuando espero 1 hora
  Entonces mi estómago no debería gruñir
![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/ejer9.png)


## Ejercicio 10: Escribir pruebas unitarias antes de escenarios BDD
Objetivo

Demostrar la secuencia TDD (pruebas unitarias) → BDD (escenarios).
Instrucciones

Escribe una prueba unitaria para una nueva función, por ejemplo, pepinos_comidos()que retorna el total de pepinos ingeridos.
Crea un escenario Gherkin que describe este comportamiento desde el punto de vista del usuario.
Implementa los pasos en Behave y verifica que pase la misma validación.
En un pipeline :
Ejecución secuencial: 1) Pytest, 2) Behave.
O en etapas separadas para una mejor retroalimentación.
Ejemplo de prueba unitaria :

def test_pepinos_restantes():
    belly = Belly()
    belly.comer(15)
    assert belly.pepinos_comidos == 15
Ejemplo de pepinillo :

Escenario: Saber cuántos pepinos he comido
  Dado que he comido 15 pepinos
  Entonces debería haber comido 15 pepinos
![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/ejer10.png)
## Ejercicio 11: Refactorización guiada por TDD y BDD
Objetivo

Refactorizar código existente sin romper funcionalidades, validado por pruebas unitarias y escenarios BDD.
Instrucciones

Elige una funcionalidad ya existente (por ejemplo, esta_gruñendo()).
Escribe (o asegura que existen) pruebas unitarias que cubran los casos clave.
Refactoriza el código ( Bellyo funciones auxiliares) para mejorar la eficiencia, legibilidad o reducir la duplicación.
Valida que todas las pruebas unitarias y escenarios BDD siguen pasando sin cambios.
En un pipeline :
Active la medición de cobertura para asegurarte de que la refactorización no rompa funcionalidades no cubiertas.
Ejemplo de prueba unitaria :

def test_estomago_gruñendo():
    belly = Belly()
    belly.comer(20)
    belly.esperar(2)
    assert belly.esta_gruñendo() == True
Ejemplo de pepinillo :

Escenario: Verificar que el estómago gruñe tras comer suficientes pepinos y esperar
  Dado que he comido 20 pepinos
  Cuando espero 2 horas
  Entonces mi estómago debería gruñir
![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/ejer11.png)


![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/121.png)
![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/111.png)

![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/12b.png)
## Ejercicio 12: Ciclo completo de TDD a BDD – Añadir nueva funcionalidad
Objetivo

Desarrollar una nueva funcionalidad desde cero con TDD (prueba unitaria) y BDD (escenarios Gherkin).
Instrucciones

Imagina una nueva funcionalidad, por ejemplo, "Predecir si el estómago gruñirá con una cantidad dada de pepinos y un tiempo de espera".
Escribe primero la prueba unitaria.
Conviértelo en una historia de usuario y escribe el escenario BDD.
Implementa y verifica que tanto la prueba unitaria como el escenario Gherkin pasen.
En tu tubería , revisa que no haya regresiones en otras pruebas.
Ejemplo de prueba unitaria :

def test_estomago_predecir_gruñido():
    belly = Belly()
    belly.comer(12)
    belly.esperar(1.5)
    assert belly.esta_gruñendo() == True
Ejemplo de pepinillo :

Escenario: Predecir si mi estómago gruñirá tras comer y esperar
  Dado que he comido 12 pepinos
  Cuando espero 1.5 horas
  Entonces mi estómago debería gruñir
![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/ejer12.png)

![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/112.png)

![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/112a.png)


![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/14.png)

  
## Ejercicio 13: Añadir criterios de aceptación claros
Objetivo

Definir con precisión los criterios de aceptación de una nueva funcionalidad y plasmarlos en Gherkin.
Instrucciones

Define una nueva historia de usuario (por ejemplo, "Ver cuántos pepinos me faltan para gruñir").
Identifique al menos 2-3 criterios de aceptación.
Convierte esos criterios en escenarios BDD.
Implementa los pasos.
En un pipeline , agrupa los escenarios bajo una misma etiqueta ( @criterio_nuevo) para ejecutarlos juntos.
Ejemplo :

Escenario: Ver cuántos pepinos puedo comer antes de que el estómago gruña
  Dado que he comido 8 pepinos
  Cuando pregunto cuántos pepinos más puedo comer
  Entonces debería decirme que puedo comer 2 pepinos más



![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/ejer13.png)


![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/113.png)

![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/113a.png)


![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/14b.png)
## Ejercicio 14: Integración con Mocking, Stubs y Fakes (para DevOps)
Objetivo

Demostrar cómo inyectar dependencias simuladas en tu clase Bellyy usarlas en pruebas BDD y TDD.
Instrucciones

Crea un archivo clock.py(por ejemplo) con una función get_current_time().
Modifica Belly para aceptar un clock_serviceopcional que se inyecta.
Crea un test unitario con Pytest que usa unittest.mockpara simular el paso del tiempo.
En Behave , usa environment.pypara inyectar un simulacro o trozo del reloj en el before_scenario.
En una canalización de DevOps :
Asegúrese de no depender de la hora real, así evitará la inestabilidad en las pruebas.
Ejemplo :

def before_scenario(context, scenario):
    from unittest.mock import MagicMock
    from src.belly import Belly
    
    fake_clock = MagicMock()
    fake_clock.return_value = 10000  # tiempo fijo
    context.belly = Belly(clock_service=fake_clock)
![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/114.png)


![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/114a.png)
## Ejercicio 15: Despliegue y validación continua en un entorno de integración (CI/CD)
Objetivo

Completar el ciclo DevOps: Cada push al repositorio desencadena pruebas automáticas BDD y TDD.
Instrucciones

Configura un pipeline (por ejemplo, en GitHub Actions o GitLab CI) con estos pasos:
Instalar dependencias (Python, Behave, Pytest).
Ejecutar pruebas unitarias (Pytest).
Ejecutar pruebas de comportamiento (Behave).
Generar informes (HTML, JUnit) y publicarlos como artefactos .
Incluye verificación de calidad de código (por ejemplo, flake8 o black).
Al aprobarse el pipeline, despliega (si corresponde) tu aplicación o script a un entorno de staging/producción.

![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/16.png)

![dgdg](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo7/img/115.png)




