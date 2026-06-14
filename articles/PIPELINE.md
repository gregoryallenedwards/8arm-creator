# 8arm — Article Pipeline Design Spec (`PIPELINE.md`)

**Author:** Gregory Allen Edwards
**Role of this file:** Single source of truth for the Substack article pipeline. Readable by Allen; buildable by Claude Code. Lives at `articles/PIPELINE.md` in the 8arm repo and is committed to git. Conventions live here (not in the JSON data file, which can't hold comments).

---

## ▶ The one build prompt

After this file is in the repo, paste this to Claude Code:

```
Read articles/PIPELINE.md and build the entire pipeline exactly as specified:
the articles/articles.json data file (meta with post_targets and gates per the
spec; empty articles array — no records), and the working/ and archive/ folders.
Add a concise "## Article Pipeline" orientation block to CLAUDE.md that points
to articles/PIPELINE.md as the source of truth and covers: the stages + commands,
the 1-5 score directions, the gate_class model and meta.gates dates, the image
strategy, and post_targets — do NOT duplicate the full spec. Do NOT populate any
article records and do NOT score anything. Then create the three settled skills
(/kindle /rank /board) in the same convention as /wrap and /sync; leave /work
/write /creative /post /archive as documented stages, to be built after the first
article runs end-to-end. When done, show me the tree under articles/, cat
articles.json, and show the new CLAUDE.md section so I can verify — then /wrap.
```

> The five deferred stages run as plain-English instructions for now; codify them into skills once their real shape is proven by the first article.

---

## The pipeline

Seven stages, bookended by your existing `/sync` (start) and `/wrap` (end). Articles move left-to-right; each article sits at its own stage independently. You generally work the board in balanced-scorecard priority order.

| # | Stage | Command | Transition |
|---|-------|---------|------------|
| 1 | **Kindling** — capture an idea, or auto-research a subject into proposed topics | `/kindle` | → `kindling` |
| 2 | **Ranked** — score on the 4-axis scorecard; lands on the board | `/rank` | → `ranked` |
| 3 | **Working** — pull an actionable item; external work + optional joint research | `/work` | → `working` |
| 4 | **Writing** — outline first, then draft together | `/write` | → `writing` |
| 5 | **Creative** — diagrams, screenshots checklist, cover-image prompt, social copy | `/creative` | → `creative` |
| 6 | **Posting** — Cowork publishes to each target; URLs recorded | `/post` | → `posting` |
| 7 | **Archived** — move everything + posting record to the archive | `/archive` | → `archived` |

`/board` renders the current scorecard view at any time.

---

## The data file — `articles/articles.json`

Single structured source of truth: list + scores + stage + pointers. Heavy content (drafts, research, assets) lives in folders, referenced by `slug`.

```json
{
  "meta": {
    "version": 1,
    "post_targets": ["substack"],
    "gates": { "employer-specific": "2027-01-01", "commercial": "2027-01-01" }
  },
  "articles": [
    {
      "id": "a001",
      "slug": "what-ai-sized-teams-means",
      "title": "What 'AI-sized teams' means",
      "category": 1,
      "tags": ["flagship"],
      "gate_class": "clear",
      "stage": "kindling",
      "scores": { "virality": null, "resume": null, "ease": null, "timeliness": null },
      "priority": null,
      "paths": { "working": null, "archive": null },
      "assets": [],
      "posted_to": [],
      "notes": ""
    }
  ]
}
```

### Field reference
- **id** — stable handle (`a001`, `a002`, …). Never reused.
- **category** — `1`–`7` per the master article list.
- **tags** — `flagship` | `artifact` | `experiment` | `crown-jewel-adjacent`.
- **gate_class** — drives the garden-leave gate. This is the legal-risk axis, *not* content type (`category` already carries type): `clear` (always publishable under own name — analysis, own-project builds, lifehacks) | `employer-specific` (names current-employer specifics) | `commercial` (sells a service, solicits/names clients, or reveals competing business activity).
- **stage** — one of the seven stage names above.
- **scores** — `1`–`5` each, directions below. `null` until ranked.
- **priority** — intentionally `null`. No composite formula is hardcoded; views define their own weighting later.
- **paths** — folder pointers, filled when the article enters `working` / `archived`.
- **assets** — manifest filled during `creative` (filenames + alt text + type).
- **posted_to** — array of `{ site, url, date }`, filled during `posting`. Expansion-ready.

### Score directions (state once, never ambiguous)
- **virality** `1–5` — 5 = most shareable in game-dev / AI circles.
- **resume** `1–5` — 5 = strongest proof of the Claim / most linkable artifact.
- **ease** `1–5` — 5 = easiest / least prep.
- **timeliness** `1–5` — 5 = decays fastest if we wait / most urgent.

---

## Folder structure

```
8arm/
├── CLAUDE.md                      # stages + conventions + gate documented here
├── articles/
│   ├── PIPELINE.md                # this file
│   ├── articles.json              # the single data file
│   ├── working/<slug>/            # research.md, outline.md, draft.md, assets/
│   └── archive/<slug>/            # everything post-publish + posting-record.md
```

---

## Stage specs (Claude Code behavior per command)

**`/kindle`**
- `/kindle "<idea>"` → add one record at `kindling`; assign id/slug/category; scores null.
- `/kindle category: "<subject>"` → web-research the subject, propose ~5–8 angles, wait. On `keep 2,4,6` → add those as `kindling` records.

**`/rank <id|kindling>`**
- Propose `1–5` on each axis with a one-line rationale per axis, then stop.
- Allen edits: `set <id> virality N resume N ease N timeliness N` → stage `ranked`.

**`/work <id>`**
- Create `working/<slug>/`; stage → `working`; write a checklist of external (outside-repo) work Allen must do.
- Plain-English progress reports fold into `working/<slug>/research.md`.
- `/research <id>` (or freeform) → joint online research saved to `research.md` with sources.

**`/write <id>`**
- Produce `outline.md` first and stop. On approval/edits → write `draft.md`; stage → `writing`.
- Voice: capability-first, facts-over-hype, full name in-post for GEO.

**`/creative <id>`** — see image strategy below. Produces:
- Claude-generated **SVG diagrams** as needed → `assets/`.
- A **screenshot checklist** for Allen to capture from real builds.
- A **paste-ready Midjourney prompt** for the cover image.
- Social / cross-post copy.
- Updates the `assets` manifest; stage → `creative`.

**`/post <id>`**
- **Garden-leave gate check first** (below). If blocked, refuse and explain.
- Publish via Cowork to every site in `meta.post_targets` (currently `["substack"]`).
- Write live `{site, url, date}` into `posted_to`; stage → `posting`.

**`/archive <id>`**
- Move `working/<slug>/` → `archive/<slug>/`; write `posting-record.md` (sites, URLs, dates, asset list); stage → `archived`.

**`/board`**
- Render ranked articles as a scorecard table (current view).

---

## Image strategy

Brand rule: facts-over-hype. Real artifacts beat glossy AI art. So:
- **Diagrams / conceptual visuals** → Claude generates SVG (on-brand, credible). Workhorse.
- **Screenshots of real builds** → Allen captures. Most credible asset; `/creative` lists exactly which to grab.
- **Cover / hero image** → Midjourney *or* skip (a diagram/screenshot cover is fine). `/creative` always outputs a paste-ready Midjourney prompt so the choice is yours per post.

---

## Posting config

- **Targets now:** `["substack"]` only. Cowork **publishes** (no manual staging step).
- **Expansion:** add sites to `meta.post_targets` later (LinkedIn, dev communities); `/post` will fan out automatically. No code change needed.

---

## Garden-leave gate

The only safety check before a Cowork auto-publish goes live. Per-class, because the two restricted classes unblock at different contractual milestones.

- `meta.gates` maps each restricted class to a date: `{ "employer-specific": <date|null>, "commercial": <date|null> }`. `null` = blocked. (`clear` is never gated, so it isn't listed.)
- `/post` **blocks** an article while its `gate_class` is restricted AND (`gates[class]` is `null` OR `today < gates[class]`).
- `gate_class: "clear"` always passes — analysis and own-project builds under your own name are fine now.
- On a block, `/post` refuses, names the `gate_class`, and states what unblocks it: reclassify to `clear`, or wait for that class's gate date.
- **Dates (set; verify against your actual contract — not legal advice):** restrictions apply through **2026-12-31**, so both `employer-specific` and `commercial` are gated to **`2027-01-01`** — blocked through Dec 31 2026, open on/after Jan 1 2027.
- **Under-the-table rule:** contract/client work done during the restricted period may happen privately, but anything that would *expose* it on the public record — a client case study, a "what I built for X" post, naming a client — is `commercial`, so the gate keeps it off Substack *and* off the resume spine until 2027-01-01. Tag accordingly; that's what protects the arrangement.
- Genuinely confidential / NDA-bound material is never published regardless of date — that's a "don't write it" case, not a gate-date case.

---

## Resolved decisions
1. **Gates** — per-class dates in `meta.gates`, both set to `2027-01-01` (restrictions apply through 2026-12-31; clear from Jan 1 2027). Only `clear` publishes before then.
2. **Gate classes** — three: `clear` | `employer-specific` | `commercial`.
3. **Skills** — build `/kindle`, `/rank`, `/board` now; defer `/work` `/write` `/creative` `/post` `/archive` until after the first article runs end-to-end.
