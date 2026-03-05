# Instrucciones para levantar la aplicación y probar la API

## Requisitos

* Java 21
* Maven

## Levantar la aplicación

Ejecutar:

```
mvn spring-boot:run
```

La aplicación quedará disponible en:

```
http://localhost:8080
```

Para probar los endpoints se puede usar Postman, curl o Swagger.

---

# 1. Login

Endpoint

```
POST http://localhost:8080/auth/login
```

Body

```json
{
  "username": "tu_usuario",
  "password": "tu_contraseña"
}
```

Respuesta

```json
{
  "token": "jwt_token"
}
```

El token debe enviarse en los siguientes endpoints en el header:

```
Authorization: Bearer <jwt_token>
```

---

# 2. Obtener todas las tareas

Endpoint

```
GET http://localhost:8080/tasks
```

Header

```
Authorization: Bearer <jwt_token>
```

Respuesta

Lista de tareas en formato JSON.

---

# 3. Crear tarea

Endpoint

```
POST http://localhost:8080/tasks/create
```

Header

```
Authorization: Bearer <jwt_token>
```

Body

```json
{
  "nombre": "Nueva Tarea",
  "descripcion": "Descripción de la tarea",
  "estado": {
    "id": 1
  }
}
```

Respuesta

Código 201 con la tarea creada.

---

# 4. Obtener tarea por id

Endpoint

```
GET http://localhost:8080/tasks/gettask/{id}
```

Header

```
Authorization: Bearer <jwt_token>
```

Ejemplo

```
GET http://localhost:8080/tasks/gettask/1
```

---

# 5. Actualizar tarea

Endpoint

```
PUT http://localhost:8080/tasks/update/{id}
```

Header

```
Authorization: Bearer <jwt_token>
```

Body

```json
{
  "nombre": "Tarea Actualizada",
  "descripcion": "Nueva descripción",
  "estado": {
    "id": 2
  }
}
```

---

# 6. Eliminar tarea

Endpoint

```
DELETE http://localhost:8080/tasks/delete/{id}
```

Header

```
Authorization: Bearer <jwt_token>
```

Ejemplo

```
DELETE http://localhost:8080/tasks/delete/1
```

---

# Notas

* Primero se debe obtener el token usando `/auth/login`.
* Luego usar ese token en el header `Authorization`.
* Los ids utilizados deben existir en la base de datos.
