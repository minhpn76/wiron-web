# review-checklist

Method for the `reviewer` agent. Follow top to bottom.

## 0. Open Code Review (delegation mode)

- OCR selects the files and routes each to its rule — you are the model, so no key, no `ocr config`, never `ocr review`, and OCR never writes anything.
- Use `ocr delegate` commands to fan out per-file checks; collect results before proceeding.

## 1. Repo law

- `CLAUDE.md` compliance.
- `.claude/skills` compliance (astro-workflow, component-implementation, page-implementation, design-fidelity).
- `docs/decisions/` ADRs (if any) — "What becomes law" lines are citable.

## 2. Spec axis

- Every acceptance criterion in the issue + planner's plan is met.
- Unmet criterion = needs changes, regardless of code quality.

## 3. Design fidelity

- Visual match against `html/` for the affected screens (spacing, type, color, radius, shadow, motion, responsive).
- No invented tokens or values; design gaps are reported, not silently filled.

## 4. Astro / TypeScript correctness

- Correct Astro component usage, prop typing, layout composition.
- Stack truth: Astro SSG + TypeScript per `package.json`.

## 5. Accessibility

- Semantic HTML, heading hierarchy, focus visibility, keyboard operability, aria where needed.

## 6. Responsive

- No horizontal overflow; correct behavior across 360 / 390 / 820 / 1440 / 1920 (min).

## 7. Verification evidence

- Builder pasted real `npm run build` (and lint/test if configured) output covering the reviewed tip.
- Missing / paraphrased / stale / contradictory evidence = standards finding, return to coder.

## 8. Smell baseline

- No dead code, no speculative abstraction, no unnecessary client JS, no hardcoded design values that should be tokens.

## 9. Verdict format

One comment using this shape:

```
## Code Review Results

### Findings
- `path:line [category] [axis]` — description
  Recommendation: ...

### Notes
- Smells / follow-ups (one line each, naming the file)

### Verdict
- Standards: approve | needs changes
- Spec: approve | needs changes
- Verdict: approve (both axes) | needs changes

Base: <sha>
Branch: feature/<ISSUE-KEY>-<slug>
Target: main

[@all](mention://all/all) <routing line>
[@<next-agent>](mention://agent/<id>)
```

- `axis` is `standards` or `spec`.
- Follow-ups outside the diff go under Notes so the leader can open backlog issues.
- The comment ends with `@all` + exactly one mention — without it, the verdict is a dead stop.
