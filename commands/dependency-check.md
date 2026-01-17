---
name: dependency-check
description: Audit project dependencies for updates, vulnerabilities, unused packages
tags: [dependencies, security, maintenance]
args:
  - name: path
    description: Project root directory
    default: "."
  - name: focus
    description: What aspect to check
    default: all
    options: [security, updates, unused, all]
---

# Dependency Audit

Audit dependencies in `{{path}}` with focus on: **{{focus}}**

## Checks

### Security
- Known vulnerabilities in dependencies
- Deprecated packages with security issues
- Transitive dependency risks

### Updates
- Available major version updates
- Minor/patch updates available
- Breaking changes to consider

### Unused
- Dependencies not imported anywhere
- Dev dependencies used in production
- Duplicate functionality across packages

## Analysis Process

1. Parse dependency manifest (package.json, go.mod, requirements.txt, etc.)
2. Check each dependency against focus criteria
3. Identify action items with priority

## Output

### Security Issues
For each vulnerability:
- Package name and version
- Severity level
- Fix available? Recommended version

### Update Opportunities
For each outdated package:
- Current vs latest version
- Breaking changes summary
- Upgrade recommendation

### Unused Dependencies
- List of potentially removable packages
- Confidence level (certain, likely, check manually)

### Action Items
Prioritized list of recommended changes with commands to execute.
