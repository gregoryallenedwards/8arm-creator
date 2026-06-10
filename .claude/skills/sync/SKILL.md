---
name: sync
description: Sync and orient at the start of a session — pull latest, then summarise where things stand from CLAUDE.md. Use when the user says "/sync", "catch me up", or wants to resume work.
---

# /sync — Start-of-session catch-up

Pull the latest changes and brief the user on where the project stands.

## Steps

1. Run `git pull --rebase`. If it reports conflicts or fails, stop and flag the conflicts clearly to the user — list the conflicted files and do not attempt further git operations until resolved.

2. Run `git status` and `git branch --show-current` to confirm the working tree state and current branch.

3. Read `CLAUDE.md` at the repo root and locate the `## Session State` section.

4. Report back to the user, concisely:
   - **Branch:** the current branch.
   - **Last session (date):** what was being worked on, from Session State.
   - **Open questions:** any listed.
   - **Next action:** the recorded next step.
   - **Working tree:** clean, or a one-line note of uncommitted changes.

   If there is no `## Session State` section, say so and summarise from recent git log instead (`git log --oneline -10`).

## Notes

- Flag any merge conflicts or a dirty/diverged tree prominently — that's the main thing this skill exists to catch.
- Keep the briefing tight; the goal is to orient quickly, not to dump full file contents.
