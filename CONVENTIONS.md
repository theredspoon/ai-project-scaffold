# Conventions

Universal conventions for this project. Apply to all content generated, regardless of tool.

---

## Markdown

The lint-enforceable markdown rules for this repository live in `.markdownlint.jsonc`.

**Fenced code blocks:** Use `text` for directory trees, file paths, terminal output, plain prose, and anything that isn't a recognized format. When in doubt, `text` is always valid.

**Tables:** Use compact style with single-space padding inside each cell, leading and trailing pipes.

```text
| Column A | Column B |
| --- | --- |
| value | value |
```

Never use aligned style (padding cells to align columns) or tight style (no spaces around content).

**Blockquotes:** Prefix every line with `>`, including blank lines between paragraphs or speaker turns. Keep this as human guidance; `markdownlint` catches some malformed blockquote cases but doesn't fully encode this exact style rule.

---

## Prose

The deterministic prose rules for this repository live in `.vale.ini` and `styles/`.

- Use the Oxford comma.
- Reserve ellipsis for genuine omission or trailing-off.
- Passive voice is acceptable when the agent is genuinely unknown or irrelevant.
- Present tense for documentation and instructions.
- Front-load the point.
- One idea per sentence in instructional or reference writing.
- Sentence case for headings unless the project has an established pattern.

---

## Git

- Format: Conventional Commits, `type(scope): description` (for example, `feat(auth): add login`, `fix: handle null`)
- Subject line: imperative mood, lowercase after the type prefix, 72-character limit
- Body: only when the why isn't self-explanatory from the subject
- No emoji in commit messages
- Stop at commit. Don't push or open PRs unless explicitly asked.

---

## Toolchain

- **JavaScript/TypeScript:** Use `bun` for new projects (runtime, package manager, test runner). For existing npm projects, stay with npm and don't migrate.
- **Python:** Use `uv` (`uv add`, `uv run`, `uv sync`). Don't use pip or Poetry for new projects.
- For existing projects: follow whatever is already in place.
