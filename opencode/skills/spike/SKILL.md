---
name: spike
description: Playbook for a spike, a read-only research ticket. Use for "how does X work", "why is Y slow", "should we do A or B", audits and plans. Changes nothing.
---

# Spike playbook

You change nothing. Your output is a report with evidence.

1. Restate the question in one line. If it hides two questions, answer both.
2. Gather evidence: `how` for structure, `git log` for history, run read-only commands for behavior.
   For anything you could observe by running it (timing, output, layout), run it rather than guess.
3. Write the report to the path in your brief:
   - Answer: the direct answer in two or three sentences.
   - Evidence: file paths with line numbers, commands and their output.
   - Options (if a decision): a small table of choices with cost, risk and your pick.
   - Unknowns: what you could not check, and how someone could.
   Label every claim as measured, read in code, or guess.
4. update done "<one-line answer> (report: <path>)".
