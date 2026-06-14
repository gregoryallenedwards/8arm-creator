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
- **Branch:** claude/amazing-turing-xskasw
- **What was done:** Built the article pipeline from articles/PIPELINE.md (new source of truth, added verbatim). Created articles/articles.json (meta with post_targets + 2027-01-01 gates; empty articles array, no records), and articles/working/ and articles/archive/ folders. Added the "## Article Pipeline" orientation block to CLAUDE.md. Built the three settled skills /kindle, /rank, /board in the /sync + /wrap convention; left /work /write /creative /post /archive as documented doc-stages.
- **Open questions:** None blocking. PIPELINE.md uses em dashes (kept verbatim despite PROTOCOL's no-em-dash rule, since it is the provided spec). No prior pipeline doc existed to replace, so this was created fresh; strategy/substack-workflow.md and research-workflow.md were left untouched.
- **Next action:** Run the first article through the pipeline end-to-end (/kindle to /archive), then codify the five deferred stages into skills.
