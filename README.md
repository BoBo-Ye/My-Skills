# My-Skills

A personal collection of custom Claude Code skills to extend agent capabilities.

## Skills

### git-commit

Execute git commits with conventional commit message analysis, intelligent staging, and message generation.

- **Type:** Built from [claude-code-skill-template](https://github.com/anthropics/claude-code)
- **Location:** `.agents/skills/git-commit/SKILL.md`
- **Features:**
  - Auto-detects commit type and scope from staged/unstaged diffs
  - Generates [Conventional Commits](https://www.conventionalcommits.org/) compliant messages
  - Intelligent file staging for logical grouping
  - Supports interactive type/scope/description overrides

## Usage

Skills are automatically discovered from the `.agents/skills/` directory and can be invoked in Claude Code with `/skill-name`.

## License

MIT
