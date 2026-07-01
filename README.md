# My-Skills

A personal collection of custom/useful skills to extend agent capabilities.

## Usage

Skills are automatically discovered from the `.agents/skills/` directory and will be soft-linked to the `.claude` folder through the command `mklink /D .claude .agents` executed with **administrator** privileges.


## Skills

### git-commit

Execute git commits with conventional commit message analysis, intelligent staging, and message generation.

- **Location:** `.agents/skills/git-commit/SKILL.md`
- **Features:**
  - Auto-detects commit type and scope from staged/unstaged diffs
  - Generates [Conventional Commits](https://www.conventionalcommits.org/) compliant messages
  - Intelligent file staging for logical grouping
  - Supports interactive type/scope/description overrides

