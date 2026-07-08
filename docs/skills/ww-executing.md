# Skill: ww-executing

- **Skill**: `ww-executing` (command `/ww-execute`)
- **Role**: Development path — execute.

## Purpose

Execute a Plan's tasks in order — verifying and committing each — manage in-flight changes, then hand off to `ww-archiving`.

## Core principle

- **Faithful execution.** No scope creep, no silent deviations; every in-flight change is classified by magnitude and recorded.

## Source-of-truth stance

- The Plan (`plan.md` + `tasks.md` + `spec.md` / `design.md`) is the **source of truth (during execution)**; docs lag and are merged by `ww-archiving`.
- If execution reveals the Plan is wrong, amend it per change management; if it reveals spec/design is wrong, stop and ask the user.

## Artifact

- Code + Plan amendments: `tasks.md` status notes, `spec.md` / `design.md` / `## Scope` amendments, and `## Deviations` entries appended to `plan.md`.

## Routing

- `ww-archiving`.

## Key design decisions

- **Per-task verify-then-commit.** A task is complete only when its verification passes; each task's code and Plan amendments are committed together so the Plan and code stay in sync per commit.
- **Change management by magnitude:**
  - **Plan-level change** (contradicts neither spec nor design): amend the Plan in place + append a Deviation; no extra gate.
  - **Scope drift (small):** amend `## Scope` + append a Deviation; continue.
  - **Scope error (fundamental):** STOP, ask the user; if reverting, run `git revert` with per-commit confirmation (code is touchable here — `ww-archiving` cannot touch code); append a Deviation; hand off to `ww-archiving` to close out as abandoned (no merge); then return to a research skill, carrying the archived Plan's path as superseded.
- **Deviations log is append-only.** Never edit or delete prior entries; one entry per in-flight change.
- **No live doc to contradict.** `spec.md` / `design.md` are not merged until archive, so every change is a Plan amendment + Deviation (except a fundamental scope error, which closes the Plan as abandoned).
- **Gating.** Self-review default-on, skippable; user acceptance is a HARD-GATE.

## Boundaries

- Does NOT touch canonical docs (`docs/specs/`, `docs/design/`, `architecture.md`) — merged by `ww-archiving`.
- Does NOT write docs outside the Plan directory.
- Does NOT silently deviate.
- Does NOT touch code outside the Plan's tasks.

## Hard constraints

- MUST execute only the Plan's tasks (no scope creep).
- MUST touch only code and the Plan directory (`plan.md`, `tasks.md`, `spec.md` / `design.md`).
- MUST NOT touch canonical docs.
- MUST NOT commit without explicit user approval (confirm the message before each commit).
- MUST NOT skip the user-acceptance HARD-GATE.
