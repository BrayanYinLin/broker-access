# 🛡️ Bróker de Acceso Temporal

Este proyecto es un **Bróker de Acceso Temporal a Recursos** para equipos de desarrollo. Permite crear usuarios temporales, gestionar accesos a recursos críticos y mantener un registro de auditoría. El monorepo contiene:

* `/apps/backend` 🖥️: Spring Boot API
* `/apps/client` 🌐: Frontend React
* `/docs` 📄: Documentación, análisis y diseño del sistema

Arquitectura:

👤 Usuario (Navegador) → 🔗 Nginx (Frontend + Proxy)
Nginx → 🌐 Frontend React
Nginx → 🖥️ Spring Boot API → 🗄️ PostgreSQL / Recursos

---

## ⚙️ Configuración del proyecto

**Backend (Spring Boot)**

1. Entrar a `/apps/backend`
2. Configurar `application.properties` o `application.yml` (URL de PostgreSQL, credenciales, JWT secret) 🔑
3. Ejecutar: `./mvnw spring-boot:run` 🚀

**Frontend (React)**

1. Entrar a `/apps/client`
2. Instalar dependencias: `npm install` 📦
3. Ejecutar: `npm start` ▶️

---

## 🏃‍♂️ Flujo principal del sistema

1. 🛠️ Setup inicial: crear primer admin y registrar recursos.
2. 🔑 Login: usuarios autenticados reciben JWT en cookies.
3. 🕒 Solicitud de acceso temporal: backend genera credenciales temporales y registra log.
4. ⏱️ Revocación automática: Spring Scheduler revisa accesos expirados y revoca usuarios temporales.

---

## 📝 Notas importantes

* Nginx sirve **frontend React** y hace **reverse proxy** a `/api` hacia Spring Boot.
* Backend valida JWT y API key en cabecera enviada por Nginx.
* Logs y auditoría se guardan en PostgreSQL 🗄️.
* Para desarrollo, el proxy se puede simplificar con configuración local.

---

## 📂 Estructura de carpetas

`/apps`
 `/backend` 🖥️ → Spring Boot
 `/client` 🌐 → React
`/docs` 📄 → Documentación y diagramas

---

## 🚀 Futuras mejoras

* Registro de usuarios auto-registrados con aprobación de admin 👤
* Métricas y dashboard de accesos temporales 📊
* Soporte de múltiples tipos de recursos (bases de datos, servidores, etc.) 🗄️🖥️
