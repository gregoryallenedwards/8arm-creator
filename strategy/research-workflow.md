# Research Workflow Protocol

This document defines the standardized process for utilizing the `research/` files. This protocol creates an "execution engine" that turns static lists into active content, tools, and distribution.

## Trigger
This workflow is triggered manually by the recurring `ACTIONS.md` reminder whenever Allen asks: **"What is there to do?"**

---

## 1. Intelligence Intake
**Goal:** Pull fresh market signals and identify trends without staring at a blank page.

* **Action:** Claude will actively use web browsing tools to check 2-3 sources from `research/intelligence-feeds.md`.
* **Selection:** Sources will be chosen based on current priorities (e.g., AI models, Game dev trends, B2B SaaS).
* **Output:** Claude will summarize the top trends and translate them into actionable ideas.
* **Handoff:** These ideas are immediately added as `[ ] idea` items in `research/post-topics.md` or added to the project backlog in `PROJECTS.md`.

## 2. Content Creation
**Goal:** Draft and publish content systematically.

* **Action:** Review the backlog in `research/post-topics.md`.
* **Process:** Select an idea, draft an outline, and write the post in `content/drafts/` following the rules in `strategy/substack-workflow.md`.
* **Output:** Change the topic status to `drafted`.
* **Handoff:** Once published, update the status to `published` and move the markdown file to `content/published/`.

## 3. Distribution & Validation Drops
**Goal:** Put free tools directly in front of targeted audiences to validate ideas and capture users.

* **Action:** When a new build is ready, cross-reference it with the tiers in `research/reddit-communities.md` to identify the optimal target subreddit.
* **Process:** Drop the free tool in the community. Focus on solving a genuine pain point without making it a "sales pitch."
* **Output:** 
  1. Change the subreddit's status from `target` to `dropped` in `reddit-communities.md`.
  2. Log the drop details, metrics, and learnings in `research/drop-results.md`.
