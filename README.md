# CORP.skill
**A company in a folder. Lightweight multi-agent org structure for AI coding assistants.**

Drop a `.claude/` folder into any repo and give your AI a CEO, a dev lead, a designer, a QA engineer, and a systems architect; all in markdown. No frameworks, no orchestration layer, no dependencies. Just files.

Compatible with **Claude Code · Codex CLI · Cursor · Gemini CLI · OpenCode · Windsurf** and any tool that reads the Agent Skills standard.

---

## What It Is
Most agent skills teach Claude *how* to do a task. Corp teaches Claude *who to ask*.

Each agent is a markdown file with a defined role, domain knowledge, and a handoff protocol. The dispatcher (`CLAUDE.md`) routes tasks to the right agent. Agents call each other when work crosses domains. Nothing is loaded that isn't needed.

```
.claude/
├── CLAUDE.md            ← dispatcher, always read first
└── agents/
    ├── CEO.md           ← scope, priorities, what not to build
    ├── DEV.md           ← code, backend, database
    ├── DESIGN.md        ← UI, components, CSS, interactions
    ├── QA.md            ← quality gate, ship/no-ship
    └── ARCH.md          ← schema, API contracts, system boundaries
```

---

## Install
```bash
# Clone into your project
git clone https://github.com/zblauser/corp .claude-tmp
cp -r .claude-tmp/.claude ./
rm -rf .claude-tmp
```

Or just download the `.claude/` folder and drop it in your repo root.

---

## Setup (5 minutes)
**1. Edit the `[PROJECT]` block in `.claude/CLAUDE.md`**
```
Name: your-project
Stack: your stack
Structure: your folder layout
Entry: your entrypoints
Docs: where to find more context
```

**2. Update entity/contract section in `.claude/agents/ARCH.md`**
Sketch your data model and API shapes. Keep it terse. This is what Claude consults before touching any data layer.

**3. Update file paths in `.claude/agents/DEV.md`**
Point the `KNOWS` section at your actual folder structure.

**4. Leave everything else alone**
`CEO.md`, `QA.md`, and `DESIGN.md` are intentionally abstract — they port as-is.

Full guide: [CONTRIBUTING.md](.claude/CONTRIBUTING.md)

---

## How It Works
```
Task arrives
  → Claude reads CLAUDE.md
  → Identifies domain
  → Reads relevant agent
  → Agent may call another agent
  → Implements
  → QA.md checklist
  → Ships
```

Agents are **referential, not prescriptive** — they tell Claude what it knows and who to consult, not what to do step by step. This keeps token usage low and lets the model reason rather than follow a script.

Each agent tags its output: `[CEO]`, `[DEV]`, `[DESIGN]`, `[QA]`, `[ARCH]` so context is operating in.

---

## Design Principles
**Token-first.** Every line earns its place. Agents load on demand, not upfront. The whole org is under 430 lines.

**Referential over prescriptive.** Agents know what they know. They don't script every step; they orient the model and hand off.

**Generic core, project-specific edges.** Only the `[PROJECT]` block in `CLAUDE.md` and the entity section in `ARCH.md` change per repo. Everything else ports.

**Output-tagged.** Every agent response carries its tag. You always know who's talking.

---

## Adding Agents
When a domain grows large enough (auth, infra, ML, data):

1. Copy the structure: `ROLE · KNOWS · CALLS · OUTPUT FORMAT`
2. Add it to the Agent Map table in `CLAUDE.md`
3. Reference it from relevant existing agents' `CALLS` sections
4. Keep it under ~60 lines; if longer, split it

---

## Compatibility
| Tool | Path | Status |
|---|---|---|
| Claude Code | `.claude/agents/` | ✅ native |
| Codex CLI | `codex.md` + agents | ✅ compatible |
| Cursor | `.cursor/rules/` | ✅ copy agents there |
| Gemini CLI | `GEMINI.md` + agents | ✅ compatible |
| OpenCode | `.agents/` | ✅ compatible |
| Any AGENTS.md tool | root `AGENTS.md` | ✅ copy dispatcher |

---

## Inspired By
- Caveman Claude compression principles
- Karpathy's LLM wiki / idea file patterns
- The Agent Skills open standard (`agentskills.io`)

---

*corp is a skill, not a framework. It has no runtime, no install, no version to update. It's just files that know how to work together.*

