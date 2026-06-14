---
name: kindle
description: Capture an article idea, or auto-research a subject into proposed topics, landing them at the kindling stage. Use when the user says "/kindle", wants to log a new article idea, or wants topic ideas researched for a subject.
---

# /kindle — Stage 1: capture or research ideas

Adds ideas to the article pipeline at the `kindling` stage. Read `articles/PIPELINE.md` for the full spec; the data file is `articles/articles.json`.

## Two modes

### Mode A: single idea — `/kindle "<idea>"`

1. Add one record to the `articles` array in `articles/articles.json` at stage `kindling`.
2. Assign fields:
   - **id** — next free `aNNN` (highest existing id + 1, zero-padded to 3 digits; start at `a001`). Never reuse an id.
   - **slug** — kebab-case from the title, unique across all records.
   - **title** — a clean title from the idea text.
   - **category** — `1`–`7` per the master article list; if unclear, propose one and say why.
   - **tags** — propose from `flagship` | `artifact` | `experiment` | `crown-jewel-adjacent` (ask if unsure).
   - **gate_class** — propose `clear` | `employer-specific` | `commercial` per the gate model in PIPELINE.md. Default `clear` only when clearly safe; flag if it names a current employer (`employer-specific`) or sells/names clients (`commercial`).
   - **scores** — all `null` (not ranked yet).
   - **priority** `null`, **paths** both `null`, **assets** `[]`, **posted_to** `[]`, **notes** `""`.
3. Report the new record's id, slug, category, tags, and gate_class. Do not score it.

### Mode B: research a subject — `/kindle category: "<subject>"`

1. Web-research the subject.
2. Propose roughly 5 to 8 distinct article angles, numbered, each one line.
3. Stop and wait. Do not add records yet.
4. On `keep 2,4,6` (or similar): add only those angles as new `kindling` records following Mode A's field rules for each.

## Notes

- Validate JSON after every write (the file must stay parseable).
- Never populate `scores` here; that happens at `/rank`.
- One record per idea. Do not create folders at this stage (folders are created at `/work`).
- Keep the brief tight: confirm what was added, nothing more.
