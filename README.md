# gelobee

A lightweight agent workflow for opencode, run like a scrum team.
You are the product owner. You talk to one agent, the scrum master. It turns requests into tickets,
assigns each to a dev in its own git worktree and tmux window, runs a zero-token standup in bash,
and tells you outcomes.

Ideas from firstmate (Kun Chen, MIT) and pstack (Lauren Tan, MIT), cut down to the core.

```
tmux new -s gelobee
cd ~/gelobee_ai_dev_workflow && bin/scrum
```

| Path | What it is |
| --- | --- |
| AGENTS.md | The scrum master's contract |
| data/projects.md | Repos the team may touch |
| opencode/agents/ | scrum-master, dev, qa, tech-lead, ba |
| opencode/TEAM.md | The product owner's behaviour and writing rules. Loaded for every agent by opencode/opencode.json |
| data/decision-register.tsv | Append-only log of tech lead decisions (bin/register writes it) |
| opencode/skills/ | story, bug, spike, how, architect, make-verify-skill |
| bin/scrum | Start the scrum master |
| bin/assign | Ticket to an agent (dev, ba, or tech-lead; default dev): worktree + tmux window + brief + opencode run |
| bin/register | Appends one row to the decision register |
| bin/standup | Zero-token watcher. Returns on done, blocked, needs-decision, failed, exited, stale |
| bin/board | The scrum board, one line per ticket |
| bin/update | How devs post status |
| tickets/ | Status files, briefs, reports (not committed) |

| Scrum term | Here |
| --- | --- |
| Product owner | You |
| Scrum master | The agent you talk to. Never codes, removes blockers |
| Dev | One agent per ticket, in its own worktree |
| Tech lead | Decides design and architecture. A dev spawns it, or bin/assign starts it. Logs each decision |
| BA | Technical business analyst. Writes ASD-STE100 docs, opens a PR, drafts tickets. The scrum master assigns the drafts |
| QA | Code reviewer on a different vendor's model |
| Story | A ticket that changes code and ends in a PR |
| Spike | A read-only research ticket that ends in a report |
| Standup | bin/standup, the watcher |
| Impediment | A `blocked` update |

Set the three `CHANGE-ME` models in opencode/agents/ first. Use `opencode models` for ids.
