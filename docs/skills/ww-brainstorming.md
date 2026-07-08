# Skill: ww-brainstorming

- **Skill**: `ww-brainstorming` (command `/ww-brainstorm`)
- **Role**: Research phase — divergent.

## Purpose

Surface genuinely distinct alternatives for an undecided direction, then converge on a decision. Use when the direction deserves open exploration (architecture/future decisions, "should we adopt X", "which approach for Y").

## Core principle

- **Diverge before converge.** Offer multiple distinct alternatives; make trade-offs visible; do not anchor on the first option.
- **Converge only on a chosen alternative + rationale.** A still-divergent state is not a conclusion.

## Source-of-truth stance

- Produces **no artifact**; touches **no truth**.
- The conclusion lives in the conversation; the routed skill persists what it needs.

## Artifact

- Decision conclusion: chosen alternative + rationale + intended doc changes (global design / ADR) if any.
- No file.

## Routing

- **documentation** → `ww-writing-doc`.
- **development** → `ww-planning` — **only** when the conclusion contains a chosen alternative. If still divergent, loop back to divergence or stop.

## Key design decisions

- **No file artifact.** Brainstorming is exploration, not truth-writing; persistence is deferred to the routed skill.
- **One question at a time** via `question`. Let each answer shape the next; avoids over-constraining the user.
- **Work-kind is open; research kind is fixed.** Only the work-kind (documentation / development) is determined during the skill; the research kind (brainstorming) is given.
- **Planning routing is gated on convergence.** A still-divergent conclusion MUST NOT route to `ww-planning`.
- **Gating.** Self-review default-on, skippable; user review is a HARD-GATE.

## Boundaries

- Does NOT converge a rough idea into scope — use `ww-exploring`.
- Does NOT diagnose defects / performance issues — use `ww-analyzing`.
- Does NOT write Plans or docs.
- Does NOT touch any file.

## Hard constraints

- MUST touch no file.
- MUST NOT route to `ww-planning` with a still-divergent conclusion.
- MUST NOT skip the user-review HARD-GATE.
