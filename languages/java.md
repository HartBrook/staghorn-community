## Java Guidelines

- Follow Oracle's Java Code Conventions and Google Java Style Guide
- Use Java 17+ features where appropriate (records, sealed classes, pattern matching)
- Prefer immutability - use `final` liberally
- Use Optional over null for optional return values

## Naming Conventions

- PascalCase for classes and interfaces
- camelCase for methods and variables
- SCREAMING_SNAKE_CASE for constants
- Use meaningful, pronounceable names

## Error Handling

- Use checked exceptions sparingly - prefer runtime exceptions for programming errors
- Always include context in exception messages
- Use try-with-resources for closeable resources
- Create custom exceptions for domain-specific errors

## Project Structure

```
src/
  main/
    java/
      com/example/
        Application.java
        domain/
        service/
        repository/
    resources/
  test/
    java/
      com/example/
        ...
pom.xml or build.gradle
```

## Dependencies

- Use Maven or Gradle for dependency management
- Keep dependencies up to date
- Audit dependencies for security vulnerabilities
- Minimize the dependency tree

## Testing

- Use JUnit 5 for unit tests
- Use Mockito for mocking
- Write integration tests for database/API interactions
- Use AssertJ for fluent assertions

## Common Commands

- Run tests: `mvn test` or `./gradlew test`
- Build: `mvn package` or `./gradlew build`
- Format: `mvn spotless:apply` or IDE formatter
- Check: `mvn verify` or `./gradlew check`
