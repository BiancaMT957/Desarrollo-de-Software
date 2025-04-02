## ¿Qué problemas o limitaciones existían antes del surgimiento de la computación en la nube y cómo los solucionó la centralización de servidores en centros de datos?
Mucho antes de el surgimiento de cimputacion en la nube, las organizaciones debian de tener un hardware fisico en sus instalacciones, lo cual era muy costos y tenia problemas en las gestion de recursos.
## ¿Por qué se habla de “The Power Wall” y cómo influyó la aparición de procesadores multi-core en la evolución hacia la nube?
Se habla de eso porque hacia referencia a la barrera termina y de consumo de energia que logro hacer que la frecuencia de procesadores siguiera aumentando.Los multi-core tienen objetivos de mejorar rendimiento sin incrementar el gran consumo y gasto de energia.
## Explique cómo la necesidad de atender grandes volúmenes de tráfico en sitios web condujo a la adopción de clústeres y balanceadores de carga.

Habia mucha necesidad de disstribuir la carga y los clusteres de serviio y balanceadores de carga podian repartise las solicitudes y ademas optimizar el rendimiento de aplicaciones web.
## Describa un ejemplo práctico de cómo un desarrollador de software puede beneficiarse del uso de balanceadores de carga para una aplicación web. 
Un desarrollador que gestiona una aplicación de e-commerce con alto tráfico podría usar un balanceador de carga para distribuir solicitudes entre varios servidores. Esto evitaría sobrecargas en un solo nodo, mejoraría la experiencia del usuario reduciendo tiempos de respuesta y garantizaría la disponibilidad de la plataforma, incluso si uno de los servidores falla. 
## Define con tus propias palabras el concepto de Elastic Computing.
capacidad de ajustar automaticamente los recursos de infraestructura teniendo mucho en cuenta la demanda, haciendo posible ir hacia arriba o abajo sin problemas.
##  ¿Por qué la virtualización es una pieza clave para la elasticidad en la nube? 
Porque hace posible creary gestionar muchas maquinas virtuales sobre un hardware fisico, haciendo mas facil la asignacion dinamica de recursos de demanda .
##  Menciona un escenario donde, desde la perspectiva de desarrollo, sería muy difícil escalar la infraestructura sin un entorno elástico.
eventos como "Black Friday" necesitaría una infraestructura que pueda escalar rápidamente para manejar la alta demanda. Sin computación elástica, el sistema podría colapsar o quedar con capacidad infrautilizada el resto del año. 
# Actividades de investigacion
Algunas empresas que han migrado a la nube son Amazon, Microsoft y Google. 
## Motivaciones 
Reducir costos operativos
Mejorar el rendimiento
Proteger los datos
Modernizar las cargas de trabajo
Mejorar la escalabilidad
Acelerar la innovación
Mejorar la flexibilidad
## Beneficios 
Ahorro de costos
Mayor agilidad y flexibilidad
Mayor escalabilidad
Mayor seguridad
Mejor cumplimiento
Copia de seguridad, recuperación y conmutación por error
Administración y supervisión simplificadas
Tiempo de salida al mercado más rápido
Colaboración mejorada
Prevención de pérdida de datos 

# Comparativa de Modelos de Servicio (IaaS, PaaS, SaaS)

| **Aspecto**                 | **IaaS (Infrastructure as a Service)** | **PaaS (Platform as a Service)** | **SaaS (Software as a Service)** |
|-----------------------------|----------------------------------------|----------------------------------|---------------------------------|
| **Responsabilidad del desarrollador** | Control total sobre el sistema operativo, redes, y almacenamiento. | Despliegue de aplicaciones, pero sin acceso directo a la infraestructura. | Uso del software, sin acceso a la infraestructura o plataforma subyacente. |
| **Responsabilidad del proveedor**  | Proporciona la infraestructura subyacente (máquinas virtuales, almacenamiento). | Proporciona la plataforma, herramientas y servicios para desarrollo de aplicaciones. | Proporciona y mantiene el software listo para usar. |
| **Responsabilidad del equipo de operaciones** | Gestionar servidores, redes, almacenamiento, y garantizar la disponibilidad. | Gestionar la plataforma y asegurar el funcionamiento de las aplicaciones. | No es necesario, ya que el proveedor maneja el software y la infraestructura. |
| **Instalación de S.O.**           | El equipo de operaciones instala y gestiona el S.O. | El proveedor ya gestiona el S.O., el desarrollador usa la plataforma. | El software ya está disponible para usar, sin necesidad de instalación. |
| **Despliegue de aplicaciones**   | El equipo de desarrollo gestiona el despliegue en máquinas virtuales. | El desarrollador despliega en la plataforma proporcionada sin gestionar infraestructura. | El software se usa tal cual, sin necesidad de desplegarlo. |
| **Escalado automático**         | Requiere configuración manual o herramientas externas para el escalado. | Generalmente es automático dentro de la plataforma. | El escalado lo maneja el proveedor. |
| **Parches de seguridad**         | El equipo de operaciones se encarga de la aplicación de parches. | El proveedor aplica parches a la plataforma subyacente. | El proveedor aplica parches a la aplicación sin intervención del cliente. |

---

# Estrategia Multi-Cloud o Híbrida

Una empresa con infraestructura distribuida entre un centro de datos propio y un proveedor de nube pública busca migrar el 50% de sus cargas de trabajo a un segundo proveedor para evitar la dependencia de uno solo y mejorar la resiliencia.

Estrategia de Migración
Base de Datos: Se mantiene la alta disponibilidad mediante replicación entre proveedores (ej. AWS RDS → Azure SQL).

Red y Conectividad: Se configuran VPNs y redes privadas virtuales (VPC) para asegurar la comunicación entre los entornos.

Plan de Contingencia: Implementación de failover y monitoreo con herramientas como Prometheus y Grafana para detectar fallos y reaccionar rápidamente.

Comparativa de Costos y Tipos de Nube
Tipo de Nube	Ventajas	Desventajas
Nube Pública	Bajo costo inicial, escalabilidad, sin mantenimiento de hardware	Dependencia del proveedor, preocupaciones de seguridad
Nube Privada	Control total, mayor seguridad, cumplimiento de regulaciones	Altos costos iniciales, mantenimiento constante
Nube Híbrida	Flexibilidad, resiliencia	Mayor complejidad y costos de integración
Multi-Cloud	Reducción de dependencia, optimización de costos	Complejidad en la gestión e integración
Costos: CAPEX vs OPEX
CAPEX: Inversión en hardware, mayor costo inicial pero amortizable.

OPEX: Pago por uso en la nube, más flexible pero con costos operativos a largo plazo.

Conclusión
Las estrategias basadas en nube pública o multi-cloud permiten mayor flexibilidad y menor inversión inicial, aunque pueden generar costos operativos elevados. La nube privada es más costosa al principio pero ideal para organizaciones con requisitos estrictos de seguridad y control.
---

# Debate sobre Costos: Comparativa de Nubes

## Pros y Contras de Cada Tipo de Nube

| **Tipo de Nube**   | **Pros**                                                                                           | **Contras**                                                                                          |
|--------------------|----------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| **Nube Pública**    | - Bajo costo inicial (pago por uso) <br> - Escalabilidad y flexibilidad <br> - Sin mantenimiento de hardware | - Dependencia de un proveedor <br> - Preocupaciones de seguridad y privacidad                       |
| **Nube Privada**    | - Control total sobre los recursos y la seguridad <br> - Cumple con regulaciones estrictas (ej. HIPAA) <br> - Mejor rendimiento | - Altos costos iniciales (CAPEX) <br> - Mantenimiento constante de hardware y personal especializado |
| **Nube Híbrida**    | - Flexibilidad de combinar lo mejor de nubes públicas y privadas <br> - Redundancia y resiliencia    | - Complejidad en la gestión de recursos <br> - Costos adicionales por gestión y integración           |
| **Multi-Cloud**     | - No dependencia de un solo proveedor <br> - Optimización de costos entre diferentes proveedores    | - Complejidad en la gestión de recursos y redes <br> - Desafíos de integración y monitoreo            |


