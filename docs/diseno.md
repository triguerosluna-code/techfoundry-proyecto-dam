# Sección 5.1: Definición y Planificación del Proyecto (Booklu)

## 1. Objetivo del Proyecto
El sistema Booklu es una API REST desarrollada para la gestión y catalogación de bibliotecas personales, permitiendo el control centralizado de obras en formatos físicos y digitales junto con el seguimiento de préstamos a terceros. La solución está dirigida a lectores particulares que buscan resolver la dispersión geográfica de sus libros y mantener la trazabilidad de su colección. El backend está construido en Java con Spring Boot, integrado a una base de datos MySQL y probado mediante Postman para garantizar la correcta persistencia y manipulación de datos.

## 2. Justificación Tecnológica
Para el desarrollo de la API REST se ha seleccionado Java con Spring Boot. Esta elección se justifica por la robustez del ecosistema Java, su tipado fuerte y la facilidad que ofrece Spring Boot para implementar la arquitectura de tres capas (Controlador, Servicio, Repositorio/DAO). Además, permite una integración limpia con MySQL mediante Spring Data JPA/JDBC y facilita la creación de endpoints CRUD bien estructurados y seguros.

## 3. Tabla de Endpoints de la API REST
| Método | URL | Descripción | Request Body (Entrada) | Response (Salida esperada) |
|---|---|---|---|---|
| GET | /api/usuarios | Lista todos los usuarios/lectores. | Ninguno | 200 OK + Array JSON de usuarios |
| POST | /api/usuarios | Registra un nuevo usuario/lector. | {"nombre": "String", "email": "String"} | 201 Created + JSON del usuario creado |
| PUT | /api/usuarios/{id} | Actualiza el nombre o email de un usuario. | {"nombre": "String", "email": "String"} | 200 OK + JSON actualizado (o 404 Not Found) |
| DELETE | /api/usuarios/{id} | Elimina un usuario por su ID. | Ninguno | 204 No Content (o 404 Not Found) |
| GET | /api/libros | Lista todos los libros en la biblioteca. | Ninguno | 200 OK + Array JSON de libros |
| GET | /api/prestamos | Lista préstamos uniendo datos de usuario y libro (JOIN). | Ninguno | 200 OK + Array JSON con información combinada |
| GET | /api/prestamos?usuario_id={id} | Filtra los préstamos pertenecientes a un usuario específico. | Ninguno | 200 OK + Array JSON filtrado |