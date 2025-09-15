# Requisitos del Sistema

## 1. Introducción

Breve descripción del sistema, su propósito y alcance.

---

## 2. Requisitos Funcionales

Estos describen **qué debe hacer el sistema**.

| ID   | Requisito                   | Descripción Detallada                                                                                     |
| ---- | --------------------------- | --------------------------------------------------------------------------------------------------------- |
| RF01 | Crear usuario admin         | Crear usuario admin si el sistema no se ha inicializado                                                   |
| RF02 | Crear usuario temporal      | Permitir crear un usuario con acceso limitado a un recursos y expiración                                  |
| RF03 | Listar recursos             | Mostrar todos los recursos disponibles con sus atributos                                                  |
| RF04 | Gestionar permisos          | Asignar y revocar permisos a usuarios temporales                                                          |
| RF05 | Crear solicitudes           | Crear solicitudes de acceso a un recursos especificando tiempo, nivel de permiso y motivo                 |
| RF06 | Aceptar y negar solicitudes | Permitir que las solicitudes sean aceptadas o negadas                                                     |
| RF07 | Registar recursos           | Permitir registrar recursos (PostgreSQL, SQL Server)                                                      |
| RF08 | Revocar accesos automáticos | El sistema debe revocar accesos temporales al expirar el tiempo definido.                                 |
| RF09 | Renovar accesos             | Permitir extender el tiempo de un usuario temporal antes de su expiración.                                |
| RF10 | Registro de auditoría       | Mantener un historial de accesos, solicitudes y cambios en permisos.                                      |
| RF11 | Reportes                    | Generar reportes de usuarios activos, solicitudes aprobadas/denegadas y accesos a recursos.               |
| RF12 | Búsqueda y filtrado         | Permitir buscar usuarios, recursos y solicitudes por atributos.                                           |
| RF13 | Notificaciones              | Enviar alertas al admin o usuario (correo/SMS) sobre accesos próximos a expirar o solicitudes pendientes. |
| RF14 | Multi-rol                   | Permitir roles adicionales (ej. auditor, supervisor) con permisos distintos al admin.                     |


---

## 3. Requisitos No Funcionales

Estos describen **cómo debe comportarse el sistema**, restricciones y criterios de calidad.

| ID    | Requisito      | Descripción Detallada                      | Métrica / Indicador        |
| ----- | -------------- | ------------------------------------------ | -------------------------- |
| RNF01 | Seguridad      | Los accesos deben ser auditables y seguros | Log de auditoría + cifrado |
| RNF02 | Escalabilidad  | Debe soportar 1000 usuarios simultáneos    | Pruebas de carga           |
| RNF03 | Rendimiento    | El sistema debe responder en < 2 segundos  | Test de respuesta promedio |
| RNF04 | Disponibilidad | Debe tener uptime > 99.5%                  | Monitoreo de servicios     |
| ...   | ...            | ...                                        | ...                        |

---

## 4. Requisitos de Integración (Opcional)

Describe **cómo interactuará el sistema con otros sistemas o servicios**.

| ID   | Integración              | Descripción                               | Prioridad |
| ---- | ------------------------ | ----------------------------------------- | --------- |
| RI01 | Base de datos PostgreSQL | Gestión de recursos y atributos dinámicos | Alta      |
| RI02 | Servicio de correo       | Notificación de expiración de usuarios    | Media     |
| ...  | ...                      | ...                                       | ...       |

---

## 5. Glosario

Define términos clave que se usarán en los requisitos.

- Recurso: Cualquier elemento crítico que requiera control de acceso (PostgreSQL, servidor, bucket S3, etc.)
- Usuario temporal: Usuario con acceso limitado en tiempo y permisos.
- Atributo dinámico: Propiedad de un recurso que puede variar según el tipo de recurso.
