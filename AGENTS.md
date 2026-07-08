# AGENTS.md

Wishing Well is a set of agentic coding extensions for OpenCode, including agents, skills, commands, scripts and more.

## Repository Layout

```txt
wishing-well/
├── AGENTS.md
├── README.md
├── LICENSE
├── skills/
├── commands/
└── docs/
    ├── design/
    │   └── doc-model.md
    ├── references/
    │   └── opencode-<slug>.md
    └── skills/
```

## Conventions

### Artifact Writting

- **Language:** All artifacts MUST be written in English.
- **Style:** Writing SHOULD be structured, precise, and concise. Prefer lists, tables, and mermaid diagrams over verbose paragraphs.
- **Terminology:** Use ONLY industry-standard professional terminology; MUST NOT invent, fabricate, or repurpose terms in non-standard ways.
- **Requirement Levels:** RFC 2119 keywords (MUST, SHOULD, MUST NOT, SHOULD NOT, etc.) SHOULD be used to clearly express requirement levels.

## Hard Constraints

- MUST treat this repo as a normal codebase.
- `docs/` is this repo's SSOT.
- Commit only after user approval, never commit unprompted.

## Alignment Workflow

This dev repo SHOULD follow a docs-led maintenance model: the human reviews and modifies `docs/`; the agent aligns artifacts to match.

### Consistency Checks

- Every `skills/<name>/SKILL.md` has a matching `docs/skills/<name>.md`, and vice versa.
- SKILL.md Hard constraints MUST NOT contradict the design doc's Hard constraints.
