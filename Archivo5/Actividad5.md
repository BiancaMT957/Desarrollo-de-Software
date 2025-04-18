## 1) Clona un repositorio Git con multiples ramas

### Pregunta: ¿En qué situaciones recomendaría evitar el uso de git merge --ff? Reflexiona sobre las desventajas de este método. 
No usaria cuando se tienen ramas con historiales de commits configurados  anterormente. Tampoco cuando la rama base haya recibido commits al momento de 
crearse la nueva rama “feature”. Como desventaja no puedes preservar el contexto de fusion ni tampoco tener claridad de historial de cambios. 
![Diagrama de ramas](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo5/img/imagen1.png?raw=true)


## 2)  Simula un flujo de trabajo de equipo.  
### Pregunta: ¿Cuáles son las principales ventajas de utilizar git merge --no-ffen un proyecto en equipo? ¿Qué problemas podrían surgir al depender excesivamente de commits de fusión?  
Haber como ventaja podria resaltar que se preserva el contexto de fusion, esto es esencial para los que desarrolladores que deseen mucha claridad en el historial de cambios(por ejemplo cuando hacemos commits o aggregamos codigo de python o texto o archivo html).
![2](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo5/img/imagen2.png?raw=true)


## 3)))  Crea múltiples commits en una rama.  
### Pregunta: ¿Cuándo es recomendable utilizar una calabaza fusión? ¿Qué ventajas ofrece para proyectos grandes en Corparacion con fusiones estándar?
Es recomendable usar “git rebase-2 o “calabaza fusión” cuando deseas tener un historial de confirmaciones tipo lineal, pero también reescribir tu historial y no borrarlo como en otros casos. 
![3](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo5/img/imagen3.png?raw=true)

## 4)))  Resolver conflictos en una fusión sin avance rápido 
Preguntas: 
### ¿Qué pasos adicionales tuviste que tomar para resolver el conflicto? 
Tuve que arreglarlos manualmente, osea tecnicamente hablando abri el archivo usando el comando “nano.index.html” y cuando lo abri el archivo procedi a borrar los “>>>” , “==” y elencabezado “HEAD”.  

###  ¿Qué estrategias podrías emplear para evitar conflictos en futuros desarrollos colaborativos? 
Uhm podria revisar paso por paso los comandos que voy escribiendo en el terminal, pensando bien en lo que hago y bien concentrada , de paso que aprendo mas y no me confundo. Mas que todo seguiría  el proceso usando bien la teoría aprendida, podria ver el historial y el archivo que voy agregando. 
![4](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo5/img/imagen4.png?raw=true)

## 5))) Ejercicio: Comparar los historiales con git log después de diferentes fusiones 
### Preguntas: 
### ¿Cómo se ve el historial en cada tipo de fusión? 
Caso1:  git log --graph --oneline --merges --first-parent –branches 
Se puede apreciar el historial mas resumido, con las cosas mas importantes. 
 
Caso 2: git log --graph --oneline –merges 
Se puede apreciar únicamente un paso, que fue la resolución del conflicto. Es el 
historial más corto. 
 
Caso 3: git log --graph --oneline --merges --decorate –all  
Se tiene el historial mas largo. 
![5](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo5/img/imagen5.png) 
###  ¿Qué método prefieres en diferentes escenarios y por qué? 
Prefiero el método donde se usa “git log --graph --oneline --merges --first-parent –
branches”, porque tiene los commits mas importantes a mi parecer. 
![by](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo5/img/imagen5b.png)
## 6))) Ejercicio: fusiones Usando automáticas y revertir fusiones 
  
Acá se pudo apreciar en la interfaz de “Visual Studio Code” el archivo del “MERGE_MSG”. 
Preguntas: 
### ¿Cuándo usarías un comando como git revert para deshacer una fusión? 
Cuando acab de realizar una fusion y luego me arrepiento y procedo a deshacerla 
sin alteral el historial. 

![uu](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo5/img/imagen6a.png)

###  ¿Qué tan útil es la función de fusión automática en Git? 
Demasiado util y por esa razon muchos profesionales destacados la usan.  
![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo5/img/imagen6b.png)

![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo5/img/imagen6c.png)

![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo5/img/imagen6d.png)


## 7)))  Ejercicio: Fusión remota en un repositorio colaborativo 
### ¿Cómo cambia la estrategia de fusión cuando colaboras con otras personas en un repositorio remoto? 
Se deja de realizar merge directo y ahora se utiliza o se cambia por “pull request” para poder realizar la fusion de rama.

![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo5/img/imagen7a.png)
### ¿Qué problemas comunes pueden surgir al integrar ramas remotas? 
Pueden ocurrrir conflictos de fusion o tambien llamados “merge conflicts”, tambien puedo ocasionar un historial medio incompleto o desordenado.  


![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo5/img/imagen7c.png)
## 8))) Ejercicio final: flujo de trabajo completo
### Revisa el historial para entender cómo los diferentes métodos de fusión afectan el árbol de commits. 
### Compara los resultados y discute con tus compañeros de equipo cuál sería la mejor estrategia de fusión para proyectos más grandes.

 
![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo5/img/imagen8a.png)
 Cree todo, tambien hize cambios en las ramas feature1 y feature2.Despues leshize sus commits, los confirme y despues hize sus fusiones.
 
![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo5/img/imagen8b.png)

 
![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo5/img/imagen8c.png)
Se arreglo la fusion en la rama feature2


![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo5/img/imagen8cpng.png)
Se puede apreciar la fusion "squash", que aplasta commits, en la rama feature3


![er](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo5/img/imagen8d.png)
Al final se pueden apreciar los commits y tambien sus cambios que se hicieron.

 
 

  
  


 

 

