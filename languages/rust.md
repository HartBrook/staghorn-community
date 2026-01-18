## Rust Guidelines

- Follow the Rust API Guidelines
- Use `rustfmt` for formatting
- Use `clippy` with `-- -D warnings` to treat warnings as errors
- Prefer safe code; document any `unsafe` blocks with safety invariants
- Use Rust 2021 edition

## Ownership and Borrowing

- Prefer borrowing (`&T` or `&mut T`) over ownership when the function doesn't need to own the data
- Use `Clone` explicitly rather than implicit copies; be mindful of clone costs
- Return owned data when the caller needs to store or modify it
- Use `Cow<'a, T>` when you might or might not need to clone

```rust
// Prefer borrowing for read-only access
fn process_name(name: &str) -> String {
    name.to_uppercase()
}

// Return owned when caller needs ownership
fn create_user(name: String) -> User {
    User { name }
}
```

## Error Handling

- Use `Result<T, E>` for recoverable errors
- Use `?` operator for error propagation
- Use `thiserror` for library error types (structured, typed)
- Use `anyhow` for application-level errors (convenient, contextual)
- Add context with `.context()` or `.with_context()`

```rust
use thiserror::Error;

#[derive(Error, Debug)]
pub enum UserError {
    #[error("user not found: {0}")]
    NotFound(String),
    #[error("invalid email format")]
    InvalidEmail,
    #[error("database error")]
    Database(#[from] sqlx::Error),
}
```

## Lifetimes

- Let the compiler infer lifetimes when possible
- Name lifetimes descriptively when explicit (`'conn`, `'query`)
- Prefer owned types in structs unless you have a specific reason for references
- Use `'static` only when data truly lives for the entire program

## Async

- Use `tokio` as the default async runtime
- Prefer `async fn` over returning `impl Future`
- Use `tokio::spawn` for concurrent tasks
- Use `tokio::select!` for racing futures
- Be mindful of `Send` and `Sync` bounds in async contexts

## Dependencies

- Keep dependencies minimal; each adds compile time and attack surface
- Use `cargo audit` for security vulnerability scanning
- Use `cargo deny` for license and dependency policy checks
- Use workspace for multi-crate projects
- Prefer `no_std` compatible crates when building libraries

## Testing

- Use `#[cfg(test)]` module for unit tests
- Place integration tests in `tests/` directory
- Use `proptest` or `quickcheck` for property-based testing
- Use `criterion` for benchmarks

```rust
#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn test_parse_valid_input() {
        let result = parse("valid");
        assert!(result.is_ok());
    }

    #[test]
    fn test_parse_invalid_input() {
        let result = parse("");
        assert!(matches!(result, Err(ParseError::Empty)));
    }
}
```

## Common Commands

- Run tests: `cargo test`
- Build release: `cargo build --release`
- Lint: `cargo clippy -- -D warnings`
- Format: `cargo fmt`
- Check (fast): `cargo check`
- Audit deps: `cargo audit`
- Unused deps: `cargo machete`
