---
name: changelog
description: Generate changelog entries from recent commits
tags: [changelog, releases, documentation]
args:
  - name: from
    description: Starting point (tag or commit)
    default: "last-tag"
  - name: to
    description: Ending point
    default: "HEAD"
  - name: format
    description: Changelog format
    default: keep-a-changelog
    options: [keep-a-changelog, simple, detailed]
---

# Changelog Generator

Generate changelog from **{{from}}** to **{{to}}** in **{{format}}** format.

## Formats

### Keep a Changelog
```markdown
## [Version] - YYYY-MM-DD

### Added
- New feature description

### Changed
- Modified behavior

### Fixed
- Bug fix description

### Removed
- Removed feature
```

### Simple
```markdown
## Changes

- Change 1
- Change 2
- Change 3
```

### Detailed
```markdown
## [Version] - YYYY-MM-DD

### Features
- **feature-name**: Description (PR #123)

### Bug Fixes
- **component**: Fix description (Issue #456)

### Breaking Changes
- Description of breaking change and migration path
```

## Process

1. Get commits in range: `git log {{from}}..{{to}}`
2. Parse commit messages for type/scope
3. Group by category
4. Format according to chosen style

## Guidelines

- Write for users, not developers
- Focus on impact, not implementation
- Highlight breaking changes prominently
- Link to PRs/issues where helpful

## Output

Complete changelog section ready to add to CHANGELOG.md.
