# Contributing to Staghorn Community Standards

Thank you for your interest in improving the community standards!

## How to Contribute

### Suggesting Changes

1. Open an issue describing the proposed change
2. Include rationale and examples
3. Wait for maintainer feedback before submitting a PR

### Submitting Pull Requests

1. Fork the repository
2. Create a feature branch
3. Make your changes following the guidelines below
4. Submit a PR with a clear description

## Content Guidelines

### General Principles

- **Quality over quantity** - Every guideline should be actionable and valuable
- **Language-agnostic where possible** - Core standards should apply broadly
- **Opinionated but not dogmatic** - Provide clear guidance while acknowledging alternatives

### Language Files

- Follow the existing format (sections: Guidelines, Error Handling, Project Structure, Testing, Common Commands)
- Include practical, real-world advice
- Keep file length reasonable (under 50 lines typically)

### Command Files

- Use the YAML frontmatter format consistently
- Include helpful default arguments
- Provide clear output format expectations

### Templates

- Focus on architectural patterns, not language specifics
- Include testing, deployment, and documentation sections

## File Format

### Languages

```markdown
## [Language] Guidelines

- Guideline 1
- Guideline 2

## Error Handling

- Pattern 1
- Pattern 2

## Project Structure

[directory tree]

## Testing

- Framework recommendation
- Testing patterns

## Common Commands

- command 1: `description`
- command 2: `description`
```

### Commands

```yaml
---
name: command-name
description: Brief description
tags: [tag1, tag2]
args:
  - name: arg-name
    description: What this arg does
    required: true  # or default: "value"
    options: [opt1, opt2]  # optional
---

# Command Title

Prompt content with {{arg-name}} placeholders.
```

## Review Process

All changes are reviewed by maintainers. We aim to respond within 7 days.

## Code of Conduct

Be respectful and constructive. We welcome diverse perspectives.
