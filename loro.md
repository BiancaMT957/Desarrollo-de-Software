## Flujo de los mensajes entre Clientes y  Mediator

1. **cliente_a/send_message.sh** genera `cliente_a/message_a.txt` con el mensaje en formato JSON.
2. El Mediator (por medio de los scripts `mediator_read.sh` y `mediator_forward.sh`) toma ese archivo y lo copia a `mediator/message_b.txt`.
3. **cliente_b/recibir_message.sh** lee el archivo `mediator/message_b.txt` y lo imprime en la terminal.

#### Diagrama
cliente_a/send_message.sh
        │
        ▼
cliente_a/message_a.txt
        │
        ▼
cp cliente_a/message_a.txt mediator/tmp_message.txt
        │
        ▼
mediator/mediator_forward.sh
        │
        ▼
mediator/message_b.txt
        │
        ▼
cliente_b/recibir_message.sh

---

### Ejemplo de prueba aislada

```bash
# Se ejecuta en cliente_a/
bash send_messageejecuta.sh "Hola Mediator"

# Se mueve el mensaje al Mediator desde la raiz del proyecto

bash cp cliente_a/message_a.txt mediator/tmp_message.txt

# Desde Mediator/  se ejecuta manualmente el script de mediator
bash mediator_forward.sh

# Luego se  ejecuta en cliente_b/
bash recibir_message.sh

Ejemplo de prueba:

### Ejemplo de output

```bash
# En cliente_a
bash send_message.sh "Hola Mediators"
[cliente_a] Mensaje escrito en message_a.txt:
{"msg": "Hola Mediators", "timestamp": "2025-06-13T21:53:56-04:00"}

# Desde la raíz del proyecto
cp cliente_a/message_a.txt mediator/tmp_message.txt

# En mediator
bash mediator/mediator_forward.sh
[Mediator] Reenviando el mensaje a mediator/message_b.txt...
[Mediator] Mensaje reenviado exitosamente.

# Contenido en mediator/message_b.txt:
{"msg": "Hola Mediators", "timestamp": "2025-06-13T21:53:56-04:00"}

# En cliente_b
bash receive_message.sh
[cliente_b] Mensaje recibido de ../mediator/message_b.txt:
{"msg": "Hola Mediators", "timestamp": "2025-06-13T21:53:56-04:00"}
