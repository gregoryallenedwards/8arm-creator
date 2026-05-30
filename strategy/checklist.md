# Session Checklist

Claude runs through this at the start of every session, in order, before deciding on actions or priorities.

---

## Step 1 — Ingest
- [ ] Read INGEST.md
- [ ] If items exist: act on each one, move to PROCESSED.md, clear INGEST.md
- [ ] If empty: proceed to Step 2

## Step 2 — Diff Check
- [ ] Check if any files in the repo have changed since last session (git diff or system reminders)
- [ ] Update memory files if anything meaningful changed
- [ ] Note any file changes that affect priorities or actions

## Step 3 — Actions Audit
- [ ] Read ACTIONS.md
- [ ] Are there any high-priority (🔴) items that can be moved forward today?
- [ ] Are there any items that are now blocked or need clarification from Allen?

## Step 4 — Build Files Check
- [ ] Read PROJECTS.md
- [ ] For every project listed: does a build file exist in builds/backlog/?
- [ ] If not: add an action to ACTIONS.md to create the missing brief

## Step 5 — Experiments Backlog
- [ ] Read experiments/backlog.md
- [ ] Are there any experiments queued that could be run this session?
- [ ] Are there any results from recent experiments that need to be logged in experiments/_log.md?

## Step 6 — Research Refresh (weekly, not every session)
- [ ] Scan research/post-topics.md — is there a topic ready to draft?
- [ ] Scan research/intelligence-feeds.md — anything worth pulling into a post or experiment?
- [ ] Scan research/reddit-communities.md — any community ready for a drop?

## Step 7 — Ready
- [ ] Summarize what you found and propose the session's focus to Allen
- [ ] Wait for confirmation before starting major work

---

## Notes on Frequency

- Steps 1–5: every session
- Step 6: weekly (or when Allen asks "what should I post next?")
- Never skip Step 1 (ingest) or Step 3 (actions audit)
