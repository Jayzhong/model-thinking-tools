# CLAUDE.md

This repo is a collection of **agent skills themed around mental models (思维模型)** — each skill packages a way of thinking into a capability Claude can invoke.

## Before creating or modifying a skill

**Read [`docs/skill-authoring.md`](./docs/skill-authoring.md) first.** The general workflow is handled by the `skill-creator` skill; that playbook only records what's specific to this repo or non-obvious (language convention, multi-turn persistence, gotchas from real runs, compressing by behavioral value, etc.).

## Repo-specific conventions (everything else: see skill-creator and the playbook)

- **`description` is bilingual (Chinese + English)** — it's the trigger, and Chinese-speaking users need Chinese trigger phrases to match. **SKILL.md body instructions are written in English**; for user-facing phrasings, instruct the model to **respond in the user's language**.
- **After adding / changing a skill, update the skill table in README.**
