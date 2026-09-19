# architecture-decisions

Method for the `architect` agent in wiron-website.

## Seam catalog (what you own)

- Page vs. component boundary: where a shared section becomes a component in `src/components/`.
- Layout vs. page ownership: what lives in `src/layouts/BaseLayout.astro` vs. per-page.
- Token vs. inline: what becomes a token in `src/styles/` vs. scoped style.
- Island boundary: where client JS is required vs. where static Astro + CSS suffices.
- Route mapping: which HTML screen maps to which Astro route, and how shared shells compose.

You do NOT decide: visual values (human/design), scope/priority/acceptance criteria (planner/human), or anything requiring an external design source beyond `html/`.

## Decision-comment structure

Every decision comment follows this shape:

```
## Decision: <one-sentence name>

### Context
<what is being decided and why it matters>

### Options
1. <option A> — trade-offs
2. <option B> — trade-offs

### Decision
<chosen option and why>

### What becomes law
- `path/to/file:line` — rule a reviewer can cite (e.g. "Shared hero sections live in src/components/Hero.astro")
- ...

### Rejected
- <option> — why rejected

### Assumptions
- <explicit assumption>
```

## What becomes law

- Each bullet must be phrasable as a file:line citable rule.
- Ratified ADRs in `docs/decisions/` and prior decision comments on the same issue are already law — cite them, do not re-decide.
- Your decision takes effect the moment the comment is posted. There is no ratification PR.

## Refuse and stop

Post a comment refusing and stop when:

- The question needs an external design source beyond `html/` / `DESIGN-MANIFEST.json`.
- It is a scope/priority/acceptance-criteria question (planner/human).
- There is exactly one legal answer under existing law — point at the rule instead.

End every comment with exactly one routing line:

- `Decision recorded — next stage: plan`  (when decided)
- `Blocked: <the one thing only the human can answer>`  (when blocked)
