# Action Items

Running list of things Allen and/or Claude need to do. Review at the start of each session.

**Owner:** Allen | Claude | Both  
**Priority:** 🔴 High | 🟡 Medium | 🟢 Low  
**Status:** pending | in_progress | done

---

## 🔴 High Priority

| # | Action | Owner | Status | Notes |
|---|--------|-------|--------|-------|
| 1 | Re-examine the validation engine — is it still the right moat or has the Gemini VC discussion changed it? | Both | pending | See strategy/vc-pitch-context.md and strategy/validation-engine.md |
| 2 | Figure out how to build with Claude Code where Claude can see changes in real time | Both | pending | Current flow: Claude builds → GitHub Actions compiles → slow, Claude can't see output. Need a live feedback loop. |
| 3 | Install GitHub MCP server in Claude desktop config | Allen | in_progress | Use @modelcontextprotocol/server-github via npx + scoped PAT (repo scope only). Will enable Claude to push/pull without terminal. See conversation 2026-05-30. |
| 4 | Start job search automation project (separate project) | Allen | pending | Feed Gemini job search data into a new Cowork project. Background task: generate resumes + cover letters from job specs. |
| 5 | Move personal This60 parked action items into a Cowork project with weekly reminder | Allen | pending | Separate project — weekly spool-up reviews parked items |

## 🟡 Medium Priority

| # | Action | Owner | Status | Notes |
|---|--------|-------|--------|-------|
| 6 | Try using a code project, check it in with Claude, then continue on Antigravity | Both | pending | Goal: switch between Claude and Google Antigravity IDE when running out of tokens on one. Need a handoff workflow. |
| 7 | Write Substack post: "Everything you should be able to automate in game/app development" | Both | pending | Original note: "For all the platforms, where are the headaches and time wasters that an LLM could handle for us?" Post each stage — keep adding to it. |
| 8 | Create build files for any projects in PROJECTS.md that don't have a brief in builds/backlog/ | Claude | pending | Run this check each session — see strategy/checklist.md |
| 9 | Create VC pitch deck (slides) once context is solid | Both | pending | See strategy/vc-pitch-context.md for full outline. Needs vertical slice / prototype first. |
| 10 | Set up Substack | Allen | pending | Create account, set up profile, first post |
| 11 | Set up LinkedIn presence | Allen | done | Already set up |
| 12 | Set up drops web page | Allen | pending | Simple landing page: free app links + Substack CTA |
| 15 | Update gregoryallenedwards.com strategy | Allen | pending | Figure out if we should kill the Vercel site entirely and just point the domain directly to Substack. |
| 16 | Post on Eric Seufert's "The Prosperous Society" | Both | pending | Substack post analyzing this concept |

## 🟢 Low Priority

| # | Action | Owner | Status | Notes |
|---|--------|-------|--------|-------|
| 13 | Set up Patreon | Allen | pending | Defer until audience traction |
| 14 | Define research file usage protocol | Claude | pending | How and when do we actively use reddit-communities.md, intelligence-feeds.md, post-topics.md? |

---

## Done

| # | Action | Completed | Notes |
|---|--------|-----------|-------|
| — | Initialize repo folder structure | 2026-05-30 | — |
| — | Seed all strategy, research, build files | 2026-05-30 | — |
| — | Capture Gemini VC pitch discussion | 2026-05-30 | strategy/vc-pitch-context.md |
