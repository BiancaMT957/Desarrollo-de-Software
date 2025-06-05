## Ejercicio 2.3: Mutaciones avanzadas con Prototype

Agregue este método dentro del archivo Prototype.py. 

Primero se tiene un diccionario dentro del método(da una configuracion de recursos de Terraform).  Se hacen cambios a los triggers de un recurso null_resource 

Al final se grega un recurso local file, que tiene como funcion agregar un archivo de texto


```python
def add_welcome_file(block: dict): 

        block["resource"]["null_resource"]["app_0"]["triggers"]["welcome"] = "¡Hola!" 

        block["resource"]["local_file"] = { 

        "welcome_txt": { 

            "content": "Bienvenido", 

            "filename": "${path.module}/bienvenida.txt" 

        } 

    }
```


Dentro de main.tf.json  agregue el bloque local_file, para que me compile un archivo de bienvenida.txt, con su mensaje “¡Hola, bienvenida!” 


```
{ 

            "local_file": { 

                "bienvenida": { 

                    "content": "¡Hola, bienvenida!", 

                    "filename": "${path.module}/bienvenida.txt" 

                } 

            } 

        }
```


Me fui a mi ruta de Terraform y active el entorno virtual .venv. 

Primero hice “terraform init" , luego  “terraform plan”,  al final ejecuto Terraform mediante "Terraform Apply".





![cc](https://github.com/Jharvichu/Actividades_grupales_DS/blob/main/Actividad_21/img/2.3.1.png)



Se ejecuto perfectamente bien “Terraform Apply”



![io](https://github.com/Jharvichu/Actividades_grupales_DS/blob/main/Actividad_21/img/2.3.2.png)



Se generó un archivo de bienvenida.txt, tal como se tenía planeado desde que se agrego el bloque “local_file” .



![pp](https://github.com/Jharvichu/Actividades_grupales_DS/blob/main/Actividad_21/img/2.3.3.png)



