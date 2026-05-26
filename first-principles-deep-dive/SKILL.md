---
name: first-principles-deep-dive
description: >-
  引导用户用第一性原理深拆一个概念的四阶段交互流程，产出针对用户具体处境的专家级深度回答（而非入门解释）。当用户想"真正搞懂 / 真正理解 / 深入理解"某个概念、说自己"听过但说不清 / 一直没真懂"、要求用"第一性原理"分析或拆解某个概念、或追问"X 的本质是什么 / X 在更深一层意味着什么"这类挖深请求时，请主动使用本 skill —— 即使用户没有明说"第一性原理"也应触发。A four-stage interactive flow that guides the user to deconstruct a concept from first principles and produce an expert-level, situation-specific deep answer (not a beginner explanation). Use this skill whenever the user wants to "really understand / truly grasp / deeply understand" a concept, says they've "heard of it but can't really articulate it," asks to analyze or break down a concept "from first principles," or probes "what is the essence/nature of X" or "what does X mean at a deeper level" — trigger it even if the user never says the words "first principles." 不要用于：用户只想要入门解释（"什么是 X""解释一下 X"）、没有标准化共识知识的话题（如某公司的产品策略）、极度主观的话题（如"什么算好设计"）、或 LLM 不熟悉的极新概念。Do NOT use for: requests for a basic/introductory explanation ("what is X", "explain X"), topics with no standardized consensus knowledge (e.g. a specific company's product strategy), highly subjective topics (e.g. "what counts as good design"), or very new concepts the model isn't familiar with.
---

# First-Principles Deep Dive

Walk the user through a four-stage process that deconstructs a concept to expert level, ending in a deep answer useful to **their specific situation** — not a beginner explanation.

**Language**: The openings and questions below are English samples. In the actual conversation, **respond in the user's language** (Chinese if they write Chinese, etc.) — convey the same meaning, don't copy the samples verbatim or mix languages at the user.

## Core flow

**Division of labor**: you enumerate the possibilities, the user chooses. You list exhaustively; the user only recognizes / picks / confirms.

**End each stage with one question, then stop and hand the floor back — don't pre-run the next stage.** Once started, stay in this flow every turn until the user says "just explain it," the four stages finish, or they explicitly exit; don't drift back to normal one-shot Q&A after several turns, and if unsure, default to still being in the flow.

- **Stage 0 · Informed consent**
  - Concept unclear → first ask which concept to unpack.
  - Internal fit check (don't narrate): does this concept have an enumerable, expert-level layer of consensus knowledge? If not (subjective / no standardized knowledge / too new) → gently say so and suggest normal mode.
  - Opening: "I can use a four-stage process to deeply unpack this concept — about 5–10 minutes, with a few light choices from you along the way. If you'd rather just have a quick beginner explanation, say 'just explain it.' Want to start?" If the user says "just explain it" → exit the skill and answer normally.

- **Stage 1 · Meme layer** — List **~5–7** surface-level takes most people hold about the concept, one sentence each. Then ask: "Is this roughly the whole of your understanding, or do you already know more?" The calibration sets where Stage 2 starts: "roughly this" → start just beyond the meme layer; "I know more" → pitch higher and skip what they already have.

- **Stage 2 · Real questions** — **Pitched to the level they reported**, list **~5–7** real questions / facts beyond the meme layer that people who genuinely understand the concept know, one sentence each. Ask the user to pick **1–2** they most want to dig into or that most surprise them. Gentle pointing is fine ("I'd especially love you to look at #N"), but don't pick for them.

- **Stage 3 · Sub-questions** — Expand the chosen real question into **~4–5** sub-questions across four angles: **descriptive** (what it is) / **mechanism** (why) / **boundaries** (where it's most/least extreme) / **application** (what it means for their decisions). Ask the user to confirm / edit / drop / add, **especially inviting their situation** ("as a PM…", "applied to the X I'm working on…") — the application angle is where the deep answer pays off most. In the same message, ask how to close: "① I give you the deep answer directly; or ② you commit your own judgment first and I verify/extend it (highest density, but you think first). Default is ① if you don't choose."

- **Stage 4 · Deep answer** (follow the Stage 3 choice; default to A)
  - **Path A (default · level 3)**: answer deeply. Don't start from basics; expand the application sub-questions in the most detail, with immediately usable criteria / examples / self-checks; length is welcome but not sprawl — hold it with structure and end on a one-line takeaway.
  - **Path B (user chose · level 4)**: first ask the user to commit their own judgment ("Before I answer — what's your own judgment or guess? Rough is fine") → **stop and wait** → then do a **diff review** rather than re-explaining: confirm what's right, correct what's wrong, fill what's missing, temper overstated claims.
  - Either path closes by asking: "Anything you'd like to go deeper on?" Yes → continue (back to Stage 2 for another question, or switch path); No → end the skill.

## Why it's built this way (read once)

- **Stop after each stage**: the user's choice determines the next stage's content. Pre-running = producing from a guess that will likely be overturned, and it defeats the whole point of the interaction. This is the crux.
- **Keep cognitive load minimal**: the user only recognizes / picks / confirms, never deconstructs. The one exception is Path B — where they *choose* to spend effort for the highest density.
- **Stay conversational**: like a knowledgeable peer thinking alongside them, not a machine running a checklist. Gentle pointing is fine; deciding for them is not.
- **Why Stage 4 can fork to level 4**: Stages 1–3 are themselves walking the user through the deconstruction — which is the prerequisite for forming *their own* judgment. So by the end of 1–3 they're equipped to attempt Path B; Path B upgrades the interaction from "LLM teaches them" to "LLM verifies their judgment," the highest density this skill produces — don't waste it.

## Contrast examples

**Meme layer vs real question** (Stage 2's most common trap: re-skinning the meme layer as a "real" question — pseudo-depth)
- ✗ Re-skinned meme layer: "few-shot is more accurate than zero-shot."
- ✓ Real question: "few-shot leaks the surface patterns and biases of the examples, so it's sometimes worse than zero-shot."
- Self-check: would someone who genuinely understands this say "outsiders usually don't know this"? If no → it's still meme layer, replace it.

**Rubber-stamping vs verifying** (Path B's most common trap: agreeing along with the user)
- ✗ Rubber-stamp: "Your judgment is spot on, really insightful!"
- ✓ Verify: "Direction is right; point 2 is wrong, the correct version is X; you missed Y; 'activation is no longer scarce' is overstated — precisely, *generic* activation isn't scarce, but *precise* activation still has room."

## Field notes (from real walkthroughs)

- **User confirmed the sub-questions but gave no situation**: infer their situation from the conversation so far + say you're inferring ("you didn't specify, so I'll assume X — correct me"); don't silently fall back to a generic answer, and don't burn a whole extra turn just for this — only ask again briefly if there's truly nothing to infer from.
- **User picked 2 real questions at once**: if they connect → weave one throughline, don't let sub-questions balloon to 8–10; if they don't → run one full cycle per question, asking which to start with if needed.
- **User volunteers their own judgment anywhere in the flow**: handle it as a Path B diff review (confirm / correct / fill / temper), don't rubber-stamp.
