# Claude Instructions

Read `PROTOCOL.md` first and follow it exactly. It is the operating manual for this repo.

The canonical strategy lives in `strategy/PLAN.md`. Enforce it; do not reinvent it.

**The roadmap IS `strategy/PLAN.md`** (the Phases and Milestones tables). There is no separate roadmap file, no liveops roadmap, and no other plan document. If you believe a file is referenced but you cannot find it, say so; never invent or assume files that do not exist in this repo.

## Article Pipeline

Source of truth: `articles/PIPELINE.md`. Read it before doing any pipeline work; this is orientation only, not the full spec. Data lives in `articles/articles.json` (single file: list, scores, stage, pointers). Heavy content lives in `articles/working/<slug>/` and moves to `articles/archive/<slug>/` after posting.

**Stages and commands** (seven stages, bookended by `/sync` start and `/wrap` end):

| Stage | Command | Status |
|-------|---------|--------|
| kindling | `/kindle` | skill built |
| ranked | `/rank` | skill built |
| working | `/work` | doc stage (plain-English until first article runs end-to-end) |
| writing | `/write` | doc stage |
| creative | `/creative` | doc stage |
| posting | `/post` | doc stage |
| archived | `/archive` | doc stage |

`/board` renders the current scorecard. The five doc stages get codified into skills only after the first article runs through end-to-end.

**Score directions** (1 to 5, set at `/rank`): virality (5 = most shareable in game-dev/AI circles), resume (5 = strongest proof of the Claim / most linkable), ease (5 = easiest, least prep), timeliness (5 = decays fastest if we wait). `priority` stays `null`; views weight axes themselves.

**Gate model** (`gate_class` per article, the legal-risk axis, not content type): `clear` (always publishable under own name) | `employer-specific` (names current-employer specifics) | `commercial` (sells a service, names/solicits clients, or reveals competing business). `meta.gates` dates each restricted class; both `employer-specific` and `commercial` are gated to `2027-01-01` (restrictions run through 2026-12-31). `/post` blocks a restricted article when its gate date is `null` or in the future; `clear` always passes.

**Image strategy:** Claude-generated SVG diagrams are the workhorse; real-build screenshots (Allen captures) are the most credible asset; cover image is Midjourney-or-skip. Facts over hype.

**post_targets:** `meta.post_targets` is `["substack"]` now; `/post` fans out to every target automatically. Add sites later (no code change).

## Session State

- **Date:** 2026-06-14
- **Branch:** main
- **What was done:** Cleaned up the todo system and populated the article pipeline. ACTIONS.md now has a single high-priority item (#18 Substack articles) and two medium-priority items (#26 Match 3 white label, #27 This 60 MCP). Kindled and ranked 17 articles into articles/articles.json (all gate_class clear, all with proposed 4-axis scores). Moved Games, Free Apps, Stripe, Joy Projects, and Automation experiment articles out of PROJECTS.md and into the article pipeline. Added Workdeck definition. Updated ACTIONS.md todos rule to hide done items.
- **Open questions:** None.
- **Next action:** Work the first article through the pipeline. Strongest candidate for the 2026-07-15 first-post deadline: a002 "Fewer managers, more doers" (V:5 R:5 E:4 T:4).
