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

- Build: `<điền lệnh build>`
- Test: `<điền lệnh test>`
- Lint: `<điền lệnh lint>`

## Conventions

<điền convention code style, cấu trúc thư mục, ngôn ngữ dùng trong repo>

## Known gotchas

<cập nhật khi cùng một lỗi lặp lại quá 1 lần — đây là chỗ để agent không mắc lại>
