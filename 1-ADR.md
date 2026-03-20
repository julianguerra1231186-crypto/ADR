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

### 📂 2. ADR-002 — Implementación de MapStruct para Mapeo Automático

Esta carpeta contiene:
- La documentación del ADR-002 
- La implementación de MapStruct en el microservicio ms-users  
- Evidencias de:
  - Eliminación del mapeo manual en la capa de servicios
  - Implementación de UserMapper con MapStruct (@Mapper)  
  - Eliminación de la interfaz EntityMapper
  - Generación automática de código de mapeo en tiempo de compilación
  - Correcta ejecución del microservicio en Docker
  - Pruebas de endpoints en Postman con respuestas correctas

🔗 Enlace al ADR-002:

https://github.com/julianguerra1231186-crypto/ADR/blob/main/ARD2/2-ADR.md

---

### 📂 3. ADR-003 — Excepciones Personalizadas por Dominio  

Esta carpeta contiene:
- La documentación del ADR-003  
- La implementación del manejo de excepciones en el microservicio ms-users  
- Evidencias de:  
  - Eliminación del uso de RuntimeException en la capa de servicios  
  - Implementación de ResourceNotFoundException como excepción de dominio  
  - Implementación de GlobalExceptionHandler (@RestControllerAdvice)  
  - Centralización del manejo de errores en la aplicación  
  - Respuestas estructuradas en formato JSON  
  - Uso correcto de códigos HTTP (400)  
  - Correcta ejecución del microservicio en Docker  
  - Pruebas de endpoints en Postman con manejo de errores controlado  
🔗 Enlace al ADR-003:  
https://github.com/julianguerra1231186-crypto/ADR/blob/main/ADR3/3-ADR.md
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
