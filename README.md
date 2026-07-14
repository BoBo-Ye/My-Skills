# My-Skills

个人维护的 Agent Skills 集合，包含自用技能和来自社区的实用技能。每个技能都是一个带有 YAML frontmatter 的 `SKILL.md`，可以通过 [`skills`](https://github.com/vercel-labs/skills) CLI 安装到 Codex、Claude Code、Cursor 等支持 Agent Skills 的工具中。

## 快速开始

查看这个仓库提供的所有技能：

```bash
npx skills add BoBo-Ye/My-Skills --list
```

安装全部技能到当前项目可检测到的 Agent：

```bash
npx skills add BoBo-Ye/My-Skills --all
```

只安装指定技能到 Codex：

```bash
npx skills add BoBo-Ye/My-Skills --skill skill-creator --agent codex
```

如果希望安装到用户级目录，添加 `--global`（或 `-g`）：

```bash
npx skills add BoBo-Ye/My-Skills --skill git-commit --agent codex --global
```

> [!TIP]
> 安装后可以使用 `npx skills list` 查看当前项目已安装的技能，使用 `npx skills update` 更新技能。

## 技能清单

| 技能 | 用途 |
| --- | --- |
| [`create-agentsmd`](.agents/skills/create-agentsmd/SKILL.md) | 为仓库生成完整的 `AGENTS.md`，补充项目结构、开发命令和协作约定。 |
| [`create-readme`](.agents/skills/create-readme/SKILL.md) | 创建结构清晰、易读且适合开源项目的 `README.md`。 |
| [`documentation-writer`](.agents/skills/documentation-writer/SKILL.md) | 按 Diátaxis 框架编写教程、操作指南、解释型文档和参考文档。 |
| [`find-skills`](.agents/skills/find-skills/SKILL.md) | 根据任务发现、搜索和安装 Agent Skills。 |
| [`git-commit`](.agents/skills/git-commit/SKILL.md) | 分析变更、智能暂存文件，并生成符合 Conventional Commits 的提交。 |
| [`skill-creator`](.agents/skills/skill-creator/SKILL.md) | 创建、修改、评估和优化 Agent Skills。 |

## 仓库结构

```text
.
├── .agents/
│   └── skills/
│       ├── create-agentsmd/
│       ├── create-readme/
│       ├── documentation-writer/
│       ├── find-skills/
│       ├── git-commit/
│       └── skill-creator/
├── skills-lock.json
└── package.json
```

技能仓库遵循通用的 Agent Skills 目录约定：每个技能目录至少包含一个 `SKILL.md`，并在 frontmatter 中声明 `name` 和 `description`。

## 添加新技能

在 `.agents/skills/<skill-name>/SKILL.md` 创建技能文件：

```markdown
---
name: my-skill
description: 简要说明技能的作用以及适用场景
---

# My Skill

在这里编写 Agent 使用该技能时应遵循的指令。
```

建议技能名称使用小写字母和连字符，并让 `description` 同时说明“做什么”和“什么时候使用”。完成后，可以运行下面的命令验证仓库是否能发现新技能：

```bash
npx skills add BoBo-Ye/My-Skills --list
```

## 本地开发

这个仓库不需要构建步骤。若要使用本地 `skills` CLI 或更新锁文件，可以安装依赖：

```bash
npm install
```

技能内容的主要来源和版本信息记录在 [`skills-lock.json`](skills-lock.json) 中。

## 相关链接

- [Agent Skills](https://agentskills.io/)
- [skills CLI](https://github.com/vercel-labs/skills)
- [skills.sh](https://skills.sh/)
