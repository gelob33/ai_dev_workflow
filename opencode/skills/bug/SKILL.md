---
name: bug
description: Playbook for fixing a reported bug with evidence. Use for any story ticket that says something is broken.
---

# Bug playbook

Be scientific. Every line you ship traces to evidence. A change that "might help" is a guess and does not ship.
Copy these steps into your todo list first.

1. Reproduce it yourself on the real surface, the way a user would (verify-* skill if the project has one).
   If it won't reproduce, tighten the conditions or add logging until it does. If you truly cannot, update blocked with what you tried.
2. Find the cause by elimination. List the candidate causes. Use `how` on the subsystem and `git log -p` on the area for recent changes.
   Each step, test the split that rules out the most. Add logging and read it as the code runs. Don't guess.
   Stop when one cause survives and you can show the mechanism.
3. If the fix crosses a function boundary, `architect` first.
4. Write a test or repro script that fails because of the bug. Commit it.
5. Fix with the smallest change the evidence supports. Commit the fix on top, so history shows fail then pass.
6. Prove it on the same surface as step 1. The original repro now passes. Unit tests alone are not proof.
7. Review: call the `qa` subagent with the branch and "fixes <bug>: <root cause>". Fix every ACT ON finding.
8. Push and open the PR. Body: what was broken, root cause, fix, the failing-then-passing evidence pasted in full, risk.
9. update done "<PR URL> root cause: <one line>".

Adapted from pstack (MIT, Lauren Tan).
