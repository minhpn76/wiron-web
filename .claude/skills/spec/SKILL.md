---
name: spec
description: Dùng sau khi intent.md đã được duyệt — viết docs/specs/<feature>/spec.md mô tả acceptance criteria, không mô tả cách implement.
---

# Spec

Mục tiêu: chốt "cái gì đúng khi xong", không chốt cách làm. Đọc `intent.md` cùng feature trước khi viết.

## Việc cần làm

1. Đọc `docs/specs/<feature-slug>/intent.md`. Nếu chưa có hoặc chưa duyệt, dừng và yêu cầu chạy skill `intent` trước.
2. Diễn giải intent thành acceptance criteria cụ thể, kiểm chứng được (đo được đúng/sai).
3. Nêu case biên, lỗi, trạng thái rỗng nếu liên quan.
4. Không đề cập file nào sẽ sửa, thứ tự code — đó là việc của `plan.md`.
5. Viết `docs/specs/<feature-slug>/spec.md` theo template dưới, dừng lại chờ duyệt.

## Template spec.md

```markdown
# Spec: <tên feature>

- Dựa trên: intent.md (<ngày>)

## Acceptance criteria
- [ ] <tiêu chí 1, đo được>
- [ ] <tiêu chí 2>

## Case biên / lỗi cần xử lý
<liệt kê>

## Ngoài phạm vi
<kế từ intent.md, nhắc lại nếu cần>

## Câu hỏi mở còn lại
<nếu có>
```

## Đầu ra

Commit `docs/specs/<feature-slug>/spec.md`. Không tự chuyển sang plan khi chưa có xác nhận duyệt.
