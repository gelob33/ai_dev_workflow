---
name: make-verify-skill
description: Create a project-local verify-<app> skill that drives the real app the way a user does and captures evidence. Use once per project, or when a project has no scripted way to prove behavior.
---

# Make a verify skill

Devs can only prove their work if the project tells them how to drive it. This writes that recipe into the project itself, at `.opencode/skills/verify-<app>/SKILL.md`, for an agent that has never seen the app.

1. Learn from the repo, not the product owner. Find out:
   - Surface: web UI, CLI, API, desktop app? Pick the main one.
   - Run: the project's own dev command, ports, env vars, seed data, how to log in.
   - Drive: existing Playwright/Cypress tests, scripts, curl-able endpoints. Else a generic recipe:
     Playwright MCP or a Playwright script for web, tmux for CLI, curl for APIs.
   - Evidence: screenshots, terminal transcripts, response bodies, logs, DB state.
   - Isolation: can two copies run at once (different ports, data dirs)? If not, say so.
2. Write the skill with frontmatter (`name: verify-<app>`, a description naming the app and when to use it) and these sections:
   Launch (exact command and how to know it is ready), Doctor (one check that the instance is the right one and healthy),
   Drive (real selectors and commands from this repo), Evidence (what to capture and where it is saved),
   Cleanup (stop only what you started; keep the evidence).
3. Add `features/` beside it: one short file per top user feature (start with 3 to 5). Each says how a user reaches it, how to drive it, and what end state proves it works.
4. Run the skill once end to end on one feature: launch, doctor, drive, capture, clean up. Confirm the evidence survived cleanup.
   A skill that was never run is a draft. Fix what failed and run it again.
5. Commit the skill to the project on your branch and open a PR like any story.

Adapted from pstack's create-verification-skill (MIT, Lauren Tan).
