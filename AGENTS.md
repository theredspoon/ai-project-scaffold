# Agents

> This file is the single source of truth for this project.
> `CLAUDE.md` and all tool-specific instruction files redirect here.
> Also read `CONVENTIONS.md` — universal style, git, and toolchain conventions.

[One sentence: what this project is and what it does.]

---

## Constraints (CRITICAL)

IMPORTANT: [The rule that must never be broken, stated explicitly.]

- [Additional binding constraints.]

---

## Boundaries

Always:

- Confirm before any destructive or irreversible action.
- Use `TASKS.md` only to track work that changes maintained project assets, such as code, documentation, configuration, tests, rules, or workflow. Do not use it for operational steps or generated outputs unless those outputs are themselves maintained assets.
- Before starting any non-trivial work that changes maintained project assets, record it in `TASKS.md` as an active phase with what it delivers, the files or folders the phase is likely to affect, and the remaining items in `Tasks:`. Minor isolated edits, such as one-off typo or formatting fixes, do not require a phase. In `Expected Touches:`, do not include tracking workflow files unless the work is modifying their expected behavior.
- Mark a phase complete in `TASKS.md` before moving to the next task. Do not batch updates.
- [Add always-do rules.]

Never:

- [Add never-do rules.]

---

## Scope Escalation Protocol

When beginning work, if initial assessment reveals the actual scope materially exceeds what the request implied, then STOP.

**Trigger:** Any of the following discovered on first pass:

- The artifact is significantly larger, more broken, or more complex than the request suggested
- Completing the request requires substantial investigation or remediation before the actual ask can begin
- The work contains multiple independently deliverable phases — each could be completed, reviewed, and validated before the next begins

Stop at the first signal — you do not need to fully understand the scope before surfacing it.

**Response:**

1. Stop — do not open more files, run commands, or continue exploring
2. Write to `TASKS.md`: what you found, proposed phases, what each delivers
3. Tell the user: the discovery, how it changes scope, what's in `TASKS.md`
4. Wait for explicit confirmation before starting any phase

---

## Tracking Workflow

The tracking workflow means routine maintenance of project-tracking files: updating active phases in `TASKS.md`, archiving completed phases into `PHASE_INBOX.md`, and consolidating history into `MILESTONES.md`.

Changes made only to support that workflow should not be treated as file touches worth recording unless the work is also modifying the expected behavior of those files.

---

## Validation

- Validate work at the level that best proves the active phase outcome defined in `TASKS.md`, not necessarily at the level of each checklist item.
- For code changes: use the strongest relevant checks available for the scope and risk of the change, such as targeted tests, integration tests, linting, builds, or manual execution. Do not assume each checklist item needs its own test; prefer validation that covers meaningful behavior, risk boundaries, or end-to-end outcomes, even when that spans multiple checklist items.
- For documentation changes: validate that the document fulfills its intended purpose, that required information is present, that unnecessary or misplaced content is not included, and that related documents remain aligned.
- For mixed changes: validate both the behavior and the documentation updates.
- If existing validation is insufficient, add or extend validation when that is reasonably within scope. When that requires non-trivial additional work, track it explicitly in the active phase in `TASKS.md`.
- In the completion response: state what validation was performed, whether it passed or what gaps remain, what it confirms, and any follow-up work still needed.

---

## Milestone Recording

- `MILESTONES.md` stores consolidated, outcome-level project history, not a verbatim phase archive.
- After the Wrap Protocol archives a completed phase into `PHASE_INBOX.md`, assess the new inbox entry together with any related unconsolidated inbox entries and the current contents of `MILESTONES.md`.
- Decide whether the completed work should update an existing milestone, create a new milestone, or remain unresolved for now.
- Prefer updating an existing milestone when adjacent phases contribute to the same higher-level outcome.
- Create a new milestone only when completed work represents a distinct, meaningful result worth preserving on its own.
- If one or more entries remain unresolved after milestone review, leave them in `PHASE_INBOX.md` as orphan inbox entries.
- If orphan inbox entries remain, state that explicitly in the completion response, including the orphan count and the phase names when useful.
- When orphan inbox entries remain, offer the user clear next actions: defer (leave them unresolved for now), discard, merge, or promote.
- Remove inbox entries only when they have been consolidated into `MILESTONES.md`, intentionally discarded, or otherwise explicitly resolved.
- In milestone entries: summarize the meaningful outcome, keep `Actual Touches:` only when it materially helps future review, exclude files touched only by the tracking workflow, and note validation or follow-up work only when it adds lasting value.

---

## Structure

- `[path/]` — [what lives here and why]

---

## Commands *(code projects — remove for ops, docs, or business projects)*

- Build: `[command]`
- Test: `[command]`
- Lint: `[command]`

---

## Document Responsibilities

List only operationally important document types here. A document type is a role a file plays in the project, not a list of every file in the repo. Include files agents must consult or update to do work correctly, and files whose boundary with another document is easy to confuse. For each listed document, name it, state what it stores, and state when it should be updated.

- `README.md` is the human-facing onboarding document. It explains what the project is, how to use it, and what the important top-level files are for. Update it when project purpose, setup, usage, workflow, or top-level structure changes.
- `TASKS.md` tracks current execution only. Keep it focused on active work, live deferred items, open questions, and assumptions. Remove completed phase detail once the phase is finished.
- `PHASE_INBOX.md` stores completed phases copied from `TASKS.md` as a temporary pre-consolidation execution record. Append a phase when it is removed through the Wrap Protocol, using the phase name as the heading, adding a `Completed:` date, and replacing `Expected Touches:` with `Actual Touches:` for the files or folders changed for reasons unrelated to the expected behavior of the tracking workflow. Leave unresolved entries here as orphan inbox entries until they are explicitly resolved.
- `MILESTONES.md` stores consolidated milestone-level history. Update it after the Wrap Protocol when the milestone guidance in this file indicates the newly archived phase, together with any related entries in `PHASE_INBOX.md`, should create or update a milestone.
- `CONTEXT.md` stores durable project memory, including implementation rationale, accepted tradeoffs, intentional omissions, and the conditions that should trigger revisiting a past decision.
- `AGENTS.md` stores stable operating rules, scope boundaries, and project-level constraints.

---

## Conventions

See `CONVENTIONS.md` for universal style, git, and toolchain conventions.

- [Project-specific naming conventions, file organization.]

---

## Non-Goals

- [What this project explicitly does not do.]

---

## External References

| Resource | Purpose |
| --- | --- |
| | |
