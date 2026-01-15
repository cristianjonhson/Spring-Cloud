# Spring Cloud

Spring Cloud es un conjunto de herramientas para construir sistemas distribuidos y microservicios en Java. Proporciona soluciones para problemas comunes en arquitecturas distribuidas, como configuración centralizada, descubrimiento de servicios, balanceo de carga, tolerancia a fallos, y más.

## Características principales

- **Configuración centralizada**: Administra la configuración de múltiples aplicaciones desde un solo lugar.
- **Descubrimiento de servicios**: Facilita la comunicación entre microservicios mediante un registro central.
- **Balanceo de carga**: Distribuye las solicitudes entre instancias de servicios.
- **Tolerancia a fallos**: Implementa patrones como circuit breakers y retries.
- **Gateway API**: Proporciona un punto de entrada único para las solicitudes.
- **Monitoreo y trazabilidad**: Integra herramientas para rastrear y monitorear servicios.

## Requisitos previos

- **Java 11 o superior**
- **Maven o Gradle**
- **Spring Boot 2.5+**

## Instalación

1. Agrega las dependencias necesarias en tu archivo `pom.xml` o `build.gradle`:

    **Maven:**
    ```xml
    <dependency>
         <groupId>org.springframework.cloud</groupId>
         <artifactId>spring-cloud-starter</artifactId>
    </dependency>
    ```

    **Gradle:**
    ```groovy
    implementation 'org.springframework.cloud:spring-cloud-starter'
    ```

2. Configura el archivo `application.yml` o `application.properties` según tus necesidades.

3. Habilita las anotaciones necesarias en tu aplicación, como `@EnableDiscoveryClient` o `@EnableConfigServer`.

## Ejemplo básico

### Configuración del servidor de configuración

1. Crea un proyecto Spring Boot y agrega la dependencia:
    ```xml
    <dependency>
         <groupId>org.springframework.cloud</groupId>
         <artifactId>spring-cloud-config-server</artifactId>
    </dependency>
    ```

2. Habilita el servidor de configuración:
    ```java
    @SpringBootApplication
    @EnableConfigServer
    public class ConfigServerApplication {
         public static void main(String[] args) {
              SpringApplication.run(ConfigServerApplication.class, args);
         }
    }
    ```

3. Configura el repositorio de configuración en `application.yml`:
    ```yaml
    spring:
      cloud:
         config:
            server:
              git:
                 uri: https://github.com/tu-repositorio/config-repo
    ```

### Cliente de configuración

1. Agrega la dependencia en el cliente:
    ```xml
    <dependency>
         <groupId>org.springframework.cloud</groupId>
         <artifactId>spring-cloud-starter-config</artifactId>
    </dependency>
    ```

2. Configura el cliente para conectarse al servidor de configuración:
    ```yaml
    spring:
      application:
         name: mi-aplicacion
      cloud:
         config:
            uri: http://localhost:8888
    ```

## Recursos adicionales

- [Documentación oficial de Spring Cloud](https://spring.io/projects/spring-cloud)
- [Guías de inicio rápido](https://spring.io/guides)

## Licencia

Este proyecto está bajo la licencia [MIT](LICENSE).