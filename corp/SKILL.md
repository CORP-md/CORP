---
name: corp
description: Multi-agent org structure for any repo. Loads a CEO, DEV, DESIGN, QA, and ARCH agent from .claude/agents/. Use when a task spans multiple domains, when you need to prioritize before building, or when working in a repo that contains corp agents. Dispatcher lives in CLAUDE.md — always read first.
---

# corp
> A company in a folder. Referential multi-agent org for AI coding assistants.

## Entrypoint
Always start at `.claude/CLAUDE.md`. It dispatches to the right agent.

## Agents
| File | Domain | Call when |
|---|---|---|
| `agents/CEO.md` | Scope, priorities, product decisions | Before building anything non-trivial |
| `agents/DEV.md` | Code, backend, database | Writing or fixing anything |
| `agents/DESIGN.md` | UI, components, CSS, interactions | Touching the frontend |
| `agents/QA.md` | Quality gate, ship/no-ship | Before declaring done |
| `agents/ARCH.md` | Schema, API contracts, system boundaries | Before touching data layer |

## Usage Pattern
```
Task arrives
  → Read CLAUDE.md
  → Identify domain → read that agent
  → Agent may call another → follow it
  → Implement
  → QA.md checklist
  → Ship
```

## Token Protocol
- Load agents on demand, never all at once
- Tag all output: [CEO] [DEV] [DESIGN] [QA] [ARCH]
- Prefer targeted edits over rewrites
- Summarize before acting

## Setup
1. Copy `.claude/` to repo root
2. Edit `[PROJECT]` block in `CLAUDE.md`
3. Update entity/contract section in `ARCH.md`
4. Update file paths in `DEV.md` KNOWS section
5. See `CONTRIBUTING.md` for full guide

## Version
0.1.0
