---
name: sync
description: Sync and orient at the start of a session — pull latest, then summarise where things stand from AGENTS.md. Use when the user says "/sync", "catch me up", or wants to resume work.
---

# /sync — Start-of-session catch-up

Pull the latest changes, run the PROTOCOL.md session start procedure, and brief the user.

## Steps

### 1. Git sync

Detect the current branch's upstream:

```
git rev-parse --abbrev-ref --symbolic-full-name @{u} 2>/dev/null
```

- If an upstream exists: run `git pull --rebase`. If it reports conflicts, stop and list the conflicted files clearly. Do not attempt further git operations until resolved.
- If NO upstream exists (new local branch): run `git fetch origin main && git rebase origin/main`. This is the correct default — the feature branch is local only, so rebase against main.

Then run `git status` and `git branch --show-current` to confirm working tree state.

### 2. PROTOCOL.md session start (mandatory — do not skip)

Read and act on each of these files in order:

1. `strategy/PLAN.md` — note the next upcoming milestone and days remaining.
2. `PROJECTS.md` — note what is currently Active.
3. `ACTIONS.md` — note any pending high-priority actions.
4. `INGEST.md` — if it contains items (anything above the empty placeholder line): act on them top to bottom, move each completed item to `PROCESSED.md` with today's date, then empty `INGEST.md`. Never erase an item that has not been acted on.

File names are uppercase. Use the exact names above — do not glob or guess case.

### 3. Report to user

Concise summary:

- **Branch:** current branch and whether it is clean or has uncommitted changes.
- **Last session (date):** what was being worked on, from `AGENTS.md` Session State.
- **Open questions:** any listed in Session State.
- **Next action:** the recorded next step.
- **INGEST:** how many items were processed (or "empty — nothing to process").
- **Next milestone:** date, name, and days remaining from PLAN.md.
- **Active projects:** list from PROJECTS.md.

## Notes

- Flag merge conflicts or a dirty/diverged tree prominently.
- Flag if INGEST had items that could not be fully acted on.
- Keep the briefing tight. Orient quickly, do not dump file contents.
