---
name: todo-scan
description: Find, categorize, and triage TODO/FIXME/HACK comments
tags: [todos, maintenance, planning]
args:
  - name: path
    description: Directory to scan
    default: "."
  - name: action
    description: What to do with found items
    default: list
    options: [list, prioritize, create-issues]
---

# TODO Scanner

Scan `{{path}}` for TODO/FIXME/HACK comments and **{{action}}**.

## What to Find

- `TODO:` - Tasks to complete
- `FIXME:` - Known bugs to fix
- `HACK:` - Temporary workarounds
- `XXX:` - Problematic code
- `NOTE:` - Important context (lower priority)

## Analysis

For each item found, extract:
- Location (file and line)
- Type (TODO/FIXME/HACK/etc.)
- Content/description
- Author (from git blame if available)
- Age (when it was added)

## Output Modes

### List
Simple list of all items with locations.

### Prioritize
Categorized list with suggested priority:
- **High**: FIXME, security-related, blocking issues
- **Medium**: TODO with clear scope, technical debt
- **Low**: Nice-to-have, minor improvements

### Create Issues
For each item, generate:
- Issue title
- Description with context
- Suggested labels
- File reference

## Output

Provide organized report with:
1. Summary statistics (count by type)
2. Items organized by priority/type
3. Recommendations for addressing oldest/most critical items
