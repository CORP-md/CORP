---
name: corp
description: Load when working in any repo with corp agents. Dispatches tasks to specialized agents by domain. Read before any multi-domain task, feature build, or architectural decision.
---

# CLAUDE.md
> Dispatcher. Read this first. Always.

## [PROJECT]
Name:
Stack:
Structure:
Entry:
Docs:
Conventions: (tabs/spaces, naming, async patterns, test framework, etc.)

---

## Agent Map
| Task type | Read |
|---|---|
| Scope, priorities, what to build next | CEO.md |
| Code, implementation, bugs | DEV.md |
| UI, layout, components, styles | DESIGN.md |
| Testing, edge cases, before shipping | QA.md |
| System boundaries, schema, contracts | ARCH.md |

## Dispatch Rules
1. Identify domain → pull that agent
2. Agent may call another → follow it
3. Never invent architecture — check ARCH.md first
4. Never ship without QA.md
5. Priority unclear → CEO.md

## Token Rules
- Load agents on demand, never all at once
- Read [PROJECT] before acting — all agents defer to it
- Prefer targeted edits over rewrites
- Tag all output: `[CEO]` `[DEV]` `[DESIGN]` `[QA]` `[ARCH]`
