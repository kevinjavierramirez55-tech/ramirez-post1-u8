# CRUD Estudiantes - Spring Boot con JPA y MySQL

## Autor

- **Nombre:** Kevin Ramirez  
- **Código:** 02220131008  
- **Programa:** Ingeniería de Sistemas  
- **Unidad:** 8 Persistencia con JPA/Hibernate  
- **Actividad:** Post-Contenido 1  
- **Fecha:** 20/04/2026  

Aplicación Web Java con Spring Boot que implementa un CRUD completo de estudiantes utilizando JPA, Hibernate y MySQL.

---

## Descripción del Proyecto

Este proyecto consiste en el desarrollo de una aplicación web para la gestión de estudiantes, utilizando **Spring Boot** junto con **Spring Data JPA** y **Hibernate** como proveedor ORM.

La aplicación permite realizar operaciones CRUD (Crear, Leer, Actualizar, Eliminar) sobre la entidad *Estudiante*, con persistencia real en una base de datos MySQL. Además, se implementan validaciones con anotaciones de Bean Validation y manejo de formularios con Thymeleaf.

---

## Prerrequisitos

Antes de ejecutar el proyecto, se debe contar con:

- JDK 17 o superior instalado y configurado en el PATH.
- MySQL 8.x instalado y en ejecución.
- IntelliJ IDEA o VS Code.
- Maven 3.x o usar el wrapper `mvnw`.
- Conocimientos en:
  - Spring Boot (controladores, Thymeleaf)
  - JPA (@Entity, @Id, @GeneratedValue)

---

## Estructura del Proyecto


estudiantes/
├── src/main/java/com/universidad/estudiantes/
│ ├── EstudiantesApplication.java
│ ├── controller/
│ │ └── EstudianteController.java
│ ├── model/
│ │ └── Estudiante.java
│ ├── repository/
│ │ └── EstudianteRepository.java
│ └── service/
│ └── EstudianteService.java
├── src/main/resources/
│ ├── application.properties
│ └── templates/
│ └── estudiantes/
│ ├── lista.html
│ ├── formulario.html
│ └── confirmar-eliminar.html
├── pom.xml
└── mvnw


---

## Arquitectura del Proyecto

**Modelo:**
- Estudiante: entidad JPA con validaciones (@NotBlank, @Email, @Size).

**Repositorio:**
- EstudianteRepository: extiende JpaRepository para acceso a datos.

**Servicio:**
- EstudianteService: contiene lógica de negocio y manejo transaccional.

**Controlador:**
- EstudianteController: gestiona rutas HTTP y validaciones.

**Vista:**
- Thymeleaf para renderizado dinámico.
- Formularios con validación y mensajes de error.

---

## Configuración de la Base de Datos

1. Crear la base de datos en MySQL:


CREATE DATABASE estudiantes_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'appuser'@'localhost' IDENTIFIED BY 'apppass';
GRANT ALL PRIVILEGES ON estudiantes_db.* TO 'appuser'@'localhost';
FLUSH PRIVILEGES;


2. Configurar `application.properties`:


spring.datasource.url=jdbc:mysql://localhost:3306/estudiantes_db?useSSL=false&serverTimezone=UTC
spring.datasource.username=appuser
spring.datasource.password=apppass
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect

server.port=8080


---

## Funcionalidades Implementadas

- Registro de estudiantes.
- Listado de estudiantes.
- Edición de datos.
- Eliminación de registros.
- Persistencia en MySQL.
- Validaciones:
  - Nombre obligatorio y con longitud mínima.
  - Correo válido y único.
  - Campos obligatorios.
- Manejo de errores en formularios.
- Uso de JPA con Hibernate.

---

## Instrucciones de Ejecución

1. Clonar el repositorio:


https://github.com/kevinjavierramirez55-tech/ramirez-post1-u8.git


2. Configurar la base de datos MySQL (ver sección anterior).

3. Ejecutar la aplicación:


mvn spring-boot:run


O con wrapper:


./mvnw spring-boot:run


4. Acceder en el navegador:


http://localhost:8080/estudiantes


---

## Checkpoint de Verificación

- La aplicación inicia sin errores.
- Hibernate crea automáticamente la tabla `estudiantes`.
- Se pueden registrar nuevos estudiantes.
- Los datos se almacenan en MySQL correctamente.
- Se pueden editar registros existentes.
- Se pueden eliminar estudiantes.
- Las validaciones muestran errores sin perder datos del formulario.

---

## Capturas del Proyecto

Las capturas se encuentran en la carpeta `evidencias/`.

### Aplicación corriendo, Hibernate genera tabla estudiantes

![app corriendo](evidencias/app%20arrancando.png)

### Agregar y registrar 3 estudiantes 

![crear](evidencias/registro%20de%20estudiantes.png)

### Editar y eliminar estudiante
![editar eliminar error](evidencias//editar%20y%20eliminar%20estudiante.png)
