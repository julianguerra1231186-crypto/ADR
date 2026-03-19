# 📂 PORTADA — REPOSITORIO DE ADR Y EVIDENCIAS  
## 🧾 Proyecto: PulpApp - Sistema Distribuido de Venta Online de Pulpas Naturales

---

## 👨‍💻 Autor
**Julian Guerra**

---

## 📌 Mesa de Trabajo — Historias de Usuario

Las historias de usuario relacionadas con la implementación del ADR-001 y el seguimiento del desarrollo pueden ser evidenciadas en la siguiente mesa de trabajo en Jira.

En este espacio se documenta la planificación, ejecución y avance de las actividades realizadas durante el proceso de refactorización del microservicio `ms-users`.

🔗 Acceso a la mesa de trabajo:  
https://julianguerra1231186-1773894024267.atlassian.net/jira/software/projects/KAN/list?jql=project+%3D+KAN+ORDER+BY+created+DESC&atlOrigin=eyJpIjoiMTY5NjZiNWRmY2I3NDg1ZWExMDJjOTIyMDJkMjg3YjUiLCJwIjoiaiJ9

---

## 📘 Descripción General

Este repositorio contiene la documentación, implementación y evidencias de las decisiones arquitectónicas (ADR - *Architecture Decision Records*) aplicadas en el desarrollo del sistema **PulpApp**.

Cada carpeta representa un ADR específico, donde se incluye:

- 📄 Documento del ADR (explicación técnica completa)  
- 💻 Código implementado en el microservicio  
- 🧪 Evidencias de funcionamiento (Docker, Postman, ejecución del sistema)  

El objetivo de este repositorio es demostrar la aplicación de buenas prácticas de desarrollo backend, principios de arquitectura limpia y diseño orientado a objetos en Java.

---

## 📁 Estructura del Repositorio

### 📂 1. ADR-001 — Refactorización de la Capa de Servicios

Esta carpeta contiene:

- La documentación del ADR-001  
- La implementación de la refactorización en el microservicio `ms-users`  
- Evidencias de:
  - Eliminación de duplicación de código CRUD  
  - Uso de `BaseServiceImpl`  
  - Implementación de `EntityMapper`  
  - Correcta ejecución en Docker  
  - Pruebas de endpoints en Postman  


🔗 Enlace al ADR-001:  
https://github.com/julianguerra1231186-crypto/ADR/blob/main/ARD1/adr.md



---

### 📂 2. ADR-002 — (Espacio para siguiente decisión arquitectónica)

Esta carpeta está destinada para documentar futuras decisiones arquitectónicas del sistema.

Aquí se incluirán:

- Nuevas mejoras estructurales  
- Cambios en la arquitectura  
- Nuevas implementaciones relevantes  

---

### 📂 3. ADR-003 — (Espacio para evolución del sistema)

Esta carpeta permitirá documentar la evolución del sistema a medida que se agreguen nuevas funcionalidades, como:

- Seguridad (JWT, autenticación)  
- Manejo de roles  
- Optimización de servicios  

---

## 🎯 Objetivo del Repositorio

Este repositorio tiene como finalidad:

- Documentar decisiones arquitectónicas de forma clara y estructurada  
- Evidenciar la implementación real en código  
- Mostrar pruebas funcionales del sistema  
- Aplicar buenas prácticas de ingeniería de software  

---

## 🚀 Tecnologías Utilizadas

- Java 17  
- Spring Boot  
- Spring Data JPA  
- Spring Security  
- PostgreSQL  
- Docker  
- Maven  

---

## 🧾 Nota Final

Este repositorio evidencia la aplicación de principios de:

- Clean Architecture  
- SOLID  
- DRY (Don't Repeat Yourself)  

en un entorno real de desarrollo backend basado en microservicios.
