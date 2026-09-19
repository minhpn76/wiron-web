---
name: plan
description: Use after spec.md is approved — enter plan mode and write docs/specs/<feature>/plan.md (files, order, risks, verification) before touching code.
---

# Plan

Goal: lock in HOW in a readable, reviewable form before touching code. Runs in plan mode (read-only) — do not edit files in this step.

## Tasks

1. Read `docs/specs/<feature-slug>/spec.md`. If it does not exist or is not approved, stop and ask to run the `spec` skill first.
2. Read the relevant existing code (do not guess).
3. Determine: which files to create/modify, execution order, tests to write/run, riskiest step, and alternatives considered and rejected (if any).
4. Write `docs/specs/<feature-slug>/plan.md` using the template below.
5. Stop and wait for approval. Only after approval, exit plan mode and start coding.

## Template plan.md

```markdown
# Plan: <feature name>

- Based on: spec.md (<date>)

## Files to change
- `path/to/file` — <reason>

## Execution order
1. <step 1>
2. <step 2>

## Tests / verification
<unit tests, manual scripts, pass criteria>

## Risks
<most error-prone step and why>

## Alternatives considered and rejected
<if any, and why rejected>
```

## Output

Commit `docs/specs/<feature-slug>/plan.md`. After approval, code according to the plan — if implementation diverges significantly, update plan.md so it stays accurate.
