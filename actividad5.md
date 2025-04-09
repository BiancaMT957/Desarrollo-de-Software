
## 1 ) Clona un repositorio Git con múltiples ramas.
Bianca@MSI MINGW64 ~
$ cd C:/Users/Bianca/Documents/repositorio/activity-5


Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5 (main)
$ mkdir prueba-fast-forward-merge

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5 (main)
$ cd prueba-fast-forward-merge/

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-fast-forward-merge (main)
$ git init
Initialized empty Git repository in C:/Users/Bianca/Documents/repositorio/activity-5/prueba-fast-forward-merge/.git/

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-fast-forward-merge (master)
$ echo "#mi proyecto" > README.md

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-fast-forward-merge (master)
$ git add README.md
warning: in the working copy of 'README.md', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-fast-forward-merge (master)
$ git commit -m"commit inicial en main"
[master (root-commit) 24298e2] commit inicial en main
 1 file changed, 1 insertion(+)
 create mode 100644 README.md

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-fast-forward-merge (master)
$ git checkout -b add-description
Switched to a new branch 'add-description'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-fast-forward-merge (add-description)
$ echo "este proyecto es un ejemplo de como usar Git." >> README.md

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-fast-forward-merge (add-description)
$ git add README.md
warning: in the working copy of 'README.md', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-fast-forward-merge (add-description)
$ git commit -m "agregar descripcion al README.md"
[add-description 707a811] agregar descripcion al README.md
 1 file changed, 1 insertion(+)

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-fast-forward-merge (add-description)
$ git checkout main
error: pathspec 'main' did not match any file(s) known to git

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-fast-forward-merge (add-description)
$ git merge add-description
Already up to date.

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-fast-forward-merge (add-description)
$ git checkout master
Switched to branch 'master'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-fast-forward-merge (master)
$ git merge add-description
Updating 24298e2..707a811
Fast-forward
 README.md | 1 +
 1 file changed, 1 insertion(+)

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-fast-forward-merge (master)
$ git log --graph --oneline
* 707a811 (HEAD -> master, add-description) agregar descripcion al README.md
* 24298e2 commit inicial en main
## Comentario: Primero se creo una carpeta y luego se fue a esa carpeta, que tiene el nombre del problema, luego de eso se agrego un readme en la rama "master", depsues se creo y cambio a otra rama y se hicieron cambios en esa rama(agrego readme). Al finalse hizo el merge fast foward a la rama nueva creaday al final se pudoa preciar eso.
## ¿En qué situaciones recomendaría evitar el uso de git merge --ff? Reflexiona sobre las desventajas de este método.
cuando uno quiere tener un historial vacio no es recomendable usarlo.
Pienso que seria mejor usar otras alternativas como --no-ff o git merge, dependiendo de lo que quiera uno.Es mejor esto a arriesgarse a contaminar el historial de rama de funciones.
# 2 ) Simula un flujo de trabajo de equipo.

$ cd ..

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5 (main)
$ mkdir prueba-no-fast-forward-merge

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5 (main)
$ cd prueba-no-fast-forward-merge/
Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-no-fast-forward-merge (main)
$ git init
Initialized empty Git repository in C:/Users/Bianca/Documents/repositorio/activity-5/prueba-no-fast-forward-merge/.git/

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-no-fast-forward-merge (master)
$ echo "#Mi proyecto" > README.md

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-no-fast-forward-merge (master)
$ git add README.md
warning: in the working copy of 'README.md', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-no-fast-forward-merge (master)
$ git commit -m"commit inicial en main"
[master (root-commit) 91bfe6f] commit inicial en main
 1 file changed, 1 insertion(+)
 create mode 100644 README.md

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-no-fast-forward-merge (master)
$ git reset --hard HEAD~1
fatal: ambiguous argument 'HEAD~1': unknown revision or path not in the working tree.
Use '--' to separate paths from revisions, like this:
'git <command> [<revision>...] -- [<file>...]'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-no-fast-forward-merge (master)
$ git branch -m main

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-no-fast-forward-merge (main)
$ git init
Reinitialized existing Git repository in C:/Users/Bianca/Documents/repositorio/activity-5/prueba-no-fast-forward-merge/.git/

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-no-fast-forward-merge (main)
$ echo "#mi proyecto" > README.md

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-no-fast-forward-merge (main)
$ git add README.md
warning: in the working copy of 'README.md', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-no-fast-forward-merge (main)
$ git commit -m"commit inicial en main"
[main 558fe9c] commit inicial en main
 1 file changed, 1 insertion(+), 1 deletion(-)

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-no-fast-forward-merge (main)
$ git checkout -b add-feature
Switched to a new branch 'add-feature'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-no-fast-forward-merge (add-feature)
$ echo "implementando una nueva caracteristica..." >> README.md

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-no-fast-forward-merge (add-feature)
$ git add README.md
warning: in the working copy of 'README.md', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-no-fast-forward-merge (add-feature)
$ git commit -m"Implementar una nueva caracteristica"
[add-feature b20ae2d] Implementar una nueva caracteristica
 1 file changed, 1 insertion(+)

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-no-fast-forward-merge (add-feature)
$ git checkout main
Switched to branch 'main'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-no-fast-forward-merge (main)
$ git merge --no-ff add-feature
Merge made by the 'ort' strategy.
 README.md | 1 +
 1 file changed, 1 insertion(+)
$ git log --graph --oneline
*   d8b4955 (HEAD -> main) Merge branch 'add-feature'
|\
| * b20ae2d (add-feature) Implementar una nueva caracteristica
|/
* 558fe9c commit inicial en main
* 91bfe6f commit inicial en main
## tuve que cambiar el nombre de la rama "master" a "main", para hacerlo mas practico. Se creo una nueva rama "add-feature" y se le añadieron cosas, despues se uso el comando "git merge --no-ff add-feature" para hacer la fusion no fast foward.
## Pregunta: ¿Cuáles son las principales ventajas de utilizar git merge --no-ffen un proyecto en equipo? ¿Qué problemas podrían surgir al depender excesivamente de commits de fusión?
Facilita una colaboracion entre equipos de desarrollo, nos da el historial conservado completo, resuelve conflictos de manera sencilla, integra correciones dentro del mismo proyecto.
Uno de los problemas que podriamos tener al usar estos commits seria el de tener un grafico desordenado.

 
# 3  ) Crea múltiples commits en una rama.
$ cd ..

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5 (main)
$ mkdir prueba-squash-merge

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5 (main)
$ cd prueba-squash-merge

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (main)
$ git init
Initialized empty Git repository in C:/Users/Bianca/Documents/repositorio/activity-5/prueba-squash-merge/.git/

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (master)
$ echo "#Mi proyecto" > README.md

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (master)
$ git add README.md
warning: in the working copy of 'README.md', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (master)
$ git commit -m"commit inicial en main"
[master (root-commit) 9bcc9df] commit inicial en main
 1 file changed, 1 insertion(+)
 create mode 100644 README.md

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (master)
$ git checkout -b add-basic-files
Switched to a new branch 'add-basic-files'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (add-basic-files)
$ echo "#COMO CONTRIBUIR" >> CONTRIBUTING.md

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (add-basic-files)
$ git add CONTRIBUTING.md
warning: in the working copy of 'CONTRIBUTING.md', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (add-basic-files)
$ git commit -m "Agregar CONTRIBUTING.md"
[add-basic-files 0cf4f75] Agregar CONTRIBUTING.md
 1 file changed, 1 insertion(+)
 create mode 100644 CONTRIBUTING.md

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (add-basic-files)
$ echo "#LICENCIA" >> LICENSE.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (add-basic-files)
$ git add LICENSE.txt
warning: in the working copy of 'LICENSE.txt', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (add-basic-files)
$ git commit -m"Agregar LICENSE.txt"
[add-basic-files 2af068d] Agregar LICENSE.txt
 1 file changed, 1 insertion(+)
 create mode 100644 LICENSE.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (add-basic-files)
$ git checkout main
error: pathspec 'main' did not match any file(s) known to git

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (add-basic-files)
$ git branch main

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (add-basic-files)
$ git checkout main
Switched to branch 'main'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (main)
$ git merge --squash add-basic-files
Already up to date. (nothing to squash)

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (main)
$ git checkout main
Already on 'main'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (main)
$ git reset --hard master
HEAD is now at 9bcc9df commit inicial en main

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (main)
$ git merge --squash add-basic-files
Updating 9bcc9df..2af068d
Fast-forward
Squash commit -- not updating HEAD
 CONTRIBUTING.md | 1 +
 LICENSE.txt     | 1 +
 2 files changed, 2 insertions(+)
 create mode 100644 CONTRIBUTING.md
 create mode 100644 LICENSE.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (main)
$ git add .

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (main)
$ git commit -m"Agregar documentacion estandar del repositorio"
[main e48aaf5] Agregar documentacion estandar del repositorio
 2 files changed, 2 insertions(+)
 create mode 100644 CONTRIBUTING.md
 create mode 100644 LICENSE.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/prueba-squash-merge (main)
$ git log --graph --oneline
* e48aaf5 (HEAD -> main) Agregar documentacion estandar del repositorio
* 9bcc9df (master) commit inicial en main
## Comentario: Se crreo una nueva carpeta con tematica del problema, "prueba-squash-merge", se agrega contenido a la rama master y como queri aque fuera main, por defecto se cambiaba master asi que yo la cambie a "main"; luego de eso cree una rama " add-basic-files" y se agregaron dos archivos de diferente naturaleza .Al final desde la rama main se hizo la fusion usando "git merge --squash add-basic-files".

## ¿Cuándo es recomendable utilizar una calabaza fusión? ¿Qué ventajas ofrece para proyectos grandes en comparación con fusiones estándar?
Es recomendable usarlo cuando se tiene una rama principaly se ramifica a una rama de funcionalidad para introducir cambios, tambien para tener mas limpieza en el grafico requerido.
Ofrece ventajas como evitar el deesorden de muchas confirmaciones y aminorar la canidad de commits.

# 4  )Resolver conflictos en una fusión sin avance rápido

 $ cd ..

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5 (main)
$ mkdir pruebaa-merge-conflict

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5 (main)
$ cd  pruebaa-merge-conflict

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (main)
$ git init
Initialized empty Git repository in C:/Users/Bianca/Documents/repositorio/activity-5/pruebaa-merge-conflict/.git/

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (master)
$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (master)
$ git branch

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (master)
$ git checkout main
error: pathspec 'main' did not match any file(s) known to git

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (master)
$ git branch main
fatal: not a valid object name: 'master'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (master)
$ git checkout -b main
Switched to a new branch 'main'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (main)
$ git init
Reinitialized existing Git repository in C:/Users/Bianca/Documents/repositorio/activity-5/pruebaa-merge-conflict/.git/

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (main)
$ echo "<html><body><h1>Proyecto inicial CC3S2</h1></body></html>" > index.html

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (main)
$ git add index.html
warning: in the working copy of 'index.html', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (main)
$ git commit -m "commit inicial del  index.html en main"
[main (root-commit) b4410ae] commit inicial del  index.html en main
 1 file changed, 1 insertion(+)
 create mode 100644 index.html

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (main)
$ git checkout -b feature-update
Switched to a new branch 'feature-update'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (feature-update)
$ echo "<p>.....</p>" >> index.html

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (feature-update)
$ cat index.html
<html><body><h1>Proyecto inicial CC3S2</h1></body></html>
<p>.....</p>

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (feature-update)
$ git add index html
fatal: pathspec 'index' did not match any files

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (feature-update)
$  git add index.html
warning: in the working copy of 'index.html', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (feature-update)
$ git commit -m"Actualiza..."
[feature-update d7e7810] Actualiza...
 1 file changed, 1 insertion(+)

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (feature-update)
$ git checkout main
Switched to branch 'main'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (main)
$ cat index.index
cat: index.index: No such file or directory

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (main)
$ cat index.html
<html><body><h1>Proyecto inicial CC3S2</h1></body></html>

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (main)
$ echo "<footer>Contacta aquí example@example.com</footer>" >> index.html

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (main)
$ git add index.html
warning: in the working copy of 'index.html', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (main)
$ git commit -m "....index.html"
[main c69cf61] ....index.html
 1 file changed, 1 insertion(+)

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (main)
$ cat index.html
<html><body><h1>Proyecto inicial CC3S2</h1></body></html>
<footer>Contacta aquí example@example.com</footer>

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (main)
$ git merge --no-ff feature-update
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (main|MERGING)
$ nano index.html

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (main|MERGING)
$ git add index.html

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (main|MERGING)
$ git commit
[main 00dbca3] Merge branch 'feature-update'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/pruebaa-merge-conflict (main)
$ git log --graph --oneline
*   00dbca3 (HEAD -> main) Merge branch 'feature-update'
|\
| * d7e7810 (feature-update) Actualiza...
* | c69cf61 ....index.html
|/
* b4410ae commit inicial del  index.html en main 
## Comentario: Lo que genero un conflicto fue que Git detectó que ambas ramas modificaron el mismo archivo.
## ¿Qué pasos adicionales tuviste que tomar para resolver el conflicto?
Borre los simbolos ">>>" o "===" del archivo index.html .


## ¿Qué estrategias podrías emplear para evitar conflictos en futuros desarrollos colaborativos?

Ver bien mis codigos como los voy ejecutando, fijarme en el historial y concentrarme mas en como realizo los cambios y tod ese proceso importantisimo.



  # 5 ) Comparar los historiales con git log después de diferentes fusiones

cd ..
mkdir prueba-compare-merge
cd prueba-compare-merge/
git init

echo "Version 1.0" > version.txt
git add version.txt
git commit -m "..."

git checkout -b feature-1
echo "Característica 1 agregada" >> version.txt
git add version.txt
git commit -m "Agregar característica 1"

git checkout main
git checkout -b feature-2
echo "Característica 2 agregada" >> version.txt
git add version.txt
git commit -m "Se agrega característica 2"

git checkout main
git merge feature-1 --ff

git merge feature-2

nano version.txt
git add version.txt
git commit -m "resolver conflictos"
git checkout -b feature-3
echo "Característica 3 paso 1" >> version.txt
git add version.txt
git commit -m "Característica 3 paso 1"

$ git checkout main
Switched to branch 'main'

$ git merge --squash feature-3
Updating f386ba8..c6dd7d3
Fast-forward
Squash commit -- not updating HEAD
 version.txt | 2 ++
 1 file changed, 2 insertions(+)

$ git commit -m "Agregar característica 3 en un commit"
[main b33d551] Agregar característica 3 en un commit
 1 file changed, 2 insertions(+)

$ git log --graph --oneline --merges --first-parent --branches
* b33d551 (main) Agregar característica 3 en un commit
* f386ba8 resolver conflictos

$ git log --graph --oneline --merges --decorate --all
error: switch `l` expects a numerical value

$ git log --graph --oneline --merges --decorate --all
fatal: unrecognized argument: --decorate

$ git log --graph --oneline --merges --decorate=all
* b33d551 (main) Agregar característica 3 en un commit
* f386ba8 resolver conflictos
* c6dd7d3 (feature-3) Característica 3 paso 2
* fd8e32d Característica 3 paso 1
* 0009035 (feature-2) Se agrega característica 2
* e409dca (feature-1) Agregar característica 1
## Este ejercicio es importante porque nos da una vision de como se ve cada tipo de fusion .
## ¿Cómo se ve el historial en cada tipo de fusión?
SE ven completamente iguales

## ¿Qué método prefieres en diferentes escenarios y por qué?
Prefiero el metodo no fast foward porque  preserva el contexto de la fusión y ada mucha claridad al historil de cambios, que es muy importante para mi y pienso para ver el trabajo entre un grupo de personas que trabajen juntas.

# 6 ) Ejercicio: fusiones Usando automáticas y revertir fusiones

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5 (main)
$ cd ..

Bianca@MSI MINGW64 ~/Documents/repositorio (main)
$ mkdir prueba-auto-merge

Bianca@MSI MINGW64 ~/Documents/repositorio (main)
$ cd prueba-auto-merge


Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (main)
$ git init
Initialized empty Git repository in C:/Users/Bianca/Documents/repositorio/prueba-auto-merge/.git/

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (master)
$ echo "Linea 1" > file.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (master)
$ git add file.txt
warning: in the working copy of 'file.txt', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (master)
$ git commit -m "Agrega linea1"
[master (root-commit) 9f684b1] Agrega linea1
 1 file changed, 1 insertion(+)
 create mode 100644 file.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (master)
$ echo "linea2" >> file.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (master)
$ git add file.txt
warning: in the working copy of 'file.txt', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (master)
$ git commit -m " ..linea2"
[master b97d808]  ..linea2
 1 file changed, 1 insertion(+)

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (master)
$ git checkout -b auto-merge
Switched to a new branch 'auto-merge'

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (auto-merge)
$ echo "linea3" >>file.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (auto-merge)
$ git add file.txt
warning: in the working copy of 'file.txt', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (auto-merge)
$ git commit -m"..linea3"
[auto-merge c964aa3] ..linea3
 1 file changed, 1 insertion(+)

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (auto-merge)
$ git checkout main
error: pathspec 'main' did not match any file(s) known to git

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (auto-merge)
$ git branch main

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (auto-merge)
$ git checkout main
Switched to branch 'main'

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (main)
$ nano file.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (main)
$ cat file.txt
Linea 1
linea2
linea3

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (main)
$ git add file.txt
warning: in the working copy of 'file.txt', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (main)
$ git commit -m "agrega cabecera"
On branch main
nothing to commit, working tree clean

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (main)
$ git merge auto-merge
Already up to date.

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (main)
$ git branch
  auto-merge
* main
  master

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (main)
$ git branch -m master main
fatal: a branch named 'main' already exists

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (main)
$ git branch
  auto-merge
* main
  master

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (main)
$ git branch -d master
Deleted branch master (was b97d808).

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (main)
$ git merge auto-merge
Already up to date.

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (main)
$ git log --oneline --graph --all --decorate
* c964aa3 (HEAD -> main, auto-merge) ..linea3
* b97d808  ..linea2
* 9f684b1 Agrega linea1

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (main)
$
Linea 1
linea2
linea3
## Comentario:  Se puede apregiar como la herramienta "Git"  puede fusionar ramas en el momento que no hay conflictos, y cómo manejar ramas que ya no utiles y estan innecesarias en el proyecto.
## ¿Cuándo usarías un comando como git revert para deshacer una fusión?
Lo usaria cuando la fusion no me parezca correcta o me de error.
## ¿Qué tan útil es la función de fusión automática en Git
ES demsaiado util.
   # 7 ) Ejercicio: Fusión remota en un repositorio colaborativo

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (main)
$ git clone https://github.com/walterRGUni/Prueba.git
Cloning into 'Prueba'...
remote: Enumerating objects: 13, done.
remote: Counting objects: 100% (13/13), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 13 (delta 0), reused 3 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (13/13), done.

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (main)
$ ls
Prueba/  file.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge (main)
$ cd Prueba

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge/Prueba (main)
$ git checkout -b colaboracion
Switched to a new branch 'colaboracion'

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge/Prueba (colaboracion)
$ echo "colaboracion remota" > colaboracion.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge/Prueba (colaboracion)
$ git add colaboracion.txt
warning: in the working copy of 'colaboracion.txt', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge/Prueba (colaboracion)
$ git commit -m"..."
[colaboracion a21dc36] ...
 1 file changed, 1 insertion(+), 1 deletion(-)

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge/Prueba (colaboracion)
$ git puch origin colaboracion
git: 'puch' is not a git command. See 'git --help'.

The most similar command is
        push

Bianca@MSI MINGW64 ~/Documents/repositorio/prueba-auto-merge/Prueba (colaboracion)
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 309 bytes | 309.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: 
remote: Create a pull request for 'colaboracion' on GitHub by visiting:
remote:     https://github.com/WalterRGuni/Prueba/pull/new/colaboracion
remote:
To https://github.com/WalterRGuni/Prueba.git
 * [new branch]      colaboracion -> colaboracion
  
## ¿Cómo cambia la estrategia de fusión cuando colaboras con otras personas en un repositorio remoto?

El comando git merge toma las líneas de desarrollo independientes creadas por la rama git e integraslas en una sola rama 
La rama que recibe los cambios siempre es la rama HEAD actualmente desprotegida. 

## ¿Qué problemas comunes pueden surgir al integrar ramas remotas?
Conflictos de fusion y problemas de permisos he visto mas, pero tambien hay errores en la URL del repositorio(en especial cuando se quiere clonar).

# 8) Ejercicio final: flujo de trabajo completo
$ cd C:/Users/Bianca/Documents/repositorio/activity5
bash: cd: C:/Users/Bianca/Documents/repositorio/activity5: No such file or directory

Bianca@MSI MINGW64 ~
$ cd C:/Users/Bianca/Documentod/repositorio/acitvity5
bash: cd: C:/Users/Bianca/Documentod/repositorio/acitvity5: No such file or directory

Bianca@MSI MINGW64 ~
$  C:/Users/Bianca/Documentos/repositorio/activity5
bash: C:/Users/Bianca/Documentos/repositorio/activity5: No such file or directory

Bianca@MSI MINGW64 ~
$ cd C:/Users/Bianca/Documents/repositorio/activity-5

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5 (main)
$ mkdir mi-proyecto

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5 (main)
$ cd mi-proyect
bash: cd: mi-proyect: No such file or directory

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5 (main)
$ cd mi-proyecto

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (main)
$ git init
Initialized empty Git repository in C:/Users/Bianca/Documents/repositorio/activity-5/mi-proyecto/.git/

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (master)
$ git checkout -b main
Switched to a new branch 'main'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (main)
$ git checkout -b feature1
Switched to a new branch 'feature1'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (feature1)
$ git checkout -b feature2
Switched to a new branch 'feature2'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (main)
$ git branch
  feature1
  feature2
  main

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (main)
$ git checkout feature1
Switched to branch 'feature1'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (feature1)
$ git status
On branch feature1
nothing to commit, working tree clean

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (feature1)
$ echo "Cambios en feature1" > archivo1.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (feature1)
$ git add archivo1.txt
warning: in the working copy of 'archivo1.txt', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (feature1)
$ git commit -m "Cambios en feature1"
[feature1 c7f3578] Cambios en feature1
 1 file changed, 1 insertion(+), 1 deletion(-)

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (feature1)
$ git checkout feature2
Switched to branch 'feature2'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (feature2)
$

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (feature2)
$

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (feature2)
$ echo "Cambios en feature2" > archivo2.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (feature2)
$ git add archivo2.txt
warning: in the working copy of 'archivo2.txt', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (feature2)
$ git commit -m "Cambios en feature2"
[feature2 372c62b] Cambios en feature2
 1 file changed, 1 insertion(+)
 create mode 100644 archivo2.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (feature2)
$ git checkout main
Switched to branch 'main'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (main)
$ git merge feature1 --ff
Updating 9a92b78..c7f3578
Fast-forward
 archivo1.txt | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (main)
$ git checkout main
Already on 'main'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (main)
$ git merge feature2 --no-ff
Merge made by the 'ort' strategy.
 archivo2.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 archivo2.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (main)
$ git checkout -b feature3
Switched to a new branch 'feature3'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (feature3)
$ echo "Cambios en feature3" > archivo3.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (feature3)
$ git add archivo3.txt
warning: in the working copy of 'archivo3.txt', LF will be replaced by CRLF the next time Git touches it

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (feature3)
$ git commit -m "Cambios en feature3"
[feature3 a09f990] Cambios en feature3
 1 file changed, 1 insertion(+)
 create mode 100644 archivo3.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (feature3)
$ git checkout main
Switched to branch 'main'

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (main)
$ git merge feature3 --squash
Updating 4907d0d..a09f990
Fast-forward
Squash commit -- not updating HEAD
 archivo3.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 archivo3.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (main)
$ git commit -m "Fusionando feature3 con squash"
[main a962016] Fusionando feature3 con squash
 1 file changed, 1 insertion(+)
 create mode 100644 archivo3.txt

Bianca@MSI MINGW64 ~/Documents/repositorio/activity-5/mi-proyecto (main)
$ git log --oneline --graph --all
* a962016 (HEAD -> main) Fusionando feature3 con squash
| * a09f990 (feature3) Cambios en feature3
|/
*   4907d0d Merge branch 'feature2'
|\
| * 372c62b (feature2) Cambios en feature2
* | c7f3578 (feature1) Cambios en feature1
|/
* 9a92b78 Cambios en feature1




