# CONTRIBUTING.md
> Adapt corp to your project in ~10 minutes.

## What Changes vs What Doesn't

**Never touch (generic core):**
- Agent files: `CEO.md` `DEV.md` `DESIGN.md` `QA.md`
- Dispatch protocol and token rules in `CLAUDE.md`

**You own these:**
- `[PROJECT]` block in `CLAUDE.md` — your stack, structure, conventions
- Entity/contract section in `ARCH.md` — your data model and API shapes

That's it. Two edits. Everything else works as-is.

---

## Setup

### 1. Fill in `CLAUDE.md` → `[PROJECT]`
```
Name: your project
Stack: language · framework · DB · frontend
Structure: /src · /api · /etc
Entry: main entrypoint(s)
Docs: where to find more context
Conventions: tabs/spaces, naming style, async patterns, etc.
```

The `Conventions` line is important — DEV and DESIGN derive style from here, not from hardcoded rules.

### 2. Fill in `ARCH.md`
Replace the placeholder sections with your actual system diagram, entities, and API conventions. Keep it under 40 lines — if it's longer, you're writing docs, not an architecture reference.

### 3. Done
All agents read `[PROJECT]` at runtime. They infer what they don't know from existing code.

---

## Composing With Other Instructions

corp is designed to layer with existing `CLAUDE.md` content, wiki files, `AGENTS.md`, or any other context files you already use. The agents defer to `[PROJECT]` — so whatever you put there is what they operate from.

If you have existing instructions: paste the relevant parts into `[PROJECT]` or link to them. Corp reads what it's given.

---

## Adding Agents

When a domain grows large enough (auth, infra, ML, data pipeline):

1. Copy any agent as a template — `ROLE · KNOWS · CALLS · OUTPUT`
2. Keep it under 40 lines
3. Add to Agent Map in `CLAUDE.md`
4. Reference from relevant existing agents' `CALLS` sections

---

## Token Philosophy

Every line competes for context. When editing these files:
- Cut before adding
- One fact per line
- No paragraphs where a list works
- No lists where a single line works
- Agents should orient, not script
