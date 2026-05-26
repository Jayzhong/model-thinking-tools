---
name: first-principles-deep-dive
description: >-
  引导用户用第一性原理深拆一个概念的四阶段交互流程，产出针对用户具体处境的专家级深度回答（而非入门解释）。当用户想"真正搞懂 / 真正理解 / 深入理解"某个概念、说自己"听过但说不清 / 一直没真懂"、要求用"第一性原理"分析或拆解某个概念、或追问"X 的本质是什么 / X 在更深一层意味着什么"这类挖深请求时，请主动使用本 skill —— 即使用户没有明说"第一性原理"也应触发。A four-stage interactive flow that guides the user to deconstruct a concept from first principles and produce an expert-level, situation-specific deep answer (not a beginner explanation). Use this skill whenever the user wants to "really understand / truly grasp / deeply understand" a concept, says they've "heard of it but can't really articulate it," asks to analyze or break down a concept "from first principles," or probes "what is the essence/nature of X" or "what does X mean at a deeper level" — trigger it even if the user never says the words "first principles." 不要用于：用户只想要入门解释（"什么是 X""解释一下 X"）、没有标准化共识知识的话题（如某公司的产品策略）、极度主观的话题（如"什么算好设计"）、或 LLM 不熟悉的极新概念。Do NOT use for: requests for a basic/introductory explanation ("what is X", "explain X"), topics with no standardized consensus knowledge (e.g. a specific company's product strategy), highly subjective topics (e.g. "what counts as good design"), or very new concepts the model isn't familiar with.
---

# 第一性原理深拆 / First-Principles Deep Dive

帮用户**真正搞懂**一个概念——不是入门解释，而是带他走一个四阶段流程，完成专家级的概念拆解，最终拿到对其**具体处境**有用的深度回答。

Help the user **genuinely understand** a concept — not a beginner explanation, but a guided four-stage process that walks them through an expert-level deconstruction and lands on a deep answer useful to **their specific situation**.

---

## 这个 skill 怎么工作 / The operating model

分工是整个流程的核心：**你负责枚举可能性，用户负责做选择。** 你穷尽地列出某一层有哪些东西，用户只需要做"识别 / 选择 / 确认"这种低成本动作。不要替用户拆解，也不要替用户做决定。

The division of labor is the whole point: **you enumerate the possibilities, the user makes the choices.** You exhaustively lay out what exists at a given layer; the user only has to recognize, pick, or confirm — all low-effort moves. Don't do the deconstruction *for* them, and don't make their choices *for* them.

流程是：**阶段 0（知情同意，含适配性自检）→ 阶段 1（模因层）→ 阶段 2（真问题）→ 阶段 3（子问题）→ 阶段 4（深度回答）。** 用户侧称它为"四阶段"，因为阶段 0 只是入口闸门，真正的四步是 1–4。

The flow is: **Stage 0 (informed consent + fit check) → Stage 1 (the meme layer) → Stage 2 (the real questions) → Stage 3 (sub-questions) → Stage 4 (the deep answer).** Call it a "four-stage" process to the user — Stage 0 is just the gate; the real four steps are 1–4.

---

## 命门：每阶段做完就停 / The crux: stop after every stage

这是整个 skill 能不能正常工作的命门，所以从一开始就讲清楚为什么：

This is the single thing that makes or breaks the skill, so here's the *why* up front:

> **用户在每一阶段的选择，决定了下一阶段的内容。** 阶段 2 列什么真问题，取决于用户在阶段 1 报的水位；阶段 3 展开哪些子问题，取决于用户在阶段 2 挑了哪条。所以如果你在用户回复之前就把后面的阶段一起做了，你只能基于*猜测*产出——而那个猜测大概率会被用户的实际选择推翻，既浪费了输出，也彻底废掉了这个流程交互的意义。流程的价值恰恰来自"等用户说话"。

> **The user's choice at each stage determines the content of the next one.** Which real questions you list in Stage 2 depends on the level the user reported in Stage 1; which sub-questions you expand in Stage 3 depends on what they picked in Stage 2. So if you run ahead and do later stages before the user replies, you can only produce them from a *guess* — and that guess will most likely be overturned by their actual choice, wasting the output and defeating the entire point of the interaction. The value of this flow comes precisely from waiting for the user to speak.

**因此：每个阶段结束，以一个清晰的问句收尾，然后结束本回合、把发言权交还用户。不要预先做下一个阶段。** 这条会在每个阶段里再提醒一次——不是啰嗦，是因为完成任务的惯性很强，需要在每个边界处主动压住。

**So: end each stage with one clear question, then end your turn and hand the floor back to the user. Do not pre-run the next stage.** This gets repeated at every stage below — not out of redundancy, but because the pull to "just finish the task" is strong and needs to be actively resisted at each boundary.

---

## 全程原则 / Principles that hold throughout

1. **每阶段做完就停。** 见上。每个阶段只做它自己那一段。
   **Stop after each stage.** See above. Each turn does only its own stage.

2. **不替用户做选择。** 阶段 2 列完真问题，让用户挑；阶段 3 列完子问题，让用户确认。你的角色是把可能性摆出来，选择权始终在用户。
   **Don't choose for the user.** After listing the real questions in Stage 2, let them pick; after listing sub-questions in Stage 3, let them confirm. Your job is to lay out options; the choice stays with them.

3. **每一步认知负担保持低。** 用户只做识别（"我在哪一层"）、选择（"我选这个"）、确认（"对 / 调一下"），永远不需要他自己做拆解。
   **Keep each step low-effort.** The user only recognizes ("which layer am I at"), selects ("I'll take this one"), or confirms ("yes / tweak it") — never does the deconstruction themselves.

4. **保持对话感，不要机械执行流程。** 你可以做温和的指向（"我特别想让你看一下第 3 条"），但温和指向 ≠ 替用户决定。语气像一个懂行的人在陪聊，不像一个在跑 checklist 的机器。
   **Stay conversational, not mechanical.** You may gently point ("I'd especially love you to look at #3") — but a gentle nudge is not making the decision for them. Sound like a knowledgeable person thinking alongside the user, not a machine running a checklist.

5. **全程使用用户的语言。** 本文件双语只是为了记录；面对用户时检测他用的语言并始终用那一种回应，不要中英混着抛给用户。
   **Respond throughout in the user's language.** This file is bilingual only for documentation; with the user, detect their language and stick to it — don't dump both languages on them.

---

## 阶段 0：知情同意（含适配性自检与概念确认）/ Stage 0: Informed consent (with fit check & concept check)

触发后，按顺序处理三件事：

When triggered, handle three things in order:

**(a) 概念是否明确？/ Is the concept specified?**
如果用户没说清要拆哪个概念（例如只说"帮我用第一性原理拆一下"），先问他想深入哪个概念。**问完就停，等回复。**
If the user hasn't named a concept (e.g. just "help me break something down from first principles"), ask which concept they want to go deep on. **Ask, then stop and wait.**

**(b) 适配性自检（内部判断，不必说给用户）/ Fit check (internal — don't narrate it).**
默念一句：这个概念有没有可枚举的、专家级的共识知识层？如果它属于——极度主观（"什么算好设计"）、没有标准化知识（某公司的产品策略）、或 LLM 不熟悉的极新概念——那么阶段 1 的"模因层枚举"会垮掉。这种情况下温和说明，并建议切回普通模式，例如：
Silently ask yourself: does this concept have an enumerable, expert-level layer of consensus knowledge? If it's highly subjective ("what counts as good design"), has no standardized knowledge (a specific company's product strategy), or is a very new concept the model isn't familiar with — then Stage 1's "meme-layer enumeration" will fall apart. In that case, gently say so and suggest normal mode, e.g.:

> 这个话题更偏主观判断 / 没有一套公认的标准化知识，四阶段深拆流程不太吃得上力。我可以直接跟你聊聊我的想法，你看行吗？
> This topic is more subjective / lacks a body of agreed-upon standardized knowledge, so the four-stage deep-dive won't add much. I can just share my thinking with you directly — does that work?

**(c) 知情同意 / Informed consent.**
概念明确、且适配性 OK 时，给出这段开场（按用户语言）：
When the concept is clear and the fit check passes, open with this (in the user's language):

> 我可以用一个四阶段流程帮你深拆这个概念。整个过程大约 5–10 分钟，你需要在每一步做一些轻量级的选择。如果你只想要快速的入门解释，告诉我"直接讲"，我会切换到普通解释模式。要开始吗？
> I can walk you through a four-stage process to deeply unpack this concept. It takes about 5–10 minutes, and you'll make a few light-touch choices along the way. If you'd rather just have a quick beginner-level explanation, say "just explain it" and I'll switch to normal mode. Want to start?

- 用户说"直接讲" / "just explain it" → **退出 skill**，用普通方式回答这个概念。
  User says "just explain it" → **exit the skill** and answer normally.
- 用户确认要走 → 进入阶段 1。
  User confirms → go to Stage 1.

**问完开场就停，等回复。不要提前列模因层。**
**After the opening, stop and wait. Do not pre-list the meme layer.**

---

## 阶段 1：识别模因层 / Stage 1: Identify the meme layer

"模因层"= 大多数人对这个概念的理解：那些被反复重复、听起来对、其实只是表面的说法。

The "meme layer" = how most people understand the concept: the takes that get repeated endlessly, sound right, but are only surface-deep.

- 列出 **5–7 条**模因层说法，每条一句话。
  List **5–7** meme-layer statements, one sentence each.
- 然后问用户校准水位：
  Then ask the user to calibrate their level:

> 这些说法是不是大致就是你对这个概念的全部理解？还是你其实已经懂得比这更多？
> Is this roughly the extent of your understanding of this concept — or do you actually already know more than this?

这个校准问句很重要：用户的回答决定阶段 2 把"真问题"定在多高。说"差不多就这些"→ 阶段 2 从紧贴模因层之外起步；说"我懂得更多"→ 阶段 2 直接抬高，跳过他已知的。

This calibration matters: their answer sets how high to pitch the "real questions" in Stage 2. "Pretty much just this" → start Stage 2 just beyond the meme layer; "I know more" → pitch Stage 2 higher and skip what they already have.

**列完、问完，停下，等回复。不要自己接着枚举真问题。**
**List, ask, then stop and wait. Don't go on to enumerate the real questions yourself.**

---

## 阶段 2：枚举真问题 / Stage 2: Enumerate the real questions

根据用户报的水位，列出**模因层之外**关于这个概念的真问题或真事实——真正懂行的人知道、但通常不会出现在入门解释里的那些东西。

Based on the level the user reported, list the real questions or real facts **beyond the meme layer** — the things people who genuinely understand the concept know, but that don't show up in introductory explanations.

- 列出 **5–7 条**，每条一句话说清楚。
  List **5–7**, each stated clearly in one sentence.
- 让用户挑出 **1–2 条**最让他感兴趣、或最让他"没想过"的。
  Ask the user to pick the **1–2** that most interest them or most make them go "huh, never thought about that."

这里可以做温和指向（"第 4 条是大多数人完全没意识到的，我个人觉得最值得挖"），但**最终选哪条是用户的事**。

A gentle nudge is fine here ("#4 is the one most people never realize, and personally I think it's the most worth digging into"), but **which one to pick is the user's call**.

**列完、请用户选，停下，等回复。不要自己选、也不要提前展开子问题。**
**List, ask them to choose, then stop and wait. Don't pick for them, and don't pre-expand into sub-questions.**

---

## 阶段 3：扩展为子问题 / Stage 3: Expand into sub-questions

把用户选中的真问题，扩展成 **4–5 个具体子问题**，覆盖四个角度：

Take the real question the user selected and expand it into **4–5 concrete sub-questions** spanning four angles:

- **描述层 / Descriptive** — 这个事实具体是什么。What the fact actually is.
- **原理层 / Mechanism** — 背后的机制为什么是这样。Why the underlying mechanism works this way.
- **边界层 / Boundaries** — 在什么场景下最极端、最不极端。Where it's most and least extreme.
- **应用层 / Application** — 对用户的实际决策意味着什么。What it means for the user's real decisions.

列出后，请用户确认是否要修改、删除或新增。**特别欢迎用户加入和他自己具体处境相关的部分**（如"作为产品经理…""作为内容创作者…""用在我正在做的 X 上…"），因为应用层正是深度回答最值钱的地方。

After listing, ask the user to confirm, edit, drop, or add. **Especially invite them to add pieces tied to their own situation** ("as a PM…", "as a content creator…", "applied to the X I'm working on…") — because the application angle is where the deep answer pays off most.

> 这样拆你觉得对吗？有要改、要删、要加的吗？尤其欢迎你告诉我你自己的处境，我好把它接进来。
> Does this breakdown look right? Anything to change, drop, or add? I'd especially welcome your own context so I can wire it in.

**列完、请用户确认，停下，等回复。不要提前写深度回答。**
**List, ask for confirmation, then stop and wait. Don't pre-write the deep answer.**

---

## 阶段 4：深度回答 / Stage 4: The deep answer

基于确认后的子问题，给出深入回答。执行要求：

Based on the confirmed sub-questions, deliver the deep answer. Requirements:

- **不要从入门讲起。** 用户已经懂模因层了，重复它是侮辱。
  **Don't start from the basics.** The user already has the meme layer; rehashing it is insulting.
- **对应用层的子问题特别详细地展开。** 这是用户真正想要的产出。给到具体的、能立刻拿去用的判断标准、案例、自检问题。
  **Expand the application sub-questions in particular depth.** This is what the user actually came for. Give concrete, immediately usable decision criteria, examples, and self-check questions.
- **长度可以长。** 这一步不必克制——深度和可用性优先于简洁。
  **Length is welcome here.** Don't hold back — depth and usefulness beat brevity.

回答完成后，问：

When done, ask:

> 还有什么想继续深入的吗？
> Anything you'd like to go deeper on?

有 → 继续（可以回到阶段 2 挑另一条真问题，或就着这条再展开）。没有 → 结束 skill。

Yes → continue (loop back to Stage 2 for another real question, or go further on this one). No → end the skill.
