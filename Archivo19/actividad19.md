## Actividad 19

Clone el repo Kapumota, luego el archivo de Proyecto_iac_local lo guarde en Ubuntu y ahi lo guarde y abri con Visual Studio Code

![b](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo19/img/C1.png)


Instale Terraform en Ubuntu.
Ahora me aseguro que esta instalado


![b](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo19/img/c2.png)



Descargue la extension de Terraform, en Visual Studio Code.
Cree un entorno virtual usando loc comandos:


´´´
python3 -m venv venv
´´´


Y lo active con:


´´´
source venv/bin/activate
´´´

Todo esto para trabajar de una manera más cómoda
Puse la ruta correcta de Python, del entorno virtual, en la parte de :


´´´
variable "python_executable" { description = "Ruta al ejecutable de Python (python o python3)." type = string default = "/home/devasc/Documents/Proyecto_iac_local/venv/bin/python" }
´´´


Al hacer “terraform init” y luego “terraform plan” no tuve problemas, despues al hacer “terraform apply”, tuve problemas porque no habia permisos para los archivos bash.

![b](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo19/img/c3.png)

Luego les di permisos mediante :


´´´
chmod +x scripts/bash/start_simulated_service.sh
´´´


Y ahora despues volvi a hacer “terraform apply”, despues escribir “yes”, tuve exito :


![b](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo19/img/c4.png)




![b](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo19/img/c5.png)




Se creo la carpeta “generated_environmet”, tambien el archivo de texto “bienvenida.txt” y otros mas.

**Fase 1: Fundamentos de terraform y primer recurso local**

  * **Concepto:** Creación básica de recursos.
  * **Archivos a crear/modificar:**
      * `versions.tf`:
        ```terraform
        terraform {
          required_version = ">= 1.0"
          required_providers {
            local = {
              source  = "hashicorp/local"
              version = "~> 2.5"
            }
            random = {
              source  = "hashicorp/random"
              version = "~> 3.6"
            }
          }
        }
        ```
      * `main.tf`:
        ```terraform
        resource "local_file" "bienvenida" {
          content  = "Bienvenido al proyecto IaC local! Hora: ${timestamp()}"
          filename = "${path.cwd}/generated_environment/bienvenida.txt"
        }

        resource "random_id" "entorno_id" {
          byte_length = 8
        }

        output "id_entorno" {
          value = random_id.entorno_id.hex
        }

        output "ruta_bienvenida" {
          value = local_file.bienvenida.filename
        }
        ```



#### Fase 2: Variables, archivos de configuración y scripts Bash


  * **Conceptos:** Parametrización, ejecución de scripts locales.
  * **Archivos a crear/modificar:**
      * `variables.tf`:
        ```terraform
        variable "nombre_entorno" {
          description = "Nombre base para el entorno generado."
          type        = string
          default     = "desarrollo"
        }

        variable "numero_instancias_app_simulada" {
          description = "Cuántas instancias de la app simulada crear."
          type        = number
          default     = 2
        }

        variable "mensaje_global" {
          description = "Un mensaje para incluir en varios archivos."
          type        = string
          default     = "Configuración gestionada por Terraform."
          sensitive   = true # Para demostrar
        }
        ```
      * `terraform.tfvars.example`:
        ```hcl
        nombre_entorno = "mi_proyecto_local"
        numero_instancias_app_simulada = 3
        // mensaje_global se puede omitir para usar default, o definir aquí.
        ```
      * `modules/environment_setup/main.tf`:
        ```terraform
        variable "base_path" {
          description = "Ruta base para el entorno."
          type        = string
        }

        variable "nombre_entorno_modulo" {
          description = "Nombre del entorno para este módulo."
          type        = string
        }

        resource "null_resource" "crear_directorio_base" {
          # Usar provisioner para crear el directorio si no existe
          # Esto asegura que el directorio existe antes de que otros recursos intenten usarlo
          provisioner "local-exec" {
            command = "mkdir -p ${var.base_path}/${var.nombre_entorno_modulo}_data"
          }
          # Añadir un trigger para que se ejecute si cambia el nombre del entorno
          triggers = {
            dir_name = "${var.base_path}/${var.nombre_entorno_modulo}_data"
          }
        }

        resource "local_file" "readme_entorno" {
          content  = "Este es el entorno ${var.nombre_entorno_modulo}. ID: ${random_id.entorno_id_modulo.hex}"
          filename = "${var.base_path}/${var.nombre_entorno_modulo}_data/README.md"
          depends_on = [null_resource.crear_directorio_base]
        }

        resource "random_id" "entorno_id_modulo" {
          byte_length = 4
        }

        resource "null_resource" "ejecutar_setup_inicial" {
          depends_on = [local_file.readme_entorno]
          triggers = {
            readme_md5 = local_file.readme_entorno.content_md5 # Se re-ejecuta si el README cambia
          }
          provisioner "local-exec" {
            command     = "bash ${path.module}/scripts/initial_setup.sh '${var.nombre_entorno_modulo}' '${local_file.readme_entorno.filename}'"
            interpreter = ["bash", "-c"]
            working_dir = "${var.base_path}/${var.nombre_entorno_modulo}_data" # Ejecutar script desde aquí
          }
        }

        output "ruta_readme_modulo" {
          value = local_file.readme_entorno.filename
        }
        ```
      * `modules/environment_setup/variables.tf`: (declarar `base_path`, `nombre_entorno_modulo`): Aca procedi a poner las variables: base_path y nombre_entorno_modulo, en “variables.tf”. Esto tiene mas sentido, porque están en declaracion de variables donde deben estar, no en “main.tf”.

      * variable "base_path" {
      description = "Ruta base para el entorno."
      type        = string
       }

       variable "nombre_entorno_modulo" {
       description = "Nombre del entorno para este módulo."
       type        = string
       }
      ´´´

* `modules/environment_setup/scripts/initial_setup.sh`:
        ```bash
        #!/bin/bash
        # Script: initial_setup.sh
        ENV_NAME=$1
        README_PATH=$2
        echo "Ejecutando setup inicial para el entorno: $ENV_NAME"
        echo "Fecha de setup: $(date)" > setup_log.txt
        echo "Readme se encuentra en: $README_PATH" >> setup_log.txt
        echo "Creando archivo de placeholder..."
        touch placeholder_$(date +%s).txt
        echo "Setup inicial completado."
        # Simular más líneas de código
        for i in {1..20}; do
            echo "Paso de configuración simulado $i..." >> setup_log.txt
            # sleep 0.01 # Descomenta para simular trabajo
        done
        ```
      * Modificar `main.tf` (raíz) para usar el módulo `environment_setup`:
        ```terraform
        module "config_entorno_principal" {
          source                = "./modules/environment_setup"
          base_path             = "${path.cwd}/generated_environment"
          nombre_entorno_modulo = var.nombre_entorno
        }

        output "readme_principal" {
          value = module.config_entorno_principal.ruta_readme_modulo
        }
        ```
  
Ejecute y me salian errores, los fui analizando y me di cuenta que debia darle permiso a bash y que habian algunos errores. 

Luego de darle permiso al archivo bash “modules/environment_setup/scripts/initial_setup.sh”( escribiendo en  la terminal “chmod +x    [ruta] ”  ) y de arreglar errores en main.tf de “environment_setup” y alguno que otro error,  procedi a ejecutar y me sale todo bien. 

 

![b](https://github.com/BiancaMT957/Desarrollo-de-Software/blob/main/Archivo19/img/c6.png)

 

 
