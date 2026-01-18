## Python Guidelines

- Use Python 3.10+ with modern type hint syntax (`list[str]` not `List[str]`)
- Use type hints for all function signatures and class attributes
- Prefer f-strings over `.format()` or `%` formatting
- Follow PEP 8 style guide
- Use `ruff` for linting and formatting

## Type Safety

- Use `pyright` or `mypy` for static type checking
- Prefer Pydantic models or dataclasses over plain dicts for structured data
- Use `TypedDict` when you need dict compatibility with type safety
- Avoid `Any`; use `object` or proper generics when types are truly unknown

```python
# Prefer
@dataclass
class User:
    id: int
    name: str
    email: str

# Over
user = {"id": 1, "name": "Alice", "email": "alice@example.com"}
```

## Error Handling

- Raise specific exceptions; never use bare `except:`
- Create custom exceptions inheriting from a base project exception
- Include context in error messages
- Let exceptions propagate unless you can meaningfully handle them

```python
class AppError(Exception):
    """Base exception for the application."""

class UserNotFoundError(AppError):
    """Raised when a user cannot be found."""
    def __init__(self, user_id: str) -> None:
        super().__init__(f"User not found: {user_id}")
        self.user_id = user_id
```

## Async

- Use `async`/`await` for I/O-bound operations
- Prefer `asyncio.TaskGroup` (3.11+) for concurrent tasks
- Use `httpx` or `aiohttp` for async HTTP requests
- Never mix sync and async I/O in the same code path

## Dependencies

- Use `uv` for dependency management (fast, modern)
- Pin dependency versions in production (`==` or lock files)
- Keep `pyproject.toml` as the single source of truth
- Use optional dependency groups for dev/test dependencies

## Testing

- Use `pytest` with fixtures for test setup
- Use `pytest-asyncio` for async tests
- Use `unittest.mock` or `pytest-mock` for mocking
- Use factory classes or `factory_boy` for test data

```python
@pytest.fixture
def user() -> User:
    return User(id=1, name="Test", email="test@example.com")

def test_user_display_name(user: User) -> None:
    assert user.display_name == "Test"
```

## Docstrings

- Use one-line docstrings when the function name and signature are clear
- Use Google-style docstrings when more detail is needed
- Document public APIs; skip obvious internal functions

## Common Commands

- Run tests: `pytest`
- Run tests with coverage: `pytest --cov=src --cov-report=html`
- Format code: `ruff format .`
- Lint code: `ruff check .`
- Type check: `pyright` or `mypy .`
