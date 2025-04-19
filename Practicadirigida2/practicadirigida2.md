Actividad: Exploración y administración avanzada de Git mediante un script interactivo
Materiales necesarios
Un entorno de terminal (Linux, macOS o Windows con Git Bash).
Un repositorio Git (puede ser uno de prueba).
El guión interactivo (por ejemplo, git_avanzado.sh).
Puedes revisar una versión del script interactivo aquí .

Instrucciones previas
Descarga y mira el script:

Copia el contenido del script proporcionado (el ejemplo extendido) y guárdalo en un archivo llamado git_avanzado.sh.
Asignar permisos de ejecución:

Abra la terminal en el directorio donde guarde el archivo y ejecute:
chmod +x git_avanzado.sh
Ubicación:

Asegúrese de ejecutar el script dentro de la raíz de un repositorio Git, ya que el script interactúa con el entorno Git.
Procedimiento de la actividad
A continuación se muestra un ejemplo de uso que ilustra una sesión interactiva con el guión. Este ejemplo simula cómo un usuario podría interactuar con algunas de las opciones del menú. Recuerde que, al ejecutarlo, verá mensajes en tiempo real en la terminal y deberá ingresar las opciones y datos solicitados.

Inicio del script

Tras darle permisos de ejecución y ejecutar el script desde la raíz de un repositorio Git, se muestra el siguiente menú en la terminal:

====== Menú avanzado de Git ======
1) Listar reflog y restaurar un commit
2) Agregar un submódulo
3) Agregar un subtree
4) Gestión de ramas
5) Gestión de stashes
6) Mostrar estado y últimos commits
7) Gestión de tags
8) Gestión de Git Bisect
9) Gestión de Git Diff
10) Gestión de Hooks
11) Salir
Seleccione una opción:
Opción: agregar un submódulo (Opción 2)

Usuario: Ingresa 2y presiona Enter.
El guión pide:
Ingrese la URL del repositorio para el submódulo:
Usuario: Escribe, por ejemplo:
https://github.com/usuario/repositorio-submodulo.git
El script solicita:
Ingrese el directorio donde se ubicará el submódulo:
Usuario: Escribe, por ejemplo:
libs/submodulo
Guión: Ejecuta:
git submodule add https://github.com/usuario/repositorio-submodulo.git libs/submodulo
git submodule update --init --recursive
Salida esperada:
El mensaje confirmando que el submódulo ha sido agregado:
Submódulo agregado en: libs/submodulo
Opción: Gestión de ramas (Opción 4)

Usuario: Regrese al menú principal y seleccione la opción 4.
El script despliega un submenú:
=== Gestión de Ramas ===
a) Listar ramas
b) Crear nueva rama y cambiar a ella
c) Cambiar a una rama existente
d) Borrar una rama
e) Volver al menú principal
Seleccione una opción:
Ejemplo A: Listar ramas (Opción a)
Usuario: Ingresa ay presiona Enter.
Guión: Ejecuta git branchy muestra la lista de ramas:
  master
* feature/nueva-funcionalidad
Ejemplo B: Crear una nueva rama (Opción b)
Usuario: Ingresa b, luego la pregunta del script:
Ingrese el nombre de la nueva rama:
Usuario: Escribe feature/login.
Script: Ejecuta git checkout -b feature/loginy confirma:
Rama 'feature/login' creada y activada.
Opción: Gestión de git diff (Opción 9)

Usuario: Selecciona la opción 9del menú principal.
El submenú de diferencias se muestra:
=== Gestión de git diff ===
a) Mostrar diferencias entre el working tree y el área de staging (git diff)
b) Mostrar diferencias entre el área de staging y el último commit (git diff --cached)
c) Comparar diferencias entre dos ramas o commits
d) Volver al menú principal
Seleccione una opción:
Ejemplo:
Usuario: Ingresa cpara comparar dos revisiones.
El guión solicitado:
Ingrese el primer identificador (rama o commit):
Usuario: Escribe master.
El guión luego pregunta:
Ingrese el segundo identificador (rama o commit):
Usuario: Escribe feature/login.
Guión: Ejecuta git diff master feature/loginy muestra las diferencias entre ambas ramas en la terminal.
Opción: Gestión de ganchos (Opción 10)

Usuario: Elija la opción 10para gestionar ganchos.
Se despliega el submenú de ganchos:
=== Gestión de hooks ===
a) Listar hooks disponibles
b) Crear/instalar un hook (ej. pre-commit)
c) Editar un hook existente
d) Borrar un hook
e) Volver al menú principal
Seleccione una opción:
Ejemplo: Crear un gancho de confirmación previa.
Usuario: Ingresa b.
La pregunta del guión:
Ingrese el nombre del hook a instalar (por ejemplo, pre-commit):
Usuario: Escribe pre-commit.
Luego el script solicita:
Ingrese el contenido del hook (una línea, se agregará '#!/bin/bash' al inicio):
Usuario: Escribe una línea, por ejemplo: echo "Ejecutando pre-commit hook..." && exit 0
Script: Crea el archivo .git/hooks/pre-commit, lo hace ejecutable y confirma:
Hook 'pre-commit' instalado.
Finalizar la sesión

Usuario: Cuando termine de utilizar las opciones deseadas, regresa al menú principal y selecciona 11para salir:
Saliendo del script.
Preguntas
¿Qué diferencias observas en el historial del repositorio después de restaurar un commit mediante reflog?
¿Cuáles son las ventajas y desventajas de utilizar submódulos en comparación con subárboles?
¿Cómo impacta la creación y gestión de ganchos en el flujo de trabajo y la calidad del código?
¿De qué manera el uso git bisectpuede acelerar la localización de un error introducido recientemente?
¿Qué desafíos podrían enfrentar al administrar ramas y alijos en un proyecto con múltiples colaboradores?
