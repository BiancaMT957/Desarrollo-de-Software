# Actividad: Exploración y administración avanzada de Git mediante un script interactivo

### Materiales necesarios
Un entorno de terminal (Linux, macOS o Windows con Git Bash).
Un repositorio Git (puede ser uno de prueba).
El guión interactivo (por ejemplo, git_avanzado.sh).
Puedes revisar una versión del script interactivo aquí .

### Instrucciones previas
### Descarga y mira el script:

Copia el contenido del script proporcionado (el ejemplo extendido) y guárdalo en un archivo llamado git_avanzado.sh.
### Asignar permisos de ejecución:

Abra la terminal en el directorio donde guarde el archivo y ejecute:
chmod +x git_avanzado.sh
### Ubicación:

Asegúrese de ejecutar el script dentro de la raíz de un repositorio Git, ya que el script interactúa con el entorno Git. 
# Procedimiento de la actividad

![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejemplosdir22.png)

Se procede a ver las ramas existentes, las que se crearon en otros trabajos


![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejemplosdir2.png)

Se pudo abrir el archivo que contiene un menu interactivo, esta en lenguaje Bash.

![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejemplosdir234.png)

Se ve la opcion de gestion de ramas

![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejemplosdir45.png)


Se io la diferencia entre las ramas "perrito" y feature/login"

# Preguntas

## ¿Qué diferencias observas en el historial del repositorio después de restaurar un commit mediante reflog?

El reflog actúa como una especie de "historial secreto" que registra todos los movimientos del puntero HEAD, incluso si un commit fue eliminado o sobrescrito. Al restaurar un commit desde ahí, el historial visible no se borra, pero pueden aparecer ramas "fantasma" o estados antiguos que si no se gestionan bien pueden causar confusión. Sin embargo, es una herramienta valiosa para recuperar trabajo perdido sin perder la trazabilidad.

## ¿Cuáles son las ventajas y desventajas de utilizar submódulos en comparación con subárboles?

Submódulos:

 Permiten mantener repositorios completamente independientes, ideal si el proyecto externo se desarrolla por separado.

 Requieren comandos adicionales para clonar y actualizar, lo que puede complicar el flujo.

Subárboles:

 Son más fáciles de manejar para equipos pequeños, ya que se integran de forma más transparente.

 Menos flexibilidad si necesitas mantener separados los historiales o colaborar en el proyecto externo.
## ¿Cómo impacta la creación y gestión de ganchos en el flujo de trabajo y la calidad del código?
Implementar hooks mejora el flujo de trabajo automatizando tareas como linters, validación de commits y ejecución de pruebas. Esto permite detectar errores antes de que lleguen al repositorio remoto, fomentando calidad desde el origen. Sin embargo, si no se configuran adecuadamente, pueden ser molestos o incluso bloquear el trabajo, especialmente para quienes no entienden qué está fallando.

## ¿De qué manera el uso git bisectpuede acelerar la localización de un error introducido recientemente?

permite identificar rápidamente el commit que introdujo un error usando búsqueda binaria. En vez de revisar manualmente muchos commits, divide el historial en mitades, probando hasta encontrar el punto exacto. En grandes repositorios, esto puede reducir horas de investigación a minutos.

## ¿Qué desafíos podrían enfrentar al administrar ramas y alijos en un proyecto con múltiples colaboradores?
Al aplicar un stash, pueden aparecer conflictos si el código base cambió demasiado. Si los nombres de ramas no son claros o se usan convenciones distintas, puede haber confusión o errores. Los stash son volátiles: si alguien se olvida de aplicar uno o lo sobrescribe, se puede perder trabajo. La falta de comunicación puede llevar a que dos personas trabajen en lo mismo sin saberlo, o a sobrescribir avances ajenos.

## Ejercicios 
### 1 . Extiende el menú de gestión de ramas para incluir la funcionalidad de renombrar ramas

![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejer1b.png)


Se entra al archivo y se agrega en el menu principal y en el codigo, una nuev opción


![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejerc1c.png)


"cat" se cambio a "pet"


### 2 . Amplia la sección de "Gestión de git diff" para permitir ver las diferencias de un archivo específico entre dos commits o ramas.


![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejer2a.png)

Ahora se pueden compara diferencias entre un archivo especifico, esto se logro porque se agrego algo nuevo en la seccion de Git Diff.

![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejer2b.png)


"desarrollo" y "funcion_x"

### 3 . Crea una función que permita instalar automáticamente un gancho que, por ejemplo, verifique si se han agregado comentarios de documentación en cada confirmación.

![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejercicio3.png)

![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejercicio3a.png)


![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejercicio3b.png)


![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejercicio3c.png)


### 4.  Implemente una opción en el script que realiza una fusión automática de una rama determinada en la rama actual, incluyendo la resolución automática de conflictos (siempre que sea posible).

![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejercicio4a.png)



![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejercicio4b.png)


![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejercicio4c.png)



### 5.  Implemente una opción en el script que genere un reporte con información relevante del repositorio (estado, ramas, últimas confirmaciones, stashes, etc.) y lo guarde en un archivo.


![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejer5a.png)

Se crea una nueva fucnion en el menu desde el Sscript


![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejerc5b.png)


Se aprecian todas las ramas trabajadas

![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejerc5c.png)

Se ven los ultimos 5 commits

![o](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Practicadirigida2/img/ejerc5d.png)



