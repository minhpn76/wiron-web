---
name: spec
description: Use after intent.md is approved — write docs/specs/<feature>/spec.md describing acceptance criteria without implementation details.
---

# Spec

Goal: lock in "what is correct when done", not how to build it. Read the `intent.md` for the same feature before writing.

## Tasks

1. Read `docs/specs/<feature-slug>/intent.md`. If it does not exist or is not approved, stop and ask to run the `intent` skill first.
2. Translate the intent into specific, verifiable acceptance criteria (measurable pass/fail).
3. List edge cases, error handling, and empty states if relevant.
4. Do not mention which files will change or the implementation order — that belongs in `plan.md`.
5. Write `docs/specs/<feature-slug>/spec.md` using the template below, then stop and wait for approval.

## Template spec.md

```markdown
# Spec: <feature name>

- Based on: intent.md (<date>)

## Acceptance criteria
- [ ] <criterion 1, measurable>
- [ ] <criterion 2>

## Edge cases / errors to handle
<list>

## Out of scope
<from intent.md, restate if needed>

## Remaining open questions
<if any>
```

## Output

Commit `docs/specs/<feature-slug>/spec.md`. Do not move to plan without approval.
