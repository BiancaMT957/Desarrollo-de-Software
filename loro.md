Actividad 22 

### Fase 2: Inyección de dependencias 

A este archivo main.py lo modifico



``` 

import json 

import ipaddress 

 

class NetworkMetadata: 

    def __init__(self, name, cidr, subnet_id, vpc_id): 

        self.name = name 

        self.cidr = cidr 

        self.subnet_id = subnet_id 

        self.vpc_id = vpc_id 

 

 

class ServerFactory: 

    def __init__(self, server_name, network_metadata): 

        self.server_name = server_name 

        self.network_metadata = network_metadata 

 

    def allocate_ip(self): 

        network = ipaddress.IPv4Network(self.network_metadata.cidr) 

        return str(list(network.hosts())[4]) 

 

    def build(self): 

        return { 

            "resource": { 

                "aws_instance": { 

                    self.server_name: { 

                        "ami": "ami-0c55b159cbfafe1f0", 

                        "instance_type": "t2.micro", 

                        "subnet_id": self.network_metadata.subnet_id, 

                        "private_ip": self.allocate_ip(), 

                        "tags": { 

                            "env": "dev", 

                            "team": "infra" 

                        }, 

                        "metadata_options": { 

                            "http_endpoint": "enabled" 

                        } 

                    } 

                } 

            } 

        } 

 

 

def get_network_metadata(path="network/network_metadata.json"): 

    with open(path) as f: 

        data = json.load(f) 

    return NetworkMetadata( 

        name=data["name"], 

        cidr=data["cidr"], 

        subnet_id=data["subnet_id"], 

        vpc_id=data["vpc_id"] 

    ) 

 

 

if __name__ == "__main__": 

    metadata = get_network_metadata() 

    factory = ServerFactory(server_name="web_server", network_metadata=metadata) 

    result = factory.build() 

 

    with open("server.tf.json", "w") as f: 

        json.dump(result, f, indent=2) 

 

    print(" server.tf.json generado con inyección de dependencias.") 

 

``` 

 

 

 

 

 

Picture   

Se creo un archivo main.tf.json 

 

 

{ 

  "resource": { 

    "aws_instance": { 

      "web_server": { 

        "ami": "ami-0c55b159cbfafe1f0", 

        "instance_type": "t2.micro", 

        "subnet_id": "subnet-abc123", 

        "private_ip": "10.0.0.5", 

        "tags": { 

          "env": "dev", 

          "team": "infra" 

        }, 

        "metadata_options": { 

          "http_endpoint": "enabled" 

        } 

      } 

    } 

  } 

} 

 

 

 

 

#  Principio de Inversión de Control (IoC) en tu código 

En el main.py inicial, la clase ServerFactoryModule controlaba de manera directa cómo se obtenía la metadata de red, cargándola desde un archivo JSON dentro de su constructor. Esto proporcionaba  una fuerte dependencia entre la lógica del servidor y el origen de los datos de red. 

Se aplico inversión de control al: 

Separar la responsabilidad de obtener la metadata de red (get_network_metadata) de la clase ServerFactory. 

Inyectar un objeto NetworkMetadata como dependencia en el constructor de ServerFactory. 

Esto da a entender  que ServerFactory ya no decide cómo se obtiene la información de red, solo la usa. Este cambio permite: 

Mayor flexibilidad: puedes inyectar metadata desde archivos, bases de datos o incluso pruebas unitarias sin modificar la clase. 

 Menor acoplamiento: ServerFactory no depende de funciones externas o rutas específicas. 

 Mejor mantenibilidad y testeo: puedes simular fácilmente diferentes redes en tests. 

  

 

 

 

 

 

 

 

### Fase 5: Patrón Mediator 

# mediator.py 

Acá se tiene el patrón Mediator comentado. 

 

``` pyton  

import json  

from pathlib import Path 

# Funciones para verificar si los archivos de configuración existen 

def check_network_state():  

# Verifica si el archivo de configuración de red existe  

return Path("network.tf.json").exists() 

def check_server_state():  

# Checkea si el archivo de configuración del servidor existe  

return Path("server.tf.json").exists() 

def check_firewall_state():  

# Checkea si el archivo de configuración del firewall existe  

return Path("firewall.tf.json").exists() 

# Clase que actúa como el Mediador 

class TerraformMediator:  

def __init__(self):  

# Guarda el estado de cada módulo (True si existe el archivo correspondiente) 

self.states = { "network": check_network_state(), 

 "server": check_server_state(),  

"firewall": check_firewall_state() } 

def validate_dependencies(self): 
    # Valida que los módulos están ahi 
    if not self.states["network"]: 
        raise RuntimeError(" Falta la configuración de la red (network.tf.json)") 
    if not self.states["server"]: 
        raise RuntimeError(" Falta la configuración del servidor (server.tf.json)") 
    if not self.states["firewall"]: 
        raise RuntimeError(" Falta la configuración del firewall (firewall.tf.json)") 
 
def generate_main_tf(self): 
    print(" Todos los módulos están presentes. Generando main.tf.json...") 
 
    # Estructura centralizada con dependencias simuladas 
    main_tf = { 
        "resource": { 
            "null_resource": { 
                "network": { 
                    "triggers": { 
                        "name": "vpc-dev" 
                    } 
                }, 
                "server": { 
                    "triggers": { 
                        "subnet": "subnet-1234", 
                        "ip": "10.0.0.5" 
                    }, 
                    "depends_on": ["null_resource.network"] 
                }, 
                "firewall": { 
                    "triggers": { 
                        "allow_ssh": True 
                    }, 
                    "depends_on": [ 
                        "null_resource.network", 
                        "null_resource.server" 
                    ] 
                } 
            } 
        } 
    } 
 
    # Guarda la estructura JSON en el archivo final main.tf.json 
    with open("main.tf.json", "w") as f: 
        json.dump(main_tf, f, indent=2) 
 
    print(" main.tf.json generado con éxito.") 
  

# Punto de entrada principal del script 

if name == "main":  

mediator = TerraformMediator()  

try:  

     # Valida que todos los archivos estén presentes  

     mediator.validate_dependencies()  

     # Genera el archivo main.tf.json con dependencias  

     mediator.generate_main_tf()  

except RuntimeError as e:  

# Captura y muestra errores si falta algún archivo  

print(e) 

```  

 

 

Ejercicio práctico 

Cree el archivo mediator.py dentro de el patrón Mediator, con las configuraciones necesarias. 

Luego me fui a mi ruta cd Actividad_22/Mediator 

Luego ejecute: python3 main.py 

Me genera un archivo main.tf.json dentro de el patrón Mediator,  con los triggers, firewall:  

 

Picture  

 

 

 

 

 

 

 

``` 

{ 

  "terraform": { 

    "required_providers": {} 

  }, 

  "resource": { 

    "null_resource": { 

      "network": { 

        "triggers": { 

          "name": "hello-world-network" 

        } 

      }, 

      "server": { 

        "triggers": { 

          "name": "hello-world-server", 

          "depends_on": "null_resource.network" 

        } 

      }, 

      "firewall": { 

        "triggers": { 

          "port": "22", 

          "depends_on": "null_resource.server" 

        } 

      } 

    } 

  } 

} 

 ``` 

 

 

 

 

 

 Mediator vs Facade 

 

 Propósito: 
 El patrón Mediator se enfoca en coordinar la comunicación entre varios objetos o módulos. Es especialmente útil cuando esos componentes necesitan interactuar entre sí de forma compleja o cambianteEn cambio, el patrón Facade busca simplificar el acceso a un sistema complicado. Ofrece una interfaz más sencilla para trabajar con múltiples clases o funcionalidades. 

Nivel de control: 
 El Mediator tiene un control alto sobre cómo los objetos interactúan entre sí. Centraliza toda la lógica de interacción en un solo lugar. 
 La Facade, por otro lado, no controla tanto; su función es simplemente agrupar y ordenar llamadas a otros subsistemas sin alterar su lógica interna. 

Acoplamiento: 
 El Mediator reduce el acoplamiento entre componentes, ya que evita que los objetos se comuniquen directamenteLa Facade sí mantiene el acoplamiento con los subsistemas, pero lo hace de forma más ordenada y lo oculta tras una interfaz sencilla. 

Flujo de interacción: 
 Con Mediator, el flujo de comunicación es dinámico y puede variar según la situación, porque está diseñado para coordinar múltiples partes. 
 En el caso de Facade, el flujo suele ser más lineal y directo: se llama a un método de la fachada y esta se encarga de ejecutar acciones en orden. 

Ejemplo común: 
 Un buen ejemplo del uso de Mediator sería un sistema de chat o de eventos, donde muchos componentes necesitan coordinarse sin depender unos de otros. 
 Un ejemplo típico de Facade sería una API que ofrece funciones sencillas para acceder a una biblioteca compleja, como por ejemplo una que se encargue de procesar imágenes o acceder a servicios en la nube. 

  

 

 

 

 

 

 

 

 

###  Ejercicios adicionales 

 

## 6. Diseña un flujo de trabajo de Git (ramas, etiquetas, pull request) adecuado para ambos modelos, destacando diferencias en la gestión de versiones compartidas. 

* Mono-repositorio: 

Flujo: 

main → estable, producción. 

develop → integración de nuevas características. 

feature/* → ramas para nuevas funciones. 

release/* → preparaciones de lanzamiento. 

hotfix/* → correcciones urgentes. 

 

Gestión de versiones: 

Etiquetas aplicadas en main para identificar versiones globales del repositorio (v1.2.0). 

Coordinación fuerte entre módulos (versiones sincronizadas). 

*Multi-repositorio: 

Flujo por repositorio (por módulo): 

main → rama estable del módulo. 

feature/* → cambios individuales. 

Pull Request → revisión y merge en main. 

Etiquetas (v1.0.1, v1.1.0, etc.) por módulo. 

 

Gestión de versiones: 

Cada módulo tiene su propio ciclo de versiones. Mayor independencia, menor coordinación global. 

 

 ## 7. Justifica el uso de versionado semántico en módulos Terraform. ¿Qué consecuencias podría tener omitirlo? 

La justificación se debe:  

El versionado semántico (MAJOR.MINOR.PATCH) permite: 

Claridad para consumidores del módulo, compatibilidad garantizada cuando solo cambian versiones MINOR o PATCH, automatización de upgrades seguros (con constraints como ~> 1.2.0). 

Consecuencias de omitirlo: 

Usuarios no sabrán si una actualización rompe compatibilidad. 

Difícil conservación en proyectos grandes. 

Aumento de errores en CI/CD y en despliegues automatizados. 

Dificultad para auditar cambios entre versiones. 

 

## 8. Política de gestión de lanzamientos para un registro privado de módulos 

La política de versiones sigue el esquema semántico MAJOR.MINOR.PATCH, con normas claras y una cadencia establecida para cada tipo de versión: 

Versión PATCH: Se utiliza para correcciones de errores que no afectan la interfaz pública ni introducen nuevas funcionalidades. 

Ejemplo: v1.2.1 

Cadencia: Bajo demanda, cada vez que se corrige un bug. 

Versión MINOR: Se libera cuando se agregan nuevas funcionalidades que son compatibles con versiones anteriores. 

Ejemplo: v1.3.0 

Cadencia: Cada 2 a 4 semanas. 

Versión MAJOR: Se utiliza para cambios que rompen compatibilidad con versiones anteriores, como cambios en nombres de recursos o variables requeridas. 

Ejemplo: v2.0.0 

Cadencia: Cada 3 a 6 meses. 

Normas adicionales: 

Cada Pull Request (PR) significativo debe actualizar el archivo CHANGELOG.md. 

Todas las versiones, sin excepción  deben ser verificadas en entornos de staging antes de aplicar el tag correspondiente. 

 

## 9. Ventajas y desventajas de publicar módulos en Terraform Cloud Registry frente a un repositorio Git interno 

Terraform Cloud Registry ofrece accesibilidad global, integración con búsqueda, y documentación automática. Es ideal cuando se quiere compartir módulos públicamente o entre múltiples organizaciones. Pero, depende de un servicio externo y requiere cuentas en Terraform Cloud (con mejores opciones en la versión Enterprise). La autenticación es más limitada y el control del entorno es menor. 

Repositorio Git Interno, por otro lado, da un control total sobre la infraestructura, autenticación, y procesos de CI/CD. Es ideal para entornos corporativos con políticas estrictas de seguridad. Requiere más mantenimiento e infraestructura adicional para manejar el versionado, autenticación, y visibilidad, pero puede aislarse completamente de internet. 

 

10. Implementación de autenticación y control de acceso para un registro privado de módulos en un entorno corporativo 

Mecanismo propuesto: 
 Usar un registro privado como Artifactory, Harbor, o un backend personalizado sobre S3, GCS, o almacenamiento local para servir módulos de Terraform de forma segura. 

Infraestructura: 

Exponer el frontend del registro a través de un proxy autenticado. 

Usar un backend de almacenamiento como S3, GCS, o filesystem local accesible por terraform init. 

Autenticación y autorización: 

Integración con sistemas corporativos como LDAP, Active Directory, OAuth2 o SAML. 

Definición de roles y permisos según grupo: 

Admin: puede publicar y borrar módulos. 

DevOps: puede consumir módulos. 

QA: tiene solo acceso de lectura. 

Medidas de seguridad adicionales: 

Encriptación y acceso obligatorio vía HTTPS. 

Escaneo automático de archivos subidos en busca de vulnerabilidades. 

Auditoría y registro de accesos. 

Uso de tokens personales o temporales para autenticar (bearer tokens). 

Implementación práctica: 

Configurar Artifactory (u otro sistema) con soporte para Terraform. 

Definir grupos y roles con permisos adecuados. 

Publicar módulos usando terraform publish o mediante peticiones curl. 

Configurar las credenciales en el archivo ~/.terraformrc para que Terraform pueda autenticar de forma segura.  
