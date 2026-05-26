# CLAUDE.md

本仓库是一组以**思维模型（mental models）为主题的 agent skills** 合集。每个 skill 把一种思考框架封装成 Claude 可调用的能力。

## 创建或修改 skill 前，先读这个

**动手写 / 改任何 skill 之前，先读 [`docs/skill-authoring.md`](./docs/skill-authoring.md)**——它沉淀了本仓库的 skill 创作最佳实践（description 写法、信任模型、多轮持续性、Gotchas 来自实跑、按行为价值压缩等）。按原理取舍，不要当教条照搬。

## 关键约定（速查）

- **结构**：每个 skill 一个 kebab-case 目录 + `SKILL.md`；frontmatter 必填 `name`（与目录名一致）、`description`。
- **description = 触发器**：写"做什么 + 何时触发 + 何时*不*触发(近似负例)"，略 pushy 防漏触发，**保持中英双语**（英文用户靠英文触发词命中）。
- **正文语言**：指令用中文（单语）；面向用户的话术给中文范例 + 指示模型**用用户的语言作答**。
- **流程**：捕捉意图 → 先 review 计划再动手 → 起草 → **实跑验证**（交互型尤其重要，最好用非专家话题测）→ 回填实测 Gotchas。
- **新增 / 改动 skill** 后更新 README 的清单表。
- **提交**：按逻辑步骤 commit + push，message 说清做了什么。
