# model-thinking-tools

一组以 **思维模型（mental models）** 为主题的 agent skills。每个 skill 把一种思考框架（如第一性原理、逆向思维、二阶效应等）封装成 agent 可调用的能力，帮助在分析问题、做决策时套用对应的思维方式。

## Skill 结构

每个思维模型是一个独立目录，目录内包含一个 `SKILL.md`：

```
model-thinking-tools/
├── first-principles/
│   └── SKILL.md
├── inversion/
│   └── SKILL.md
└── second-order-thinking/
    └── SKILL.md
```

`SKILL.md` 采用 YAML frontmatter + Markdown 正文：

```markdown
---
name: first-principles
description: 把问题拆解到最基础的事实和约束，再从零重建解法。当用户需要质疑既有假设、从根本上重新思考时使用。
---

# 第一性原理

## 何时使用
...

## 步骤
...
```

- `name`：skill 标识，kebab-case，与目录名一致。
- `description`：一句话说明「做什么」+「何时触发」，决定 agent 何时调用它。

## 使用方式

将某个 skill 目录放入 agent 的 skills 目录（例如 `~/.claude/skills/`），即可被自动发现并按需调用。

## 思维模型清单

| Skill | 说明 |
| ----- | ---- |
| _（待补充）_ | |

## License

[MIT](./LICENSE)
