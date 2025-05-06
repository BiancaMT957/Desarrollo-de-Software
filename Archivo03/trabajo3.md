## ¿Qué problemas o limitaciones existían antes del surgimiento de la computación en la nube y cómo los solucionó la centralización de servidores en centros de datos?
Mucho antes de el surgimiento de cimputacion en la nube, las organizaciones debian de tener un hardware fisico en sus instalaciones, lo cual era muy costoos y daba problemas en los recursos.
## ¿Por qué se habla de “The Power Wall” y cómo influyó la aparición de procesadores multi-core en la evolución hacia la nube?
Se habla de eso porque hacia referencia a la barrera termina y de consumo de energia que logro hacer que la frecuencia de procesadores siguiera aumentando. Los procesadores multi-core han permitido que los sistemas manejen más tareas simultáneamente, lo que ha mejorado el rendimiento en tareas como la edición de video y el renderizado 3D. 
Esto ha sido clave para la evolución hacia la nube, ya que los sistemas con procesadores multi-core son más eficientes para manejar cargas de trabajo grandes y complejas. 
## Explique cómo la necesidad de atender grandes volúmenes de tráfico en sitios web condujo a la adopción de clústeres y balanceadores de carga.
Se necesitaba distribuir la carga y los clusteres de serviio y balanceadores de carga tenian la habilidad de optimizar la eficiencia de las aplicaciones web.
## Describa un ejemplo práctico de cómo un desarrollador de software puede beneficiarse del uso de balanceadores de carga para una aplicación web. 
Un desarrollador de software podria agregar facilmente nuevos servidores a la infraestructura, en caso de el trafico aumentara.
## Define con tus propias palabras el concepto de Elastic Computing.
Es parte de la computacion en la nube. Es la capacidad para aumentar o disminuir a gran velocidad los recursos de una computadora con la finalidad de resolver las demandas cambiantes.
##  ¿Por qué la virtualización es una pieza clave para la elasticidad en la nube? 
 permite escalar la infraestructura de TI de manera eficiente.
##  Menciona un escenario donde, desde la perspectiva de desarrollo, sería muy difícil escalar la infraestructura sin un entorno elástico.
eventos como "Black Friday" lo necesitarian. Sin computación elástica, el sistema podría colapsar u obtener  infrautilizada por mucho tiempo, aproximadamente un año.
##  ¿En qué casos un desarrollador optaría por PaaS en lugar de IaaS?
Cuando no se puede permitir crear una plataforma de desarrollo y despliegue completa, cuando se necesita una solución fácilmente disponible, cuando se trabaja en un proyecto con varios desarrolladores remotos, cuando se necesita un entorno de desarrollo de aplicaciones compartido 

##  Enumera tres ejemplos concretos de proveedores o herramientas que corresponden a cada tipo de servicio.
Proveedores de servicios de TI
Ofrecen servicios como supervisión de red, ciberseguridad, copia de seguridad de datos, asistencia técnica, gestión de software y hardware. 
Proveedores de servicios en la nube
Ofrecen servicios como alojamiento de aplicaciones web, analíticas de datos, servicios de IA, entre otros. Algunos ejemplos de proveedores de servicios en la nube son IBM, Alibaba, Oracle, Red Hat, DigitalOcean y Rackspace. 
Proveedores de servicios gestionados (MSP)
Son empresas externas que asumen las responsabilidades diarias, la supervisión y el mantenimiento de una serie de tareas y funciones para otra empresa. 

## ¿Cuáles son las ventajas de implementar una nube privada para una organización grande?
Tiene mayor control mayor seguridad, puede personalizar su infraestructura, hay mejor rendimiento, mayor privacidad y mayor disponiblidad.


## ¿Por qué una empresa podría verse afectada por el “bloqueo de proveedor”?
Porque depende tanto de un solo proveedor que cambiarlo resultaria muy costoro o complicado.Ademaslimitaria la libertad de la empresa y esto podria repercutir sobre su competividad. 

## ¿Qué papel juegan los “hyperscalers” en el ecosistema de la nube?
Son proveedores que permiten que las empresas de diferentes tipos accedan a tecnologias muy avanzadas.
# Actividades de investigacion
Amazon, Microsoft y Google. 
## Motivaciones 
Mejorar la escalabilidad
Acelerar la innovación
Mejorar la flexibilidad
## Beneficios 
Ahorro de costos
Mayor agilidad y flexibilidad
Mayor escalabilidad
Mayor seguridad

## desafios 
estafas
fraudes
proteger el acceso a cuentas y entornos de Amazon Web Services
# Comparativa de Modelos de Servicio (IaaS, PaaS, SaaS)

| **Aspecto**                 | **IaaS (Infrastructure as a Service)** | **PaaS (Platform as a Service)** | **SaaS (Software as a Service)** |
|-----------------------------|----------------------------------------|----------------------------------|---------------------------------|
| **Responsabilidad del desarrollador** | Control total sobre el sistema operativo, redes, y almacenamiento. | Despliegue de aplicaciones, sin acceso  la infraestructura. | Uso del software, sin acceso a la infraestructura o plataforma subyacente. |
| **Responsabilidad del proveedor**  | Proporciona la infraestructura subyacente (máquinas virtuales, almacenamiento). | Otorga la plataforma, herramientas y servicios para desarrollo de aplicaciones. | Proporciona y mantiene el software listo para su uso. |
| **Responsabilidad del equipo de operaciones** | Gestionar servidores, redes, almacenamiento, y garantizar la disponibilidad. | Gestionar la plataforma y asegurar el funcionamiento de las aplicaciones. | No es necesario, ya que el proveedor maneja el software y la infraestructura. |
| **Instalación de S.O.**           | El equipo de operaciones instala y gestiona el S.O. | El proveedor ya gestiona el S.O., el desarrollador usa la plataforma. | El software ya está disponible para usar, sin necesidad de instalación. |
| **Despliegue de aplicaciones**   | El equipo de desarrollo gestiona el despliegue en máquinas virtuales. | El desarrollador despliega en la plataforma proporcionada sin gestionar infraestructura. | El software se usa tal cual, sin necesidad de desplegarlo. |
| **Escalado automático**         | Requiere configuración manual . | Generalmente es automático . | El escalado lo maneja el proveedor. |
| **Parches de seguridad**         | El equipo de operaciones se encarga de la aplicación de parches. | El proveedor aplica parches a la plataforma subyacente. | El proveedor aplica parches a la aplicación sin intervención del cliente. |

---

# Estrategia Multi-Cloud o Híbrida
Una empresa con infraestructura distribuida busca migrar el 50% de su carga de trabajo a un segundo proveedor para evitar la dependencia y mejorar la resiliencia. Las estrategias de migración incluyen replicación de datos, red y conectividad, y planes de continuidad con herramientas como Prometheus y Grafana. Se comparan los costos y tipos de nube: la nube pública tiene costos iniciales más bajos, la nube privada ofrece mayor seguridad, la nube híbrida ofrece flexibilidad pero mayores costos de integración, y la multinube reduce la dependencia y optimiza los costos. La empresa compara los costos de CAPEX y OPEX: CAPEX representa la inversión en hardware y OPEX el pago por el uso de la nube.

Conclusión
Las estrategias basadas en nube pública o multi-cloud son mas flexibles, pero tambien mas caros. La nube privada es más costosa al principio pero ofrece una muy buena seguridad y es muy util en empresas grandes eso.
---

# Debate sobre Costos: Comparativa de Nubes

## Pros y Contras de Cada Tipo de Nube

# Comparación de Modelos de Nube

| Característica  | Ventajas | Desventajas |
|----------------|----------|-------------|
| **Nube Pública** | - Menor costo inicial.  <br> - Alta escalabilidad y fácil implementación. <br> - Menos carga administrativa. | - Menor control y seguridad compartida. <br> - Personalización limitada. <br> - Dependencia del proveedor. |
| **Nube Privada** | - Control total y seguridad personalizada. <br> - Alto nivel de personalización. <br> - Optimizada para necesidades específicas. | - Mayor inversión inicial y costos fijos. <br> - Gestión interna más compleja. <br> - Depende de la infraestructura propia. |
| **Nube Híbrida** | - Flexibilidad y equilibrio entre rendimiento y seguridad. <br> - Adaptabilidad a diferentes necesidades. <br> - optimiza costos según la distribución de recursos. | - Requiere gestión combinada de recursos. <br> - Puede ser más dificil de administrar. <br> - Control variado según el recurso y ubicación. |
| **Multinube** | - Alta flexibilidad y optimización del rendimiento. <br> - Aprovecha lo mejor de cada proveedor. <br> - Reduce la dependencia de un solo proveedor. | - Compleja gestión de múltiples interfaces y proveedores. <br> - Costos variables según los servicios en uso. <br> - Dependencia de la estabilidad de varios proveedores. |

