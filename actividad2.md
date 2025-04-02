## 1. Definición de IaC y su cambio de paradigma frente a la configuración manual

Infraestructura como Código (IaC) es un enfoque que permite gestionar la infraestructura usando archivos de configuración en vez de realizar configuraciones manuales a través de interfaces gráficas o herramientas de administración tradicionales. Este enfoque describe el estado deseado de la infraestructura utilizando un lenguaje declarativo o imperativo, lo que facilita la creación, modificación y administración de recursos de manera automática.

### Cambio de paradigma

La diferencia principal entre IaC y la configuración manual es que en IaC la infraestructura se gestiona como código, permitiendo la automatización completa del ciclo de vida de los recursos. Esto reduce significativamente los errores humanos, ya que las configuraciones y cambios se pueden revisar, versionar y auditar a través de herramientas de control de versiones como Git.

### Beneficios de IaC

- **Consistencia en la configuración**: La infraestructura definida como código puede aplicarse de manera consistente en diferentes entornos (desarrollo, prueba, producción) sin la posibilidad de diferencias manuales.
- **Control de versiones**: Los archivos de configuración son versionados, lo que permite hacer un seguimiento de los cambios, revertir configuraciones erróneas y mantener un historial completo de la infraestructura.
- **Automatización**: La infraestructura se aprovisiona, configura y gestiona automáticamente sin intervención manual. Esto optimiza el tiempo y esfuerzo de los equipos de TI.
- **Reducción de errores humanos**: Al evitar configuraciones manuales, el riesgo de cometer errores en el proceso de configuración se reduce considerablemente, ya que todo el proceso está automatizado y auditado.



## 2. Herramientas populares para IaC

Algunas de las herramientas más populares para implementar IaC son:

- **Terraform**: Utilizada para  múltiples proveedores de nube como AWS, Azure y Google Cloud. Utiliza el HashiCorp Configuration Language (HCL) para definir y gestionar la infraestructura.
- **Ansible**: Ansible npermite definir la infraestructura como código. Utiliza YAML para las describir tareas.
- **Pulumi**: Permite escribir IaC utilizando lenguajes de programación modernos como JavaScript, TypeScript, Python y Go.
- **AWS CloudFormation**: Específica para AWS, permite definir recursos de infraestructura en la nube utilizando archivos en JSON o YAML.



##  Buenas prácticas en la escritura de IaC

- **Nombres claros de recursos**: Utilizar nombres descriptivos y consistentes para los recursos ayuda a identificar rápidamente su propósito y facilita la gestión en entornos grandes.
- **Uso de variables**: Las variables permiten reutilizar configuraciones de manera eficiente y hacer que los recursos sean más dinámicos y personalizables según el entorno.
- **Modularización del código**: Es recomendable dividir la infraestructura en módulos que se puedan reutilizar en diferentes proyectos o entornos. Por ejemplo, un módulo para redes, otro para bases de datos y otro para aplicaciones.
- **Uso de repositorios de control de versiones (Git)**: Mantener el código de la infraestructura en un repositorio Git permite un control completo sobre los cambios, además de colaborar y hacer auditoría sobre las configuraciones.

---

## 3. Patrones para módulos en IaC

### Modularización

Ayuda a la reutiliacion y la gestión. Por ejemplo, un módulo para configurar redes, otro para definir bases de datos y otro para gestionar servidores de aplicaciones.Los modulos pueden ser independientes y ggestionados de diferente manera, permitiendo su reutilización en diferentes proyectos.

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
├──main.tf
├── variables.tf
└── outputs.tf
```

Aquí, cada módulo tiene su propio conjunto de archivos que describen los recursos y las configuraciones, y luego los módulos se llaman en el archivo `main.tf` del proyecto principal.

---

## 4. Patrones para dependencias en IaC

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

Los contenedores son unidades de software que empaquetan una aplicación y sus dependencias, como bibliotecas, archivos de configuración y herramientas necesarias para ejecutar el software. A diferencia de las máquinas virtuales (VMs), que requieren un sistema operativo completo para funcionar, los contenedores comparten el mismo núcleo del sistema operativo subyacente, lo que los hace mucho más ligeros y rápidos de arrancar.

### Diferencia con máquinas virtuales (VMs):

- **Máquinas virtuales (VMs):** Virtualizan un sistema operativo completo y requieren una cantidad significativa de recursos (memoria y CPU).
- **Contenedores:** Solo virtualizan el espacio de usuario y comparten el núcleo del sistema operativo subyacente, lo que los hace más ligeros y eficientes.

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
### Docker y Kubernetes se integran en pipelines de despliegue continuo (CD) para automatizar la creación, configuración, escalado, y gestión de aplicaciones. 
 
# Tarea teorica 2
-**El desarrollador sube el código a GitHub**

-**Jenkins detecta el commit utilizando un webhook**

-**La imagen es construida y enviada al Docker Hub después de las pruebas**

-**Jenkins despliega la aplicación en el clúster de Kubernetes**

### Estrategias de implementación en Kubernetes:


## **Ventajas de Kubernetes para Escalar en un Evento de Alto Tráfico**
Kubernetes posee una característica importante llamada autoescalado. Este permite que las apicaciones se ajusten automáticamente a los cambios den la demanda eficientemente. Para esto, se emplea el escalado horizontal de pods (HPA). Este es un mecanismo que ajusta  automáticamente la cantidad de copias de los Pods en función al uso de la CPU u otras métricas.
Esto es útil ya que maneja picos de tráfico sin que la aplicación caiga, evita problemas de hardware distribuyendo la carga y también se adapta a las interrupciones de red asegurando que la aplicación siempre
esté disponible.

### **Ejemplo práctico**  
Durante el **Black Friday**, una tienda online experimenta un aumento en la demanda. Kubernetes:
1. **Escala automáticamente** de 3 a 20 réplicas según el consumo de CPU.
2. **Redirige el tráfico** entre los pods disponibles.
3. **Mantiene la disponibilidad** incluso si algunos nodos fallan.
4. **Reduce los recursos** después del evento para ahorrar costos.

✅ **Resultado**: La aplicación maneja el pico de tráfico sin interrupciones y sin intervención manual. 🚀
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
posibilidad de que ocurran errores humana. La automatizacion de pruebas tambien ofrece flexibilidad, ya que los equipos de desarrollo puede reutilizar sus scripts de prueba para cualquier conjunto de pruebas relacionado.

