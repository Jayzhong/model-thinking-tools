[English](./README.md) | **简体中文**

# model-thinking-tools

[![Add with skills.sh](https://skills.sh/b/Jayzhong/model-thinking-tools)](https://skills.sh/Jayzhong/model-thinking-tools)

一组以 **思维模型（mental models）** 为主题的 agent skills。每个 skill 把一种思考框架（第一性原理、逆向思维、二阶效应等）封装成 agent 可调用的能力，用于分析问题、做决策时套用对应的思维方式。

## 安装

### 用 `npx skills`（支持 Claude Code、Codex、Cursor 等）

```bash
# 交互式：勾选要哪些 skill、装到哪些 agent
npx skills add Jayzhong/model-thinking-tools

# 只列出有哪些 skill，不安装
npx skills add Jayzhong/model-thinking-tools --list

# 单独装某一个 skill（非交互），装到 Claude Code
npx skills add Jayzhong/model-thinking-tools --skill concept-deep-dive -a claude-code

# 全装
npx skills add Jayzhong/model-thinking-tools --skill '*'

# 或直接指向单个 skill
npx skills add https://github.com/Jayzhong/model-thinking-tools/tree/main/skills/concept-deep-dive
```

### 作为 Claude Code 插件

```
/plugin marketplace add Jayzhong/model-thinking-tools
/plugin install model-thinking-tools@model-thinking-tools
```

### 手动

把任意 `skills/<name>/` 目录拷进 agent 的 skills 目录（例如 `~/.claude/skills/`）。

## 目录结构

每个 skill 是 `skills/` 下的一个 kebab-case 目录，内含一个 `SKILL.md`：

```
model-thinking-tools/
├── .claude-plugin/          # Claude Code 插件 + 市场清单
└── skills/
    ├── concept-deep-dive/
    │   └── SKILL.md
    └── first-principles-derivation/
        └── SKILL.md
```

`SKILL.md` 采用 YAML frontmatter + Markdown 正文：

```markdown
---
name: inversion
description: >-
  引导用户用"逆向思维"拆解问题：与其问"怎么成功"，先问"怎么必然失败"再反推。当用户……时使用。
  Guide the user through inversion — instead of "how to succeed," ask "how would this
  guaranteed fail" and work backwards. Use when … 不要用于：……
---

# Inversion

正文指令用英文；面向用户的话术由模型按用户的语言作答。
详见 docs/skill-authoring.md（英文），可参考已有的 concept-deep-dive。
```

- `name`：skill 标识，kebab-case，与目录名一致。
- `description`：**是触发器，不是摘要**——写清「做什么 + 何时触发 + 何时*不*触发」，并保持**中英双语**（英文用户靠英文触发词命中）。

## 思维模型清单

| Skill | 说明 |
| ----- | ---- |
| [`concept-deep-dive`](./skills/concept-deep-dive/) | 深拆一个概念的四阶段交互流程：识别模因层 → 枚举真问题 → 扩展子问题 → 深度回答。适合"想真正搞懂某个概念"而非要入门解释时。 |
| [`first-principles-derivation`](./skills/first-principles-derivation/) | 从第一性原理**重新推导**一个答案的交互流程：浮出继承框架的假设、识别领域的"原子"、把假设拿到原子前对质、仅用原子重新推导。适合质问惯例、做再推导——不是用来"深入理解某个概念"（那是 `concept-deep-dive`）。|

## 贡献

创建或修改 skill 前，请先读 [`docs/skill-authoring.md`](./docs/skill-authoring.md)（英文）—— 本仓库的 skill 创作最佳实践。

## License

[MIT](./LICENSE)
