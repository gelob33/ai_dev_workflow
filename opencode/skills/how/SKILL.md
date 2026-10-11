---
name: how
description: Explain how a part of the codebase works before changing it. Use before any non-trivial change, and for "how does X work", "where should this live", "which module owns this".
---

# How

Build a working mental model of the subsystem you are about to touch. Senior-engineer onboarding level, not annotated source.

1. Scope it. Small (one module or function): explore it yourself. Large (several files or services): split into 2 to 4 angles and send each to an `explore` subagent in ONE message, so they run at the same time. Ask each for file paths and short findings only.
2. Write the explanation with these sections, dropping any that don't apply:
   - Overview: what it is for, in two or three sentences.
   - Key concepts: the data shapes and names you need.
   - How it works: the runtime flow, step by step, with file paths.
   - Where things live: which file owns what.
   - Gotchas: what will surprise the next person.
3. Keep it. Paste it into your notes for the task. The rest of the task builds on it.

Adapted from pstack (MIT, Lauren Tan).
