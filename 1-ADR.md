# 📂 PORTADA — REPOSITORIO DE ADR Y EVIDENCIAS  
## 🧾 Proyecto: PulpApp - Sistema Distribuido de Venta Online de Pulpas Naturales

---

## 👨‍💻 Autor
**Julian Guerra**

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
