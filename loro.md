##Archivo adapter_output.py
Este script tiene como objetivo generar una salida JSON estática que puede ser utilizada por otros componentes del sistema. Realiza las siguientes operaciones:

- Importa el módulo estándar json de Python, que permite trabajar con datos en formato JSON.

- Utiliza la función json.dumps() para convertir un diccionario de Python en una cadena JSON válida.

- Imprime el resultado en la salida estándar, lo que permite redirigirlo a un archivo (> adapter_output.json) o capturarlo desde otros scripts.

Este script se puede ejecutar primero con : python3 adapter_output.py

Esto imprimirá:


{"status": "OK", "code": 200}


Este tipo de script se usa generalmente para: generar archivos .json de forma automática dentro de flujos como Terraform (local-exec), pipelines CI/CD, o procesos de prueba.



##Archivo adapter_parse.sh

Este archivo automatiza la lectura de datos generados por un script Python (adapter_output.py) y transforma dicha información en un archivo .tfvars legible por Terraform. También registra logs y exporta variables de entorno para su posible reutilización. Realiza las siguientes operaciones:

-  Verificación de dependencias
- Verificación de archivo de entrada
- Ejecución del script Python y parseo JSON
- Creación de archivo Terraform .tfvars
- Registro en log
- Exportación de variables de entorno

Se puede ejecutar primero dando permisos:

```
chmod +x adapter/adapter_parse.sh
```

después : 

```
./adapter_parse.sh
```


Este script es bastante útil para automatizar flujos donde: 

- Se generan valores dinámicos desde scripts.

- Esos valores deben ser leídos por Terraform.

- Se quieren reutilizar variables en otras partes del sistema.




##Archivo main.tf


Este archivo es importante porque:

- Se encarga de generar archivos locales con datos incluidos( adapter/.terraform.lock.hcl, adapter/.terraform/, adapter/adapter_output.json, adapter/terraform.tfstate ), que luego podemos utilizar en el proyecto.
- Convierte información o estados previos en un archivo para que luego se consuma.
- Automatiza tareas externas como generar configuraciones, hacer parsing, ejecutar validaciones.

Este script se puede ejecutar primero haciendo "terraform init", luego "terraform plan" y después "terraform apply".


Lastimosamente no es portable: si otra persona usa Windows o no tiene instalado python3, fallará.

Si se desea instalar python3 desde Ubuntu puedes ejecutar: 


```bash
sudo apt update
sudo apt install python3 python3-pip -y
```

y verificas mediante:

```
python3 --versión
```


