---
name: checkout
description: Checkout to a branch, creating it if it doesn't exist, using conventional branch naming
---

# Git Checkout Command

Delegates to: `@git-checkout-agent`

## Usage

```bash
/git:checkout
```

## What it does

1. Checks current branch
2. Determines target branch name from context (follows conventional naming)
3. Creates branch if it doesn't exist, or checks out existing branch
4. Verifies successful checkout

## Branch Naming Convention

The agent follows conventional branch naming:
- `feat/<description>` - for new features
- `fix/<description>` - for bug fixes
- `refactor/<description>` - for refactoring
- `docs/<description>` - for documentation
- `test/<description>` - for tests
- `chore/<description>` - for maintenance

Uses kebab-case and descriptive names.

## Examples

```bash
# Checkout to a feature branch
/git:checkout
# Context: "I want to work on user authentication"
# Result: Creates/checks out `feat/user-authentication`

# Checkout to a fix branch
/git:checkout
# Context: "I need to fix the login bug"
# Result: Creates/checks out `fix/login-bug`
```

## Agent Details

This command delegates to `git-checkout-agent` which:
- Runs on Claude Haiku for fast execution
- Automatically determines branch name from context
- Handles both creation and checkout scenarios
- Verifies success automatically

