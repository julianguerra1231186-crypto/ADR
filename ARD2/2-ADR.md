# ADR-002: Implementación de MapStruct para Mapeo Entity ↔ DTO

## Estado
Aceptado

## Fecha
2026-03

---

## Descripcion

En el microservicio `ms-users`, la conversión entre entidades (`User`) y objetos de transferencia de datos (`UserRequestDTO`, `UserResponseDTO`) se realizaba mediante mapeo manual dentro de la capa de servicios.

Este enfoque generaba:

- Duplicación de código
- Mayor probabilidad de errores
- Baja mantenibilidad
- Código más difícil de escalar

Adicionalmente, ya se había implementado una arquitectura basada en servicios genéricos (`BaseServiceImpl`), por lo que era necesario complementar esta mejora eliminando la lógica manual de mapeo.

---

## Decisión

Se decidió implementar **MapStruct** como herramienta de mapeo automático entre entidades y DTOs.

MapStruct permite generar código de mapeo en tiempo de compilación, eliminando la necesidad de escribir conversiones manuales.

---

## Implementación

### 1. Se agregó MapStruct al proyecto

Se configuró en el `pom.xml` junto con el `maven-compiler-plugin` para soportar la generación automática de código dentro del entorno Docker.
![](https://github.com/julianguerra1231186-crypto/ADR/blob/main/ARD2/img/Captura%20de%20pantalla%20(299).png)

---

### 2. Se creó el mapper con MapStruct


@Mapper(componentModel = "spring")
public interface UserMapper {

    UserResponseDTO toResponseDto(User user);

    User toEntity(UserRequestDTO dto);

    void updateEntityFromDto(UserRequestDTO dto, @MappingTarget User entity);
}

![](https://github.com/julianguerra1231186-crypto/ADR/blob/main/ARD2/img/Captura%20de%20pantalla%20(306).png)


---

### 3. Eliminación de mapeo manual

Se eliminó la lógica manual de conversión que utilizaba setters dentro de la implementación del servicio.

---

### 4. Eliminación de EntityMapper

La interfaz EntityMapper fue eliminada debido a que su funcionalidad fue completamente reemplazada por MapStruct.

![](https://github.com/julianguerra1231186-crypto/ADR/blob/main/ARD2/img/Captura%20de%20pantalla%20(305).png)
![](https://github.com/julianguerra1231186-crypto/ADR/blob/main/ARD2/img/Captura%20de%20pantalla%20(306).png)

---

### 5. Integración con Docker

La compilación del proyecto se realizó dentro del contenedor Docker utilizando:

docker-compose build --no-cache
docker-compose up

MapStruct generó automáticamente las implementaciones necesarias durante el build del contenedor.
![](https://github.com/julianguerra1231186-crypto/ADR/blob/main/ARD2/img/Captura%20de%20pantalla%20(308).png)

---

### 6. Validación
Se realizaron pruebas funcionales utilizando Postman:
 - GET /users
Retorna lista de usuarios correctamente
![](https://github.com/julianguerra1231186-crypto/ADR/blob/main/ARD2/img/Captura%20de%20pantalla%20(309).png)
 - POST /users
Crea usuarios correctamente
![](https://github.com/julianguerra1231186-crypto/ADR/blob/main/ARD2/img/Captura%20de%20pantalla%20(307).png)

Todas las respuestas se generaron correctamente usando el mapper automático de MapStruct.


