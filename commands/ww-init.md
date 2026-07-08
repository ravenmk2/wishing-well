---
description: Bootstrap the docs/ foundation — AGENTS.md, docs/README.md index, and the full doc structure; greenfield gets empty stubs, brownfield generates content per-doc interactively.
---

You are initializing this project's documentation foundation. `AGENTS.md` foregrounds `docs/constitution.md` and points to `docs/README.md` — no workflow instructions, no skill or command names. The workflow is driven by installed skills, not by `AGENTS.md`.

Follow these steps in order.

### 1. Explore the codebase

Thoroughly explore the repo: README, package manifest / build files / lockfiles, source tree, tests, CI config, existing `docs/` and `AGENTS.md`. Determine whether this is **greenfield** (little or no existing code/docs) or **brownfield** (existing codebase). Build a picture of: what the project is, its purpose, primary language/framework, architecture shape, tech stack, build/test/lint/run commands, and any existing specs/design/adr/plans.

### 2. Draft the doc foundation

Draft `AGENTS.md`, `docs/README.md`, and the doc structure. The mode (greenfield vs brownfield) shapes how the doc content is produced.

**`AGENTS.md`** (both modes) — foregrounds `docs/constitution.md` and points to `docs/README.md`:

```
# <Project>

<one-sentence project description>

`docs/constitution.md` is the project charter — purpose, principles, invariants. Read it first; it governs all work.

Read `docs/README.md` for the documentation index and build/test/lint commands.
```

No workflow instructions, no skill/command names.

**`docs/README.md`** — a one-sentence project description + a documentation index (a nested list mirroring the `docs/` tree, each entry with a one-line description) + a build/test/lint commands block. For greenfield, the commands block is a placeholder: `> TODO: document build/test/lint commands.`

**Greenfield** — create the full structure with empty (heading-only) stubs and empty directories. The structure MUST be preserved even where content is absent:

- `docs/constitution.md`, `docs/glossary.md`, `docs/architecture.md`, `docs/conventions.md` — heading-only stubs (e.g. `# Constitution\n`).
- `docs/experience/pitfalls.md` — heading-only stub.
- `docs/adr/index.md` — stub: `# Architecture Decision Records\n\nNo decisions yet.\n`.
- `docs/contracts/`, `docs/specs/`, `docs/design/`, `docs/references/` — empty directories (`.gitkeep`).
- `docs/plans/active/`, `docs/plans/completed/` — empty directories (`.gitkeep`).

**Brownfield** — interactive per-doc proposal: for each inferable doc (`architecture.md`, `conventions.md`, `glossary.md`, `contracts/api.md`), draft content from the codebase and propose it to the user one at a time via `question` (approve / adjust / skip). If `specs/` or `design/` content can be inferred from the code, propose those too; otherwise leave the directories empty. For non-inferable docs (`constitution.md`, `experience/pitfalls.md`) and `docs/adr/index.md`, create heading-only stubs. Create the empty directories (`contracts/`, `specs/`, `design/`, `plans/active/`, `plans/completed/`, `references/`) with `.gitkeep`.

### 3. Self-review — default on, skippable

Ask via `question` whether to skip self-review (`yes` / `no`). If `no`, check: `AGENTS.md` foregrounds `docs/constitution.md` and points to `docs/README.md` (no workflow / skill / command names); `docs/README.md` has the index + commands block; greenfield has the full stub structure; brownfield has stubs for non-inferable docs; empty directories have `.gitkeep`; nothing is written under `references/`. Fix the drafts, then summarize.

### 4. User review — HARD-GATE

Present the drafted `AGENTS.md`, `docs/README.md`, and the doc structure (stubs + any generated content) together via `question` (one batched confirmation: approve all, or specify adjustments). You MUST NOT create or modify any file until the user explicitly approves. On requested changes, update and re-present. Loop until approval.

### 5. Write

Once approved, write all the files and create the directories.

### 6. Git commit — default commit, skippable

Ask via `question` whether to skip the commit (`yes` / `no`). If `no`, stage only the created/modified files, propose a message, confirm files + message with the user, then commit. MUST NOT commit without explicit approval.

$ARGUMENTS
