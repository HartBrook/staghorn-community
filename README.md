# Staghorn Community Standards

Official community configuration source for [staghorn](https://github.com/HartBrook/staghorn) - comprehensive, production-quality coding guidelines for Claude Code.

## What's Included

This repository provides:

- **CLAUDE.md** - Core engineering standards and best practices
- **commands/** - 20 reusable prompts for common development workflows
- **evals/** - Behavioral tests to verify Claude follows the guidelines
- **languages/** - Language-specific guidelines for Go, Python, TypeScript, Rust, Java, and Ruby
- **templates/** - Project templates for backend services, CLI tools, React apps, and frontend apps

## Quick Start

```bash
# Install directly
stag init --from HartBrook/staghorn-community

# Or search and discover
stag search
```

## Contents

### Languages

| Language      | Description                                      |
| ------------- | ------------------------------------------------ |
| go.md         | Go guidelines, error handling, project structure |
| python.md     | Python guidelines, type hints, testing           |
| typescript.md | TypeScript strict mode, React patterns           |
| rust.md       | Rust safety, error handling, dependencies        |
| java.md       | Java conventions, testing, build tools           |
| ruby.md       | Ruby style, RSpec testing, type checking         |

### Templates

| Template           | Use Case                             |
| ------------------ | ------------------------------------ |
| backend-service.md | REST APIs, microservices             |
| cli-tool.md        | Command-line applications            |
| react-app.md       | React frontend applications          |
| frontend-app.md    | Generic frontend (Vue, Svelte, etc.) |

### Commands

| Command          | Description                              |
| ---------------- | ---------------------------------------- |
| code-review      | Thorough code review with checklist      |
| security-audit   | Scan for common security vulnerabilities |
| pr-prep          | Prepare pull request description         |
| explain          | Explain code in plain English            |
| refactor         | Suggest refactoring improvements         |
| test-gen         | Generate unit tests                      |
| debug            | Help diagnose and fix bugs               |
| doc-gen          | Generate documentation                   |
| migrate          | Help with code migrations                |
| api-design       | Design or review API interfaces          |
| fix              | Auto-fix a specific issue                |
| optimize         | Performance optimization                 |
| dependency-check | Audit dependencies for issues            |
| error-handling   | Add/improve error handling               |
| type-annotate    | Add type annotations to code             |
| todo-scan        | Find and triage TODOs/FIXMEs             |
| commit-msg       | Generate commit message                  |
| changelog        | Generate changelog from commits          |
| onboard          | Explain codebase for new developers      |
| naming-review    | Review variable/function naming          |

### Evals

Behavioral tests that verify Claude follows the guidelines in this config:

| Eval              | Description                                    |
| ----------------- | ---------------------------------------------- |
| core-principles   | Tests code quality (naming, focus, explicitness) |
| security-basics   | Tests security practices (secrets, validation) |
| git-conventions   | Tests git conventions (imperative mood, atomic) |
| testing-standards | Tests testing practices (coverage, error paths) |

Run evals with:

```bash
stag eval                    # Run all evals
stag eval core-principles    # Run specific eval
stag eval --tag security     # Run by tag
```

## Customization

These are starting points. After installing, customize with:

```bash
# Edit your personal preferences (layered on top)
stag edit

# Edit language-specific personal preferences
stag edit -l python
```

## Contributing

Contributions are welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## Discovery

This repository uses the `staghorn-config` GitHub topic for discoverability. When users run `stag search`, this repo will appear in results.

**Language topics** (for `--lang` filtering):

- It also includes topics like `python`, `go`, `typescript`, `rust`, `java`, `ruby`
- Users can search with aliases: `golang` → `go`, `py` → `python`, `ts` → `typescript`

**Custom tags** (for `--tag` filtering):

- Users can also search by other topics: `security`, `web`, `ai`, `backend`, etc.

Example: A Python security-focused config should have topics:

```
staghorn-config, python, security
```

Users can find it with:

```bash
stag search --lang python --tag security
stag search --lang py  # aliases work too
```

## License

MIT
