# Velum Content Machine — v1.0

> Repo-ready knowledge base for Velum's social content system.
> LLM-agnostic. Load into Claude Projects, GitHub vault, or any agent runtime.
> — Velum — @thevelum.studio —

---

## What this is

A closed operating loop that turns one strategic input per week into published,
on-brand content across Instagram — carousels, statement posts, reels, and Vera
videos — with Paulina as the single approval gate.

```
INPUT (topic / observation / client signal)
   → AGENT (generate structured brief or script)
      → REVIEW (Paulina approves — nothing produced before approval)
         → PRODUCTION (Canva / Midjourney / Higgsfield)
            → PUBLISH (@thevelum.studio)
               → MEASURE (Emplifi weekly review)
                  → back to INPUT
```

## The one constraint that governs everything

**This machine exists to produce three validated Blueprint clients. Nothing else.**

Every piece of content must trace to one of three jobs:
1. Make the ICP recognise her commercial gap (Authority / Education)
2. Make Velum the obvious structural answer (Process / Offer)
3. Convert recognition into a DM or a booked call (Offer / Social Proof)

**Locked until 3 validated Blueprint clients:**
- No new content formats
- No scheduling automation (Metricool etc.)
- No additional platforms beyond Instagram
- No batch production beyond 2 weeks ahead

If a session starts drifting toward building instead of publishing, this section
is the pushback. Publish the next post.

## File map

| File | Job |
|---|---|
| `00-brand-constitution.md` | Brand DNA the machine loads into every generation. Voice, vocabulary, visual system, banned patterns. |
| `01-content-strategy.md` | Pillars, cadence, principles, funnel mapping, CTA library. |
| `02-format-specs.md` | Exact production specs per format: carousel, statement, reel, Vera video. |
| `agents/carousel-agent.md` | Topic → complete carousel brief (copy + design directions per slide). |
| `agents/reel-agent.md` | Topic → reel script (hook, beats, text overlays, caption). |
| `agents/vera-script-agent.md` | Topic → Vera script in the locked video formula. Scripts approved fully before any generation. |
| `agents/repurposing-agent.md` | One published piece → derivative formats. Runs only on validated content. |
| `03-pipeline.md` | The weekly operating loop, review gates, publish checklist, performance review. |

## How to use — Claude (current mode)

1. Start a session inside the Velum project.
2. Name the agent and the input: *"Carousel agent: [topic]"*.
3. Agent returns the structured output contract. Review. Iterate by elimination.
4. Only after explicit approval → move to Canva / Higgsfield with the format spec.

## How to use — code (future mode)

Each agent file is a self-contained system prompt: prepend `00` + `01` + `02`,
append the agent file, pass the topic as the user message. Output contracts are
structured so responses can be parsed and written to Notion via MCP.

**Do not build the code layer until the manual loop has shipped 4+ weeks of
content and 3 Blueprint clients exist.** The manual loop *is* the product right
now — code is an efficiency upgrade for a validated process, not a prerequisite.

## Source of truth & precedence

Where documents conflict, this order wins:
1. `velum-brand-guidelines-v5.html` (visual system — LOCKED)
2. `velum-manifesto-v3.md` (strategy, voice, vocabulary)
3. This bundle (operational layer, consistent with 1 & 2)
4. `velum-prompt-library-v4.md` — **superseded on typography** (still references
   Playfair Display, removed in v5). Its Canva/image prompt *structures* remain
   useful; its font specs do not.

## Changelog

**v1.0 — 2026-07-18** — Initial bundle. Typography corrected to v5
(DM Serif Display headlines; Playfair removed). Carousel photo-driven odd/even
rule encoded as primary system. Vera locked formula and approved script included.

*Living document — update when copy is tested and confirmed.*
