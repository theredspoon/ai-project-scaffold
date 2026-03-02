# Context

> This file is the single source of truth for this project.
> `AGENTS.md`, `CLAUDE.md`, and all tool-specific instruction files redirect here.

This repository is the canonical template for AI-assisted projects. Copy its files when starting a new project to get AI instruction scaffolding, multi-tool adapters, and task tracking conventions pre-wired.

---

## Constraints (CRITICAL)

- This repo contains templates only. Do not add project-specific work here.
- Changes here affect all future projects started from this scaffold — edit with that in mind.
- Substantive rules belong in `CONTEXT.md` only. Adapter files stay thin.

---

## Boundaries

Always:

- Keep template files project-agnostic.
- Preserve the adapter pattern: every tool-specific instruction file redirects to `CONTEXT.md`.
- Confirm before any destructive or irreversible action.

Never:

- Add project-specific tasks, environment details, or credentials to this repo.
- Duplicate rules across adapter files. One source, many pointers.

---

## Doc Type Responsibilities

**CONTEXT.md** — single source of truth for a project. Defines what the project is, its constraints, boundaries, and conventions. All AI tool files redirect here.

**TASKS.md** — active and deferred work tracking. Completed tasks are removed when done. Structural `[PERMANENT]` sections are never removed.

---

## Conventions

- **Starting a new project:** Copy all files to the new project root. Fill in `CONTEXT.md` with project-specific content. Adapter files require no changes.
- **Improving a pattern:** Update this repo first, then propagate to active projects manually.
- **Logbooks and runbooks:** Add them if the project warrants it. See `docfiles-private` for reference templates.

---

## Non-Goals

- Not a code scaffold. Instruction files only.
- Not tool-specific. All substantive rules live in `CONTEXT.md`; adapters contain no independent content.

---

## External References

| Resource | Purpose |
| --- | --- |
| [docfiles-private](../docfiles-private) | Infrastructure project using this pattern — reference implementation |
