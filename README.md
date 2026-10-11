# gelobee

A lightweight agent workflow for opencode, run like a scrum team.
You are the product owner. You talk to one agent, the scrum master. It turns requests into tickets,
assigns each to a dev in its own git worktree and tmux window, runs a zero-token standup in bash,
and tells you outcomes.

Ideas from firstmate (Kun Chen, MIT) and pstack (Lauren Tan, MIT), cut down to the core.

```
tmux new -s gelobee
cd ~/gelobee && bin/scrum
```

| Path | What it is |
| --- | --- |
| AGENTS.md | The scrum master's contract |
| data/projects.md | Repos the team may touch |
| opencode/agents/ | scrum-master, dev, qa |
| opencode/skills/ | story, bug, spike, how, architect, make-verify-skill |
| bin/scrum | Start the scrum master |
| bin/assign | Ticket to a dev: worktree + tmux window + brief + opencode run |
| bin/standup | Zero-token watcher. Returns on done, blocked, needs-decision, failed, exited, stale |
| bin/board | The scrum board, one line per ticket |
| bin/update | How devs post status |
| tickets/ | Status files, briefs, reports (not committed) |

| Scrum term | Here |
| --- | --- |
| Product owner | You |
| Scrum master | The agent you talk to. Never codes, removes blockers |
| Dev | One agent per ticket, in its own worktree |
| QA | Code reviewer on a different vendor's model |
| Story | A ticket that changes code and ends in a PR |
| Spike | A read-only research ticket that ends in a report |
| Standup | bin/standup, the watcher |
| Impediment | A `blocked` update |

Set the three `CHANGE-ME` models in opencode/agents/ first. Use `opencode models` for ids.
