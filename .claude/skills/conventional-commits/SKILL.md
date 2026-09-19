# conventional-commits

Commit message contract for wiron-website. Invoke before your first commit of a task.

## Format

```
<type>(<scope>): <subject>

<body (optional)>
```

## Types

- `feat` — new feature
- `fix` — bug fix
- `docs` — documentation only
- `style` — formatting, no logic change
- `refactor` — restructuring, no behavior change
- `chore` — tooling, config, dependencies
- `test` — tests

## Rules

- Subject is imperative, lowercase, no trailing period: `feat(hero): add responsive clamp for heading`
- Scope is the surface or area: `pages`, `components`, `layouts`, `styles`, `config`, or a screen slug (`pricing`, `contact`).
- One logical commit per issue unless the plan explicitly splits it.
- Do not rely on the commit message to carry `<ISSUE-KEY>` — the branch, PR title, and PR body carry it. Including it in the commit is optional.
- Never amend or rebase a commit you have already reported (`Base: <sha>` is a contract).
