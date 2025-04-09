# 2. A

## 1. Definición de IaC y su cambio de paradigma frente a la configuración manual

La infraestructura como código (IaC) es uno de los fundamentos en la ingeniería de software contemporánea. La infraestructura de TI –que incluye servidores, redes, sistemas de almacenamiento, contenedores, balanceadores de carga y otros recursos necesarios para ejecutar aplicaciones– se trata de un codigo fuente para una aplicación. Esto implica que la configuración, el aprovisionamiento y la administración de los recursos se definen mediante archivos de texto eo configuraciones declarativas, para repositorios git generalmente.

## Beneficios de IaC
Permite una gestión más eficiente de los cambios, con una trazabilidad completa gracias al versionado. Cada modificación se puede revisar mediante Pull Requests, lo que reduce los errores. Además, el uso de IaC libera a los equipos de la dependencia en configuraciones manuales y ayuda compartir harto conocimiento importante.


## 2. Herramientas populares para IaC

Algunas de las herramientas más populares para implementar IaC son:

- **Terraform**: Estas herramientas permiten describir el estado deseado de la infraestructura de forma declarativa. Con un lenguaje propio, Terraform, por ejemplo, utiliza HCL para definir recursos como instancias EC2, bases de datos o redes virtuales.
- **Ansible**: Se enfocan en la gestión de la configuración del sistema operativo y de aplicaciones, asegurando que cada máquina o contenedor se encuentre en el estado deseado.
- **Pulumi**: Permite escribir IaC usando lenguajes como JavaScript o Go.
- **AWS CloudFormation**: es un servicio de infraestructura como código (IaC) que le permite modelar, aprovisionar y administrar de manera sencilla recursos de AWS ...

##  Buenas prácticas en la escritura de IaC

- **Nombres claros de recursos**:  ayuda a identificar rápidamente su propósito y facilita la gestión en entornos grandes.
- **Uso de variables**: Las variables permiten reutilizar configuraciones de manera eficiente.
- **Modularización del código**: Es recomendable dividir la infraestructura en módulos que se puedan reutilizar en diferentes proyectos.
- **Uso de repositorios de control de versiones (Git)**: Mantener el código de la infraestructura en un repositorio Git permite un control completo sobre los cambios, además de colaborar y hacer auditoría sobre las configuraciones.



## 3. Patrones para módulos en IaC

### Modularización

Ayuda a reutilizar y gestionar.
### Estructura

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
├──main.tf
├── variables.tf
└── outputs.tf
```
--- 

# Tarea teorica 1
## Terraform 

Terraform es una herramienta que permite a los usuarios gestionar infraestructura de un proyecto mediante archivos de configuración. Para organizar mejor los proyectos, Terraform usa módulos, los cuales agrupan
archivos de configuración relacionados para facilitar su reutilización y mantenimiento.
Un modulo consiste de una colección de archivos .tf y/o .tf.json que se mantienen juntas en un directorio.
Toda configuración de Terraform tiene al menos un módulo, cono cido como el modulo raíz que consiste en los recursos definidos en los archivos .tf en el directorio de trabajo principal 
-  **main.tf**:  Define los recursos principales del módulo.
-  **variables.tf**: Contiene los parámetros de entrada
-  **outputs.tf**: Define las salidas del módulo
-  **providers.tf**: (opcional): Declara los proveedores de nube o infraestructura usados.
-  **terraform.tfvars**: (opcional): Permite definir valores por defecto para las variables. 

project-terraform/
├── modules/
│   ├── network/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   ├── outputs.tf
│   │   ├── provider.tf
│   ├── database/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   ├── outputs.tf
│   │   ├── provider.tf
│   ├── application/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   ├── outputs.tf
│   │   ├── provider.tf
├── environments/
│   ├── dev/
│   │   ├── main.tf
│   │   ├── terraform.tfvars
│   ├── prod/
│   │   ├── main.tf
│   │   ├── terraform.tfvars
├── main.tf
├── variables.tf
├── outputs.tf
├── provider.tf
├── terraform.tfvars
├── .gitignore
├── README.md
 

### ¿Qué son los contenedores?

Son tecnologías que permiten empaquetar y aislar las aplicaciones junto con todo el entorno de ejecución

### Diferencia con máquinas virtuales (VMs):

Las máquinas virtuales proporcionan una versión abstracta de todo el hardware de una máquina física, incluida la CPU, la memoria y el almacenamiento. Los contenedores en cambio, son instancias portátiles de software con sus dependencias que se ejecutan en una máquina física o virtual

### Aislamiento y ligereza
El avance de la contenerización ha revolucionado la forma en que se empaquetan y despliegan las aplicaciones. Docker se ha consolidado como el estándar de facto en este ámbito, permitiendo que las aplicaciones se ejecuten en entornos aislados y portátiles, sin importar las diferencias en los sistemas operativos de los hosts.

### Estructura básica de un Dockerfile:

```dockerfile
# 1. 
FROM ubuntu:20.04

# 2. 
RUN apt-get update && apt-get install -y python3

# 3.
 CMD ["python3", "--version"]
# 4.
docker build -t mi_imagen:1.0 .

# 5.
docker run --name contenedor_ejemplo -d mi_imagen:1.0

### Imagen vs Contenedor

Una imagen es una plantilla inmutable quetiene el codigo y tambien las dependencias . Un contenedor es una instancia en ejecución de una imagen, que puede cambiarse temporalmente pero no modificala imagen base. Para hacer cambios permanentes, hay que realizar una nueva imagen.

## Orquestación con Kubernetes

### Introducción a Kubernetes

### Componentes principales de Kubernetes:

- **Pods:**  Son la unidad mínima de implementación, encapsulando uno o varios contenedores que comparten rojo y almacenamiento..
- **Servicios:** Exponen los Pods a una red interna o externa.
- **ReplicaSet:** Asegúrese de que un número definido de réplicas de un Pod esté siempre en ejecución..
- **Implementaciones:**  Facilitan actualizaciones progresivas y permiten realizar rollbacks si es necesario, gestionando versiones de la aplicación de forma declarativa..
- **StatefulSets:** Se utilizan para aplicaciones con estado que requieren identidades de red únicas y volúmenes persistentes.

## Manifiestos en YAML

Ejemplo básico de un Deployment en Kubernetes:

apiVersion: apps/v1
kind: Deployment
metadata:
  name: mi-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: mi-app
  template:
    metadata:
      labels:
        app: mi-app
    spec:
      containers:
      - name: contenedor-web
        image: nginx:latest 
```
### Docker y Kubernetes se integran en pipelines de despliegue continuo (CD) para automatizar la creación, configuración, escalado, y gestión de aplicaciones. 
 
# Tarea teorica 2
## Describir un flujo simple de despliegue donde un desarrollador hace un cambio en el código, se construye una nueva imagen Docker y se actualiza un Deployment de Kubernetes.

-**El desarrollador sube el código a GitHub**

-**Jenkins detecta el commit utilizando un webhook**

-**La imagen es construida y enviada al Docker Hub después de las pruebas**

-**Jenkins despliega la aplicación en el clúster de Kubernetes**

### Estrategias de implementación en Kubernetes:


## **Ventajas de Kubernetes para Escalar en un Evento de Alto Tráfico**
Kubernetes posee una característica importante llamada autoescalado. Este permite que las apicaciones se ajusten automáticamente a los cambios den la demanda eficientemente. Para esto, se emplea el escalado horizontal de pods (HPA). Este es un mecanismo que ajusta  automáticamente la cantidad de copias de los Pods en función al uso de la CPU u otras métricas.
Esto es útil ya que maneja picos de tráfico sin que la aplicación caiga, evita problemas de hardware distribuyendo la carga y también se adapta a las interrupciones de red asegurando que la aplicación siempre
esté disponible.

  # Tarea teorica 3
  ## INTEGRACION DE PROMETHEUS Y GRAFANA CON KUBERNETES PARA EL MONITOREO DE CONTENEDORES Y CLUSTERES
Prometheus es un sistema de monitoreo y alerta de código abierto. Se integra con Kubernetes para extraer datos sobre el rendimiento de los nodos, pods y contenedores. Utiliza lo que se conoce como pull para consultar periodicamente las metricas de los servicios mediante su lenguaje PromQL. Grafana se utiliza para representar gráficamente las métricas recolectadas por Prometheus. Necesitamos un servidor de 1. Grafana, corriendo 
1. **Necesitamos un servidor de  Grafana, corriendo**
2. **Necesitamos que en el mismo servidor donde se encuentre
Grafana haya un servidor de Prometheus corriendo como
servicio de Linux**
3. **Necesitamos que haya un servidor Prometheus en cada uno de los clusters de Kubernetes**

## SET DE METRICAS Y ALERTAS MÍNIMAS PARA UNA APLICACION WEB

Para una aplicación web, el monitoreo debe centrarse en métricas clave que permitan detectar problemas de rendimiento, disponibilidad y estabilidad.

### **Métricas mínimas para monitorear**

#### **Latencia de peticiones**
- Medirlas en ms y establecer una alerta en el caso de se supere N ms en un intervalo determinado de tiempo.

#### **Uso de CPU**
 - El porcentaje de CPU utilizado en cada nodo o pod y establecer una alerta si el uso supera cierto porcentaje.

#### **Uso de memoria**
 - Medir cuanta memoria se usa respecto a la memoria que no se usa y establecer una alerta en el caso de  que se use mas de la que no se use.

#### **Tiempo de respuesta de la base de datos**
- Tiempo de respuesta en consultas muy importantes y establecer una alerta en el caso de que se supere el umbral de tiempo.

 # Tarea Teórica 4

## Diferencia entre Entrega Continua (*Continuous Delivery*) y Despliegue Continuo (*Continuous Deployment*)
La entrega continua (CD) cierra el ciclo mediante la automatización de aspectos de la entrega de  software. A medida que se abordan los comentarios y se implementan correcciones, estos cambios  se cargan automáticamente hasta que el equipo tome la decisión de enviar la aplicación a producción. La CD da lugar a un producto que se puede desplegar, pero depende de la autorización 
humana para implantarlo, lo que permite a los equipos decidir qué se debe lanzar y cuándo. Los desarrolladores pueden seguir perfeccionando la aplicación antes de entregarla al usuario final. El despliegue continuo es similar a la entrega continua. La principal diferencia con el despliegue continuo es que, en lugar de requerir una autorización humana para lanzar un producto, el despliegue continuo envía cada cambio de forma automatizada, que luego se envía inmediatamente a producción. No se espera un ciclo de aprobación manual, lo que significa que el código en sí mismo debe haberse probado lo suficiente antes de pasar a producción. 

## ¿POR QUÉ ES IMPORTANTE IMPLEMENTAR PRUEBAS AUTOMÁTICAS (UNITARIAS, DE INTEGRACIÓN, DE SEGURIDAD) DENTRO DEL PIPELINE?

Porque aumentan la confiabilidad, consistencia y efciencia tanto del equipo como del producto final. Ayuda a ahorrar tiempo para que el equipo pueda centrarse en otras tareas. Además, reduce la
posibilidad de que ocurran errores humana. 


## . Evaluación y discu sión final
### Evaluación de la teoría
# Introducción
La entrega ágil y confiable de software es fundamental en esta era nueva que usa mucho la digitalización. Tecnologías como Infrastructure as Code (IaC), contenedores, Kubernetes, observabilidad y CI/CD permiten reducir el tiempo de despliegue, mejorar escalabilidad y garantizar la estabilidad para sus aplicaciones.

# Importancia de cada tecnología
IaC (Infrastructure as Code): Permite gestionar la infraestructura de forma codificada y repetible.Proporciona un lenguaje común para desarrolladores y operaciones. Facilita la colaboración entre equipos de desarrollo y operaciones. Elimina la mayor parte del trabajo de provisionamiento. Garantiza que cada entorno sea idéntico, eliminando errores derivados de configuraciones manuales 

Contenedores: Hace aplicaciones portables y consistentes.. Docker es el mas utilizado de todos.

Kubernetes: Permite escalar y implantar aplicaciones más rápido.Organiza las interacciones de contenedores. Alberga grandes cantidades de datos valiosos.Facilita la implementación de CI/CD. Proporciona un flujo de trabajo eficiente y escalable CI/CD 

Observabilidad: Los entornos Kubernetes albergan grandes cantidades de datos valiosos. Permite monitorizar la infraestructura

CI/CD (Integración y Entrega Continua): Automatiza pruebas y despliegues, , reduce errores humanos . Hay herramientas como Jenkins, Gitlab CI y Github Actions. 

#  Riesgos y desafíos.
Los riesgos que pueden abarcar son:
Sobrecarga cognitiva y Configuración de seguridad
