---
name: rank
description: Score a kindling article on the 4-axis scorecard (virality, resume, ease, timeliness) and move it to the ranked stage. Use when the user says "/rank", wants an idea scored, or wants to score all kindling items.
---

# /rank — Stage 2: score onto the board

Proposes 1 to 5 scores on each axis, then lets Allen set them. Read `articles/PIPELINE.md` for the full spec; data is in `articles/articles.json`.

## Usage

- `/rank <id>` — rank one article.
- `/rank kindling` — propose scores for every record at stage `kindling`, one block each.

## Steps

### 1. Propose (then stop)

For the target record(s), propose a `1`–`5` score on each axis with a one-line rationale per axis:

- **virality** — 5 = most shareable in game-dev / AI circles.
- **resume** — 5 = strongest proof of the Claim / most linkable artifact.
- **ease** — 5 = easiest / least prep.
- **timeliness** — 5 = decays fastest if we wait / most urgent.

Present the proposal and stop. Do NOT write scores yet, and do NOT change the stage.

### 2. Set (on Allen's word)

Allen confirms or edits with: `set <id> virality N resume N ease N timeliness N`.

On that:
1. Write the four scores into the record's `scores`.
2. Set `stage` to `ranked`.
3. Leave `priority` as `null` (no composite formula; views weight axes themselves).
4. Validate the JSON, then confirm the final scores and that the record is now `ranked`.

## Notes

- Only `1`–`5` integers are valid scores. Reject out-of-range input.
- If Allen accepts the proposal as-is, treat that as the `set` for those values.
- Use `/board` to view ranked articles as a scorecard afterward.
