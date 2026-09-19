# docs/specs/

Mỗi feature/task đáng kể có 1 thư mục con:

```
docs/specs/<feature-slug>/
├── intent.md   # why — skill `intent`
├── spec.md     # cái gì đúng khi xong — skill `spec`
└── plan.md     # cách làm — skill `plan`, chạy ở plan mode
```

Thứ tự bắt buộc: intent → spec → plan. Mỗi file cần được người duyệt (comment/merge PR, hoặc xác nhận trực tiếp trong chat) trước khi sang bước kế.

Bug fix nhỏ, rõ nguyên nhân: có thể bỏ qua intent/spec, chỉ cần `plan.md` ngắn.
