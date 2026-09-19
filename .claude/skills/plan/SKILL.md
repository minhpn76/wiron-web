---
name: plan
description: Dùng sau khi spec.md đã được duyệt — vào plan mode, viết docs/specs/<feature>/plan.md (file, thứ tự, rủi ro, cách kiểm chứng) trước khi sửa code.
---

# Plan

Mục tiêu: chốt HOW ở dạng đọc được, duyệt được, trước khi động vào code. Chạy ở plan mode (read-only) — không sửa file trong bước này.

## Việc cần làm

1. Đọc `docs/specs/<feature-slug>/spec.md`. Nếu chưa có hoặc chưa duyệt, dừng và yêu cầu chạy skill `spec` trước.
2. Đọc code hiện có liên quan (đừng đoán).
3. Xác định: file nào sẽ tạo/sửa, thứ tự thực hiện, test cần viết/chạy, bước rủi ro nhất, phương án đã xem xét và loại bỏ (nếu có).
4. Viết `docs/specs/<feature-slug>/plan.md` theo template dưới.
5. Dừng lại chờ duyệt. Chỉ sau khi được duyệt mới thoát plan mode và bắt đầu sửa code.

## Template plan.md

```markdown
# Plan: <tên feature>

- Dựa trên: spec.md (<ngày>)

## File sẽ đổi
- `path/to/file` — <lý do>

## Thứ tự thực hiện
1. <bước 1>
2. <bước 2>

## Test / cách kiểm chứng
<unit test, script chạy tay, tiêu chí pass>

## Rủi ro
<bước dễ sai nhất, vì sao>

## Phương án đã xem xét và loại bỏ
<nếu có, và vì sao loại>
```

## Đầu ra

Commit `docs/specs/<feature-slug>/plan.md`. Sau khi duyệt, code theo đúng plan — nếu lệch nhiều so với plan lúc code, cập nhật lại plan.md, không để nó lỗi thời.
