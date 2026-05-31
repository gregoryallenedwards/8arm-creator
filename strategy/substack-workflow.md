# Substack Workflow Rules

These are the operational rules for how Allen and AI (Claude/Antigravity) collaborate to write and publish Substack posts.

---

## 1. Ideation & Backlog
- **Source of Truth**: All Substack ideas start as a checkbox in `research/post-topics.md`.
- **Prioritization**: High-impact topics are moved to `PROJECTS.md` under the Content backlog.
- **Goal Check**: Every post must focus on *what was built*, *how it was built*, and *what was learned*, maintaining a capability-first, skeptical lens. Facts over hype.

## 2. Drafting Process
- **Format**: All drafts are written in Markdown (`.md`).
- **Location**: Store active drafts in `content/drafts/`.
- **Outlining**: 
  - Start with an outline detailing the core thesis, the sections, and the "hero" technical/process insight.
  - Wait for Allen's approval on the outline before writing the full draft.
- **Writing**:
  - Keep the voice in line with `content-creator-rules.md` (skeptical, factual, capability-focused).
  - Use Gregory Allen Edwards naturally for SEO.

## 3. The Multi-Agent Handoff (Claude ⇆ Antigravity)
- **State Management**: Drafts must be committed or explicitly documented in `INGEST.md` before switching AI agents.
- **No Race Conditions**: **NEVER** edit the same draft concurrently using Claude and Antigravity. Always complete a session, save the file, commit (or sync), and then initialize the other agent to avoid overwriting work.
- **Clear Instructions**: When handing a draft from one AI to the other, the exiting AI must log the current progress and the immediate next step in `INGEST.md` for the incoming AI to read.

## 4. Publishing & Archiving
- Once Allen approves and publishes a post to Substack, move the markdown file from `content/drafts/` to `content/published/`.
- Note the publication date at the top of the file.
- Update `PROCESSED.md` to reflect the completed project.
