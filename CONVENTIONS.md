# Conventions

Universal conventions for this project. Apply to all content generated, regardless of tool.

---

## Markdown

**Fenced code blocks:** Always specify a language. Never leave a fence untagged.

- Use the actual language for code: `python`, `bash`, `typescript`, `json`, `yaml`, `sql`, `css`, `html`, etc.
- Use `text` for directory trees, file paths, terminal output, plain prose, and anything that isn't a recognized format.
- When in doubt, `text` is always valid.

**Tables:** Compact style — single space padding inside each cell, leading and trailing pipes.

```text
| Column A | Column B |
| --- | --- |
| value | value |
```

Never use aligned style (padding cells to align columns) or tight style (no spaces around content).

**Blockquotes:** Prefix every line with `>`, including blank lines between paragraphs or speaker turns.

**Headings vs. emphasis:** Never use bold or italic on a line by itself as a substitute for a heading. Use `##`, `###`, etc. for section titles. Bold and italic are for inline emphasis only.

---

## Git

- Format: Conventional Commits — `type(scope): description` (e.g. `feat(auth): add login`, `fix: handle null`)
- Subject line: imperative mood, lowercase after the type prefix, 72-character limit
- Body: only when the why isn't obvious from the subject
- No emoji in commit messages
- Stop at commit. Do not push or open PRs unless explicitly asked.

---

## Toolchain

- **JavaScript/TypeScript:** Use `bun` for new projects (runtime, package manager, test runner). For existing npm projects, stay with npm — don't migrate.
- **Python:** Use `uv` (`uv add`, `uv run`, `uv sync`). Do not use pip or Poetry for new projects.
- For existing projects: follow whatever is already in place.
