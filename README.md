# `ai-project-scaffold`

The canonical starting point for AI-assisted projects. Provides the instruction file structure, adapter pattern, and task tracking conventions.

## What this contains

### Core project docs

- `README.md`: Human-facing overview of what the project is, how to use it, and what the important top-level files are for.
- `AGENTS.md`: Fill in with project-specific content. This is the single source of truth.
- `CONVENTIONS.md`: Universal style, git, and toolchain conventions read by all agents via `AGENTS.md`.
- `CONTEXT.example.md`: Tracked template for the deep-background companion. Copy to `CONTEXT.md` as the local durable-context file.

### Workflow tracking

- `TASKS.example.md`: Tracked template for live task and backlog tracking. Copy to `TASKS.md` for actual work.
- `PHASE_INBOX.example.md`: Tracked template for the live completed-phase inbox. Copy to `PHASE_INBOX.md` for actual work.
- `MILESTONES.example.md`: Tracked template for live milestone history. Copy to `MILESTONES.md` for actual work.

### Linting and local tooling

- `.vale.ini`: Vale prose linter configuration. Custom rules live in `styles/Scaffold/`.
- `.markdownlint.jsonc`: Shared markdownlint rules for consistent formatting across editors and models.
- `.lychee.toml`: Link checker configuration.
- `.mega-linter.yml`: MegaLinter CI configuration. Enables Vale, markdownlint, and lychee.
- `.githooks/`: Tracked local Git hooks for fast linting before commit or push.
- `.vscode/`: Shared VS Code workspace settings and recommended extensions for repo linting.
- `.github/workflows/lint.yml`: GitHub Actions workflow that runs MegaLinter on push and PRs.
- `.gitignore`: Excludes local-only override files, live tracker state, local durable context, and Vale sync packages.

### Local-only override templates

- `AGENTS.override.example.md`: Tracked example for creating a personal `AGENTS.override.md` file for Codex.

### Tool adapters

- `CLAUDE.md`: Adapter for Claude Code. Imports `AGENTS.md` and `CONVENTIONS.md`.
- `.github/copilot-instructions.md`: Adapter for GitHub Copilot. Kept alongside `AGENTS.md` because Copilot Code Review doesn't read `AGENTS.md` yet.
- `.cursor/rules/project.mdc`: Adapter for Cursor (always-on rule).
- `.windsurfrules`: Adapter for Windsurf.

## How to use

1. Copy all tracked files to the new project root.
2. Fill in `AGENTS.md` with project-specific content.
3. Create local working copies from the tracked templates: `TASKS.example.md` -> `TASKS.md`, `PHASE_INBOX.example.md` -> `PHASE_INBOX.md`, `MILESTONES.example.md` -> `MILESTONES.md`, and `CONTEXT.example.md` -> `CONTEXT.md`.
4. In the live `TASKS.md`, set the active project name, keep candidate work in `Backlog`, and replace the placeholder phase with a current phase plus any queued phases.
5. Use the live tracker files (`TASKS.md`, `PHASE_INBOX.md`, and `MILESTONES.md`) only for work that changes maintained project assets, such as code, documentation, configuration, tests, rules, or workflow. Lint-only cleanup with no behavior or meaning change is exempt. If entries remain unresolved after milestone review, leave them in `PHASE_INBOX.md` as orphan inbox entries and report them in the completion response until you explicitly defer, discard, merge, or promote them.

The live tracker files (`TASKS.md`, `PHASE_INBOX.md`, and `MILESTONES.md`) and local `CONTEXT.md` are intentionally local working state. The tracked `*.example.md` files are the public templates.

## Personal overrides

`CLAUDE.local.md` (gitignored) stores machine-specific or personal Claude Code preferences. Create it at the project root as needed.

`AGENTS.override.md` (gitignored) is the Codex equivalent. Start from `AGENTS.override.example.md`, rename it to `AGENTS.override.md`, and keep it local. Use it for personal overrides that shouldn't change the shared project rules in `AGENTS.md`.

## Local tooling

Three system-level linters, all installed via Homebrew:

| Tool | Purpose | Install |
| --- | --- | --- |
| [Vale](https://vale.sh) | Prose style | `brew install vale` |
| [markdownlint-cli2](https://github.com/DavidAnson/markdownlint-cli2) | Markdown structure | `brew install markdownlint-cli2` |
| [lychee](https://lychee.cli.rs) | Link checking | `brew install lychee` |

After installing, run `vale sync` to pull the Vale style packages (Google, alex, and write-good).

If you use VS Code, this repo also includes workspace settings in `.vscode/`:

- `settings.json` points the Vale extension at this repo's `.vale.ini`.
- `extensions.json` recommends the Vale and markdownlint extensions for local editing.

### Enabling local git hooks

This scaffold includes tracked hooks in `.githooks/` so copied projects can keep the
hook logic in version control. Enable them once per clone:

```bash
git config core.hooksPath .githooks
chmod +x .githooks/pre-commit .githooks/pre-push
```

`pre-commit` runs Vale and markdownlint only for staged markdown files.
`pre-push` runs lychee across the project.

### Running linters locally

```bash
vale .
markdownlint-cli2 .
lychee .
```

### CI

MegaLinter runs all three on push to main and on pull requests. Configuration lives in `.mega-linter.yml`.
Keep CI required in GitHub branch protection because contributors can still skip local hooks with `--no-verify`.

## Improving a pattern

Update this repo first, then propagate to active projects manually. Keeping this repo current is what makes new projects better than the last.

## Migrating older projects

For older projects that treated `CONTEXT.md` as the canonical instruction file:

1. Add this scaffold to the project root, or place it in a temporary top-level folder and merge the relevant patterns into the existing repo.
2. Move the binding rules, operating constraints, and document responsibilities into `AGENTS.md`.
3. Keep `CONTEXT.md` for durable background only: domain knowledge, rationale, accepted tradeoffs, and historical context.
4. Update tool-specific adapters to point at `AGENTS.md` as the canonical source of truth.
5. Keep the lint config files (`.vale.ini`, `.markdownlint.jsonc`, `.lychee.toml`, `.mega-linter.yml`) as portable contracts. Adopt the system-level tools or adapt the CI workflow to the destination project's existing setup.
6. Introduce local `TASKS.md`, `PHASE_INBOX.md`, and `MILESTONES.md` working copies only when the destination project uses the scaffold's phase-tracking workflow.

### Reusable migration prompt

Paste this into a large language model (LLM) after you add this scaffold to an existing project directory:

```text
You are helping migrate an existing project to adopt the most relevant patterns from the included `ai-project-scaffold` folder.

Context:
- The existing project is the primary codebase and remains authoritative for its product, runtime, and existing toolchain.
- The `ai-project-scaffold` folder is a reference repo containing process, documentation, and agent-workflow patterns.
- Do not treat the scaffold as something to copy wholesale.
- Your job is to merge only the best-fitting patterns from the scaffold into the existing project, preserving the existing project's architecture, package manager, conventions, and operational reality.

Primary objective:
- Analyze both the existing project and the `ai-project-scaffold` folder.
- Propose and implement a migration that brings over the most useful workflow, documentation, and agent-guidance patterns from the scaffold.
- Adapt the scaffold patterns to the host project instead of forcing the host project to conform to the scaffold mechanically.

Important constraints:
- The existing project's current package manager and toolchain take precedence. Do not introduce `bun`, `npm`, `uv`, or any other tool unless it matches what the host project already uses or I explicitly approve it.
- Do not replace or overwrite the host project's source of truth until you have mapped the current equivalent files and confirmed the migration path.
- Do not copy scaffold-local maintenance tooling blindly. For example, if the scaffold has local lint tooling for maintaining itself, treat that as a pattern to adapt only if it makes sense in the host project.
- Prefer incremental migration in clearly separated phases.
- Preserve any host-project-specific documentation, constraints, and conventions that are still valid.
- Avoid destructive changes. If migration would remove or replace existing project files, explain the impact first.

What to inspect first:
1. The host project's current top-level docs and instruction files.
2. The `ai-project-scaffold` folder contents, especially:
   - `AGENTS.md`
   - `CONVENTIONS.md`
   - `TASKS.example.md`
   - `CONTEXT.example.md`
   - `PHASE_INBOX.example.md`
   - `MILESTONES.example.md`
   - `README.md`
   - `.markdownlint.jsonc`
   - any tool-specific adapter files
3. Any existing equivalents in the host project, such as:
   - agent instruction files
   - project conventions or style guides
   - task tracking docs
   - changelog, history, or milestone docs
   - markdown lint config
   - editor or CI lint setup

Migration goals:
- Determine which scaffold files should become first-class docs in the host project.
- Determine which scaffold patterns should be merged into existing host-project docs instead of added as new files.
- Establish a single canonical source of truth for agent instructions in the host project.
- Clarify the responsibilities and boundaries of each documentation file the host project should keep.
- Add or adapt task-tracking workflow only if it fits the host project's actual workflow.
- Add or adapt markdown linting rules only in a way that fits the host project's existing toolchain and editor or CI setup.
- Preserve portability and avoid introducing scaffold-specific complexity that the host project does not need.
- Do not treat routine project outputs or generated deliverables as tracker workflow state unless the host project explicitly treats them as maintained assets.

Required process:
1. First, perform a comparison between the host project and the scaffold:
   - identify equivalent files
   - identify missing capabilities
   - identify conflicts
   - identify scaffold features that should not be adopted
2. Then propose a phased migration plan with:
   - each phase name
   - what it delivers
   - expected touched files
   - risks or compatibility concerns
3. Then stop and show me the plan before doing broad migration, unless the work is obviously small and isolated.
4. After approval, implement the migration phase by phase.
5. For each completed phase:
   - validate the changes at the appropriate level
   - summarize what changed
   - note any follow-up work or unresolved decisions

How to decide what to migrate:
- Prefer patterns that improve clarity, maintainability, and agent consistency.
- Prefer adapting responsibilities and workflow concepts over copying file text verbatim.
- Only add docs that are operationally useful in the host project.
- If the host project already has a good equivalent, merge the relevant scaffold ideas into it instead of creating duplicates.
- If a scaffold feature depends on process overhead the host project does not need, skip it.
- If a scaffold feature conflicts with the host project's current runtime or toolchain, adapt it to the host project's existing tooling.

Specific migration guidance:
- If the host project currently uses `CONTEXT.md` as the main instruction file, migrate canonical agent rules into `AGENTS.md` and keep `CONTEXT.md` for durable background, rationale, and history only.
- If the host project already has tool-specific instruction files, convert them into adapters that point to the new canonical source where appropriate.
- If the host project already has task tracking, integrate the useful `TASKS.md` concepts instead of replacing the current system blindly.
- If the host project does not need `PHASE_INBOX.md` or `MILESTONES.md`, say so explicitly rather than forcing them in.
- If the host project already has markdown linting, merge the useful rule deltas from `.markdownlint.jsonc` into the host project's existing config instead of creating parallel configs.
- If the host project lacks markdown linting but should have it, propose the lightest-weight adoption path using the host project's existing package manager or editor workflow.

Deliverables I want from you:
- A migration assessment: what maps cleanly, what conflicts, what should be skipped
- A proposed phased plan
- Recommended final documentation structure for the host project
- The actual file edits, once approved
- A validation summary after each phase

When uncertain:
- Prefer preserving the host project's current behavior and toolchain.
- Prefer fewer, clearer docs over more docs.
- Ask whether a scaffold feature is worth adopting if it seems high-overhead or weakly relevant.

Start by comparing the host project root against the `ai-project-scaffold` folder and produce the migration assessment plus proposed phases.
```
