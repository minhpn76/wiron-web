---
name: intent
description: Dùng đầu tiên khi có feature/task mới đáng kể — brainstorm và viết docs/specs/<feature>/intent.md trước khi bàn cách làm.
---

# Intent

Mục tiêu: chốt WHY trước khi bàn HOW. Không đề xuất giải pháp trong bước này.

## Việc cần làm

1. Hỏi người dùng (PM) nếu chưa rõ: vấn đề đang giải quyết là gì, cho đối tượng nào, tại sao cần bây giờ.
2. Audit nhanh codebase/docs hiện có — xem đã có giải pháp/luồng tương tự chưa. Nếu có, nêu ra trước khi tiếp tục.
3. Viết `docs/specs/<feature-slug>/intent.md` theo template dưới.
4. Dừng lại, yêu cầu người dùng duyệt intent trước khi gợi ý dùng skill `spec`.

## Template intent.md

```markdown
# Intent: <tên feature>

- Ngày: <YYYY-MM-DD>
- Người yêu cầu: <tên>

## Vấn đề
<vấn đề thực tế đang gặp, có bằng chứng/số liệu nếu có>

## Cho ai
<đối tượng người dùng/hệ thống bị ảnh hưởng>

## Vì sao bây giờ
<mức độ ưu tiên, deadline, phụ thuộc>

## Constraint
<ràng buộc kỹ thuật, ngân sách, thời gian, pháp lý>

## Ngoài phạm vi
<những gì KHÔNG làm trong lần này>

## Câu hỏi mở
<những điểm chưa chốt, cần ai trả lời>
```

## Đầu ra

Commit `docs/specs/<feature-slug>/intent.md`. Không tự chuyển sang spec khi chưa có xác nhận duyệt.
