# astro-workflow

Execution model for the wiron-website Astro project. Every writing agent follows this.

## Stack truth

- Astro SSG + TypeScript. `html/` is the visual source of truth.
- `astro.config.mjs` and `package.json` are authoritative — never infer versions from training data.
- Node >= 22.12.0 (see `package.json` engines).

## Worktree + branch protocol

1. Each issue gets one branch: `feature/<ISSUE-KEY>-<slug>` forked from `origin/main`.
2. Writing agents build only in their own git worktree. Never work directly on `main`.
3. Builders never push. Only `repo-manager` pushes after reviewer approves (fast-forward only).
4. Never amend or rebase a commit you have already reported (`Base: <sha>` is a contract).
5. `html/` is read-only — never edit design reference files.

## Verification gate

- `npm run build` must pass. If `lint`/`test` scripts exist, they must pass too.
- Paste real command output in the report — no paraphrasing, no "should pass".
- The reviewer's evidence check is inheritance: reviewer reads the builder's pasted output and never re-runs the gate.

## Commits

- Follow `conventional-commits` skill. One logical commit per issue unless the plan splits it.
- Commit message must not be the sole carrier of `<ISSUE-KEY>` — the branch, PR title, and PR body carry it.

## Base / Branch / Target reporting

Every builder report ends with exactly these three lines (no extra formatting):

```
Base: <sha of origin/main at branch point>
Branch: feature/<ISSUE-KEY>-<slug>
Target: main
```

The reviewer uses `git diff <base>..<branch>` as the review range. If `Base` is missing, reviewer falls back to `git merge-base origin/main <branch>` and records it.

## Push-on-approve rule

Nothing reaches `origin` until the reviewer approves on both axes. `repo-manager` is the only agent that writes to `origin`.

## Precedence

`CLAUDE.md` > `docs/decisions/` ADRs > this skill > other squad skills > general best-practices.
