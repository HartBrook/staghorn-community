# Community Engineering Standards

Production-quality guidelines for Claude Code maintained by the staghorn community.

## Core Principles

- **Clarity over cleverness** — Write code that is obvious at first glance
- **Explicit over implicit** — Make behavior visible; avoid hidden side effects
- **Simple over complex** — Solve the problem at hand, not hypothetical future ones
- **Small and focused** — Functions should do one thing well
- **Fail fast** — Detect and report errors as early as possible

## Code Structure

- Use early returns to reduce nesting and improve readability
- Avoid deeply nested code; flatten logic or extract helper functions
- Keep functions focused; if you need comments to separate sections, consider splitting
- Don't abstract prematurely; duplication is cheaper than the wrong abstraction

## Naming Conventions

- **Classes/types are nouns** — `UserProfile`, `PaymentProcessor`
- **Functions/methods are verbs** — `fetchUser()`, `validateInput()`, `processPayment()`
- **Booleans read as questions** — `isValid`, `hasPermission`, `canExecute`
- Avoid abbreviations; `customerAddress` not `custAddr`
- Name things for what they represent, not how they're implemented

## Error Handling

- Handle errors explicitly; never silently ignore them
- Include context in error messages: what failed and why
- Create domain-specific error types for errors callers need to handle differently
- Let errors propagate unless you can meaningfully handle them at that level
- Validate at system boundaries (user input, external APIs); trust internal code

## Git Conventions

- Write commit messages in imperative mood ("Add feature" not "Added feature")
- Keep commits atomic and focused on a single change
- Reference issue numbers when applicable (`Fix login bug (#123)`)
- Write descriptive PR titles and descriptions

## Security

- Never commit secrets, API keys, or credentials
- Use environment variables or secret managers for configuration
- Validate and sanitize all external input
- Avoid SQL injection, XSS, command injection, and path traversal
- Apply the principle of least privilege
- Keep dependencies updated; use automated vulnerability scanning

## Testing

- Write tests for new functionality and bug fixes
- Test behavior, not implementation details
- Test error paths and edge cases, not just happy paths
- Keep tests deterministic; avoid flaky tests that depend on timing or external state
- Use descriptive test names that explain the scenario and expected outcome
- Isolate tests; each test should set up its own state

## Code Review Focus

When reviewing, prioritize:

1. **Correctness** — Does it work? Are there logic errors or edge cases?
2. **Security** — Are there vulnerabilities? Is input validated?
3. **Clarity** — Is the code easy to understand? Are names descriptive?
4. **Simplicity** — Is there a simpler approach? Is anything over-engineered?

## Documentation

- Document public APIs and non-obvious behavior
- Write comments for "why", not "what" — the code shows what, comments explain why
- Keep documentation close to the code it describes
