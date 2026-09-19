# planning

Method for the `planner` agent in wiron-website.

## Surface classification

Classify the issue into one or more surfaces before planning:

- `pages` — a route in `src/pages/` (one HTML screen → one route)
- `components` — reusable UI in `src/components/`
- `layouts` — shared shell in `src/layouts/` (BaseLayout, header/footer)
- `styles` — tokens / global CSS in `src/styles/`
- `config` — `astro.config.mjs`, `tsconfig.json`, build/tooling
- `docs` — `docs/**`, `*.md`

One surface per sub-issue is ideal. If the issue spans many screens, propose a split.

## Plan template

Every plan comment follows this shape:

```
## Plan: <issue title> (<ISSUE-KEY>)

### Scope
- Surfaces: <list>
- In scope: ...
- Out of scope: ...

### Steps
1. <step> — `path/to/file` — <what and why>
2. ...

### Acceptance criteria
- [ ] <criterion 1, measurable>
- [ ] <criterion 2>

### Tests / verification
- `npm run build` must pass
- Visual check: compare against `html/<screen>.html` at 390 / 820 / 1440
- No horizontal overflow at any viewport

### Risks
- <riskiest step and why>

### Alternatives considered
- <option> — rejected because ...

### Assumptions
- <explicit assumption and why>
```

## Acceptance-criteria library

Use these patterns when applicable; add issue-specific ones as needed:

- Builds: `npm run build` passes with no errors.
- Routes: each HTML screen maps to exactly one Astro route and renders.
- Fidelity: spacing / type / color / radius / shadow match `html/` pixel-faithfully.
- Responsive: no horizontal overflow at 360 / 390 / 430 / 820 / 1024 / 1440 / 1920.
- A11y: headings hierarchical, controls semantic, focus visible, keyboard operable.
- Tokens: all visual values come from `src/styles/` tokens, no hardcoded invention.

## Splitting rules

- One screen = one sub-issue is preferred for multi-screen work.
- Shared layout/tokens = its own sub-issue or the first step of the first screen.
- Never produce a mega-plan that mixes 4+ screens with shared foundations — propose the split instead.

## Traps a plan must name

- Prototype chrome in `html/` that must not reach production.
- Missing states/variants in the design (report as design gap, not assumption).
- Token extraction needed before any component work.
- Client JS islands — name where JS is actually needed vs. where CSS suffices.

## Handoff

End every plan comment with:

```
[@leader](mention://agent/leader)
```

Without the mention, the plan sits unactioned — the leader does not wake on its own.
