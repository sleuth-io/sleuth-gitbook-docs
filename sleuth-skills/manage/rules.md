---
description: >-
  Rules are coding standards and guidelines that the client applies based on
  file type or path. Unlike skills, rules do not wait to be triggered —
  they're always on when their scope matches.
---

# Rules

A **rule** codifies a standard, convention, or constraint that should apply automatically whenever the client is working in a matching context — a file type, a directory, or a whole repository.

Where a [skill](skills.md) loads when its description matches the user's goal, a rule loads when its scope matches the current file or context. Rules are the "standing orders" of the AI client.

## When to use a rule

* Enforcing a coding convention: "Always use pytest with database reuse. Mock external HTTP calls with vcrpy."
* Requiring a specific pattern: "When adding a new Django model, also update the factories module and write a migration test."
* Reminding the client to load another asset: "Load the `frontend-design` skill whenever editing files under `frontend/`."

## Directory layout

A rule follows the same packaging conventions as a skill — a directory with a markdown file and frontmatter. The convention is `RULE.md` with a `description`, plus optional scope metadata:

```markdown
---
name: testing
description: >-
  Enforce testing best practices: load the test-writer skill, use pytest with
  database reuse, leverage fixtures and factories, and mock external calls
  with vcrpy.
globs: "**/*.py"
---

# Testing rules

- Use pytest with `--reuse-db` unless migrations changed.
- Prefer factories (`factory_boy`) over ad-hoc dict fixtures.
- Mock HTTP calls with `vcrpy`; commit cassettes alongside tests.
- Load the `test-writer` skill when writing new tests.
```

`globs` tells the client which files the rule applies to. It maps to Cursor's rule-glob format and the equivalents in other clients.

## Rules vs skills

| | Skill | Rule |
|--|-------|------|
| Loading trigger | Description matches user prompt | Scope (file type / path) matches current context |
| On by default? | No — model decides | Yes — whenever scope matches |
| Typical content | How to _do_ a task | What to _always_ remember or enforce |
| Typical size | 1–10k tokens | A few hundred tokens |

If you find yourself writing a rule that's 20k tokens long, you probably want a skill referenced _by_ a short rule instead.

## Creating a rule

Same three entry points as any other asset: the home-page assistant, the **Create → Rule** button, or `sx add ~/.cursor/rules/testing`.

## Client compatibility

Rules are supported in Claude Code, Cursor, GitHub Copilot, Gemini (CLI / VS Code / JetBrains / Android Studio), Cline, and Kiro. The rule file lands under each client's rules directory (e.g. `.cursor/rules/`, `.claude/CLAUDE.md` fragments) at install time.

## Discovered rules

Sleuth Skills can discover existing rules in connected repositories and offer to promote them to vault-managed assets. The Asset list marks these entries with `Source: <repo>` so you know where they came from. This is the fastest way to bring pre-existing `.cursor/rules/` and `.github/copilot-instructions.md` into central management.
