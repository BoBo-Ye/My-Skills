---
name: update-project
description: 'Update project README based on recent changes, create a conventional git commit, and summarize the update to the user. Use when user wants to wrap up a round of development, sync the README with current project state, or make a documentation commit after feature work.'
---

# Update Project

## Overview

Review recent project changes, update the README to reflect the current state, commit with a conventional commit message, and report the update summary to the user.

## Workflow

### Step 1: Analyze Recent Changes

Determine what changed since the last meaningful update:

```bash
# Recent commits (last 3)
git log --oneline -3

# Uncommitted changes
git status --porcelain
git diff --stat
```

Identify:
- New skills, features, or capabilities added
- Structural changes (new directories, config files, etc.)
- Any renames, removals, or reorganizations
- Dependencies or tooling updates

### Step 2: Update README

Follow the [create-readme skill](.agents/skills/create-readme/SKILL.md) principles to update the project README:

- Review the entire project workspace for current structure
- Keep content concise, scannable, and professional
- Use GFM and GitHub admonition syntax
- Reflect only what exists *now* — remove stale sections, add new ones
- Do not overuse emojis

Key areas to verify for accuracy:
- Skill listing and descriptions (each skill in `.agents/skills/`)
- Project structure tree
- Installation / setup instructions
- Any new capabilities or changed workflows

### Step 3: Stage and Commit

Follow the [git-commit skill](.agents/skills/git-commit/SKILL.md) conventions:

1. Stage the README and any related documentation files:
   ```bash
   git add README.md
   ```
2. Generate a conventional commit message. For README updates, the type is typically `docs`:
   ```
   docs(readme): update README to reflect current project state
   ```
3. If other changed files belong to the same logical update, include them with an appropriate scope and description.

**Git safety protocol:**
- Never update git config
- Never run destructive commands (`--force`, hard reset) without explicit request
- Never skip hooks (`--no-verify`) unless user asks
- Never force push to main/master
- If commit fails due to hooks, fix the issue and create a new commit

### Step 4: Summarize for the User

After committing, report a clear summary:

1. **Changes detected** — What was added, changed, or removed since last update
2. **README updates made** — Specific sections or content changed and why
3. **Commit details** — The commit message and files included

Format the summary conversationally so the user understands the project update at a glance.
