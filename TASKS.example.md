# Tasks

## Execution Instructions `[PERMANENT]`

### Before Starting

1. ALWAYS read `AGENTS.md` first. Treat it as binding constraints.
2. ALWAYS assess scope against the request before starting work. If initial assessment reveals the artifact is significantly larger, more broken, or more complex than the request implied — follow the Scope Escalation Protocol in `AGENTS.md` before doing anything else.
3. ALWAYS check this file for the current active phase, deferred items, open questions, and assumptions.
4. ALWAYS record work that changes maintained project assets as a phase before starting it. See AGENTS.md Boundaries section for exemptions.

### During the Phase

1. ONLY work within the scope defined in the active project.
2. NEVER remove any part of a section marked [PERMANENT], including any nested subsections within it.
3. ALWAYS mark completed items in `Tasks:` as complete. If the result creates durable rationale worth preserving, move that rationale to `CONTEXT.md`.
4. ALWAYS track any non-trivial validation work required to satisfy the validation requirement in the active phase.
5. ALWAYS check, before treating a phase as complete, whether the phase changed project purpose, setup, usage, workflow, or top-level structure. If so, update `README.md`.

### After Completing the Phase

#### Before the Wrap Protocol

1. ALWAYS validate completed work at the appropriate level of abstraction for the type of change made, following the `Validation` guidance in `AGENTS.md`, and report the validation result in the completion response.

#### Wrap Protocol

1. ALWAYS copy the completed phase to `PHASE_INBOX.md`, using the phase name as the heading, adding a `Completed:` date, and replacing `Expected Touches:` with `Actual Touches:` for the files or folders changed for reasons unrelated to the expected behavior of the tracking workflow.
2. ALWAYS remove the completed phase from `TASKS.md`.
3. ALWAYS ensure the next phase is present above `Phase Template` and keep working if more work remains.
4. ALWAYS reset `TASKS.md` to its template state by keeping only sections marked `[PERMANENT]` and their nested subsections if no more work remains.

#### After the Wrap Protocol

1. ALWAYS assess whether the newly archived phase and any related entries in `PHASE_INBOX.md` should update `MILESTONES.md`, following the milestone guidance in `AGENTS.md`.
2. ALWAYS remove `PHASE_INBOX.md` entries once they have been explicitly resolved.
3. ALWAYS report orphan inbox entries in the completion response when one or more entries remain unresolved after milestone review, including the orphan count and available next actions: defer (leave them unresolved for now), discard, merge, or promote.
4. ALWAYS provide a concise summary of changes made in the completion response after completing a phase.

---

## Active Project `[PERMANENT]`: [project name]

---

## Phase Template `[PERMANENT]`

Create real active phases above this section while work is in progress, and remove them only through the Wrap Protocol. Use this shape for each one.

```markdown
## Phase N — [Phase Name]

Delivers: [What this phase produces.]

Expected Touches:
- [files or folders changed for reasons unrelated to the expected behavior of the tracking workflow]

Tasks:
- [ ] [checklist item that may include the file or folder target for clarity]
```

---

## Deferred Decisions `[PERMANENT]`

Decisions intentionally postponed and expected to be revisited during upcoming work. Review when planning a phase that could be affected, and before final validation. Do not store settled decisions or historical rationale here.

| Decision | Context | Resolve Before |
| --- | --- | --- |

---

## Deferred Behaviors `[PERMANENT]`

AI behaviors to activate or deactivate once a condition is met.

| Behavior | Condition | Status |
| --- | --- | --- |

---

## Open Questions `[PERMANENT]`

Things that need investigation before they can become decisions.

| Question | Why It Matters | Owner |
| --- | --- | --- |

---

## Assumptions `[PERMANENT]`

Believed to be true but not yet validated. Track to avoid silent drift.

| Assumption | Impact if Wrong | Validate By |
| --- | --- | --- |
