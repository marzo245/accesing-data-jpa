# Accesing Data JPA

Este proyecto es una implementación de ejemplo siguiendo la guía oficial de Spring: [Accessing Data with JPA](https://spring.io/guides/gs/accessing-data-jpa). El objetivo es demostrar cómo trabajar con bases de datos relacionales utilizando Spring Data JPA en una aplicación Java.

## Características

- Persistencia de entidades con Spring Data JPA
- Uso de repositorios para operaciones CRUD
- Configuración sencilla en `application.properties`
- Pruebas unitarias básicas
- Basado en la guía oficial de Spring

## Estructura del Proyecto

```
├── src
│   ├── main
│   │   ├── java
│   │   │   └── com
│   │   │       └── ejemplo
│   │   │           └── acceso
│   │   │               └── [clases_java]
│   │   └── resources
│   │       └── application.properties
│   └── test
│       └── java
│           └── com
│               └── ejemplo
│                   └── acceso
│                       └── [test_java]
├── pom.xml
└── README.md
```

## Requisitos

- Java 17+
- Maven 3.6+
- (Opcional) Docker, para bases de datos externas

## Instalación y Ejecución

1. **Clonar el repositorio**
   ```sh
   git clone https://github.com/marzo245/accesing-data-jpa.git
   cd accesing-data-jpa
   ```

2. **Construir el proyecto**
   ```sh
   mvn clean package
   ```

3. **Ejecutar la aplicación**
   ```sh
   mvn spring-boot:run
   ```

4. **Acceso**
   - La aplicación inicia por defecto en `http://localhost:8080`

## Configuración

La configuración principal se encuentra en el archivo `src/main/resources/application.properties`. Por ejemplo:

```properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.h2.console.enabled=true
```

Puedes modificar para utilizar otra base de datos (MySQL, PostgreSQL, etc.) cambiando los valores anteriores.

## Ejemplo de Entidad y Repositorio

```java
@Entity
public class Person {
    @Id @GeneratedValue
    private Long id;
    private String name;
    // getters y setters
}

public interface PersonRepository extends CrudRepository<Person, Long> {
    List<Person> findByName(String name);
}
```

## Pruebas

Para ejecutar las pruebas unitarias:
```sh
mvn test
```

## Referencias

- [Guía oficial Spring Accessing Data with JPA](https://spring.io/guides/gs/accessing-data-jpa)
- [Documentación de Spring Data JPA](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/)

## Licencia

MIT License. Consulta el archivo `LICENSE` para más detalles.

---
Inspirado en la guía oficial de Spring.
