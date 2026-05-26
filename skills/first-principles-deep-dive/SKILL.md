---
name: first-principles-deep-dive
description: >-
  A four-stage interactive flow that guides the user to deconstruct a concept from first principles into an expert-level, situation-specific deep answer — not a beginner explanation. Use it whenever the user wants to "really / truly / deeply understand" a concept, says they've "heard of it but can't articulate it," asks to analyze or break down a concept "from first principles," or probes "what is the essence/nature of X" or "what X means at a deeper level" — trigger it even if they never say the words "first principles." Do NOT use for a basic explanation ("what is X", "explain X"), topics with no standardized consensus knowledge (e.g. a company's product strategy), highly subjective topics ("what counts as good design"), or very new concepts the model isn't familiar with. 中文触发词（同样适用）：想"真正搞懂 / 真正理解 / 深入理解"某个概念、"听过但说不清 / 一直没真懂"、要求用"第一性原理"分析或拆解、追问"X 的本质是什么 / 更深一层是什么"；不要用于"什么是 X""解释一下 X"、无标准化共识的话题、极度主观的话题、或太新的概念。
---

# First-Principles Deep Dive

Walk the user through a four-stage process that deconstructs a concept to expert level, ending in a deep answer useful to **their specific situation** — not a beginner explanation.

**The spine is first-principles thinking**: separate the received wisdom everyone repeats (the *meme layer*) from what's actually, fundamentally true beneath it — then reason up from those fundamentals. Stages 1–2 draw exactly that line; Stages 3–4 build on what's underneath.

**Language**: The openings and questions below are English samples. In the actual conversation, **respond in the user's language** (Chinese if they write Chinese, etc.) — convey the same meaning, don't copy the samples verbatim or mix languages at the user.

## Core flow

**Division of labor**: you enumerate the possibilities, the user chooses. You list exhaustively; the user only recognizes / picks / confirms.

**End each stage with one question, then stop and hand the floor back — don't pre-run the next stage.** Once started, stay in this flow across turns — don't *drift* back to one-shot Q&A just because several turns have passed. But "staying in the flow" means holding the thread, not railroading the user: when they go off-script, follow them (see **When the user goes off-script**), and exit readily the moment they signal they want out.

**Meet the user at their layer — don't assume everyone enters at the meme layer, and don't require menu-style answers.** Read where the user's input actually sits and enter the flow at the matching rung: a beginner ("what is X") starts at Stage 1; someone who already knows the basics and asks a pointed question skips ahead — answer it at Stage 2/3 depth, then expand; someone who arrives with a formed judgment goes straight to Path B. Within any stage the user may reply in their own words or ask their own question instead of picking from a list — locate that reply's layer, answer there, then offer the next rung. The stages below are the default arc for a cold start; enter where they are and climb from there. **For any entry past the meme layer, skip the Stage 0 consent opening** — don't give the "four-stage, ~5–10 min" spiel to someone who arrived with a specific question or a judgment; answering them and then offering to go deeper *is* the consent. (Still run the silent fit check.)

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

## When the user goes off-script

The four stages are the default arc, not four mandatory gates. Real conversations wander — follow the user, then offer to resume.

- **Off-topic or tangential question mid-flow** → answer it normally, then offer to pick up where you paused. Don't ignore it to force the next stage.
- **They hand the choice back to you** ("you pick," "they all look good") → that's permission, not indecision: recommend one and continue. ("Don't pick for them" means don't override their choice — not refuse when they delegate.)
- **They reject, amend, or replace your list** (the meme layer or the real questions) → take the correction and adjust; don't march on with the original.
- **They want out** (forget it / just give the short version / switch concept / an unrelated task) → drop the flow and just help. The flow is a default, not a cage.
- **Advanced user wants to jump ahead** → compress or skip stages; don't force a slow march through all four.

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
