## Java Guidelines

- Use Java 21+ and leverage modern features
- Follow Google Java Style Guide
- Prefer immutability: use `final` for fields, parameters, and local variables
- Use `Optional` for return values that may be absent; never return `null`
- Prefer records for data carriers; use sealed classes for type hierarchies

## Modern Java Features

- **Records**: Use for immutable data carriers
- **Sealed classes**: Use for controlled type hierarchies
- **Pattern matching**: Use in switch expressions and instanceof
- **Virtual threads**: Use for I/O-bound concurrent tasks (Java 21+)
- **var**: Use for local variables when the type is obvious from context

```java
// Record for data
public record User(String id, String name, String email) {}

// Sealed interface for controlled variants
public sealed interface Result<T> permits Success, Failure {
    record Success<T>(T value) implements Result<T> {}
    record Failure<T>(String error) implements Result<T> {}
}

// Pattern matching in switch
String describe(Object obj) {
    return switch (obj) {
        case Integer i -> "Integer: " + i;
        case String s -> "String: " + s;
        case null -> "null";
        default -> "Unknown";
    };
}
```

## Naming Conventions

- PascalCase for classes, interfaces, records, and enums
- camelCase for methods, variables, and parameters
- SCREAMING_SNAKE_CASE for constants
- Use meaningful, pronounceable names; avoid abbreviations

## Error Handling

- Use unchecked exceptions for programming errors
- Use checked exceptions only for recoverable conditions the caller must handle
- Always include context in exception messages
- Use try-with-resources for all `AutoCloseable` resources
- Create domain-specific exception hierarchies

```java
public class UserNotFoundException extends RuntimeException {
    private final String userId;

    public UserNotFoundException(String userId) {
        super("User not found: " + userId);
        this.userId = userId;
    }

    public String getUserId() {
        return userId;
    }
}
```

## Null Safety

- Never return `null` from public methods; use `Optional<T>`
- Use `@Nullable` and `@NonNull` annotations for clarity
- Validate inputs at public API boundaries with `Objects.requireNonNull()`
- Prefer empty collections over null collections

## Stream API

- Use streams for collection transformations
- Prefer method references over lambdas when clearer
- Avoid side effects in stream operations
- Use `toList()` (Java 16+) instead of `collect(Collectors.toList())`

```java
List<String> names = users.stream()
    .filter(user -> user.isActive())
    .map(User::name)
    .toList();
```

## Dependencies

- Use Gradle (Kotlin DSL) or Maven for dependency management
- Keep dependencies up to date with Dependabot or Renovate
- Use `./gradlew dependencyCheckAnalyze` or OWASP plugin for security audits
- Minimize transitive dependencies

## Testing

- Use JUnit 5 for unit tests
- Use Mockito for mocking; prefer constructor injection for testability
- Use AssertJ for fluent, readable assertions
- Use Testcontainers for integration tests with real databases
- Test behavior, not implementation

```java
@Test
void shouldReturnUserWhenFound() {
    var user = new User("1", "Alice", "alice@example.com");
    when(repository.findById("1")).thenReturn(Optional.of(user));

    var result = service.getUser("1");

    assertThat(result).isPresent();
    assertThat(result.get().name()).isEqualTo("Alice");
}
```

## Common Commands

- Run tests: `./gradlew test` or `mvn test`
- Build: `./gradlew build` or `mvn package`
- Format: `./gradlew spotlessApply` or `mvn spotless:apply`
- Check: `./gradlew check` or `mvn verify`
- Run: `./gradlew bootRun` (Spring Boot)
