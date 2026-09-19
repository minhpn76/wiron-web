# docs/specs/

Each significant feature/task has its own subdirectory:

```
docs/specs/<feature-slug>/
├── intent.md   # why — skill `intent` (/intent)
├── spec.md     # what is correct when done — skill `spec` (/spec)
└── plan.md     # how — skill `plan` in plan mode (/plan)
```

Required order: intent → spec → plan. Each file must be approved (PR comment/merge or direct chat confirmation) before moving to the next step.

Small bug fix with clear root cause: intent/spec may be skipped, only a short `plan.md` is needed.
