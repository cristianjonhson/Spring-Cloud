# Spring Cloud Microservices Project

## Descripción del Proyecto
Este proyecto es una implementación de un sistema de microservicios utilizando Spring Cloud. El sistema incluye un servicio de departamentos (`Department-Service`) que se registra en un servidor Eureka (`Service-Registry`). El objetivo principal es demostrar cómo construir y gestionar microservicios utilizando Spring Boot y Spring Cloud.

## Tecnologías Utilizadas
- **Java 11**: Lenguaje de programación principal.
- **Spring Boot 2.7.15**: Framework para el desarrollo de aplicaciones basadas en Java.
- **Spring Cloud 2021.0.7**: Para la gestión de microservicios y registro de servicios.
- **Eureka Server**: Para el registro y descubrimiento de servicios.
- **H2 Database**: Base de datos en memoria y persistente para pruebas.
- **Hibernate**: Framework ORM para la gestión de datos.
- **Maven**: Herramienta de gestión de dependencias y construcción del proyecto.

## Estructura del Proyecto
```
Spring-Cloud/
├── Department-Service/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/company/department/
│   │   │   │   ├── controller/  # Controladores REST
│   │   │   │   ├── model/       # Clases de modelo (entidades JPA)
│   │   │   │   ├── repository/  # Repositorios JPA
│   │   │   │   └── service/     # Lógica de negocio
│   │   ├── resources/
│   │       ├── application.yml  # Configuración del servicio
│   ├── pom.xml                  # Configuración de dependencias de Maven
├── Service-Registry/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/company/registry/
│   │   │   │   └── ServiceRegistryApplication.java
│   │   ├── resources/
│   │       ├── application.yml  # Configuración del servidor Eureka
│   ├── pom.xml                  # Configuración de dependencias de Maven
├── Readme.md                    # Documentación del proyecto
```

## Requisitos Previos
- **Java 11**
- **Maven**
- **Postman** (opcional, para pruebas de los endpoints)

## Configuración del Proyecto
1. Clona este repositorio:
   ```bash
   git clone https://github.com/cristianjonhson/Spring-Cloud.git
   cd Spring-Cloud
   ```

2. Asegúrate de tener Java 11 y Maven instalados en tu sistema.
   - Verifica la versión de Java:
     ```bash
     java -version
     ```
   - Verifica la versión de Maven:
     ```bash
     mvn -version
     ```

3. Configura el archivo `application.yml` en cada servicio según tus necesidades. Por defecto, el proyecto está configurado para:
   - Puerto del `Department-Service`: `8082`
   - Puerto del `Service-Registry`: `8762`
   - Base de datos H2 persistente en la ruta `~/department-service-db`.

## Ejecución del Proyecto
1. Inicia el servidor Eureka:
   ```bash
   cd Service-Registry
   mvn spring-boot:run
   ```
   El servidor estará disponible en [http://localhost:8762](http://localhost:8762).

2. Inicia el servicio de departamentos:
   ```bash
   cd ../Department-Service
   mvn spring-boot:run
   ```
   El servicio estará disponible en [http://localhost:8082](http://localhost:8082).

3. Accede a la consola H2 para verificar la base de datos:
   - URL: [http://localhost:8082/h2-console](http://localhost:8082/h2-console)
   - **JDBC URL**: `jdbc:h2:file:~/department-service-db`
   - **User Name**: `sa`
   - **Password**: (dejar vacío)

4. Prueba los endpoints utilizando Postman o cURL. Puedes importar la colección de Postman disponible en `Department-Service/DepartmentService.postman_collection.json`.

## Endpoints del Servicio de Departamentos
- **Crear un departamento** (POST):
  - URL: `/api/departments`
  - Body (JSON):
    ```json
    {
      "name": "HR",
      "description": "Human Resources"
    }
    ```

- **Obtener todos los departamentos** (GET):
  - URL: `/api/departments`

- **Obtener un departamento por ID** (GET):
  - URL: `/api/departments/{id}`

- **Actualizar un departamento** (PUT):
  - URL: `/api/departments/{id}`
  - Body (JSON):
    ```json
    {
      "name": "Finance",
      "description": "Finance Department"
    }
    ```

- **Eliminar un departamento** (DELETE):
  - URL: `/api/departments/{id}`

## Notas
- Asegúrate de que el servidor Eureka esté en ejecución antes de iniciar el servicio de departamentos.
- La base de datos H2 se configura como persistente para facilitar las pruebas y el desarrollo.
- Puedes modificar la configuración en el archivo `application.yml` según tus necesidades.

## Contribuciones
Si deseas contribuir a este proyecto, por favor realiza un fork del repositorio, crea una rama para tus cambios y envía un pull request.

## Licencia
Este proyecto está bajo la licencia MIT. Puedes consultar el archivo `LICENSE` para más detalles.