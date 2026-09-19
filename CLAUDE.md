# CLAUDE.md

Working agreement for this repo. Claude loads this file every session.

## Workflow

Every significant feature/task goes through 3 files before coding, in order:

1. `docs/specs/<feature>/intent.md` — why, for whom, constraints. Written with Claude via the `intent` skill (or `/intent`). Must be approved before moving to spec.
2. `docs/specs/<feature>/spec.md` — what is correct when done (acceptance criteria), no implementation details. Skill `spec` (`/spec`). Must be approved before planning.
3. `docs/specs/<feature>/plan.md` — how: which files, order, tests, risks. Uses Claude Code **plan mode** (read-only) via the `plan` skill (`/plan`). Must be approved before coding.

Small bug fix (1-2 file, clear root cause): skip intent/spec, only a short `plan.md` or no file at all if trivial.

After coding: the `verifier` agent runs build/test/lint before human review — see `.claude/agents/verifier.md`.

## Commands

- Dev: `npm run dev` — run Astro dev server (http://localhost:4321)
- Build: `npm run build` — production build to `dist/`
- Preview: `npm run preview` — preview the production build
- Lint: `npm run lint` (if eslint/prettier is configured)
- Test: `npm run test` (if configured)

## Conventions

- **Stack:** Astro (SSG), TypeScript, plain HTML/CSS following the existing design.
- **Follow HTML design:** Every page/component must match the HTML design in `html/` — do not change layout, spacing, colors, or typography on your own. If the design is missing a state/variant, ask before inventing one.
- **Directory structure:**
  - `src/pages/` — Astro routes (one file = one page)
  - `src/components/` — reusable Astro/UI components
  - `src/layouts/` — shared layouts (BaseLayout, header/footer)
  - `src/styles/` — global CSS / design tokens
  - `public/` — static assets (images, fonts, favicon)
  - `docs/specs/<feature>/` — intent/spec/plan per workflow above
  - `html/` — HTML design reference (source of truth for UI)
- **Code style:** Prefer semantic HTML, CSS via design tokens, minimal JS (Astro islands only when interactivity is needed). File names kebab-case, components PascalCase.
- **Branch/commit:** `feat/<slug>`, `fix/<slug>`, clear commit messages (conventional commits encouraged).

## Known gotchas

<update when the same mistake repeats more than once — prevents the agent from repeating it>
