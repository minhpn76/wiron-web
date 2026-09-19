# design-fidelity

Visual contract discipline for wiron-website. Applies to every agent that touches UI.

## Source of truth

- `html/` + `DESIGN-MANIFEST.json` + `DESIGN-HANDOFF.md` are the visual contract.
- Tokens (background, surface, foreground, muted, border, accent, radius, shadow, spacing, type scale, motion) must be extracted from `html/` before coding — no invention, no framework defaults.
- If `html/` has no external stylesheet, sample colors/type/spacing from the entry HTML and convert to named tokens in `src/styles/`.

## Rules

- Never invent a design value (color, spacing, radius, shadow, type size, motion). If the design does not specify it, report a design gap and stop — do not substitute.
- Preserve copy, labels, and hierarchy exactly as in `html/`. Do not replace real copy with filler.
- Preserve interactive affordances present in the design: hover, focus, pressed, disabled, loading, validation, tab/accordion, modal/sheet, keyboard states.
- Preserve accessibility semantics: headings stay hierarchical, controls remain buttons/links/inputs, focus stays visible.
- Do not keep prototype-only annotations, frame labels, or design-tool chrome in production UI.

## Design gaps

When the implementation needs a value/state/variant not present in `html/`:

1. Do not invent it.
2. Post `Blocked: design gap — <what is missing, where it is needed>` and stop.
3. Route to the human via the leader — only the human can answer design-source questions.

## Responsive contract

Validate across the viewport matrix: 360 / 390 / 430 / 600 / 820 / 1024 / 1366 / 1440 / 1920. No horizontal overflow at any width. Use fluid `clamp()` for type/spacing and container queries where component width matters more than viewport width.

## For reviewers

When a diff looks off-design, read the inline comment at the site first — the deviation may be a recorded decision (architect comment or plan note). Only flag what no rule or recorded decision backs.
