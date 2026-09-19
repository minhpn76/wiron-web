---
name: intent
description: Use first for any significant new feature/task — brainstorm and write docs/specs/<feature>/intent.md before discussing implementation.
---

# Intent

Goal: lock in WHY before discussing HOW. Do not propose solutions in this step.

## Tasks

1. Ask the user (PM) if unclear: what problem is being solved, for whom, why now.
2. Quick audit of existing codebase/docs — check if a similar solution/flow already exists. If so, call it out before continuing.
3. Write `docs/specs/<feature-slug>/intent.md` using the template below.
4. Stop and ask the user to approve the intent before suggesting the `spec` skill.

## Template intent.md

```markdown
# Intent: <feature name>

- Date: <YYYY-MM-DD>
- Requested by: <name>

## Problem
<real problem being faced, with evidence/metrics if available>

## For whom
<affected users/systems>

## Why now
<priority, deadline, dependencies>

## Constraints
<technical, budget, time, legal constraints>

## Out of scope
<what will NOT be done this time>

## Open questions
<unresolved points, who needs to answer>
```

## Output

Commit `docs/specs/<feature-slug>/intent.md`. Do not move to spec without approval.
