**English** | [简体中文](./README.zh-CN.md)

# model-thinking-tools

A collection of agent skills themed around **mental models** — each skill packages a way of thinking (first principles, inversion, second-order effects, …) into a capability your agent can invoke when analyzing problems or making decisions.

## Skill structure

Each skill is a kebab-case directory containing a `SKILL.md`:

```
model-thinking-tools/
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

## Usage

Drop a skill directory into your agent's skills directory (e.g. `~/.claude/skills/`) and it will be auto-discovered and invoked on demand.

## Skills

| Skill | Description |
| ----- | ---- |
| [`first-principles-deep-dive`](./first-principles-deep-dive/) | A four-stage interactive flow that deconstructs a concept from first principles: meme layer → real questions → sub-questions → deep answer. For when you want to *truly understand* a concept rather than get a beginner explanation. |

## Contributing

Before creating or modifying a skill, read [`docs/skill-authoring.md`](./docs/skill-authoring.md) — this repo's skill-authoring best practices.

## License

[MIT](./LICENSE)
