---
name: commit
description: Creates a git commit with conventional commit message by analyzing code changes
---

# Git Commit Command

Delegates to: `@git-commit-agent`

## Usage

```bash
/git:commit
```

## What it does

1. Analyzes staged and unstaged changes
2. Generates conventional commit message
3. Stages relevant files if needed
4. Creates the commit
5. Verifies success

## Commit Message Format

Follows Conventional Commits specification:
```
<type>(<scope>): <subject>
```

**Types**: feat, fix, docs, style, refactor, perf, test, chore, ci, build

**Rules**:
- Use imperative mood ("add" not "added")
- Don't capitalize first letter
- No period at end
- Max 72 characters

## Examples

```bash
# After making changes
/git:commit

# Agent analyzes and creates:
# feat(auth): add JWT authentication
# fix(api): handle null user ID in session
# refactor(db): extract query builders to utilities
```

## Safety

- **NEVER commits to main or dev directly** - agent checks branch first
- **Atomic commits** - one logical change per commit
- **Working state** - every commit leaves code in working state

## Agent Details

This command delegates to `git-commit-agent` which:
- Runs on Claude Haiku for fast execution
- Analyzes diffs automatically
- Generates appropriate commit messages
- Handles staging automatically

