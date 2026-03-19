# 📘 ADR-001: Refactorización de la Capa de Servicios en `ms-users`

## 🧾 Información General

- **ID:** ADR-001  
- **Estado:** ✅ Aceptado  
- **Fecha:** 2026-03-19  
- **Proyecto:** PulpApp  
- **Microservicio:** ms-users  

---

## 🧠 Contexto

El microservicio `ms-users` fue desarrollado en Java utilizando Spring Boot y está encargado de la gestión de usuarios dentro de una arquitectura basada en microservicios.

En su estado inicial, la capa de servicios presentaba problemas estructurales importantes. Cada servicio implementaba manualmente las operaciones CRUD (`findAll`, `findById`, `save`, `update`, `delete`), lo que generaba duplicación de código y dificultaba la mantenibilidad del sistema.

Además, el mapeo entre entidades (`User`) y DTOs (`UserRequestDTO`, `UserResponseDTO`) se realizaba directamente dentro del servicio, aumentando el acoplamiento y la probabilidad de errores.

También se utilizaban excepciones genéricas (`RuntimeException`), lo cual no permitía un manejo adecuado de errores.

---

## ⚠️ Problema Identificado

Se detectaron los siguientes problemas:

- Duplicación de lógica CRUD en los servicios  
- Acoplamiento entre lógica de negocio y transformación de datos  
- Uso de excepciones genéricas sin contexto  
- Baja escalabilidad para nuevas entidades  
- Código repetitivo y difícil de mantener  

---

## 🎯 Decisión Arquitectónica

Se decidió refactorizar la capa de servicios aplicando principios de diseño orientado a objetos y buenas prácticas en Java.

La solución implementada se basó en tres componentes principales:

---

### 1. Implementación de una Interfaz Genérica (`IBaseService`)

Se creó una interfaz genérica que define las operaciones CRUD reutilizables para cualquier entidad:

public interface IBaseService<T, D, S> {
    List<D> findAll();
    D findById(Long id);
    D save(S dto);
    D update(Long id, S dto);
    void delete(Long id);
}
Esto permite estandarizar la lógica CRUD y evitar duplicación en múltiples servicios.

### 2. Creación de una Clase Base (BaseServiceImpl)

Se implementó una clase abstracta que centraliza toda la lógica CRUD utilizando genéricos:

public abstract class BaseServiceImpl<T, D, S, R extends JpaRepository<T, Long>>
        implements IBaseService<T, D, S> {

    protected final R repository;
    protected final EntityMapper<T, D, S> mapper;

    protected abstract String getEntityName();
}
Utiliza JpaRepository para el acceso a datos y un EntityMapper para transformar objetos.

### 3. Desacoplamiento del Mapeo (EntityMapper)

Se creó una interfaz para separar la transformación entre entidades y DTOs:

public interface EntityMapper<T, D, S> {
    D toResponseDto(T entity);
    T toEntity(S dto);
    void updateEntityFromDto(S dto, T entity);
}
Esto permite cumplir con el principio de responsabilidad única (SRP) y evita mezclar lógica de negocio con lógica de transformación.

### 4.Refactorización de UserServiceImpl

El servicio de usuarios fue modificado para heredar de la clase base:

@Service
public class UserServiceImpl
        extends BaseServiceImpl<User, UserResponseDTO, UserRequestDTO, UserRepository>
        implements IUserService {
}

Después de la refactorización, el servicio solo contiene lógica específica del dominio, como:
 - Buscar usuario por cédula
 - Validar usuario por cédula y teléfono

### 5.Mejora en el Manejo de Excepciones
Se reemplazaron las excepciones genéricas:
throw new RuntimeException("User not found");
Por una excepción personalizada:
throw new ResourceNotFoundException("User not found");

Esto mejora la claridad, trazabilidad y manejo de errores en el sistema.

### 🏗️ Resultado de la Refactorización

Antes:
 - Código duplicado en cada servicio
 - Mapeo manual dentro del servicio
 - Lógica mezclada
 - Uso de RuntimeException

Después:
 - Lógica CRUD centralizada en BaseServiceImpl
 - Mapper desacoplado
 - Servicios enfocados solo en lógica de negocio
 - Uso de excepciones personalizadas
![](https://github.com/julianguerra1231186-crypto/ADR/blob/main/ARD1/img/Captura%20de%20pantalla%20(291).png)

### 🧪 Validación y Pruebas
La implementación fue validada en un entorno real utilizando Docker y pruebas manuales con Postman.


### 🐳 Ejecución en Docker
El microservicio ms-users se ejecutó correctamente en contenedores Docker junto con PostgreSQL.
Se evidenció el correcto inicio del servicio mediante el log:
Tomcat started on port 8081

![](https://github.com/julianguerra1231186-crypto/ADR/blob/main/ARD1/img/Captura%20de%20pantalla%20(290).png)

<hr>

### 🌐 Pruebas en Postman
Se realizaron pruebas funcionales a los endpoints del microservicio:
🔹 Crear Usuario 
    POST http://localhost:8081/users
✔ Respuesta correcta con lista de usuarios
![](https://github.com/julianguerra1231186-crypto/ADR/blob/main/ARD1/img/Captura%20de%20pantalla%20(294).png)


