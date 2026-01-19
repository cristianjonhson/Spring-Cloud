# Department Service

## Descripción del Servicio
El `Department-Service` es un microservicio que gestiona la información relacionada con los departamentos de una organización. Este servicio está diseñado para ser parte de un sistema de microservicios más amplio y se registra en un servidor Eureka para el descubrimiento de servicios.

## Tecnologías Utilizadas
- **Java 11**
- **Spring Boot 2.7.15**
- **Spring Cloud 2021.0.7**
- **H2 Database**
- **Hibernate**
- **Maven**

## Estructura del Servicio
```
Department-Service/
├── src/
│   ├── main/
│   │   ├── java/com/company/department/
│   │   │   ├── controller/  # Controladores REST
│   │   │   ├── model/       # Clases de modelo (entidades JPA)
│   │   │   ├── repository/  # Repositorios JPA
│   │   │   └── service/     # Lógica de negocio
│   ├── resources/
│       ├── application.yml  # Configuración del servicio
├── pom.xml                  # Configuración de dependencias de Maven
├── DepartmentService.postman_collection.json  # Colección de Postman para pruebas
```

## Configuración del Servicio
1. Configura el archivo `application.yml` según tus necesidades. Por defecto, el servicio está configurado para:
   - Puerto: `8082`
   - Base de datos H2 persistente en la ruta `~/department-service-db`.

2. Asegúrate de que el servidor Eureka esté en ejecución antes de iniciar este servicio.

## Ejecución del Servicio
1. Navega al directorio del servicio:
   ```bash
   cd Department-Service
   ```

2. Ejecuta el servicio:
   ```bash
   mvn spring-boot:run
   ```

3. El servicio estará disponible en [http://localhost:8082](http://localhost:8082).

4. Accede a la consola H2 para verificar la base de datos:
   - URL: [http://localhost:8082/h2-console](http://localhost:8082/h2-console)
   - **JDBC URL**: `jdbc:h2:file:~/department-service-db`
   - **User Name**: `sa`
   - **Password**: (dejar vacío)

5. Prueba los endpoints utilizando Postman o cURL. Puedes importar la colección de Postman disponible en `DepartmentService.postman_collection.json`.

## Endpoints
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
- La base de datos H2 se configura como persistente para facilitar las pruebas y el desarrollo.
- Puedes modificar la configuración en el archivo `application.yml` según tus necesidades.

## Contribuciones
Si deseas contribuir a este servicio, por favor realiza un fork del repositorio, crea una rama para tus cambios y envía un pull request.

## Licencia
Este proyecto está bajo la licencia MIT. Puedes consultar el archivo `LICENSE` para más detalles.