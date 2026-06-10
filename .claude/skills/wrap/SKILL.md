---
name: wrap
description: Wrap up a work session — update the Session State section of CLAUDE.md, then commit and push all changes. Use when the user says "/wrap", "wrap up", or wants to end and save a session.
---

# /wrap — End-of-session commit

Wrap up the current work session: record session state in `CLAUDE.md`, then commit and push everything.

## Steps

1. Run `git status` and `git branch --show-current` to see what changed and which branch you're on. Also run `git diff --stat` to summarise the changes.

2. Determine today's date with `date +%Y-%m-%d`.

3. Update the `## Session State` section of `CLAUDE.md` at the repo root. If the section does not exist yet, append it to the end of the file. Set it to exactly this structure, filled in from what you observed:

   ```markdown
   ## Session State

   - **Date:** <YYYY-MM-DD>
   - **Branch:** <current branch>
   - **What was done:** <concise summary of the work in this session>
   - **Open questions:** <unresolved questions, or "None">
   - **Next action:** <the single most important next step>
   ```

   Replace the entire existing `## Session State` section (do not stack multiple copies). Keep it to this one block.

4. Stage everything: `git add -A`.

5. Commit with a descriptive message summarising the actual work done this session (not a generic message). Example: `git commit -m "Add liveops cadence to PLAN.md and update session state"`.

6. Push: `git push`. If the branch has no upstream, use `git push -u origin <branch>`.

7. Confirm to the user: report the commit hash, the commit message, the branch it was pushed to, and a one-line list of the files committed.

## Notes

- If there is nothing to commit, still update the Session State section if useful, otherwise tell the user the tree is clean and skip the commit.
- If `git push` fails (e.g. rejected, no remote, auth), report the exact error to the user rather than retrying blindly.
