# ADR-003: Excepciones Personalizadas por Dominio

## Estado
Aceptado

## Fecha
2026-03

---

## Descripcion

En la implementación inicial del microservicio `ms-users`, el manejo de errores se realizaba utilizando excepciones genéricas (`RuntimeException`), lo cual generaba:

Este enfoque generaba:

- Respuestas poco claras para el cliente
- Falta de control sobre los códigos HTTP
- Dificultad para mantener y escalar el sistema
- Inconsistencia en la estructura de errores

Esto afectaba la calidad de la API y la experiencia del consumidor.

---

## Decisión

Se decide implementar un sistema de manejo de errores basado en:

- Excepciones personalizadas por dominio
- Un manejador global de excepciones (`@RestControllerAdvice`)
- Respuestas estructuradas en formato JSON

---

## Implementación

### 1. Creación de excepción personalizada

Se implementa la clase:

public class ResourceNotFoundException extends RuntimeException {
    public ResourceNotFoundException(String message) {
        super(message);
    }
}

![](https://github.com/julianguerra1231186-crypto/ADR/blob/main/ADR3/img/Captura%20de%20pantalla%20(320).png)

### 2. Manejo global de excepciones

Se implementa:
![](https://github.com/julianguerra1231186-crypto/ADR/blob/main/ADR3/img/Captura%20de%20pantalla%20(317).png)
Esto centraliza el manejo de errores en toda la aplicación.


### 3. Integración en la capa de servicio

Se reemplazan validaciones manuales por excepciones:

User user = repository.findById(id)
    .orElseThrow(() ->
        new ResourceNotFoundException("User not found with id: " + id)
    );

![](https://github.com/julianguerra1231186-crypto/ADR/blob/main/ADR3/img/Captura%20de%20pantalla%20(318).png)


###  4. Pruebas en Postman

- Se realiza una petición a un recurso inexistente:
  - GET http://localhost:8081/users/99999
- Respuesta obtenida:
        {
          "error": "User not found"
        }
- Código HTTP:
  - 400 Bad Request
![](https://github.com/julianguerra1231186-crypto/ADR/blob/main/ADR3/img/Captura%20de%20pantalla%20(321).png)
- GET /users Retorna lista de usuarios correctamente
![](https://github.com/julianguerra1231186-crypto/ADR/blob/main/ADR3/img/Captura%20de%20pantalla%20(322).png)

### 5. Ejecución en Docker

El sistema se ejecuta correctamente en contenedores:
- ms-users-service
- postgres
Sin errores en el arranque y con manejo adecuado de excepciones.
![](https://github.com/julianguerra1231186-crypto/ADR/blob/main/ADR3/img/Captura%20de%20pantalla%20(323).png)

### 6. Consecuencias
✔ Beneficios
Manejo centralizado de errores
Respuestas claras y consistentes
Mejor experiencia para el cliente
Código más limpio y mantenible

### 7. Consideraciones
Se debe extender el sistema para otros tipos de excepciones
Mantener consistencia en todos los microservicios

## Conclusión
La implementación de excepciones personalizadas junto con un manejador global mejora significativamente la calidad del sistema, permitiendo una arquitectura más robusta, escalable y alineada con buenas prácticas de desarrollo en microservicios.




