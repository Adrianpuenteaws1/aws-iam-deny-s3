# AWS IAM - Control de acceso con DENY en S3

## Descripción

Práctica de implementación de control de acceso en Amazon S3 utilizando políticas IAM, aplicando el principio de seguridad mediante reglas explícitas de DENY.

## Objetivo

Bloquear la eliminación de archivos en un bucket S3, incluso cuando el usuario tiene permisos completos.

## Escenario

Se creó un usuario con acceso total a S3 (AmazonS3FullAccess), pero se requería restringir la eliminación de objetos para evitar pérdida de información.

## Solución implementada

Se creó una política personalizada con efecto DENY:

* Acción bloqueada: s3:DeleteObject
* Recurso: bucket específico

## Resultado

Al intentar eliminar un archivo:

* ❌ La acción fue bloqueada
* ❌ Se mostró error "Access Denied"
* ✔️ El archivo no fue eliminado

## Evidencia

### Usuario con permisos completos

![Usuario](usuario-con-deny.png)

### Política DENY aplicada

![Policy](politica-deny-json.png)

### Error al eliminar archivo

![Error](error-delete-deny.png)

## Aprendizajes

* Prioridad de DENY sobre ALLOW en AWS IAM
* Implementación de controles de seguridad
* Pruebas de acceso con diferentes usuarios
* Importancia de no usar cuentas admin para validación

## Herramientas utilizadas

* AWS IAM
* Amazon S3
* GitHub
