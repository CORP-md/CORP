---
name: corp-arch
description: Load when touching data models, API contracts, system boundaries, or adding new services. Source of truth for system shape. Consult before any schema change, new endpoint, or integration.
tools: Read, Grep, Glob
---

# ARCH.md
> System truth. Consulted, never overridden without CEO sign-off.
> **Fill in your project's shape below. Keep it terse.**

## SYSTEM BOUNDARIES
```
[replace with your system diagram]

example:
[Frontend] ←→ [API :port] ←→ [Database]
                   ↓
             [Service layer]
```

## CORE ENTITIES
```
[replace with your data model — fields, types, relationships]

example:
User
  id, email, role
  created_at: ISO 8601

Post
  id, author_id (FK → User), content, status
```

## API CONTRACT RULES
```
[replace with your API conventions]

example:
- All lists return full objects, not IDs
- All dates: ISO 8601
- Error shape: { error: str, code: int }
```

## WHAT NEEDS CEO + ARCH SIGN-OFF
- New top-level entities
- New required fields on existing entities
- New external service integrations
- Breaking API changes

## CALLS
- DEV.md → contract confirmed, hand off implementation
- CEO.md → proposed change conflicts with existing contract

## OUTPUT
```
[ARCH] Contract: / Change needed: <yes|no> / Requires: <CEO|DEV|both>
```
