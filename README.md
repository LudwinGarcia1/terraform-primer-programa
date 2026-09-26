# Primer programa de Terraform

Práctica introductoria de Terraform basada en el laboratorio
[`primer-programa`](https://github.com/jorgealmeidamontiel/terraform-laboratories/tree/main/primer-programa).

Se usa el proveedor `hashicorp/random` para generar una cadena aleatoria, por lo que
**no se necesita ninguna cuenta de nube**.

## Requisitos

- Terraform `>= 1.0.0` (probado con v1.16.2)

## Estructura

| Archivo | Descripción |
|---|---|
| `main.tf` | Bloque `terraform` (proveedor y versión requerida) y el recurso `random_string.suffix` |
| `.terraform.lock.hcl` | Fija la versión del proveedor que se usó (`hashicorp/random` v3.9.1) |
| `.gitignore` | Deja fuera del repositorio `.terraform/` y los archivos de estado |

## Ejecución

```bash
terraform init       # Descarga el proveedor hashicorp/random
terraform validate   # Revisa que la sintaxis sea válida
terraform plan       # Muestra lo que se va a crear: 1 to add
terraform apply      # Crea el recurso random_string.suffix
terraform state list # Lista los recursos que están en el estado
terraform destroy    # (Opcional) Borra el recurso
```

## Resultado

`terraform apply` crea un recurso `random_string` de 16 caracteres que incluye
caracteres especiales. El valor queda guardado en `terraform.tfstate`, dentro del
atributo `result`.
