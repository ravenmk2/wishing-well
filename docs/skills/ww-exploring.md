# Skill: ww-exploring

- **Skill**: `ww-exploring` (command `/ww-explore`)
- **Role**: Research phase — convergent.

## Purpose

Refine a roughly-formed idea into a scoped conclusion. Use when the direction is clear enough to converge but the boundaries (in/out) are not.

## Core principle

- **Converge on boundaries.** Resolve ambiguity; decide what is in and out of scope; align on requirements where useful.

## Source-of-truth stance

- Produces **no artifact**; touches **no truth**.
- The conclusion lives in the conversation; the routed skill persists what it needs.

## Artifact

- Scope conclusion: in/out boundaries, requirements where useful, intended doc changes (specs / domain design) if any.
- No file.

## Routing

- **documentation** → `ww-writing-doc`.
- **development** → `ww-planning`.

## Key design decisions

- **No file artifact.** Same rationale as brainstorming; persistence deferred to the routed skill.
- **One question at a time** via `question`. Resolve ambiguity incrementally.
- **Doc changes stay at requirements level** (specs) for documentation routing; technical detail belongs in design (downstream).
- **Distinct from brainstorming.** Exploring assumes the direction is clear enough to converge, not to diverge across alternatives.
- **Gating.** Self-review default-on, skippable; user review is a HARD-GATE.

## Boundaries

- Does NOT brainstorm divergent alternatives — use `ww-brainstorming`.
- Does NOT diagnose defects / performance issues — use `ww-analyzing`.
- Does NOT write Plans or docs.
- Does NOT touch any file.

## Hard constraints

- MUST touch no file.
- MUST NOT skip the user-review HARD-GATE.
