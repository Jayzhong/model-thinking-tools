# CLAUDE.md

本仓库是一组以**思维模型（mental models）为主题的 agent skills** 合集——每个 skill 把一种思考框架封装成 Claude 可调用的能力。

## 创建或修改 skill 前

**先读 [`docs/skill-authoring.md`](./docs/skill-authoring.md)。** 通用流程交给 `skill-creator` skill；那份 playbook 只记本仓库特有 / 非显然的增量（语言约定、多轮持续性、Gotchas 来自实跑、按行为价值压缩等）。

## 本仓库特有约定（其余见 skill-creator 与 playbook）

- **description 中英双语**（它是触发器，英文用户靠英文触发词命中）；**正文指令用中文**，面向用户的话术指示模型**用用户的语言作答**。
- **新增 / 改动 skill 后，更新 README 的清单表。**
