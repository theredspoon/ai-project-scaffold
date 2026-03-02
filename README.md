# ai-project-scaffold

The canonical starting point for AI-assisted projects. Provides the instruction file structure, adapter pattern, and task tracking conventions.

## What this contains

| File | Purpose |
| --- | --- |
| `CONTEXT.md` | Fill in with project-specific content — this becomes the single source of truth |
| `TASKS.md` | Task tracking template — clear the phases, keep the permanent sections |
| `AGENTS.md` | Adapter for Codex, Amp, and other AGENTS.md-compatible tools |
| `CLAUDE.md` | Adapter for Claude Code |
| `.github/copilot-instructions.md` | Adapter for GitHub Copilot |
| `.cursor/rules/project.mdc` | Adapter for Cursor (always-on rule) |
| `.windsurfrules` | Adapter for Windsurf |

All adapter files redirect to `CONTEXT.md`. They never need to change.

## How to use

1. Copy all files to the new project root.
2. Replace `CONTEXT.md` content with project-specific information.
3. In `TASKS.md`, set the active project name and replace the placeholder phase with real phases.

## Improving a pattern

Update this repo first, then propagate to active projects manually. Keeping this repo current is what makes new projects better than the last.
