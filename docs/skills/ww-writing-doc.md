# Skill: ww-writing-doc

- **Skill**: `ww-writing-doc` (command `/ww-write-doc`)
- **Role**: Documentation path — completion.

## Purpose

Write or update final-state docs directly from a research conclusion — for substantive documentation work. No Plan, no code.

## Core principle

- **Final-state truth, no in-flight split.** Docs read as current state (no change markers, no change history); `ww-writing-doc` lands live truth immediately on write.

## Source-of-truth stance

- Docs are the source of truth, immediately live on write.
- Spec governs **requirements**; design governs **internal shape** (incl. data structures); contracts govern **outward-facing agreements**; the charter (`constitution.md`) governs **principles**.
- No Plan, no deferred application. The change process is captured in ADRs (decisions) and git history; the docs themselves are final-state.

## Artifact

- Final-state docs under `docs/`: `constitution.md`, `glossary.md`, `architecture.md`, `conventions.md`, `contracts/`, `experience/`, `specs/`, `design/`, `adr/` (incl. `index.md`).
- ADR lifecycle updates + `docs/README.md` index mirroring.

## Routing

- Stop (no handoff).

## Key design decisions

- **Final-state prose.** Docs read as current state; change history lives in ADRs and git, not in the doc body.
- **ADR lifecycle.** Create `docs/adr/NNN-<slug>.md` (3-digit, zero-padded) with frontmatter `date` + `status: draft` → `accepted` on approval. Supersede: old ADR `status: superseded` + `superseded_by`; new ADR `supersedes`. `docs/adr/index.md` lists **only effective** (non-superseded) ADRs.
- **Append-only docs.** `glossary.md` and `experience/` MUST NOT delete entries; add new or revise definitions in place.
- **Project purity.** Docs MUST NOT reference the agent, skills, workflow, Plans, or any process — written as a human project author.
- **`references/` is user-maintained.** MUST NOT write to it.
- **Greenfield.** Establishing docs for a new area MUST produce both the spec (requirements) and the design (shape).
- **Granularity rules.** Default: one design doc per topic (`docs/design/<domain>/<slug>.md`). Split a concern out when it is large (>150 lines) and referenced elsewhere, cross-cutting, or has its own change cadence.
- **Spec vs design vs contracts.** See `ww-planning`; implementation detail belongs in a Plan's `tasks.md`, not in these docs.
- **Gating.** Self-review default-on, skippable; user review is a HARD-GATE (sets a new ADR's status to `accepted` on approval); commit default-on, skippable.

## Boundaries

- Does NOT write code.
- Does NOT touch Plans or `references/`.
- Does NOT carry doc changes as `spec.md` / `design.md` (that is the Plan's role in development).
- Does NOT introduce agent / skill / workflow / Plan / process references into docs.

## Hard constraints

- MUST create or modify ONLY files under `docs/` (incl. `docs/README.md` index).
- MUST keep `glossary.md` and `experience/` append-only.
- MUST NOT write to `references/`.
- Greenfield: MUST produce both spec and design.
- MUST keep docs project-pure.
- MUST NOT skip the user-review HARD-GATE; MUST NOT commit without explicit approval.
