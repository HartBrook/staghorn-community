## Go Guidelines

- Follow Effective Go and Go Code Review Comments
- Use `gofmt` and `goimports` for formatting
- Keep package names short, lowercase, and singular (`user` not `users`)
- Prefer embedding and interfaces over complex type hierarchies
- Use generics for type-safe reusable code; avoid overusing them for simple cases

## Error Handling

- Always handle errors explicitly; never use `_` to ignore errors
- Wrap errors with context using `fmt.Errorf("operation failed: %w", err)`
- Use `errors.Is()` and `errors.As()` for error checking, not string comparison
- Create sentinel errors with `var ErrNotFound = errors.New("not found")`
- Use custom error types for errors that need additional context

```go
// Sentinel error
var ErrUserNotFound = errors.New("user not found")

// Custom error type when you need fields
type ValidationError struct {
    Field   string
    Message string
}

func (e *ValidationError) Error() string {
    return fmt.Sprintf("%s: %s", e.Field, e.Message)
}
```

## Context

- Pass `context.Context` as the first parameter to functions that do I/O
- Use context for cancellation, timeouts, and request-scoped values
- Never store contexts in structs; pass them explicitly
- Use `context.WithTimeout` or `context.WithCancel` to manage lifecycle

## Concurrency

- Prefer channels for communication, mutexes for state protection
- Use `sync.WaitGroup` to wait for goroutine completion
- Always ensure goroutines can exit (avoid leaks)
- Use `sync.Once` for one-time initialization
- Consider `errgroup` for coordinating goroutines with error handling

## Testing

- Use table-driven tests with descriptive subtest names
- Place tests in the same package (`_test.go` files)
- Use `testify/assert` or `testify/require` for assertions
- Use `t.Parallel()` for tests that can run concurrently
- Prefer real implementations over mocks when practical

```go
func TestParseID(t *testing.T) {
    tests := []struct {
        name    string
        input   string
        want    int
        wantErr bool
    }{
        {"valid", "123", 123, false},
        {"invalid", "abc", 0, true},
    }
    for _, tt := range tests {
        t.Run(tt.name, func(t *testing.T) {
            got, err := ParseID(tt.input)
            if tt.wantErr {
                require.Error(t, err)
                return
            }
            require.NoError(t, err)
            assert.Equal(t, tt.want, got)
        })
    }
}
```

## Common Commands

- Run tests: `go test ./...`
- Run tests with coverage: `go test -coverprofile=coverage.out ./...`
- View coverage: `go tool cover -html=coverage.out`
- Build: `go build ./cmd/...`
- Lint: `golangci-lint run`
- Tidy modules: `go mod tidy`
