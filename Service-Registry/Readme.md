# Service Registry

## Descripción del Servicio
El `Service-Registry` es un servidor Eureka que actúa como un registro de servicios para un sistema de microservicios. Permite que los servicios se registren y descubran entre sí, facilitando la comunicación y la escalabilidad.

## Tecnologías Utilizadas
- **Java 11**
- **Spring Boot 2.7.15**
- **Spring Cloud 2021.0.7**
- **Eureka Server**
- **Maven**

## Estructura del Servicio
```
Service-Registry/
├── src/
│   ├── main/
│   │   ├── java/com/company/registry/
│   │   │   └── ServiceRegistryApplication.java  # Clase principal del servidor Eureka
│   ├── resources/
│       ├── application.yml  # Configuración del servidor Eureka
├── pom.xml                  # Configuración de dependencias de Maven
```

## Configuración del Servicio
1. Configura el archivo `application.yml` según tus necesidades. Por defecto, el servidor está configurado para:
   - Puerto: `8762`

## Ejecución del Servicio
1. Navega al directorio del servicio:
   ```bash
   cd Service-Registry
   ```

2. Ejecuta el servidor:
   ```bash
   mvn spring-boot:run
   ```

3. El servidor estará disponible en [http://localhost:8762](http://localhost:8762).

## Notas
- Asegúrate de que el servidor Eureka esté en ejecución antes de iniciar otros servicios que dependan de él.
- Puedes modificar la configuración en el archivo `application.yml` según tus necesidades.

## Contribuciones
Si deseas contribuir a este servicio, por favor realiza un fork del repositorio, crea una rama para tus cambios y envía un pull request.

## Licencia
Este proyecto está bajo la licencia MIT. Puedes consultar el archivo `LICENSE` para más detalles.