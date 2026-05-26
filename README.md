# model-thinking-tools

一组以 **思维模型（mental models）** 为主题的 agent skills。每个 skill 把一种思考框架（如第一性原理、逆向思维、二阶效应等）封装成 agent 可调用的能力，帮助在分析问题、做决策时套用对应的思维方式。

## Skill 结构

每个思维模型是一个独立目录，目录内包含一个 `SKILL.md`：

```
model-thinking-tools/
├── first-principles-deep-dive/
│   └── SKILL.md
├── inversion/
│   └── SKILL.md
└── second-order-thinking/
    └── SKILL.md
```

`SKILL.md` 采用 YAML frontmatter + Markdown 正文：

```markdown
---
name: inversion
description: >-
  引导用户用"逆向思维"拆解问题：与其问"怎么成功"，先问"怎么必然失败"再反推。当用户……时使用。
  Guide the user through inversion — instead of "how to succeed", ask "how would this
  guaranteed fail" and work backwards. Use when … 不要用于：……
---

# 逆向思维 / Inversion

正文指令用中文；面向用户的话术指示模型用用户的语言作答。
具体写法见 docs/skill-authoring.md，可参考已有的 first-principles-deep-dive。
```

- `name`：skill 标识，kebab-case，与目录名一致。
- `description`：**是触发器，不是摘要**——写清「做什么 + 何时触发 + 何时*不*触发」，并保持**中英双语**（英文用户靠英文触发词命中）。

## 使用方式

将某个 skill 目录放入 agent 的 skills 目录（例如 `~/.claude/skills/`），即可被自动发现并按需调用。

## 思维模型清单

| Skill | 说明 |
| ----- | ---- |
| [`first-principles-deep-dive`](./first-principles-deep-dive/) | 用第一性原理深拆一个概念的四阶段交互流程：识别模因层 → 枚举真问题 → 扩展子问题 → 深度回答。适合"想真正搞懂某个概念"而非要入门解释时。 |

## 贡献 / 新增 skill

创建或修改 skill 前，请先读 [`docs/skill-authoring.md`](./docs/skill-authoring.md) —— 本仓库的 skill 创作最佳实践。

## License

[MIT](./LICENSE)
