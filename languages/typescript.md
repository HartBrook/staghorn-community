## TypeScript Guidelines

- Enable strict mode in `tsconfig.json` (all strict flags)
- Prefer `interface` over `type` for object shapes (better error messages, extendable)
- Use `type` for unions, intersections, and mapped types
- Use `readonly` and `as const` for immutable data
- Avoid `any`; use `unknown` for truly unknown types, then narrow

## Type Patterns

- Use `satisfies` to validate types while preserving literal types
- Prefer discriminated unions over optional properties for variants
- Use branded types for type-safe IDs and primitives
- Leverage `infer` and conditional types sparingly

```typescript
// Discriminated union
type Result<T> =
  | { success: true; data: T }
  | { success: false; error: string };

// Branded type for type-safe IDs
type UserId = string & { readonly __brand: "UserId" };

// satisfies preserves literal types
const config = {
  port: 3000,
  host: "localhost",
} satisfies ServerConfig;
```

## Naming Conventions

- PascalCase for types, interfaces, and classes
- camelCase for variables, functions, and methods
- SCREAMING_SNAKE_CASE for constants
- Do not prefix interfaces with `I` (anti-pattern in modern TS)

## Error Handling

- Define explicit error types; avoid throwing strings
- Use Result types for expected failures
- Use try/catch for unexpected exceptions
- Validate data at system boundaries with Zod or similar

```typescript
class AppError extends Error {
  constructor(
    message: string,
    public readonly code: string,
  ) {
    super(message);
    this.name = "AppError";
  }
}
```

## Async

- Always handle Promise rejections
- Use `Promise.all` for concurrent independent operations
- Use `Promise.allSettled` when you need all results regardless of failures
- Prefer async/await over `.then()` chains

## Imports

- Use path aliases (`@/` or `~/`) for absolute imports
- Group imports: external libs, internal modules, relative imports
- Avoid circular dependencies; they indicate architectural issues
- Use barrel files (`index.ts`) sparingly—they can hurt tree-shaking

## React (if applicable)

- Use functional components with hooks
- Prefer named exports over default exports
- Keep components small and focused (<100 lines)
- Colocate component, styles, and tests
- Use TypeScript generics for reusable components

```typescript
interface Props<T> {
  items: T[];
  renderItem: (item: T) => React.ReactNode;
}

function List<T>({ items, renderItem }: Props<T>) {
  return <ul>{items.map(renderItem)}</ul>;
}
```

## Testing

- Use Vitest or Jest with TypeScript
- Test behavior, not implementation
- Use MSW for mocking HTTP requests
- Prefer `@testing-library` for component tests

## Common Commands

- Run tests: `npm test` or `pnpm test`
- Type check: `tsc --noEmit`
- Lint: `eslint .` or `biome check .`
- Format: `prettier --write .` or `biome format --write .`
