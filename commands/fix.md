---
name: fix
description: Auto-fix a specific issue
tags: [fix, bugfix, quick]
args:
  - name: issue
    description: Description of the problem to fix
    required: true
  - name: path
    description: File or area to focus on
    default: "."
---

# Quick Fix

Fix the following issue: **{{issue}}**

Focus area: `{{path}}`

## Process

1. **Understand**: Confirm what the issue is and its impact
2. **Locate**: Find the exact code causing the problem
3. **Fix**: Make the minimal change needed to resolve it
4. **Verify**: Ensure the fix works and doesn't break anything else

## Guidelines

- Make the smallest change that fixes the issue
- Don't refactor unrelated code
- Preserve existing behavior for unaffected cases
- Add a test if the issue wasn't covered

## Output

Provide:
1. **Root Cause**: What's causing the issue
2. **Fix**: The code changes needed
3. **Impact**: What else might be affected
4. **Test**: How to verify the fix works
