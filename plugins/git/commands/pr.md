---
name: pr
description: Creates a comprehensive pull request to the dev branch using GitHub CLI
---

# Git PR Creation Command

Delegates to: `@git-pr-creation-agent`

## Usage

```bash
/git:pr
```

## What it does

1. Verifies GitHub CLI authentication
2. Analyzes commits in current branch vs dev
3. Generates comprehensive PR title and body
4. Creates PR to dev branch
5. Returns PR URL

## PR Format

**Title**: Follows Conventional Commits format
```
<type>(<scope>): <description>
```

**Body**: Comprehensive template including:
- Summary (2-3 sentences)
- Key Features
- Changes Included (New Features, Bug Fixes, Refactoring)
- Technical Details (Endpoints, Database Changes, Configuration)

## Requirements

- GitHub CLI (`gh`) installed and authenticated
- Repository with remote named `origin`
- Current branch must not be `dev`, `main`, `master`, or `develop`
- Branch must have commits ahead of dev

## Examples

```bash
# After completing a feature
/git:pr

# Agent will:
# 1. Verify gh auth
# 2. Analyze commits: git log dev..HEAD
# 3. Generate PR with comprehensive description
# 4. Create PR and return URL
```

## Safety

- **NEVER creates PR from protected branches** - agent checks branch first
- **Uses heredoc format** - prevents shell interpolation issues
- **Comprehensive descriptions** - no vague "various improvements"
- **Includes all commits** - analyzes full branch history

## Error Handling

- If `gh auth status` fails → guides user to authenticate
- If on wrong branch → informs user and stops
- If no commits to PR → informs user branch is up to date

## Agent Details

This command delegates to `git-pr-creation-agent` which:
- Runs on Claude Haiku for fast execution
- Analyzes commit history automatically
- Generates comprehensive PR descriptions
- Handles GitHub CLI operations

