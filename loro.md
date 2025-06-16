# En cliente_b
```
receive_message.sh
[cliente_b] Mensaje recibido de ../mediator/message_b.txt:
{"msg": "Hola Mediators", "timestamp": "2025-06-13T21:53:56-04:00"}
```

###  Cambio al script  `adapter_parse.sh`

Se hizo cambios a adapter_parse.sh.
Ahora puede leer variables terraform.tfvars y registra errores en el archivo adapter.log(si es que ocurriese).

**Uso:**


```
chmod +x adapter_parse.sh
```

```
./parse.sh
```

####  Salida: 

Se genera el archivo terraform.tfvars con:

```
adapter_status = "OK"
adapter_code = 200
```

y ademas en logs/adapter.log se registra:

```
[2025-06-15 00:25:52] adapter_parse.sh ejecutado correctamente
[2025-06-15 00:25:52] STATUS: OK CODE:200
```

## Script `adapter/main.tf`
En este script puse una descripcion personalizada del `STATUS` Y `CODE`, ademas puse OUTPUTS para que se imprimiesen.

**Uso:**
```
 terraform init
```

```
 terraform apply -auto-approve
```


**Salida:**

Se genera un archivo terraform.tfstate, donde se aprecian los outputs y tambien las variables.
Una parte del código generado en ese archivo es:

```
  "outputs": {
    "adapter_code": {
      "value": 200,
      "type": "number"
    },
    "adapter_status": {
      "value": "OK",
      "type": "string"
    }
  },
```


En la consola se puede ver esto


```
Apply complete! Resources: 0 added, 0 changed, 0 destroyed.
Outputs:
adapter_code = 200
adapter_status = "OK"
```

## Script `generar_dependencies.py`
 
Este script crea un archivo dependencies.json con contenido estático, que describe las dependencias entre los módulos del proyecto.
