# Community Engineering Standards

Production-quality guidelines for Claude Code maintained by the staghorn community.

## Core Principles

- Write clear, self-documenting code
- Prefer explicit over implicit
- Keep functions small and focused (under 50 lines)
- Use meaningful variable and function names

## Code Review Standards

- All PRs require at least one approval
- Keep PRs under 400 lines when possible
- Include tests for new functionality
- Update documentation when changing public APIs

## Git Conventions

- Write commit messages in imperative mood ("Add feature" not "Added feature")
- Keep commits atomic and focused
- Reference issue numbers in commit messages when applicable

## Security Best Practices

- Never commit secrets, API keys, or credentials
- Use environment variables for configuration
- Validate all user input
- Follow OWASP security guidelines

## Testing Standards

- Write tests for all new features
- Maintain meaningful test coverage
- Include both unit and integration tests where appropriate
- Test error paths, not just happy paths

## Documentation

- Document public APIs
- Keep README files up to date
- Write clear inline comments for complex logic

---

For language-specific guidelines, see the `languages/` directory.
For project templates, see the `templates/` directory.
For reusable commands, see the `commands/` directory.
