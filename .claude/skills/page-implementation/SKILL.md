# page-implementation

Conventions for `src/pages/` and `src/layouts/` in the wiron-website Astro project.

## Source map

- Each HTML screen in `html/` maps to one Astro route in `src/pages/`:

| HTML screen | Astro route | Notes |
|-------------|-------------|-------|
| `index.html` | `src/pages/index.astro` | launcher/overview per DESIGN-MANIFEST |
| `wiron-website.html` | `src/pages/index.astro` or dedicated route | decide per plan |
| `services.html` | `src/pages/services.astro` | |
| `solutions.html` | `src/pages/solutions.astro` | |
| `work.html` | `src/pages/work.astro` | |
| `pricing.html` | `src/pages/pricing.astro` | |
| `contact.html` | `src/pages/contact.astro` | |
| `seo-performance.html` | `src/pages/seo-performance.astro` | |

The plan for each screen confirms the exact route mapping before coding.

## Conventions

- Use `src/layouts/BaseLayout.astro` (or equivalent) for shared shell: `<head>` (meta/SEO), header/nav, footer, global styles.
- Pages compose layouts + components — no duplicated header/footer per page.
- Extract shared sections (hero, feature grid, CTA, etc.) into `src/components/` when used on more than one screen.
- Styles: tokens in `src/styles/` (global.css / tokens.css), page-specific styles scoped to the page/component.
- Keep `html/` as reference — do not copy-paste unprocessed HTML verbatim if it carries prototype chrome or inline styles that should become tokens.
- Islands: only for form handling, tabs/filters, dialogs, or other client interactions visible in the design. Static screens need no JS.

## Ownership

- `src/pages/` and `src/layouts/` own presentation and composition.
- Build/data concerns (if any) live outside pages — flag to the leader if a page task implies a data-layer edit the plan never settled.

## Verification

- `npm run build` passes and each route renders.
- No horizontal overflow at any responsive viewport.
- Visual match against `html/` at 390 / 820 / 1440 / 1920 (min).
