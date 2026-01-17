---
name: commit-msg
description: Generate a commit message for staged changes
tags: [git, commits, workflow]
args:
  - name: style
    description: Commit message style
    default: conventional
    options: [conventional, descriptive, simple]
---

# Commit Message Generator

Generate a **{{style}}** commit message for the staged changes.

## Styles

### Conventional
```
type(scope): description

[optional body]

[optional footer]
```
Types: feat, fix, docs, style, refactor, test, chore

### Descriptive
```
Summary line (imperative mood, <50 chars)

Detailed explanation of what changed and why.
Wrap at 72 characters.
```

### Simple
```
One-line summary of changes
```

## Process

1. Analyze `git diff --staged` output
2. Identify the nature of changes (new feature, bugfix, refactor, etc.)
3. Summarize the "what" concisely
4. Explain the "why" if not obvious

## Guidelines

- Use imperative mood ("Add feature" not "Added feature")
- Keep first line under 50 characters
- Don't end first line with period
- Separate subject from body with blank line
- Wrap body at 72 characters
- Explain what and why, not how

## Output

Provide a complete commit message ready to use.
If changes span multiple concerns, suggest splitting into multiple commits.
