## Overview

**My-Skills** is a personal, self-use collection of agent skills — some hand-written, some sourced from the community ecosystem. Each skill is a plain Markdown file with YAML frontmatter — no dependencies, no build step, no configuration required.

This repository is designed to work with both **[Codex](https://github.com/openai/codex)** and **[Claude Code](https://claude.ai/code)**. Codex discovers skills from `.agents/skills/`, while Claude Code looks for `.claude/skills/`. To avoid maintaining two copies of every skill, the `.claude` directory is set up as a symlink pointing to `.agents` — a single source of truth shared across both tools.

## Installation

### Prerequisites

- [Codex](https://github.com/openai/codex) and/or [Claude Code](https://claude.ai/code) installed and authenticated
- [Node.js](https://nodejs.org/) >=18 (required for the `find-skills` skill only)

### Setup

1. **Clone the repository**

   ```sh
   git clone https://github.com/BoBo-Ye/My-Skills.git
   cd My-Skills
   ```

2. **Create the symlink**

   Skills live in `.agents/skills/`. Codex reads them directly; Claude Code needs them under `.claude/skills/`. A symlink keeps both in sync:

   **Windows** (PowerShell as Administrator):
   ```powershell
   mklink /D .claude .agents
   ```

   **macOS / Linux**:
   ```sh
   ln -s .agents .claude
   ```

3. **Verify**

   Restart your agent tool. The skills will appear as available slash commands in both Codex and Claude Code.

> [!NOTE]
> The `.claude` symlink is listed in `.gitignore` — each user creates it locally according to their platform. Codex users who don't use Claude Code can skip the symlink entirely.

## Skills

Skills in this collection may be hand-written or sourced from the community — each curated for quality and usefulness.

### [find-skills](.agents/skills/find-skills/SKILL.md)

Discover and install agent skills from the open ecosystem. Searches the skill marketplace and guides you through quality-gated installation.

- Browse skills by category: Web Dev, Testing, DevOps, Documentation, Code Quality, Design, Productivity
- Verify quality through install counts, source reputation, and GitHub stars
- Install skills with a single command via the Skills CLI (`npx skills`)

### [create-skill](.agents/skills/create-skill/SKILL.md)

Guide for creating effective skills following best practices. Covers structure, progressive disclosure, and the principles behind well-designed skills.

- Three-level loading system: metadata → SKILL.md → bundled resources
- 200-line rule and progressive disclosure pattern
- Degrees of freedom: high (text instructions) to low (specific scripts) for different use cases
- Skill directory layout conventions (`scripts/`, `references/`, `assets/`)

### [create-readme](.agents/skills/create-readme/SKILL.md)

Generate comprehensive, well-structured `README.md` files for any project. Analyzes the entire project first, then writes documentation inspired by top open-source repositories.

- Reviews the full project structure before writing
- Uses GitHub Flavored Markdown and [admonition syntax](https://github.com/orgs/community/discussions/16925)
- Keeps content concise, scannable, and professional

### [git-commit](.agents/skills/git-commit/SKILL.md)

Execute git commits with conventional commit message analysis, intelligent staging, and message generation.

- Auto-detects commit type (`feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`) and scope from staged/unstaged diffs
- Generates [Conventional Commits](https://www.conventionalcommits.org/) compliant messages
- Supports breaking changes via `!` marker and `BREAKING CHANGE` footer
- Intelligent file staging for logically grouped commits
- Git safety protocol: no destructive commands, no hook skipping, no force push to main

### [update-project](.agents/skills/update-project/SKILL.md)

Sync the README with project-source changes, then commit the documentation update and report what changed. The skill first determines whether the repository is a skill collection before treating `.agents/skills/` inventory or metadata changes as README-worthy project updates.

- Reviews recent commits, uncommitted changes, and repository scope before deciding what changed
- Treats skill additions, removals, and metadata updates as project changes only for skill-collection repositories like this one
- Updates README following `create-readme` best practices (concise, scannable, GFM admonitions)
- Stages and commits with a conventional commit message via `git-commit` conventions
- Reports a clear summary of what changed and what was updated

> [!TIP]
> Run `/find-skills` whenever you need a new capability — the ecosystem grows daily. New skills are added to `.agents/skills/` and available immediately.

## Project Structure

```
My-Skills/
├── .agents/
│   └── skills/
│       ├── create-readme/
│       ├── create-skill/
│       ├── find-skills/
│       ├── git-commit/
│       └── update-project/
├── .claude/          → symlink to .agents/ (for Claude Code)
├── .gitignore
└── README.md
```

## Adding Your Own Skills

A skill is a Markdown file with YAML frontmatter. The minimum structure:

```markdown
---
name: my-skill
description: What this skill does
---

## Instructions

Your skill logic and guidelines for the agent here.
```

Drop it into `.agents/skills/<skill-name>/SKILL.md` and it's available in both Codex and Claude Code immediately.
