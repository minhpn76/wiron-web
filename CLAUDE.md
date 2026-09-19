# CLAUDE.md

Working agreement cho repo này. Claude tự load file này mỗi session.

## Workflow

Feature/task đáng kể đi qua 3 file trước khi code, theo thứ tự:

1. `docs/specs/<feature>/intent.md` — why, cho ai, constraint. Viết cùng Claude qua skill `intent` (hoặc `/intent`). Duyệt trước khi sang spec.
2. `docs/specs/<feature>/spec.md` — cái gì đúng khi xong (acceptance criteria), không nói cách làm. Skill `spec` (`/spec`). Duyệt trước khi lập plan.
3. `docs/specs/<feature>/plan.md` — cách làm: file nào, thứ tự, test, rủi ro. Dùng Claude Code **plan mode** (read-only) qua skill `plan` (`/plan`). Duyệt trước khi cho code chạy.

Bug fix nhỏ (1-2 file, rõ nguyên nhân): bỏ qua intent/spec, chỉ cần `plan.md` ngắn hoặc không cần file nào nếu hiển nhiên.

Sau khi code xong: agent `verifier` tự chạy build/test/lint trước khi đưa PR cho người review — xem `.claude/agents/verifier.md`.

## Commands

- Dev: `npm run dev` — chạy Astro dev server (http://localhost:4321)
- Build: `npm run build` — build production ra `dist/`
- Preview: `npm run preview` — preview bản build
- Lint: `npm run lint` (nếu có cấu hình eslint/prettier)
- Test: `npm run test` (nếu có)

## Conventions

- **Stack:** Astro (SSG), TypeScript, HTML/CSS thuần theo design có sẵn.
- **Follow HTML design:** Mọi trang/component phải bám sát HTML design đã duyệt — không tự ý đổi layout, spacing, màu, typo. Nếu design thiếu state/variant thì hỏi trước khi tự chế.
- **Cấu trúc thư mục:**
  - `src/pages/` — route Astro (mỗi file = 1 trang)
  - `src/components/` — component Astro/UI tái sử dụng
  - `src/layouts/` — layout chung (BaseLayout, header/footer)
  - `src/styles/` — global CSS / tokens
  - `public/` — asset tĩnh (image, font, favicon)
  - `docs/specs/<feature>/` — intent/spec/plan theo workflow trên
- **Code style:** Ưu tiên semantic HTML, CSS theo design tokens, hạn chế JS không cần thiết (Astro islands khi cần interactivity). Đặt tên file kebab-case, component PascalCase.
- **Commit/branch:** `feat/<slug>`, `fix/<slug>`, commit message rõ ràng (conventional commits khuyến khích).

## Known gotchas

<cập nhật khi cùng một lỗi lặp lại quá 1 lần — đây là chỗ để agent không mắc lại>
