# Wiron Website — Dev Squad Instructions

Target: the `wiron-website` Astro repo (`src/pages/`, `src/components/`, `src/layouts/`, `src/styles/`, `public/`, `html/` as design source of truth). Tasks run in the human's live checkout, serialized by a path mutex. Writing agents therefore build only in their own git worktree, on a branch forked from `origin/main` and named `feature/<ISSUE-KEY>-<slug>`. Builders never push: after review approves, the repo-manager pushes the branch and opens its pull request against `main`, and closes the issue when that pull request merges.

Repo law is `CLAUDE.md`, the repo's `.claude/skills`, and the ratified ADRs already merged in `docs/decisions/` (if any). Those ADRs bind builders and reviewers exactly as `CLAUDE.md` does. The architect's decision comment binds its own issue's plan and build from the moment it is posted. Design law is `html/` + `DESIGN-MANIFEST.json` + `DESIGN-HANDOFF.md` — every page/component must match that visual contract.

## Pipeline

```
decide (architect, only when the issue turns on an architecture decision)
  → plan (planner)
  → build (coder — must pass verification and match html/ pixel-faithfully)
  → review (reviewer — two axes: repo law + spec)
  → publish (repo-manager pushes and opens the PR)
  → in_review → human merges the PR
  → merge trigger → repo-manager sets done
```

- The `decide` stage records its decision as an issue comment, with no branch and no diff. It takes effect immediately — the leader delegates `plan` in the same run. It is never reviewed or published.
- Trivial, unambiguous one-file fixes may skip planning; everything else plans first. Most issues need no `decide` stage — route one only for the categories under Escalation.

## Routing

| Work | Who | Notes |
|------|-----|-------|
| All build work (pages, components, layouts, styles) | `coder` | One `feature/<ISSUE-KEY>-<slug>` branch per issue, forked from `origin/main`. On multi-screen issues, scaffold shared layout/tokens first, then per-screen routes. |
| Architecture decisions (module boundaries, ownership, interfaces) | `architect` | Writes no files; output is one decision comment. Takes effect immediately. |
| Planning & scoping | `planner` | Read-only; posts one plan comment per template. |
| Review gate | `reviewer` | Two axes: diff vs. repo law and diff vs. spec. `npm run build` evidence must be real. Only approve on both axes releases the work. |
| Publish & close | `repo-manager` | Pushes approved branch, opens PR to `main`, closes issue on verified merge. Never builds/reviews/merges. |
| Orchestration | `leader` | Routes every stage; never implements. |

## Rework

- Review "needs changes" or builder reporting FAIL → re-delegate to the same `coder` with the findings; it reuses its branch; then review the new range again. Nothing reaches origin until an approve.
- On approve of both axes → delegate publish to `repo-manager`, then set `in_review`. No other member ever writes to origin.

## Owner

Owner is mandatory on every issue. It is the member field naming the human who asked for the work — whoever requested it in a chat or a comment, or created the issue themselves.

- An issue with no Owner does not get worked — the leader asks in a comment and stops.
- Owner is a custom property: `multica issue property set <ISSUE-KEY> --name Owner --value "<member>"` and confirmed with `property list`.
- An issue created under a parent inherits the parent's Owner. Owner is never an agent.
- Never leave it silently empty, and never guess a name from the thread.

## Relay contract

- Builder ends every report with `Base: <sha>`, `Branch: <branch>`, `Target: main`.
- Leader relays Base + Branch to the reviewer, and all three to repo-manager at publish time.
- Every agent report ends with exactly one `@mention` link to the next actor — a comment without a mention is a dead stop.

## Design source

- `html/` is the visual contract. Every Astro page/component must match it — typography, spacing, colors, radii, shadows, motion, responsive breakpoints, and interactive states.
- `DESIGN-MANIFEST.json` maps each HTML screen to a route; `index.html` is launcher/overview only.
- Any need beyond `html/` (Figma, external design tool, missing variant) goes to the human member — agents never invent design values.
- Design gaps: report as `Blocked: design gap — <what is missing>` and stop.

## Escalation

Route a `decide` stage to the `architect` when:

- Module/page ownership or component boundary is unclear.
- Layout vs. page-data boundary is contested.
- A shared token/component decision affects multiple screens.

The following stay the human's call (architect may record options + recommendation, never the decision):

- Visual/interaction choices not in `html/` (new variant, new state).
- Scope, priority, and acceptance criteria (planner/human).

Verification failed twice on the same issue → stop the pipeline and summarize for the human.

## Status

The leader keeps the parent issue honest (`in_progress` while stages run, `in_review` once the PR is open). Done is set by a human, or by `repo-manager` on a verified merge trigger — by nobody else and never on judgment.

## Branch & PR contract

- Branch: `feature/<ISSUE-KEY>-<slug>` forked from `origin/main`.
- Builders never push; only `repo-manager` pushes after review approve (fast-forward only).
- PR target: `main`. Title/body must contain `<ISSUE-KEY>` (branch + title + body are the three scanned locations).
- Builders never amend or rebase a reported commit; reviewers detect rewritten tips as findings.
