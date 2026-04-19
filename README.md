# Gestión de Estudiantes con Spring Boot + JPA + MySQL

## Autor

- **Nombre:** Jhoseth Esneider Rozo Carrillo
- **Código:** 02230131027
- **Asignatura:** Programación Web
- **Programa:** Ingeniería de Sistemas
- **Unidad:** 8 - Persistencia con JPA/Hibernate
- **Actividad:** Post-Contenido 1
- **Fecha:** 19/04/2026

---

## Descripción del Proyecto

Aplicación CRUD completa para gestionar estudiantes utilizando Spring Boot, Spring Data JPA, Hibernate y MySQL, implementando todos los patrones de arquitectura en capas (controller, service, repository, model).

---

## Objetivo

Implementar un sistema CRUD completo para la entidad Estudiante utilizando:

- Spring Boot
- Spring Data JPA
- Hibernate (ORM)
- MySQL
- Thymeleaf

La aplicación permite crear, listar, editar y eliminar estudiantes, con persistencia real en base de datos.

---

## Tecnologías Utilizadas

- **Spring Boot 3.2.5**: Framework principal
- **Spring Data JPA**: ORM y acceso a datos
- **Hibernate 6.4.4**: Proveedor JPA
- **MySQL Connector/J 8.3.0**: Driver JDBC
- **Thymeleaf 3.1.2**: Motor de plantillas
- **Jakarta Validation 3.0.2**: Validación de Bean Validation
- **Java 17**: Versión del lenguaje

---

## Configuración de la Base de Datos

### 1. Ingresar a MySQL

### Opción A: MySQL instalado localmente

# Verificar que MySQL está corriendo

mysql -u root -p -e "SELECT 1;"

### Opción B: Usar Docker (recomendado si no tienes MySQL)

# Crear contenedor MySQL

docker run -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root --name mysql-estudiantes mysql:8

# Esperar 10 segundos a que inicie

### 2. Crear base de datos y usuario

Ejecuta estos comandos en MYSQL:

mysql -u root -p

# Ingresa la contraseña: root (si usaste Docker) o tu contraseña de MySQL

# Dentro de la consola MySQL, copia y ejecuta:

CREATE DATABASE estudiantes_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'appuser'@'localhost' IDENTIFIED BY 'apppass';
GRANT ALL PRIVILEGES ON estudiantes_db.\* TO 'appuser'@'localhost';
FLUSH PRIVILEGES;
EXIT;

## 3: Compilar el Proyecto

Desde el directorio del proyecto:

./mvnw clean compile

Esperado: "BUILD SUCCESS"

## 4: Ejecutar la Aplicación

./mvnw spring-boot:run

Esperado: Ver en la consola:
Started EstudiantesApplication in X.XXX seconds

---

## Estructura del Proyecto

- src/main/java/com/universidad/estudiantes/
- ├── controller/
- │ └── EstudianteController.java
- ├── model/
- │ └── Estudiante.java
- ├── repository/
- │ └── EstudianteRepository.java
- ├── service/
- │ └── EstudianteService.java
- └── EstudiantesApplication.java

- src/main/resources/
- ├── application.properties
- └── templates/estudiantes/
- ├── lista.html
- ├── formulario.html
- └── confirmar-eliminar.html

---

## Arquitectura

El proyecto sigue el patrón MVC con separación en capas:

Model: Entidad Estudiante con anotaciones JPA y validaciones
Repository: Acceso a datos con JpaRepository
Service: Lógica de negocio + manejo transaccional
Controller: Manejo de rutas y formularios

---

## Checkpoints de Verificación

✔ Checkpoint 1
La aplicación inicia sin errores
Hibernate crea la tabla automáticamente
USE estudiantes_db;
SHOW TABLES;
✔ Checkpoint 2
Crear al menos 3 estudiantes desde:
http://localhost:8080/estudiantes/nuevo
Verificar en MySQL:
SELECT \* FROM estudiantes;
✔ Checkpoint 3
Editar un estudiante → cambios reflejados
Eliminar un estudiante → desaparece de la BD
Validación de correo único funciona correctamente

---

## Capturas del Proyecto

Las siguientes capturas se encuentran en la carpeta `/evidencias/`:

# Ejecutar app sin errores

![Captura app_arrancando](evidencias/captura_app_arrancando.png)

## Agregar 3 estudiantes y verificar persistencia

![Captura registros_estudiantes_persistencia](evidencias/captura_registros_estudiantes_persistidos.png)

## Editar, Eliminar y agregar usuario con datos duplicados para verificar error

![Captura editar_eliminar_error](evidencias/captura_editar_eliminar_errores_por_verificación.png)

---

## Conclusión

Se implementó correctamente un sistema CRUD completo con persistencia en MySQL utilizando JPA/Hibernate, aplicando buenas prácticas de arquitectura en capas y validación de datos.
