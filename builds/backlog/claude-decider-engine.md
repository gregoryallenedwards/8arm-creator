# Claude Decider Engine

**Status:** backlog
**Category:** Automation / Tool
**Priority:** high

---

## What It Is

A lightweight Claude-powered agent that tells you what to build or experiment with next, and signals when you're ready to move to the next phase. Acts as a "reminder and decider" — reviewing the project list, the content calendar, and the phase goals, then recommending what to focus on.

## Why Build This

- You mentioned this as a near-term build priority
- Also an excellent first post: "I built a Claude agent that decides what I should build next — here's how it works"
- Meta + on-brand: a builder using AI to manage their own build pipeline
- Demonstrates Claude Code / agentic workflow knowledge

## Post Angle

"I built a Claude agent that tells me what to build next. It reads my project list, my content calendar, and my goals — and gives me a weekly brief. Here's the prompt structure and what I learned."

## How It Works (Concept)

1. Reads `PROJECTS.md` (project list + statuses)
2. Reads `strategy/business-strategy.md` (phase goals)
3. Reads `experiments/_log.md` (what's been tried)
4. Outputs: recommended next build, recommended next post topic, and why
5. Optional: runs on a schedule (weekly Monday morning brief)

## Target Community

- r/LocalLLaMA
- r/SaaS
- Hacker News (Show HN)
- LinkedIn (builder audience)

## Scope (Minimum for a great post)

- [ ] Prompt that reads the project files and outputs a recommendation
- [ ] Test it, document what it got right and wrong
- [ ] Post the prompt + the output + the reflection

## Tech Stack

Claude API or Claude Code, markdown files as context, Python or bash runner

## Time Estimate

Prompt + test: 2-4 hours
Post: 2 hours

## Next Action

Design the prompt structure. What context does it need? What should it output?

## Notes

- Keep it simple for V1 — the post is about the idea and the prompt, not a polished product
- Can evolve into a scheduled task (weekly brief via Cowork or Claude Code)
- Aligns with "agentic decisions using Claude Code / Claude workflows" from your notes
