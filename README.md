# model-thinking-tools

A collection of agent skills themed around **mental models** — each skill packages a way of thinking (first principles, inversion, second-order effects, …) into a capability your agent can invoke when analyzing problems or making decisions.

> 一组以 **思维模型（mental models）** 为主题的 agent skills。每个 skill 把一种思考框架（第一性原理、逆向思维、二阶效应等）封装成 agent 可调用的能力，用于分析问题、做决策时套用对应的思维方式。

## Skill structure / 目录结构

Each skill is a kebab-case directory containing a `SKILL.md`.
每个 skill 是一个 kebab-case 目录，内含一个 `SKILL.md`：

```
model-thinking-tools/
├── first-principles-deep-dive/
│   └── SKILL.md
├── inversion/
│   └── SKILL.md
└── second-order-thinking/
    └── SKILL.md
```

`SKILL.md` uses YAML frontmatter + a Markdown body / 采用 YAML frontmatter + Markdown 正文：

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

- `name`: skill identifier, kebab-case, matches the directory name. / skill 标识，kebab-case，与目录名一致。
- `description`: **a trigger, not a summary** — state what it does + when to trigger + when NOT to, and keep it **bilingual** (Chinese-speaking users match on Chinese trigger phrases). / **是触发器，不是摘要**——写清「做什么 + 何时触发 + 何时*不*触发」，并保持**中英双语**。

## Usage / 使用方式

Drop a skill directory into your agent's skills directory (e.g. `~/.claude/skills/`) and it will be auto-discovered and invoked on demand.
将某个 skill 目录放入 agent 的 skills 目录（例如 `~/.claude/skills/`），即可被自动发现并按需调用。

## Skills / 思维模型清单

| Skill | Description / 说明 |
| ----- | ---- |
| [`first-principles-deep-dive`](./first-principles-deep-dive/) | A four-stage interactive flow that deconstructs a concept from first principles: meme layer → real questions → sub-questions → deep answer. For when you want to *truly understand* a concept rather than get a beginner explanation. <br> 用第一性原理深拆一个概念的四阶段交互流程：识别模因层 → 枚举真问题 → 扩展子问题 → 深度回答。适合"想真正搞懂某个概念"而非要入门解释时。 |

## Contributing / 贡献

Before creating or modifying a skill, read [`docs/skill-authoring.md`](./docs/skill-authoring.md) — this repo's skill-authoring best practices.
创建或修改 skill 前，请先读 [`docs/skill-authoring.md`](./docs/skill-authoring.md) —— 本仓库的 skill 创作最佳实践。

## License

[MIT](./LICENSE)
