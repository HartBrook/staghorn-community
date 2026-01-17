---
name: type-annotate
description: Add type annotations to untyped or partially typed code
tags: [types, typescript, python, typing]
args:
  - name: path
    description: File to add types to
    required: true
  - name: strictness
    description: How strict to be with types
    default: standard
    options: [minimal, standard, strict]
---

# Type Annotation

Add type annotations to `{{path}}` at **{{strictness}}** level.

## Strictness Levels

### Minimal
- Function parameters and return types only
- Skip complex inferred types
- Use `any`/`unknown` sparingly for difficult cases

### Standard
- All function signatures
- Class properties and methods
- Important variables
- Generic types where beneficial

### Strict
- Everything typed, no implicit `any`
- Full generic type parameters
- Discriminated unions where applicable
- Readonly where appropriate

## Process

1. Analyze existing code and infer types
2. Add annotations without changing logic
3. Ensure type safety at boundaries

## Guidelines

- Use specific types over `any`
- Prefer interfaces for object shapes
- Use union types for multiple possibilities
- Add generics for reusable functions
- Document complex types with comments

## Output

Provide fully typed version of the code with:
- All annotations added inline
- New type definitions if needed
- Comments explaining non-obvious types
