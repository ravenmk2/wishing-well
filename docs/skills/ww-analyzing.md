# Skill: ww-analyzing

- **Skill**: `ww-analyzing` (command `/ww-analyze`)
- **Role**: Research phase — diagnostic.

## Purpose

Diagnose a defect or performance issue: reproduce, locate root cause, define the fix area. Use when the symptom is known but the cause is not.

## Core principle

- **Diagnosis, not the fix.** Reproduce with evidence, isolate variables, hypothesize, verify; produce a diagnosis that scopes the fix area. The fix itself is planned and executed downstream.

## Source-of-truth stance

- Produces **no artifact**; touches **no truth**.
- The conclusion lives in the conversation; the routed skill persists what it needs.

## Artifact

- Diagnosis conclusion: root cause + fix area + intended doc changes (e.g. an ADR) if any.
- No file.

## Routing

- **development** → `ww-planning` (default; usually no doc changes).
- **documentation** → `ww-writing-doc` — only when the root cause reveals a spec/design gap warranting a doc decision.

## Key design decisions

- **Diagnosis ≠ fix.** The fix belongs to `ww-planning` / `ww-executing`; analyzing MUST NOT start coding.
- **Evidence-based root cause.** Verified against evidence, not a guess; symptom reproduced or performance issue characterized with measurements.
- **Default routing is development.** The fix will be implemented; documentation routing is the exception (spec/design gap → ADR).
- **Gating.** Self-review default-on, skippable; user review is a HARD-GATE.

## Boundaries

- Does NOT brainstorm a direction — use `ww-brainstorming`.
- Does NOT converge a rough idea — use `ww-exploring`.
- Does NOT write Plans or docs.
- Does NOT touch any file or start the fix.

## Hard constraints

- MUST touch no file.
- MUST NOT start the fix — diagnosis belongs to `ww-planning` / `ww-executing`.
- MUST NOT skip the user-review HARD-GATE.
