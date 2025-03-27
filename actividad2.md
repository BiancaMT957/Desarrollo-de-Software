## 1. Definición de IaC y su cambio de paradigma frente a la configuración manual

Infraestructura como Código (IaC) es un enfoque que permite gestionar la infraestructura mediante archivos de configuración en lugar de realizar configuraciones manuales a través de interfaces gráficas o herramientas de administración tradicionales. Este enfoque describe el estado deseado de la infraestructura utilizando un lenguaje declarativo o imperativo, lo que facilita la creación, modificación y administración de recursos de manera automática.

### Cambio de paradigma

La diferencia principal entre IaC y la configuración manual es que en IaC la infraestructura se gestiona como código, permitiendo la automatización completa del ciclo de vida de los recursos. Esto no solo mejora la eficiencia, sino que reduce significativamente los errores humanos, ya que las configuraciones y cambios se pueden revisar, versionar y auditar a través de herramientas de control de versiones como Git.

---

## 2. Beneficios de IaC

- **Consistencia en la configuración**: La infraestructura definida como código puede aplicarse de manera consistente en diferentes entornos (desarrollo, prueba, producción) sin la posibilidad de diferencias manuales.
- **Control de versiones**: Los archivos de configuración son versionados, lo que permite hacer un seguimiento de los cambios, revertir configuraciones erróneas y mantener un historial completo de la infraestructura.
- **Automatización**: La infraestructura se aprovisiona, configura y gestiona automáticamente sin intervención manual. Esto optimiza el tiempo y esfuerzo de los equipos de TI.
- **Reducción de errores humanos**: Al evitar configuraciones manuales, el riesgo de cometer errores en el proceso de configuración se reduce considerablemente, ya que todo el proceso está automatizado y auditado.

---

## 3. Herramientas populares para IaC

Algunas de las herramientas más populares para implementar IaC son:

- **Terraform**: Usada ampliamente en múltiples proveedores de nube como AWS, Azure y Google Cloud. Utiliza el HashiCorp Configuration Language (HCL) para definir y gestionar la infraestructura.
- **Ansible**: Aunque es más conocida por la automatización de configuraciones y aplicaciones, Ansible también permite definir la infraestructura como código. Utiliza YAML para describir las tareas a realizar.
- **Pulumi**: Permite escribir IaC utilizando lenguajes de programación modernos como JavaScript, TypeScript, Python y Go.
- **AWS CloudFormation**: Específica para AWS, permite definir recursos de infraestructura en la nube utilizando archivos en JSON o YAML.

---

## 4. Buenas prácticas en la escritura de IaC

- **Nombres claros de recursos**: Utilizar nombres descriptivos y consistentes para los recursos ayuda a identificar rápidamente su propósito y facilita la gestión en entornos grandes.
- **Uso de variables**: Las variables permiten reutilizar configuraciones de manera eficiente y hacer que los recursos sean más dinámicos y personalizables según el entorno.
- **Modularización del código**: Es recomendable dividir la infraestructura en módulos que se puedan reutilizar en diferentes proyectos o entornos. Por ejemplo, un módulo para redes, otro para bases de datos y otro para aplicaciones.
- **Uso de repositorios de control de versiones (Git)**: Mantener el código de la infraestructura en un repositorio Git permite un control completo sobre los cambios, además de colaborar y hacer auditoría sobre las configuraciones.

---

## 5. Patrones para módulos en IaC

### Modularización

Separar los recursos en módulos lógicos facilita la reutilización y la gestión. Por ejemplo, un módulo para configurar redes, otro para definir bases de datos y otro para gestionar servidores de aplicaciones. Cada módulo puede ser independiente y gestionado de manera aislada, permitiendo su reutilización en diferentes proyectos.

### Estructura

Una estructura de módulos típica en IaC podría organizarse de la siguiente manera:

```
├── modules/
│   ├── network/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   └── outputs.tf
│   ├── database/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   └── outputs.tf
│   └── application/
│       ├── main.tf
│       ├── variables.tf
│       └── outputs.tf
├── main.tf
├── variables.tf
└── outputs.tf
```

Aquí, cada módulo tiene su propio conjunto de archivos que describen los recursos y las configuraciones, y luego los módulos se llaman en el archivo `main.tf` del proyecto principal.

---

## 6. Patrones para dependencias en IaC

### Gestión de dependencias

Para enlazar módulos que dependen entre sí, como un módulo de base de datos que debe proporcionar credenciales a un módulo de aplicación, se utilizan salidas e entradas. Por ejemplo, un módulo de base de datos puede proporcionar una salida con las credenciales necesarias, y ese valor se pasa como entrada a un módulo de aplicación para que lo utilice.

### Salidas y entradas

El uso de salidas (`outputs`) y entradas (`inputs`) en módulos permite que los datos se pasen entre ellos. Por ejemplo:

```hcl
output "db_password" {
  value = aws_secretsmanager_secret.db_password.secret_string
}

module "application" {
  source      = "./modules/application"
  db_password = module.database.db_password
}
```

En este ejemplo, el módulo de base de datos genera un `output` con la contraseña y este valor se pasa como `input` al módulo de la aplicación.
# Infraestructura como Código (IaC) con Terraform

## Investigación sobre cómo organiza Terraform sus módulos

Terraform es una herramienta de infraestructura como código que permite a los usuarios definir y aprovisionar infraestructura a través de archivos de configuración. Terraform organiza su infraestructura en módulos, que son conjuntos de archivos de configuración de Terraform que definen recursos relacionados que se pueden reutilizar.

Los módulos en Terraform ayudan a organizar y estructurar proyectos complejos de manera que se puedan reutilizar y mantener con facilidad. Un módulo en Terraform puede ser tan simple como un único archivo `.tf` o tan complejo como un conjunto de carpetas y archivos que estructuran el proyecto en bloques lógicos.

### Terraform tiene dos tipos principales de módulos:

- **Módulos raíz:** Son los archivos `.tf` en el directorio principal de un proyecto. Este módulo se llama implícitamente y se refiere a la infraestructura del proyecto.
- **Módulos reutilizables:** Son módulos que pueden almacenarse en una carpeta separada y ser reutilizados en diferentes partes de la infraestructura.

## Propuesta de estructura de archivos y directorios para un proyecto con tres módulos: `network`, `database` y `application`

Para un proyecto que incluya tres módulos `network`, `database` y `application`, la estructura de archivos y directorios de Terraform podría ser la siguiente:

```bash
project/
├── main.tf                # Archivo principal que organiza los módulos y los recursos principales.
├── variables.tf           # Variables globales que se pueden reutilizar en todo el proyecto.
├── outputs.tf             # Variables de salida globales (por ejemplo, IP pública, nombre de la base de datos).
├── modules/
│   ├── network/           # Módulo para gestionar la red (VPC, subredes, etc.)
│   │   ├── main.tf        # Definición de recursos de red (subredes, VPC, etc.)
│   │   ├── variables.tf   # Variables específicas del módulo de red.
│   │   ├── outputs.tf     # Salidas del módulo de red (por ejemplo, CIDR de la VPC, direcciones IP).
│   ├── database/          # Módulo para gestionar la base de datos (RDS, configuraciones de acceso).
│   │   ├── main.tf        # Definición de recursos de base de datos.
│   │   ├── variables.tf   # Variables específicas del módulo de base de datos.
│   │   ├── outputs.tf     # Salidas del módulo de base de datos.
│   └── application/       # Módulo para gestionar la aplicación (EC2, aplicaciones, etc.).
│       ├── main.tf        # Definición de recursos para la aplicación (servidores, balanceadores).
│       ├── variables.tf   # Variables específicas del módulo de la aplicación.
│       ├── outputs.tf     # Salidas del módulo de la aplicación.
```

### Justificación de la jerarquía elegida

- **`main.tf`**: Organiza los módulos y puede llamar a los módulos `network`, `database` y `application`. Este archivo actúa como el punto de entrada principal para la configuración de la infraestructura.
- **`variables.tf`**: Define las variables globales que se pueden utilizar en todo el proyecto. Al centralizar las variables, se facilita la reutilización y la flexibilidad en la infraestructura.
- **`outputs.tf`**: Define las salidas globales del proyecto, lo que permite acceder fácilmente a los recursos creados, como la dirección IP pública de la aplicación.
- **`modules/`**: Cada módulo es independiente, lo que facilita su reutilización y mantenimiento. Los módulos están organizados por su función, de forma que cada uno contiene los archivos necesarios para gestionar un recurso específico.

La modularización permite un enfoque más organizado y escalable, facilitando la reutilización de la infraestructura y la colaboración entre equipos.

---

# Contenerización y Despliegue de Aplicaciones Modernas

## Contenerización de una aplicación con Docker

### ¿Qué son los contenedores?

Los contenedores son unidades de software que empaquetan una aplicación y sus dependencias, como bibliotecas, archivos de configuración y herramientas necesarias para ejecutar el software. A diferencia de las máquinas virtuales (VMs), que requieren un sistema operativo completo para funcionar, los contenedores comparten el mismo núcleo del sistema operativo subyacente, lo que los hace mucho más ligeros y rápidos de arrancar.

### Diferencia con máquinas virtuales (VMs):

- **Máquinas virtuales (VMs):** Virtualizan un sistema operativo completo y requieren una cantidad significativa de recursos (memoria y CPU).
- **Contenedores:** Solo virtualizan el espacio de usuario y comparten el núcleo del sistema operativo subyacente, lo que los hace más ligeros y eficientes.

### Beneficios de los contenedores:

- **Aislamiento de procesos:** Los contenedores pueden ejecutarse de forma independiente sin interferir entre sí.
- **Ligereza:** No necesitan un sistema operativo completo y comparten recursos con el sistema host, optimizando el uso de recursos.

## Dockerfile

Un `Dockerfile` es un archivo de texto que contiene las instrucciones para construir una imagen de Docker. Estas instrucciones definen qué sistema operativo base usar, qué dependencias instalar, cómo configurar la aplicación y cómo ejecutar el contenedor.

### Estructura básica de un Dockerfile:

```dockerfile
# 1. Especificar la imagen base
FROM ubuntu:20.04

# 2. Instalar dependencias necesarias
RUN apt-get update && apt-get install -y python3 python3-pip

# 3. Copiar archivos locales al contenedor
COPY . /app

# 4. Establecer el directorio de trabajo
WORKDIR /app

# 5. Instalar dependencias de la aplicación
RUN pip3 install -r requirements.txt

# 6. Comando para ejecutar la aplicación
CMD ["python3", "app.py"]
```

### Imagen vs Contenedor

- **Imagen:** Es una plantilla inmutable que define lo que contiene un contenedor. Se usa para crear contenedores.
- **Contenedor:** Es una instancia en ejecución de una imagen.

## Orquestación con Kubernetes

### Introducción a Kubernetes

Kubernetes es una plataforma de orquestación de contenedores que automatiza el despliegue, la escalabilidad y la gestión de aplicaciones en contenedores.

### Componentes principales de Kubernetes:

- **Pods:** Unidad más pequeña de despliegue en Kubernetes.
- **Servicios:** Exponen los Pods a una red interna o externa.
- **Implementaciones:** Aseguran que un número deseado de réplicas de un Pod esté en ejecución.
- **Conjuntos de réplicas:** Mantienen un número específico de réplicas de un Pod.

## Manifiestos en YAML

Ejemplo básico de un Deployment en Kubernetes:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
        - name: my-app-container
          image: my-app-image:v1
          ports:
            - containerPort: 80
```

### Estrategias de implementación en Kubernetes:

- **Actualizaciones continuas:** Sin tiempo de inactividad.
- **Lanzamientos Canary:** Se prueba una nueva versión con un subconjunto de usuarios.
- **Implementaciones azul-verde:** Dos versiones coexisten y el tráfico se redirige a la nueva versión una vez lista.

## **Flujo Simple de Implementación en Kubernetes**

Un flujo típico de implementación de código en un entorno basado en **Docker** y **Kubernetes** sigue estos pasos:

### **1. Desarrollador realiza un cambio en el código**  
- El desarrollador modifica el código en su entorno local y lo sube a un repositorio Git (por ejemplo, GitHub, GitLab o Bitbucket).
- Se crea un **pull request (PR)** y se revisan los cambios antes de fusionarlos a la rama principal.

### **2. Construcción de una nueva imagen Docker**  
- Un pipeline de **CI/CD (por ejemplo, GitHub Actions, GitLab CI/CD, Jenkins, ArgoCD)** detecta los cambios y ejecuta los siguientes pasos:
  - Descarga el código actualizado.
  - Construye una nueva imagen Docker con el comando:
    ```sh
    docker build -t myapp:v2 .
    ```
  - Etiqueta la imagen y la sube a un **registro de contenedores** (Docker Hub, Amazon ECR, Google Container Registry, etc.):
    ```sh
    docker push myregistry/myapp:v2
    ```

### **3. Actualización del Deployment en Kubernetes**  
- Se actualiza el manifiesto de Kubernetes (`deployment.yaml`) con la nueva imagen:
  ```yaml
  apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: myapp
  spec:
    replicas: 3
    selector:
      matchLabels:
        app: myapp
    template:
      metadata:
        labels:
          app: myapp
      spec:
        containers:
          - name: myapp
            image: myregistry/myapp:v2
            ports:
              - containerPort: 80
  ```
- Se aplica el cambio en Kubernetes:
  ```sh
  kubectl apply -f deployment.yaml
  ```
- Kubernetes realiza una **actualización continua (Rolling Update)**, reemplazando los pods con la versión antigua por nuevos pods con la nueva imagen.

### **4. Verificación y monitoreo**  
- Se supervisa el despliegue para asegurarse de que los nuevos pods están en funcionamiento:
  ```sh
  kubectl get pods
  ```
- Se revisan los logs para detectar posibles errores:
  ```sh
  kubectl logs -f myapp-pod-name
  ```
- Si algo falla, se puede hacer un rollback a la versión anterior:
  ```sh
  kubectl rollout undo deployment myapp
  ```

---

## **Ventajas de Kubernetes para Escalar en un Evento de Alto Tráfico**

### **1. Autoescalado basado en demanda**  
- Kubernetes permite **autoescalar** el número de pods en función del tráfico o el consumo de recursos.  
- Con el **Horizontal Pod Autoscaler (HPA)**, Kubernetes ajusta automáticamente la cantidad de réplicas según la carga:
  ```sh
  kubectl autoscale deployment myapp --cpu-percent=50 --min=3 --max=10
  ```
- Así, si el tráfico aumenta, Kubernetes crea más instancias de la aplicación para manejar las solicitudes sin intervención manual.

### **2. Balanceo de carga**  
- Kubernetes distribuye las solicitudes entre los diferentes pods con un **Service de tipo LoadBalancer** o **Ingress Controller**, evitando la sobrecarga de un solo servidor.

### **3. Orquestación eficiente de contenedores**  
- Kubernetes programa y reasigna contenedores en nodos disponibles, optimizando los recursos y asegurando alta disponibilidad.

### **4. Escalabilidad vertical y horizontal**  
- Si un evento de alto tráfico requiere más capacidad, Kubernetes puede:
  - **Agregar más réplicas de pods (escalado horizontal).**
  - **Aumentar los recursos de CPU/RAM asignados a los pods (escalado vertical).**

### **5. Recuperación automática (Self-healing)**  
- Si un pod falla debido a la alta demanda, Kubernetes lo reinicia automáticamente o lo reemplaza en otro nodo disponible.

### **6. Optimización de costos**  
- En un entorno en la nube, Kubernetes puede reducir costos escalando hacia arriba solo cuando es necesario y reduciendo recursos cuando el tráfico disminuye.

---

### **Ejemplo práctico**  
Durante el **Black Friday**, una tienda online experimenta un aumento en la demanda. Kubernetes:
1. **Escala automáticamente** de 3 a 20 réplicas según el consumo de CPU.
2. **Redirige el tráfico** entre los pods disponibles.
3. **Mantiene la disponibilidad** incluso si algunos nodos fallan.
4. **Reduce los recursos** después del evento para ahorrar costos.

✅ **Resultado**: La aplicación maneja el pico de tráfico sin interrupciones y sin intervención manual. 🚀
  # Integración de Prometheus y Grafana con Kubernetes para monitoreo

Prometheus y Grafana son herramientas populares utilizadas para monitorear y visualizar métricas de aplicaciones y sistemas. Su integración con Kubernetes permite monitorear contenedores y clusters, proporcionando visibilidad completa del estado de la infraestructura.

## Prometheus

Prometheus es una herramienta de monitoreo de código abierto diseñada para recopilar métricas de aplicaciones y sistemas, almacenarlas de manera eficiente y proporcionar alertas en tiempo real. Su funcionamiento en un entorno Kubernetes incluye varios pasos clave:

### Scraping de métricas
Prometheus se configura para recolectar métricas de diferentes fuentes, como aplicaciones, bases de datos y otros servicios. En Kubernetes, Prometheus generalmente se implementa como un pod o deployment que usa un servicio de descubrimiento dinámico para encontrar las direcciones de las aplicaciones y nodos.

### Kubernetes discovery
Prometheus utiliza la API de Kubernetes para descubrir dinámicamente los servicios y contenedores en el clúster. Esto incluye Pods, nodos y servicios, lo que le permite hacer scraping de métricas sin intervención manual.

### Recolección de métricas de contenedores
Prometheus recolecta métricas de contenedores a través de los exportadores. Algunos ejemplos son:

- **cAdvisor**: para recolectar métricas sobre los contenedores (uso de CPU, memoria, etc.).
- **Node Exporter**: para monitorear métricas de los nodos, como uso de CPU, memoria y espacio en disco.
- **Kube-state-metrics**: para obtener métricas del estado de los recursos de Kubernetes como Pods, Deployments, Services, etc.

### Alertas y reglas
Prometheus también se puede configurar para generar alertas basadas en las métricas que recolecta. Las alertas se pueden definir en un archivo de configuración usando **PromQL** (Prometheus Query Language) y se integran con **Alertmanager** para la gestión de notificaciones.

## Grafana

Grafana es una plataforma de visualización de métricas que se utiliza para crear paneles de control (dashboards) interactivos. Se integra con Prometheus para visualizar las métricas recopiladas.

### Conexión con Prometheus
Grafana se configura para usar Prometheus como fuente de datos. Una vez configurado, Grafana puede consultar Prometheus utilizando PromQL y mostrar los resultados en gráficos y tablas.

### Dashboards
Grafana permite crear dashboards personalizados que visualizan diferentes métricas y alertas en tiempo real. Existen dashboards predefinidos disponibles en la **Grafana Dashboard Repository**, o puedes crear los tuyos propios.

### Alertas en Grafana
Grafana también puede gestionar alertas basadas en las métricas de Prometheus y enviar notificaciones a través de canales como Slack o correo electrónico.

---

## Propuesta de métricas y alertas mínimas para una aplicación web

Para una aplicación web, el monitoreo debe centrarse en métricas clave que permitan detectar problemas de rendimiento, disponibilidad y estabilidad.

### **Métricas mínimas para monitorear**

#### **Latencia de peticiones**
- **Métrica**: Latencia promedio de las solicitudes HTTP (en milisegundos).
- **PromQL**:
  ```promql
  http_request_duration_seconds_sum / http_request_duration_seconds_count
  ```

#### **Tasa de errores (Error Rate)**
- **Métrica**: Tasa de respuestas con código de error (4xx, 5xx).
- **PromQL**:
  ```promql
  sum(rate(http_requests_total{status=~"4..|5.."}[1m])) / sum(rate(http_requests_total[1m]))
  ```

#### **Uso de CPU**
- **Métrica**: Porcentaje de uso de CPU de los contenedores de la aplicación.
- **PromQL**:
  ```promql
  avg(rate(container_cpu_usage_seconds_total{container_name!="", pod_name=~"app-.*"}[5m])) by (pod_name)
  ```

#### **Uso de memoria**
- **Métrica**: Memoria utilizada por los contenedores de la aplicación.
- **PromQL**:
  ```promql
  avg(container_memory_usage_bytes{container_name!="", pod_name=~"app-.*"}) by (pod_name)
  ```

#### **Tasa de solicitudes**
- **Métrica**: Número total de solicitudes HTTP recibidas por la aplicación.
- **PromQL**:
  ```promql
  sum(rate(http_requests_total{method="GET", status="200"}[5m])) by (pod_name)
  ```

#### **Disponibilidad del servicio**
- **Métrica**: Estado del pod (si está en estado "Running" o no).
- **PromQL**:
  ```promql
  kube_pod_status_phase{phase="Running"}
  ```

---

### **Alertas mínimas para la aplicación web**

#### **Alerta por alta latencia**
- **Condición**: Si la latencia promedio de las solicitudes HTTP excede un umbral (por ejemplo, 200 ms).
- **PromQL**:
  ```promql
  http_request_duration_seconds_sum / http_request_duration_seconds_count > 0.2
  ```

#### **Alerta por alta tasa de errores (4xx o 5xx)**
- **Condición**: Si la tasa de errores supera un umbral (por ejemplo, 5% de todas las solicitudes).
- **PromQL**:
  ```promql
  sum(rate(http_requests_total{status=~"4..|5.."}[1m])) / sum(rate(http_requests_total[1m])) > 0.05
  ```

#### **Alerta por uso elevado de CPU**
- **Condición**: Si el uso de CPU supera un umbral (por ejemplo, 90% durante 5 minutos).
- **PromQL**:
  ```promql
  avg(rate(container_cpu_usage_seconds_total{container_name!="", pod_name=~"app-.*"}[5m])) by (pod_name) > 0.9
  ```

#### **Alerta por uso elevado de memoria**
- **Condición**: Si el uso de memoria supera un umbral crítico (por ejemplo, 90% de la memoria disponible).
- **PromQL**:
  ```promql
  avg(container_memory_usage_bytes{container_name!="", pod_name=~"app-.*"}) by (pod_name) > 0.9 * container_spec_memory_limit_bytes
  ```

#### **Alerta por caída de un pod**
- **Condición**: Si un pod no está en estado "Running" (por ejemplo, si está en "CrashLoopBackOff").
- **PromQL**:
  ```promql
  kube_pod_status_phase{phase!="Running", pod_name=~"app-.*"}
  
 # Tarea Teórica

## Diferencia entre Entrega Continua (*Continuous Delivery*) y Despliegue Continuo (*Continuous Deployment*)

### **1. Entrega Continua (*Continuous Delivery*)**
La **entrega continua** es una práctica de desarrollo en la que los cambios en el código son automáticamente probados y preparados para su lanzamiento a producción. Sin embargo, el despliegue en producción **no es automático**; requiere una aprobación manual antes de que la nueva versión del software sea publicada.

**Características principales:**
- Se garantiza que el código siempre esté en un estado desplegable.
- Se automatizan las pruebas y la generación de artefactos listos para producción.
- El equipo puede decidir cuándo y cómo hacer el despliegue en producción.

📌 **Ejemplo:** Un equipo de desarrollo configura un pipeline CI/CD que ejecuta pruebas y construye una nueva versión del software, pero un ingeniero de DevOps debe aprobar manualmente el despliegue en producción.

---

### **2. Despliegue Continuo (*Continuous Deployment*)**
El **despliegue continuo** lleva la entrega continua un paso más allá al automatizar completamente el proceso de despliegue. En este caso, cada cambio en el código que pasa las pruebas **se despliega automáticamente en producción**, sin intervención manual.

**Características principales:**
- Requiere una estrategia robusta de pruebas automáticas para minimizar riesgos.
- Reduce el tiempo de entrega de nuevas funcionalidades a los usuarios finales.
- Aumenta la frecuencia de despliegues en producción.

📌 **Ejemplo:** Cada vez que un desarrollador fusiona (*merge*) cambios en la rama principal, un pipeline automatizado ejecuta pruebas, genera una nueva versión y la despliega directamente en producción sin intervención manual.

---

## Importancia de las Pruebas Automáticas en el Pipeline

Implementar pruebas automáticas dentro del pipeline de CI/CD es fundamental para garantizar la calidad del software y evitar errores en producción. Existen varios tipos de pruebas que deben incluirse:

### **1. Pruebas Unitarias**
- **Objetivo**: Validar que cada unidad de código (*función, módulo o clase*) funciona correctamente de manera aislada.
- **Beneficio**: Detectar errores en etapas tempranas y garantizar que las funciones individuales operen según lo esperado.
- **Ejemplo**: Probar que una función que suma dos números devuelva el resultado correcto.

### **2. Pruebas de Integración**
- **Objetivo**: Evaluar cómo interactúan entre sí los diferentes módulos o servicios de la aplicación.
- **Beneficio**: Detectar fallos en la comunicación entre componentes y evitar problemas de integración antes del despliegue.
- **Ejemplo**: Verificar que el backend pueda comunicarse correctamente con la base de datos.

### **3. Pruebas de Seguridad**
- **Objetivo**: Identificar vulnerabilidades en el código antes de que lleguen a producción.
- **Beneficio**: Prevenir ataques como inyección SQL, XSS (*Cross-Site Scripting*), fugas de datos o accesos no autorizados.
- **Ejemplo**: Ejecutar escaneos de seguridad automatizados con herramientas como OWASP ZAP o SonarQube.

📌 **Conclusión**: Implementar pruebas automáticas en el pipeline **reduce riesgos, mejora la estabilidad del software y acelera los tiempos de entrega** en entornos de entrega y despliegue continuo.

