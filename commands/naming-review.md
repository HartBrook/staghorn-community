---
name: naming-review
description: Review and suggest improvements for variable/function/class naming
tags: [naming, readability, refactor]
args:
  - name: path
    description: File or directory to review
    required: true
  - name: strictness
    description: How strict to be
    default: suggestions-only
    options: [suggestions-only, rename-all]
---

# Naming Review

Review naming in `{{path}}` with **{{strictness}}** mode.

## What to Check

### Variables
- Descriptive and intention-revealing
- Avoid abbreviations unless universal (id, url, etc.)
- Boolean names should be questions (isValid, hasPermission)
- Collections should be plural

### Functions/Methods
- Start with verbs (get, set, calculate, validate)
- Name describes what it returns or does
- Avoid generic names (process, handle, do)

### Classes/Types
- Nouns or noun phrases
- Describe what it is, not what it does
- Avoid suffixes like Manager, Handler unless clear

### Constants
- Describe the value's meaning
- SCREAMING_SNAKE_CASE for true constants

## Common Issues

- Single letter names (except loop indices)
- Misleading names (doesn't match behavior)
- Overly abbreviated (usr, cfg, btn)
- Too generic (data, info, temp)
- Inconsistent conventions
- Name doesn't match type/return value

## Output Modes

### Suggestions Only
List issues with recommendations. Don't change code.

### Rename All
Provide refactored code with all names improved.

## Output

For each naming issue:
1. **Location**: Where it is
2. **Current**: The problematic name
3. **Suggested**: Better name(s)
4. **Reason**: Why it's better
