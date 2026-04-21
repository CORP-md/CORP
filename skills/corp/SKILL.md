---
name: corp
description: >
  Multi-agent org structure for any repo. Loads CEO, DEV, DESIGN, QA, and ARCH agents
  from .claude/agents/. Use when a task spans multiple domains, before building anything
  non-trivial, or to check which agent handles a given task.
  Trigger: /corp, "which agent", "load corp", "who handles X".
---

# corp — company in a folder

## What this is
Corp gives your AI a team: a CEO who says no, a dev lead who reads before writing, a designer who matches existing patterns, a QA engineer who blocks bad ships, and an architect who owns the system shape. All in markdown. No runtime.

## Agent map
| Agent | Domain | Call when |
|---|---|---|
| `CEO.md` | Scope, priorities, what not to build | Before building anything non-trivial |
| `DEV.md` | Code, bugs, backend, database | Writing or fixing anything |
| `DESIGN.md` | UI, components, styles, interactions | Touching the frontend |
| `QA.md` | Quality gate, ship/no-ship | Before declaring done — always |
| `ARCH.md` | Schema, API contracts, system shape | Before touching the data layer |

## Quick dispatch
- "Should I build this?" → CEO
- "How do I implement X?" → DEV
- "Is this UI consistent?" → DESIGN
- "Is this ready to ship?" → QA
- "Will this break the schema?" → ARCH

## Protocol
```
Task arrives
  → Read .claude/CLAUDE.md
  → Identify domain → load that agent
  → Agent may hand off → follow it
  → Implement
  → QA checklist
  → Ship
```

## Setup check
If `.claude/CLAUDE.md` [PROJECT] block is empty: fill it in before using corp agents.
Required: Name, Stack, Structure. Everything else is optional but helps.

## Token rules
- Load agents on demand, never all at once
- Tag output: [CEO] [DEV] [DESIGN] [QA] [ARCH]
- Prefer targeted edits over rewrites

## Install
```bash
claude plugin install github:zblauser/CORP
```
Or drop the `.claude/` folder into any repo manually.
