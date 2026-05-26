**English** | [简体中文](./README.zh-CN.md)

# model-thinking-tools

[![Add with skills.sh](https://skills.sh/b/Jayzhong/model-thinking-tools)](https://skills.sh/Jayzhong/model-thinking-tools)

A collection of agent skills themed around **mental models** — each skill packages a way of thinking (first principles, inversion, second-order effects, …) into a capability your agent can invoke when analyzing problems or making decisions.

## Install

### With `npx skills` (works with Claude Code, Codex, Cursor, and more)

```bash
# Interactive: pick which skills + which agents to install
npx skills add Jayzhong/model-thinking-tools

# List the available skills without installing
npx skills add Jayzhong/model-thinking-tools --list

# Install one specific skill (non-interactive) into Claude Code
npx skills add Jayzhong/model-thinking-tools --skill first-principles-deep-dive -a claude-code

# Install every skill
npx skills add Jayzhong/model-thinking-tools --skill '*'

# Or point directly at a single skill
npx skills add https://github.com/Jayzhong/model-thinking-tools/tree/main/skills/first-principles-deep-dive
```

### As a Claude Code plugin

```
/plugin marketplace add Jayzhong/model-thinking-tools
/plugin install model-thinking-tools@model-thinking-tools
```

### Manually

Copy any `skills/<name>/` directory into your agent's skills directory (e.g. `~/.claude/skills/`).

## Skill structure

Each skill is a kebab-case directory under `skills/`, containing a `SKILL.md`:

```
model-thinking-tools/
├── .claude-plugin/          # Claude Code plugin + marketplace manifests
└── skills/
    ├── first-principles-deep-dive/
    │   └── SKILL.md
    ├── inversion/
    │   └── SKILL.md
    └── second-order-thinking/
        └── SKILL.md
```

`SKILL.md` uses YAML frontmatter + a Markdown body:

```markdown
---
name: inversion
description: >-
  引导用户用"逆向思维"拆解问题：与其问"怎么成功"，先问"怎么必然失败"再反推。当用户……时使用。
  Guide the user through inversion — instead of "how to succeed," ask "how would this
  guaranteed fail" and work backwards. Use when … 不要用于：……
---

# Inversion

Body instructions are written in English; for user-facing phrasings the model
responds in the user's language. See docs/skill-authoring.md; the existing
first-principles-deep-dive skill is a worked example.
```

- `name`: skill identifier, kebab-case, matches the directory name.
- `description`: **a trigger, not a summary** — state what it does + when to trigger + when NOT to, and keep it **bilingual** (Chinese-speaking users match on Chinese trigger phrases).

## Skills

| Skill | Description |
| ----- | ---- |
| [`first-principles-deep-dive`](./skills/first-principles-deep-dive/) | A four-stage interactive flow that deconstructs a concept from first principles: meme layer → real questions → sub-questions → deep answer. For when you want to *truly understand* a concept rather than get a beginner explanation. |

## Contributing

Before creating or modifying a skill, read [`docs/skill-authoring.md`](./docs/skill-authoring.md) — this repo's skill-authoring best practices.

## License

[MIT](./LICENSE)
