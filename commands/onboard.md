---
name: onboard
description: Generate codebase overview for new team members
tags: [onboarding, documentation, overview]
args:
  - name: path
    description: Project root to analyze
    default: "."
  - name: depth
    description: Level of detail
    default: standard
    options: [quick, standard, deep]
---

# Codebase Onboarding Guide

Generate onboarding documentation for `{{path}}` at **{{depth}}** level.

## Depth Levels

### Quick (5-minute overview)
- What the project does
- Key technologies used
- How to run it
- Where to start reading code

### Standard (30-minute overview)
- Everything in Quick, plus:
- Architecture overview
- Directory structure explained
- Key concepts and terminology
- Common development tasks
- Where to find things

### Deep (comprehensive)
- Everything in Standard, plus:
- Design decisions and trade-offs
- Data flow diagrams
- Testing strategy
- Deployment process
- Common gotchas
- Historical context

## Analysis

1. Read README and docs
2. Analyze directory structure
3. Identify entry points
4. Map key dependencies
5. Understand data flow

## Output

### Project Overview
What it does, who it's for, key features.

### Tech Stack
Languages, frameworks, major dependencies with versions.

### Getting Started
Step-by-step setup instructions.

### Architecture
How components fit together, data flow, key abstractions.

### Directory Guide
What each important directory contains.

### Key Files
Most important files to understand first.

### Development Workflow
How to run, test, and debug locally.

### Where to Look
Guide for finding specific types of code.
