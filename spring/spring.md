# How To Start A Spring Project

---

## Maven Dependency

```xml

<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.7.4</version>
</parent>

<dependencies>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>

<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
</dependencies>
```

## Application YAML Configuration

```yaml
# Where the application is hosted on.
server:
  port: 8080
  servlet:
    context-path: /your-application-path

spring:
  application:
    name: your-application-name
  datasource:
    driver-class-name: org.postgresql.Driver
    url: your-db-url
    username: your-db-username
    password: your-db-password
  jpa:
    database-platform: org.hibernate.dialect.PostgreSQL10Dialect
    show-sql: true
    hibernate:
      # hibernate will drop and create your tables whenever you start your application.
      ddl-auto: create-drop
```

## Application Properties Configuration

```properties
# Where the application is hosted on.
server.port=8080
server.servlet.context-path=/path

spring.application.name=application_name
spring.datasource.driver-class-name=org.postgresql.Driver
spring.datasource.url=jdbc:postgresql://localhost:5432/postgres?
spring.datasource.username=username
spring.datasource.password=password
spring.jpa.database-platform=org.hibernate.dialect.PostgreSQLDialect
spring.jpa.show-sql=true
# hibernate will drop and create your tables whenever you start your application
spring.jpa.hibernate.ddl-auto=create-drop
```

## Spring AOP

### Main Driver Class

```java

@SpringBootApplication // will scan your project for annotations
public class Main {
    public static void main(String[] args) {
        SpringApplication.run(Main.class, args); // essentially run this project as a spring boot application
    }
}
```

### Controllers

```java

@CrossOrigin // expose endpoints to public
@RestController // specify that this class is a rest controller
@RequestMapping("/auth") // this controller is mapped to path /auth
public class AuthController {
    // the controller handles all the endpoint requests

  // additional mapping
  @PostMapping("/login")
  public Principal login(@RequestBody LoginRequest) {
    ...
  }
}
```

### Services

```java

@Service // to indicate that they're holding the business logic
@Transactional // making save or update
public class UserService {

}
```

### Repositories

```java

@Repository // to catch persistence-specific exceptions and re-throw them as one of Spring’s unified unchecked exceptions.
public interface UserRepository extends CrudRepository<User, String> {

}
```

#### Native Query

```java
@Modifying
@Query(value = "INSERT INTO in_category (id, category) VALUES (?1 , ?2)", nativeQuery = true)
void addCategory(String id, String category);
```

### Entities

```java

@Entity
@Table(name = "users")
public class User {
    @Id
    private String id;

    @Column(name = "username", nullable = false)
    private String username;

    @Column(name = "password", nullable = false)
    private String password;
}
```

#### One To Many

```java
public class Category {
  @Id
  private String id;

  @Column(name = "name", nullable = false)
  private String name;

  @OneToMany(
          cascade = CascadeType.ALL,
          fetch = FetchType.EAGER,
          mappedBy = "category"
  )
  @JsonManagedReference // parent
  private List<Product> products; // one to many
}

```

- `cascade = CascadeType.ALL` deletes table without fk violation
- `fetch = FetchType.EAGER` fetch all the data relating to the parent
- `mappedBy = "category"` to define the referencing side (
  non-owning side) of the relationship.
- `@JsonManagedReference` for application/json (owning side/parent)

<br>

#### Many To One

```java
public class Product {
    @Id
    private String id;

    @Column(name = "name", nullable = false)
    private String name;

    @Column(name = "prices", nullable = false)
    private BigDecimal prices;

    @ManyToOne
    @JoinColumn(
            name = "category_id",
            nullable = false
    )
    @JsonBackReference // child
    private Category category; // category = mappedBy on parent side
}
```

- `@JoinColumn(...)` essentially references foreign key to primary key
- `name = "category_id"` column name
- `@JsonBackReference` for application/json (non-owning side/child)

<br>

#### Many To Many (Junction Table)

```java
// Products -> junction table <- Sizes (see Sizes code below)
public class Product {
    @Id
    private String id;

    @Column(name = "name", nullable = false)
    private String name;

    @Column(name = "prices", nullable = false)
    private BigDecimal prices;

    @ManyToMany
    @JoinTable( // create junction table
            name = "products_sizes", // name of junction table
            joinColumns = {@JoinColumn(name = "product_id", referencedColumnName = "id", nullable = false)},
            inverseJoinColumns = {@JoinColumn(name = "size_id", referencedColumnName = "id", nullable = false)}
    )
    @JsonManagedReference // parent
    private Set<Size> sizes; // only unique objects
}
```

- `@JoinTable(...)` create junction table (requires `joinColumns & inverseJoinColumns to make junction table)
  - `name` = junction table name
  - `joinColumns = {...}` map primary keys to junction table foreign keys (first primary key)
  - `inverseJoinColumns = {...}` map primary keys to junction table foreign keys (second primary key)

```java
public class Size {
    @ManyToMany(
            cascade = CascadeType.ALL,
            fetch = FetchType.LAZY,
            mappedBy = "sizes"
    )
    @JsonBackReference
    private Set<Product> products;
}
```

<br>

### Components

```java

@Component // to mark the beans as Spring's managed components
public class JwtConfig {

}
```
