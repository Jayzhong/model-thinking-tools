# Best Practices for Creating Skills in This Repo (deltas beyond skill-creator)

**The general workflow is handled by the `skill-creator` skill** — it already covers: the draft → test → eval → iterate loop, directory structure and progressive disclosure, "the description is a trigger (what it does + when to trigger, slightly pushy)," "explain the why instead of piling on MUSTs," when to split files / add scripts, trigger optimization, and so on. **None of that is repeated here.**

This doc only records what `skill-creator` doesn't emphasize, or what's specific to this repo. Judge by principle, not as dogma.

## This repo's genre

These are **mental-model / reasoning-facilitation** skills, not engineering ones. Thariq's 9 categories (API reference, CI/CD, runbooks…) and the scripts, config, memory, and hooks that come with them **mostly don't apply**. Skills here are usually **single-file, pure-dialogue flows** that rarely need `scripts/` or `references/`. What carries weight: description triggering, explaining the why, leaving flexibility, and (for multi-turn) persistence.

## Language convention (specific to this repo)

- **`description` stays bilingual (Chinese + English)** — it's the trigger; English-speaking users match on English phrases, Chinese-speaking users on Chinese ones.
- **Body instructions are written in English** (single language; the project's main language).
- Give user-facing phrasings as English samples + instruct the model to **respond in the user's language** (don't mix languages at the user).
- A gloss for a key term is fine, e.g. `meme layer (模因层)`.
- **Watch description length** — bilingual descriptions push toward (or past) the common **1024-char limit**. Over-limit descriptions can be **silently rejected** by some skill loaders, surfacing as "skill not found after install." Measure before committing; aim well under 1024. Cross-skill references inside the description are common length-offenders — they add bytes without adding triggering value (move them to the body if needed).

## Multi-turn / behavioral skills (not covered by skill-creator)

- **Add a persistence clause**: multi-turn skills "drift" — after a few turns the model forgets it's inside the skill and reverts to default behavior. Spell out "once started, stay in the flow until <exit condition>; if unsure, default to still being in the flow." (Learned from Matt Pocock's `caveman`.)
- **"Stop and wait for the user" is the hardest thing to hold**: explain the why (the user's choice determines the next step's content; pre-running = a guess that gets overturned) + put one short in-context reminder at each point where you should stop.

## Gotchas come from real runs, not speculation

Don't pre-write a pile of "predicted failure modes" — that's guesswork, and it often duplicates the body. **Do a real walkthrough first, see what actually breaks, then backfill**, marking each one's source (observed / latent risk).

## Compression: judge by behavioral value, not line count

- Line count is **not a hard target** (Matt argues <100 lines; skill-creator says <500 is fine — wide disagreement, don't cargo-cult).
- The criterion: cut genuine redundancy (the same instruction repeated, scaffolding the model doesn't need, **and things skill-creator / Claude already know**); keep anything with behavioral value (a load-bearing why, an actionable mapping, an edge-case fallback) — even if it makes the file longer.
- **After compressing, diff against the prior version and re-audit each deletion** to confirm you didn't cut load-bearing content just for brevity, then commit.

## Two process preferences

- **Review the plan before writing**: lay out the design and trade-offs, get confirmation, then write the finished version.
- **Test with a topic you're NOT an expert in**: that's the only way to test whether the scaffolding can take a non-expert to the target depth, rather than you supplying the expertise yourself.

## Layout & distribution

- Each skill lives at **`skills/<name>/SKILL.md`** — a "standard location" that both `npx skills` and the Claude Code plugin discover automatically.
- **Adding a skill needs no manifest edits.** Both channels auto-discover from `skills/`; `.claude-plugin/marketplace.json` lists the *plugin*, not individual skills, and `.claude-plugin/plugin.json` doesn't enumerate skills either.

## After adding a skill

Drop it in `skills/<name>/` and update the skill table in both README files. That's it.

---

Sources: Thariq Shihipar, "Lessons from Building Claude Code: How We Use Skills"; Matt Pocock's [skills repo](https://github.com/mattpocock/skills); the official skill-creator; this repo's own iteration.
