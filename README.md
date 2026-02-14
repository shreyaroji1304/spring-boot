# Spring Boot Backend Application

A RESTful API backend application built with Spring Boot, Spring Data JPA, and MySQL support.

## Project Structure

```
SpringApp/
├── src/
│   ├── main/
│   │   ├── java/com/example/springapp/
│   │   │   ├── SpringBootApp.java           # Main application class
│   │   │   ├── controller/                  # REST Controllers
│   │   │   │   └── UserController.java
│   │   │   ├── model/                       # Entity models
│   │   │   │   └── User.java
│   │   │   ├── repository/                  # Data access layer
│   │   │   │   └── UserRepository.java
│   │   │   └── service/                     # Business logic layer
│   │   │       └── UserService.java
│   │   └── resources/
│   │       └── application.properties       # Configuration file
│   └── test/                                # Unit tests
├── pom.xml                                  # Maven configuration
└── .gitignore

```

## Technology Stack

- **Java 17**
- **Spring Boot 3.2.0**
- **Spring Data JPA**
- **MySQL Driver** (configurable)
- **H2 Database** (embedded for development)
- **Lombok** (reduce boilerplate)
- **Maven** (build tool)

## Prerequisites

- Java 17 or higher
- Maven 3.6+
- MySQL 8.0+ (for production use)

## Installation & Setup

### 1. Clone/Download the project
```bash
cd SpringApp
```

### 2. Configure Database

**For Development (H2 - default):**
- H2 in-memory database is pre-configured
- H2 Console available at: `http://localhost:8080/h2-console`

**For MySQL:**
- Uncomment MySQL configuration in `src/main/resources/application.properties`
- Update connection details:
  ```properties
  spring.datasource.url=jdbc:mysql://localhost:3306/springapp_db
  spring.datasource.username=root
  spring.datasource.password=yourpassword
  ```

### 3. Build the Project

```bash
mvn clean install
```

### 4. Run the Application

```bash
mvn spring-boot:run
```

Or:
```bash
java -jar target/springapp-1.0.0.jar
```

The application will start on `http://localhost:8080`

## API Endpoints

### User Management

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/users` | Get all users |
| GET | `/api/users/{id}` | Get user by ID |
| POST | `/api/users` | Create new user |
| PUT | `/api/users/{id}` | Update user |
| DELETE | `/api/users/{id}` | Delete user |
| GET | `/api/users/health` | API health check |

### Sample Request

**Create User (POST):**
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "phone": "1234567890",
  "address": "123 Main Street"
}
```

## Configuration

Edit `src/main/resources/application.properties` to customize:

- **Server Port**: `server.port=8080`
- **Database**: Configure datasource URL, username, password
- **JPA**: Set `spring.jpa.hibernate.ddl-auto` to:
  - `create`: Drop and recreate database
  - `update`: Update existing schema
  - `validate`: Validate schema only
  - `none`: No changes

## Logging

- Default log level: `INFO`
- Application logs: `DEBUG`
- Hibernate SQL: `DEBUG`

## Development

### Add New Entity
1. Create model class in `src/main/java/com/example/springapp/model/`
2. Annotate with `@Entity` and `@Table`
3. Create repository in `src/main/java/com/example/springapp/repository/`

### Add New Controller
1. Create controller class in `src/main/java/com/example/springapp/controller/`
2. Annotate with `@RestController` and `@RequestMapping`
3. Inject required services

## Testing

Run tests:
```bash
mvn test
```

## Common Commands

```bash
# Clean and build
mvn clean install

# Run application
mvn spring-boot:run

# Run tests
mvn test

# Package as JAR
mvn package

# View dependencies
mvn dependency:tree
```

## Troubleshooting

### Port Already in Use
Change port in `application.properties`:
```properties
server.port=8081
```

### MySQL Connection Failed
- Ensure MySQL is running
- Verify credentials in `application.properties`
- Check database exists: `CREATE DATABASE springapp_db;`

### Dependency Issues
```bash
mvn clean install -U
```

## License

This project is open source and available for use and modification.

## Support

For issues or questions, refer to:
- Spring Boot Documentation: https://spring.io/projects/spring-boot
- Spring Data JPA: https://spring.io/projects/spring-data-jpa
