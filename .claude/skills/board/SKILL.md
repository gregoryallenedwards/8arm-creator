---
name: board
description: Render the current article scorecard — ranked articles in a table with their 4-axis scores and stage. Use when the user says "/board", "show the board", or wants to see the article pipeline at a glance.
---

# /board — Scorecard view

Renders the current state of the article pipeline as a table. Read-only; never edits `articles/articles.json`. Read `articles/PIPELINE.md` for context.

## Steps

1. Load `articles/articles.json`.
2. Render the `ranked` articles (those with all four scores set) as a scorecard table, highest-value first. Default sort: a balanced read across the four axes (sum of `virality + resume + ease + timeliness`), but do not write any `priority` value back: `priority` stays `null` and this ordering is just the view's own weighting. Note the sort used in one line.

   | id | title | category | gate_class | stage | virality | resume | ease | timeliness |
   |----|-------|----------|-----------|-------|----------|--------|------|------------|

3. Below the table, list anything not yet on the board in compact form:
   - **Kindling (unranked):** ids + titles still at `kindling`.
   - **In flight:** ids + titles at `working` / `writing` / `creative` / `posting`.
   - **Archived:** count only (ids on request).

## Notes

- This is a view, not a mutation. Do not change stages, scores, or `priority`.
- If there are no ranked articles, say so and just list the kindling items.
- Keep it to the table plus the compact lists. No prose analysis unless asked.
