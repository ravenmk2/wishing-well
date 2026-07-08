# Skill: ww-archiving

- **Skill**: `ww-archiving` (command `/ww-archive`)
- **Role**: Development path — completion.

## Purpose

Merge a Plan's `spec.md` / `design.md` into final-state canonical docs (diff-reviewed), archive the Plan directory, and final-commit. Closes out development work and consolidates truth.

## Core principle

- **Consolidate truth.** During execution the Plan was the source of truth; archiving merges `spec.md` / `design.md` so the docs become the live truth again, and files the Plan directory as the change-process record.

## Source-of-truth stance

- After archive, the updated docs are the source of truth.
- The archived Plan directory under `docs/plans/completed/` records the change process (scope, tasks, deviations, doc-change targets). Reconstruct "what changed when" by reading completed Plans.

## Artifact

- Merged canonical docs (`docs/specs/`, `docs/design/`, `architecture.md`) + `docs/README.md` index updates.
- Plan directory moved `docs/plans/active/` → `docs/plans/completed/` via `git mv`.

## Routing

- **Done** (normal close-out).
- **`ww-exploring` / `ww-brainstorming` / `ww-analyzing`** — only for an abandoned Plan (scope-error close-out from `ww-executing`).

## Key design decisions

- **Intelligent merge.** For each declared Doc-change target:
  - **New file** (greenfield / new topic) → the `spec.md` / `design.md` content becomes the new file.
  - **Existing file** → section-level merge: match headings, add/replace sections; the result reads as final-state (no change markers).
- **Diff HARD-GATE.** Generate a unified diff against current docs; MUST NOT apply before user approval. On an unresolvable section conflict (conflicting content, or anchor drift from a mid-flight trivial direct edit), STOP and ask the user.
- **Reconcile with Deviations.** The applied docs reflect what actually happened (per `## Deviations`), not stale Plan intentions.
- **Abandoned Plan path.** Scope-error close-out from `ww-executing`: skip the merge (the scope was wrong; the Deviations record why), archive + final-commit, then hand off to a research skill. Self-review and the user-review HARD-GATE are N/A here (the checklist is merge-focused); the final-commit confirmation is the gate.
- **Bug-fix Plan with no `spec.md` / `design.md`.** Skip the merge; just archive + commit.
- **ADR lifecycle is `ww-writing-doc`'s responsibility.** Archiving MUST NOT touch `docs/adr/`.
- **README index.** Update `docs/README.md` for any newly added doc files.
- **Gating.** Self-review default-on, skippable (merge-focused; N/A for abandoned); user review is a HARD-GATE (skipped only for abandoned / no-merge); final-commit confirmation is always a gate.

## Boundaries

- Does NOT touch code.
- Does NOT touch `docs/adr/` (`ww-writing-doc`'s responsibility).
- Does NOT edit the Plan's `spec.md` / `design.md` (read-only input; if wrong, STOP or return to `ww-executing`).
- Does NOT skip the diff HARD-GATE for a merge.

## Hard constraints

- MUST touch only `docs/specs/`, `docs/design/`, `architecture.md`, `docs/README.md` (index), and the Plan directory (`git mv`).
- MUST keep applied docs project-pure (no agent / skill / workflow / Plan / process references introduced).
- MUST NOT apply the merge before the diff HARD-GATE.
- MUST NOT commit without explicit approval (confirm the final-commit message).
