# component-implementation

Conventions for `src/components/` in the wiron-website Astro project.

## Scope

Applies when creating or editing any file under `src/components/`.

## Conventions

- Components are Astro components (`.astro`) by default. Use framework islands (React/Vue/etc.) only when interactivity requires client JS — prefer static Astro.
- Props are explicit and typed. Export a `Props` interface at the top of the component.
- Design tokens drive all visual values — colors, spacing, radii, shadows, type scale from the token table derived from `html/`. No hardcoded invention.
- No `html/`-divergent layout: component must be usable inside any page layout without visual regression.
- Keep components accessible: semantic elements, hierarchical headings, visible focus, aria where needed.
- File naming: `PascalCase.astro` for components, or `kebab-case.astro` if the repo convention says so — be consistent with existing files.

## Invariants

- Never change a component's public prop API without a plan + architect decision (if cross-screen).
- No client JS unless the design shows an interaction that requires it. Prefer CSS for hover/focus/active/transition.

## Definition of done

- Renders correctly at all viewports in the responsive matrix (360 / 390 / 430 / 820 / 1024 / 1366 / 1440 / 1920).
- No horizontal overflow at any viewport.
- `npm run build` passes.
- Matches `html/` visual contract for that component (spacing, type, color, radius, shadow, motion).
