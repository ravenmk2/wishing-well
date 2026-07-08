# Skill: ww-planning

- **Skill**: `ww-planning` (command `/ww-plan`)
- **Role**: Development path — plan.

## Purpose

Turn a research conclusion (or a clear user goal) into an executable Plan of fine-grained, verifiable tasks, plus any doc changes carried as `spec.md` / `design.md`.

## Core principle

- **Plan = execution path.** During execution the Plan is the source of truth; docs lag and are merged at archive.
- **No contradiction.** A Plan MUST NOT contradict spec or design; gaps are noted as revision suggestions, not silently worked around.

## Source-of-truth stance

- Spec governs **requirements**; design governs **shape**; Plan governs **execution**.
- During the Plan lifecycle, the Plan is the source of truth (docs lag). If spec/design is wrong, the Plan carries the correction as `spec.md` / `design.md` (applied at archive); if the gap is fundamental, return to a research skill.

## Artifact

- Plan directory: `docs/plans/active/YYYY-MM-DD-<slug>/`.
  - `plan.md` — **mandatory** manifest (traceability + `## Scope` + `## Doc-change targets` + `## Deviations`).
  - `spec.md` / `design.md` / `tasks.md` — optional, created only when they have content; each declared in `plan.md`.

## Routing

- `ww-executing`.

## Key design decisions

- **Only `plan.md` is mandatory.** Optional files exist only when they have content and are declared in `## Doc-change targets`.
- **Doc-change targets drive archive.** For `spec.md` / `design.md`, state the canonical merge target and whether it is a new file or a section merge into an existing file; `tasks.md` is execution-only (not merged). `ww-archiving` reads this declaration to drive the intelligent merge.
- **Limited doc surface.** A Plan carries doc changes only to `docs/specs/`, `docs/design/`, and `architecture.md`. All other docs (constitution, glossary, conventions, contracts, experience, adr) are `ww-writing-doc`'s responsibility.
- **Greenfield invariant.** A Plan covering an area with no existing spec/design MUST carry both `spec.md` and `design.md`; code MUST NOT land for an undocumented area.
- **Spec vs design vs contracts.** Spec = what (requirements); design = how (internal shape, incl. `db-schema`); contracts = outward-facing agreements (maintained by `ww-writing-doc`, not carried by a Plan). Implementation detail belongs in `tasks.md`.
- **Task granularity.** Fine-grained, atomic; each task carries a verification method; prefer test-first for behavior-bearing tasks; prefer automated checks over manual inspection.
- **Gating.** Self-review default-on, skippable; user review is a HARD-GATE; commit default-on, skippable; handoff via `question`.

## Boundaries

- Does NOT write code.
- Does NOT edit canonical docs (`docs/specs/`, `docs/design/`, `architecture.md`) — notes revision suggestions instead.
- Does NOT touch constitution / glossary / conventions / contracts / experience / adr.
- Does NOT perform research — use a research skill.

## Hard constraints

- MUST create or modify ONLY files within the Plan directory.
- MUST keep only `plan.md` mandatory; optional files exist only with content and are declared in `plan.md`.
- MUST carry doc changes only to `docs/specs/`, `docs/design/`, `architecture.md`.
- Greenfield: MUST carry both `spec.md` and `design.md`.
- MUST NOT skip a gated step; MUST NOT commit without explicit approval.
