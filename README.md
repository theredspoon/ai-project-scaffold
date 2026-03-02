# ai-project-scaffold

The canonical starting point for AI-assisted projects. Provides the instruction file structure, adapter pattern, and task tracking conventions.

## What this contains

| File | Purpose |
| --- | --- |
| `AGENTS.md` | Fill in with project-specific content — this is the single source of truth |
| `CONTEXT.md` | Optional deep-background companion (domain knowledge, rationale, history) |
| `TASKS.md` | Task tracking template — clear the phases, keep the permanent sections |
| `CLAUDE.md` | Adapter for Claude Code — imports `AGENTS.md` |
| `.github/copilot-instructions.md` | Adapter for GitHub Copilot — kept alongside `AGENTS.md` because Copilot Code Review doesn't read `AGENTS.md` yet |
| `.cursor/rules/project.mdc` | Adapter for Cursor (always-on rule) |
| `.windsurfrules` | Adapter for Windsurf |
| `.gitignore` | Excludes `CLAUDE.local.md` and `.claude/settings.local.json` |

## How to use

1. Copy all files to the new project root.
2. Fill in `AGENTS.md` with project-specific content.
3. In `TASKS.md`, set the active project name and replace the placeholder phase with real phases.
4. Delete `CONTEXT.md` if you don't need a deep-background companion. Add it back when the project warrants it.

## Personal overrides

`CLAUDE.local.md` (gitignored) is for machine-specific or personal Claude Code preferences that shouldn't be shared. Create it at the project root as needed.

## Improving a pattern

Update this repo first, then propagate to active projects manually. Keeping this repo current is what makes new projects better than the last.
