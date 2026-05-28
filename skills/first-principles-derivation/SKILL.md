---
name: first-principles-derivation
description: >-
  An interactive flow that helps the user derive an answer from first principles: surface what the conventional frame quietly assumes, identify the foundational truths / constraints of the domain (the "atoms"), test the assumptions against the atoms, and re-derive an answer from atoms alone. Trigger when the user wants to "use / apply first principles," "challenge the assumptions," "re-derive from fundamentals or from scratch," "question the conventional approach," doubts the inherited framing, or asks "are we missing something basic about X" — even when they don't explicitly name the framework. Do NOT use for deeper understanding of a concept that doesn't need re-derivation (use `concept-deep-dive` instead), purely subjective topics ("what counts as good art"), or domains with no identifiable mechanisms or constraints to ground on. 中文触发词（同样适用）：要"用第一性原理拆 / 分析 / 推导"、"从根本 / 最底层重新推"、"质问 / 推翻惯例 / 默认假设"、"我们是不是把 X 的基本东西搞错了"；不要用于：只想深入理解某概念（→ `concept-deep-dive`）、纯主观话题、无机制可锚的领域。
---

# First-Principles Derivation

Guide the user to derive an answer **from first principles**: surface what the conventional frame *quietly assumes*, identify what's *foundationally true* in the domain (the "atoms"), test the assumptions against the atoms, and re-derive from atoms alone. The payoff is often a derivation that **differs from** — or sharpens — the conventional take.

**Language**: The openings and questions below are English samples. In the actual conversation, **respond in the user's language** (Chinese if they write Chinese, etc.) — convey the same meaning, don't copy verbatim or mix languages at the user.

## Core flow

**Division of labor**: you enumerate possibilities and do the explicit reasoning chain; the user supplies the question, the inherited frame to pressure-test, and their judgment at each branch. Where listing is involved, the **~N** counts below keep lists digestible — they're defaults, not quotas: adjust to the domain, never pad to hit a number or drop something important to stay under one.

**End each stage with one question, then stop and hand the floor back — don't pre-run the next stage.** Once started, stay in this flow across turns — don't *drift* back to one-shot Q&A just because several turns have passed. But "staying in the flow" means holding the thread, not railroading the user: when they go off-script, follow them (see **When the user goes off-script**), and exit readily the moment they signal they want out.

**Meet the user at their layer.** If they arrive with a half-formed first-principles take, skip ahead to test it (Stage 3) or to a diff-review of their derivation (Path B). The stages below are the cold-start arc; enter where they are and climb from there. **For any entry past Stage 0, skip the consent opening** — answering and offering to go deeper *is* the consent.

- **Stage 0 · Frame + fit check**
  - Get the user's question, claim, problem, or design.
  - **Silent fit check** (don't narrate): does this domain have identifiable atoms — real mechanisms, physical/mathematical/economic constraints, or stable definitions to ground on? If not (purely subjective; no underlying mechanism), gently say so and offer a different mode.
  - Ask in one question: **"What's the conventional answer or framing here that you want to pressure-test?"** That's the inherited frame this work will challenge.

- **Stage 1 · Surface inherited assumptions** — List **~3–5** assumptions the conventional frame quietly depends on, one sentence each. Pick the **load-bearing** ones (if false, the conventional answer wobbles), not trivial details. Then ask: "Which of these had you not questioned? Any to add, rephrase, or drop?"

- **Stage 2 · Identify the atoms** — List **~3–5** things that are foundationally true in this domain regardless of convention — real mechanisms, physical/economic constraints, mathematical identities, precise definitions. These are what's *left* when you strip the convention. Ask the user to add, dispute, or sharpen. **Be honest where an atom is contestable**: flag it explicitly ("this one I'm less sure is irreducible — push on it if it feels like a smuggled assumption"). First principles fails silently when "atoms" are themselves assumptions in disguise.

- **Stage 3 · Test assumptions against atoms** — For each Stage-1 assumption, check: does it actually follow from the Stage-2 atoms, or is it convention / analogy / historical accident? Be specific about *which atom* each assumption survives by or collapses against. Surface what survives, what fails. Ask: "Do these verdicts match your intuition, or do any feel forced?" In the same message, ask how to close: "① I derive an answer from the surviving atoms (default); or ② you take a derivation first and I diff-review it."

- **Stage 4 · Re-derive** (follow the Stage 3 choice; default to A)
  - **Path A (default)**: from atoms alone, derive an answer / approach to the user's original question. Show the chain step by step — each step traceable to an atom or a prior derived step. Make **explicit where this differs from the conventional answer**, and where the conventional answer came from (path-dependency, analogy, historical contingency). Length is welcome but not sprawl — end on what changes for the user.
  - **Path B (user chose)**: user commits their own first-principles derivation first → **stop and wait** → then do a **diff review**: confirm what's genuinely grounded in atoms, correct where derivation skipped a step, fill missing pieces, and **temper overreaches** ("this conclusion goes further than the atoms support — they only get you as far as Y").
  - Either path closes by asking: "Anything you'd like to push on further? — testing another assumption, sharpening an atom, or re-deriving a related question." Yes → continue; No → end the skill.

## Why it's built this way

- **Atoms before derivation**: derivation is only as good as your atoms. A wrong "atom" is worse than no first-principles attempt — it dresses up convention as derivation.
- **Assumptions before atoms (in conversation order)**: stating what the inherited frame assumes makes the user *see* what they've been taking for granted; atoms then have something concrete to land against.
- **Difference, not just depth**: the payoff of first principles isn't "deeper explanation" — it's seeing where the conventional answer is *contingent* and what is actually *mandatory*.
- **Honest contestability**: this skill produces real derivations only when atoms are real. Flag contested ones; refuse to fake derivations dressed in first-principles language.

## Contrast examples

**Assumption vs atom** (Stages 1–2's most common trap: smuggling an assumption in as an atom)
- ✗ "Atom": "Rockets need expensive aerospace alloys." — This is a manufacturing convention, not an atom; it bakes in a whole industry's approach.
- ✓ Atom: "Raw material costs are bounded by what aluminum / steel / liquid oxygen actually cost on the open market." — Verifiable, mechanism-grounded.
- Self-check for each candidate atom: *would this still hold in a counterfactual where the conventional industry didn't exist?* If no → it's an assumption, not an atom.

**Derivation vs assertion** (Stage 4's most common trap: stating a different conclusion without actually deriving it)
- ✗ Assertion in derivation clothing: "From first principles, rockets should be much cheaper."
- ✓ Derivation: "Raw materials cost C; assembly is N hours at rate R; reusing the first stage amortizes the per-flight cost across F flights; therefore feasible price-per-launch is roughly C/F + RN/F — an order of magnitude below the historical $X." — Each step traces to an atom or a prior step.

## When the user goes off-script

The stages are the default arc, not gates. Follow the user.

- **They reject one of your "atoms" as actually an assumption** → great, that *is* the work. Move it from Stage 2 back to Stage 1 and revise.
- **They want to skip straight to re-derivation** → do it, but check at least one assumption against at least one atom on the way; otherwise you're opinion-swapping in first-principles costume.
- **They give an unrelated question mid-flow** → answer it normally, then offer to come back.
- **They want out** (forget it / change topic / just give a normal answer) → drop the flow and just help. The flow is a default, not a cage.

## Field notes (from real walkthroughs)

_None yet — populated after real runs._
