---
name: error-handling
description: Add or improve error handling in code
tags: [errors, reliability, defensive]
args:
  - name: path
    description: File or function to improve
    required: true
  - name: style
    description: Error handling style to use
    default: auto
    options: [exceptions, result-types, error-codes, auto]
---

# Error Handling Improvements

Improve error handling in `{{path}}` using **{{style}}** style.

## Analysis

1. Identify operations that can fail
2. Check current error handling (or lack thereof)
3. Suggest improvements following best practices

## Error Handling Patterns

### Exceptions (Python, Java, JavaScript)
- Use specific exception types
- Add context to error messages
- Handle at appropriate level
- Don't catch and ignore

### Result Types (Rust, Go-style)
- Return errors explicitly
- Wrap errors with context
- Handle all error cases
- Use early returns for errors

### Error Codes (C-style)
- Define clear error codes
- Check return values consistently
- Document error conditions

## What to Look For

- Unhandled exceptions
- Silent failures (catch and ignore)
- Missing null/undefined checks
- Incomplete error messages
- Missing cleanup on error paths
- Errors that should propagate but don't

## Output

For each issue found:
1. **Location**: Where the problem is
2. **Risk**: What could go wrong
3. **Fix**: Improved error handling code
4. **Message**: Suggested error message with context
