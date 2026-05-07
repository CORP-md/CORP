---
name: corp-init
description: >
  Interactive setup wizard for corp. Fills in the [PROJECT] block in .claude/CLAUDE.md
  and the entity/contract section in .claude/agents/ARCH.md by asking the user questions.
  Run once when dropping corp into a new repo.
  Trigger: /corp:init, "set up corp", "configure corp", "corp setup".
---

# corp:init — setup wizard

You are setting up corp for a new project. Walk through this in order. Ask one section at a time, not all at once.

## Step 1 — Read current state

Read `.claude/CLAUDE.md`. Check if [PROJECT] block is already filled in.
- If filled: confirm with user before overwriting.
- If empty: proceed.

## Step 2 — Collect [PROJECT] info

Ask the user (one message, all at once):

> To configure corp, I need a few things:
> 1. **Project name** — what's this called?
> 2. **Stack** — language, framework, database, frontend (e.g. "TypeScript · Next.js · Postgres · Tailwind")
> 3. **Structure** — top-level folders (e.g. "/src · /api · /components · /tests")
> 4. **Entry points** — main files or commands to run the app
> 5. **Conventions** — tabs or spaces? naming style? async pattern? test framework?
> 6. **Docs** — any READMEs, wikis, or spec files to reference?

Wait for response. Fill in what they give you. Leave blank any field they skip — don't invent values.

## Step 3 — Collect ARCH.md info

Ask:

> Now for system shape (skip anything that doesn't apply yet):
> 1. **System boundaries** — how do the pieces connect? (e.g. "Frontend ↔ API :3000 ↔ Postgres")
> 2. **Core entities** — main data models with key fields (e.g. "User: id, email, role")
> 3. **API conventions** — response shape, date format, error format?

Wait for response.

## Step 4 — Write files

Write the [PROJECT] block into `.claude/CLAUDE.md` with the collected values.
Write the system boundaries, entities, and API rules into `.claude/agents/ARCH.md`, replacing the placeholder sections.

Keep both files' structure intact — only replace the content sections, not the agent headers or output formats.

## Step 5 — Confirm

Tell the user:
- What was written and where
- Which fields were left blank (if any) and how to fill them later
- What to do next: "Run /corp to verify, then start building."

## Rules
- Never invent stack details. Only write what the user provides.
- If user skips ARCH.md questions entirely, leave those sections as-is with their placeholder examples.
- Keep all writes surgical — don't reformat or reorder anything outside the target sections.
