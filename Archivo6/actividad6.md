# Git, Scrum y Sprints
## Fase 1: Planificación del sprint (planificación del sprint)
## Ejercicio 1: Crear ramas de funcionalidades

![u](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo6/img/Fase1.png)
### Pregunta: ¿Por qué es importante trabajar en ramas de funcionalidades separadas durante un sprint?
Trabajar en ramas independientes permite que cada desarrollador avance en su funcionalidad sin interferir con el trabajo de los demás. Esto fomenta la autonomía, reduce conflictos y facilita la integración de código más limpia al final del sprint.
## Fase 2: Desarrollo del sprint (ejecución del sprint)




### Pregunta: ¿Qué ventajas proporciona el rebase durante el desarrollo de un sprint en términos de integración continua?
El rebase ayuda a mantener una historia de commits más lineal y coherente. Esto facilita el trabajo en equipo, reduce los conflictos de integración y hace más claro el flujo de cambios cuando otros revisan el historial. También es ideal para detectar problemas antes de integrarlos a la rama principal.
![u](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo6/img/ejercico2.png)

## Fase 3: Revisión del sprint (sprint review)
## Ejercicio 3: Integración selectiva con git cherry-pick




### Pregunta: ¿Cómo ayuda git cherry-picka mostrar avances de forma selectiva en un sprint review?
Permite seleccionar solo los commits que realmente queremos mostrar, sin tener que fusionar una rama completa. Es útil cuando algunas funcionalidades aún están en progreso o tienen errores. De esta manera, presentamos únicamente lo que está listo y aprobado.


![u](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo6/img/ejercicio3.png)
![u](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo6/img/fase3a.png)
![u](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo6/img/ejercicio3b.png)

## Fase 4: Retrospectiva del sprint
## Ejercicio 4: Revisión de conflictos y resolución


### Pregunta: ¿Cómo manejas los conflictos de fusión al final de un sprint? ¿Cómo puede el equipo mejorar la comunicación para evitar conflictos grandes?
Detectarlos temprano: hacer git fetch y merge o rebase de forma habitual ayuda a anticiparlos.Usar herramientas de ayuda visual como git mergetool o editores modernos que muestren los cambios claramente.Consultar al autor del código en caso de dudas.
### Pregunta : ¿Cómo manejas los conflictos de fusión al final de un sprint? ¿Cómo puede el equipo mejorar la comunicación para evitar conflictos grandes? 
Hacer merges frecuentes desde main o develop para mantener el código actualizado.Tener sincronizaciones diarias rápidas para comentar en qué archivos está trabajando cada persona.Establecer zonas o módulos de responsabilidad clara dentro del proyecto.Documentar y etiquetar bien los PRs.Revisar código anticipadamente para prever colisiones antes de que sean un problema.

![u](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo6/img/fase4c.png)

![u](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo6/img/fase4d.png)


![u](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo6/img/fase4e.png)

![u](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo6/img/fase4f.png)


![u](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo6/img/fase4g.png)

## Fase 5: Fase de desarrollo, automatización de integración continua (CI) con git rebase

## Ejercicio 5: Automatización de rebase con hooks de Git

### Pregunta: ¿Qué ventajas y desventajas observas al automatizar el rebase en un entorno de CI/CD?
* Ventajas:
Mantiene una historia de commits limpia, sin merges innecesarios.Facilita entender la evolución del código y seguir qué se hizo en cada paso.Permite detectar conflictos temprano, antes del mergeMejora herramientas como git bisect para rastrear errores.Evita que los desarrolladores tengan que hacer el rebase manualmente.


* Desventajas:
Riesgo de sobrescribir historial compartido y Conflictos automáticos sin intervención humana. Si el rebase automático se ejecuta sobre ramas que ya están en uso colaborativo, puede causar conflictos o pérdida de trabajo si no se maneja bien.



![u](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo6/img/fase5a.png)

![u](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo6/img/fase5b.png)

![u](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo6/img/fase5c.png)

# Preguntas 
## 1. Ejercicio para git checkout --ours y git checkout --theirs

## Contexto :
En un sprint ágil, dos equipos están trabajando en diferentes ramas. Se produce un conflicto de fusión en un archivo de configuración crucial. El equipo A quiere mantener sus cambios mientras el equipo B solo quiere conservar los suyos. El proceso de entrega continúa está detenido debido a este conflicto.

## Pregunta :
¿Cómo utilizarías los comandos git checkout --ours y git checkout --theirs para resolver este conflicto de manera rápida y eficiente? Explique cuándo preferiría usar cada uno de estos comandos y cómo impacta en la tubería de CI/CD. ¿Cómo te asegurarías de que la resolución elegida no comprometa la calidad del código?

git checkout --ours, la usaria aplicar la versiondesde la misma rama actual.Portanto la usaria cuando confías en que los cambios locales son los correctos (por ejemplo, el equipo A quiere conservar sus cambios).

git checkout --theirs, aplica la versión del archivo desde la rama que se está fusionando.por lo tanto yo la usaria  si prefieres los cambios entrantes (por ejemplo, el equipo B.

Impacto en CI/CD: 
Ejecutar pruebas automáticas después de resolver el conflicto.

Revisar manualmente los archivos afectados.

Hacer code review colaborativo si es un archivo crítico.



## 2. Ejercicio para git diff

## Contexto : 
Durante una revisión de código en un entorno ágil, se observa que un pull request tiene una gran cantidad de cambios, muchos de los cuales no están relacionados con la funcionalidad principal. Estos cambios podrían generar conflictos con otras ramas en la tubería de CI/CD.

## Pregunta :
Utilizando el comando git diff, ¿cómo compararías los cambios entre ramas para identificar diferencias específicas en archivos críticos? Explique cómo podría utilizar git diff feature-branch..mainpara detectar posibles conflictos antes de realizar una fusión y cómo esto contribuye a mantener la estabilidad en un entorno ágil con CI/CD.
Con git diff feature-branch..main puedes ver las diferencias entre dos ramas. Es muy útil para saber qué ha cambiado antes de hacer un merge.

¡Comose evitan conflictos? 
Revisa los archivos importantes antes de combinar.
Detecta líneas que se pisan entre ramas.

## 3.Ejercicio para git merge --no-commit --no-ff

Contexto : En un proyecto ágil con CI/CD, tu equipo quiere simular una fusión entre una rama de desarrollo y la rama principal para ver cómo se comporta el código sin comprometerlo inmediatamente en el repositorio. Esto es útil para identificar posibles problemas antes de completar la fusión.
Aporte al CI/CD:
Previene errores antes de que el código entre en producción. También ayuda a enfocarte en lo importante durante las revisiones. 
## Pregunta :
Describe cómo usarías el comando git merge --no-commit --no-ffpara simular una fusión en tu rama local. ¿Qué ventajas tiene esta práctica en un flujo de trabajo ágil con CI/CD, y cómo ayuda a minimizar errores antes de hacer commits definitivos? ¿Cómo automatizarías este paso dentro de una tubería CI/CD?

Este comando (git merge --no-commit --no-ff rama) te deja hacer una fusión "en pausa": no se hace commit ni se aplana el historial. Es ideal para revisar antes de confirmar.
Con esto se puede : Puedes correr pruebas y ver qué pasó, evitar errores antes de que toquen el repositorio.
Para la CI/CD:
 Añade una etapa que pruebe la fusión antes de hacer commit.

Usa scripts para automatizar: merge → test → commit solo si todo va bien.




## 4.Ejercicio para git mergetool

## Contexto :
Tu equipo de desarrollo utiliza herramientas gráficas para resolver conflictos de manera colaborativa. Algunos desarrolladores prefieren herramientas como vimdiff o Visual Studio Code. En medio de un sprint, varios archivos están en conflicto y los desarrolladores prefieren trabajar en un entorno visual para resolverlos.

## Pregunta :
Explique cómo configurarías y utilizarías git mergetoolen tu equipo para integrar herramientas gráficas que faciliten la resolución de conflictos. ¿Qué impacto tiene el uso de git mergetoolen un entorno de trabajo ágil con CI/CD, y cómo aseguras que todos los miembros del equipo mantengan consistencia en las resoluciones?
git mergetool abre una app visual para resolver conflictos más cómodamente.

Lo configuraria con git congfig --global merge.tool vscode
Beneficios:
Resuelve conflictos en equipo, de forma visual.

Menos posibilidad de errores humanos.
Pa tener todo ordenado:  Documenta las herramientas preferidas, Comparte una configuración común con .gitattributes y gitconfig.

## 5.Ejercicio para git reset

## Contexto : 
En un proyecto ágil, un desarrollador ha hecho un compromiso que rompe la tubería de CI/CD. Se debe revertir el commit, pero se necesita hacerlo de manera que se mantenga el código en el directorio de trabajo sin deshacer los cambios.

## Pregunta :
Explique las diferencias entre git reset --soft, git reset --mixedy git reset --hard. ¿En qué escenarios dentro de un flujo de trabajo ágil con CI/CD utilizaría cada uno? Describe un caso en el que usarías git reset --mixedpara corregir un commit sin perder los cambios no commiteados y cómo afecta esto a la tubería.

--soft: mueve el puntero, pero mantiene staging y cambios.

--mixed: deshace el staging, pero conserva tus archivos.

--hard: borra  todo (¡cuidado!).
Uso practico: Si haces un commit que rompe algo en la pipeline.
git reset --mixed HEAD~1
Impacto: 

Arreglas rápido sin tener que rehacer todo.

Reduces el tiempo muerto de la integración continua.


## 6.Ejercicio para git revert

## Contexto : 
En un entorno de CI/CD, su equipo ha desplegado una característica de producción, pero ha detectado un error crítico. La rama principal debe revertirse para restaurar la estabilidad, pero no puedes modificar el historial de commits debido a las políticas del equipo.

## Pregunta :
Explica cómo utilizarías git revertpara deshacer los cambios sin modificar el historial de confirmaciones. ¿Cómo te aseguras de que esta acción no afecta la tubería de CI/CD y permite una rápida recuperación del sistema? Proporciona un ejemplo detallado de cómo revertirías varios compromisos consecutivos.

crea un nuevo commit que deshace uno anterior, sin modificar el historial.

En CI/CD:

El historial sigue limpio.

Ideal para entornos donde no se permite reescribir historial.

Si quiero revertir vario commits: 
git revert HEAD~3..HEAD(borra 3 ultimos commits).




## 7.Ejercicio para git stash

## Contexto :
En un entorno ágil, tu equipo está trabajando en una corrección de errores urgente mientras tienes cambios no guardados en tu directorio de trabajo que aún no están listos para ser comprometidos. Sin embargo, necesitas cambiar rápidamente a una rama de hotfix para trabajar en la corrección.

## Pregunta :
Explica cómo utilizarías git stashpara guardar temporalmente tus cambios y volver a ellos después de haber terminado el hotfix. ¿Qué impacto tiene el uso de git stashen un flujo de trabajo ágil con CI/CD cuando trabajas en múltiples tareas? ¿Cómo podrías automatizar el proceso de stashing dentro de una tubería CI/CD?

git stash guarda tus cambios pendientes, como si los metieras en una caja temporal. Luego puedes cambiar de rama sin perder nada. Después los recuperas con git stash pop.

¿Cómo ayuda en CI/CD?

Si hay una urgencia, como un hotfix, puedes pausar tu trabajo sin perderlo.

Automatización posible: 

git stash
( cambiar de rama)
git stash pop  # recuperar cambios

## 8.Ejercicio para .gitignore

## Contexto : 
Tu equipo de desarrollo ágil está trabajando en varios entornos locales con configuraciones diferentes (archivos de registros, configuraciones personales). Estos archivos no deben ser parte del control de versiones para evitar confusiones en la tubería de CI/CD.

## Pregunta :
Diseña un archivo .gitignoreque excluye archivos innecesarios en un entorno ágil de desarrollo. Explique por qué es importante mantener este archivo actualizado en un equipo colaborativo que utiliza CI/CD y cómo afecta la calidad y limpieza del código compartido en el repositorio.


Es importante porque no subes archivos personales que nadie necesita.

Evitas errores en la CI/CD por archivos de tu máquina.

Mejora general:

Historial limpio, menos conflictos por cosas que no deberían estar en el repo.

 
## Ejercicios adicionales
### Ejercicio 1: Resolución de conflictos en un entorno ágil
## Contexto:
Estás trabajando en un proyecto ágil donde múltiples desarrolladores están enviando cambios a la rama principal cada día. Durante una integración continua, se detectan conflictos de fusión entre las ramas de dos equipos que están trabajando en dos funcionalidades críticas. Ambos equipos han modificado el mismo archivo de configuración del proyecto.
## Pregunta:

¿Cómo gestionarías la resolución de este conflicto de manera eficiente utilizando Git y manteniendo la entrega continua sin interrupciones? ¿Qué pasos seguirías para minimizar el impacto en la CI/CD y asegurar que el código final sea estable?

Usa git fetch para tener lo último, Crea una rama temporal para arreglar el conflicto, haz el merge y usa git mergetool si es necesario, corre pruebas, si todo va bien, haz commit y push.

### Ejercicio 2: Rebase vs. Merge en integraciones ágiles
## Contexto:
En tu equipo de desarrollo ágil, cada sprint incluye la integración de varias ramas de características. Algunos miembros del equipo prefieren realizar merge para mantener el historial completo de confirmaciones, mientras que otros prefieren rebase para mantener un historial lineal.

## Pregunta:

¿Qué ventajas y desventajas presenta cada enfoque (merge vs. rebase) en el contexto de la metodología ágil? ¿Cómo impacta esto en la revisión de código, CI/CD, y en la identificación rápida de errores?

Merge

(bien) Mantiene todo el historial.

(mal)A veces genera muchos commits extra y ruido.

Rebase

 (bien)Historial limpio, más lineal.

 (mal)Reescribe historial (ten cuidado si ya compartiste la rama).

En la práctica CI/CD:

Merge conserva el contexto y es ideal para revisión.

Rebase hace más clara la línea del tiempo del proyecto.





## Ejercicio 3: Git Hooks en un flujo de trabajo CI/CD ágil
## Contexto:
Tu equipo está utilizando Git y una tubería de CI/CD que incluye pruebas unitarias, integración continua y despliegues automatizados. Sin embargo, algunos desarrolladores comiten accidentalmente códigos que no pasan las pruebas locales o no siguen las convenciones de estilo definidas por el equipo.

## Pregunta:

Diseña un conjunto de Git Hooks que ayudará a mitigar estos problemas, integrando validaciones de estilo y pruebas automáticas antes de permitir los commits. Explique qué tipo de validaciones implementarías y cómo se relaciona esto con la calidad del código y la entrega continua en un entorno ágil.


permiten ejecutar acciones automaticamente
ALugunos sosn:
pre-commit: correr linters o tests antes de cada commit.

commit-msg: validar el formato del mensaje.

pre-push: ejecutar tests antes de hacer push.

Ejemplo de pre-commit:

#!/bin/sh
npm run lint
npm test || exit 1

Aporte a CI/CD:

Detectas errores antes de subir código.

Mejora la calidad desde el primer paso. 





## Ejercicio 4: Estrategias de ramificación en metodologías ágiles
## Contexto:
Tu equipo de desarrollo sigue una metodología ágil y está utilizando Git Flow para gestionar el ciclo de vida de las ramas. Sin embargo, a medida que el equipo ha crecido, la gestión de las ramas se ha vuelto más compleja, lo que ha provocado retrasos en la integración y conflictos de fusión frecuentes.

## Pregunta:

Explica cómo adaptarías o modificarías la estrategia de ramificación para optimizar el flujo de trabajo del equipo en un entorno ágil y con integración continua. Considere cómo podrían integrar ramas de características, ramas de lanzamiento y ramas de revisión de manera que apoyen la entrega continua y minimicen conflictos.
Consejos prácticos:

No mantengas ramas vivas por semanas.

Usa feature flags para probar cosas sin romper producción.

Considera trunk-based development para flujos más simples.

En la pipeline:

Automatiza los merges a develop y main con validaciones.

Exige revisiones de código con pull requests.

 


## Ejercicio 5: Automatización de reversiones con git en CI/CD
## Contexto:
Durante una integración continua en tu pipeline de CI/CD, se detecta un error crítico después de haber fusionado varios commits a la rama principal. El equipo necesita revertir los cambios rápidamente para mantener la estabilidad del sistema.

## Pregunta:

¿Cómo diseñarías un proceso automatizado con Git y CI/CD que permita revertir cambios de manera eficiente y segura? Describe cómo podrías integrar comandos como git reverto git reseten la tubería y cuáles serían los pasos para garantizar que los errores se reviertan sin afectar el desarrollo en curso.
¿Qué hacer si algo falla?

Deja que los tests automáticos detecten el error.

Usa un script que haga git revert de los últimos commits.

Crea un pull request con esos cambios.

Ejemplo de script:

git revert HEAD~2..HEAD --no-edit
git push origin HEAD:revert-fix

¿Por qué es útil?

Respuesta rápida.

No interrumpe a todo el equipo.

Queda todo documentado y rastreable.





