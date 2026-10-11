---
name: story
description: Playbook for a user story, new or changed behavior. Use for any story ticket that adds or changes what the product does.
---

# Story playbook

Copy these steps into your todo list first. A step you skip stays in the list as "skip: <reason>".

1. `how` over the affected subsystem.
2. `architect` if the change crosses a function boundary. Otherwise name the data shape in one line.
3. Plan the work in small units. Each unit ends in a check you can run (a test, a command, a screenshot).
4. Build unit by unit. Run its check before starting the next. Commit after each unit.
5. Prove it on the real surface with the project's verify-* skill. Capture evidence (screenshot, output, log).
   "Inconclusive" or the wrong surface is not a pass. Say so if that is all you have.
6. Tidy history into small, ordered commits (git rebase is fine on your own branch).
7. Review: call the `qa` subagent with your branch name and the intent. Fix every ACT ON finding.
   Note CONSIDER items you declined in the PR body with one line each.
8. Push and open the PR. Body: intent, what changed, how you verified (paste the evidence), what
   qa found and what you did, risk (low / medium / high and why).
9. update done "<PR URL> <one line>".

Adapted from pstack (MIT, Lauren Tan) and firstmate (MIT, Kun Chen).
