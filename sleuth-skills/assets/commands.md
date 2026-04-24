---
description: >-
  Commands are explicit slash commands the user types. They are the right tool
  when you want a named shortcut with predictable behavior, not a
  description-triggered skill.
---

# Commands

A **command** is a slash command the user invokes directly (e.g. `/flush-toilet`, `/review`, `/fix-pr`). Commands are the fastest way to give your team a named shortcut: deterministic, discoverable, and cheap because they only load when explicitly run.

## When to use a command vs a skill

* **Command** — the user knows what they want. They'd like a short name that produces a predictable behavior. Example: `/review` always runs the same review flow on the current branch.
* **Skill** — the user describes a task in their own words and the model chooses what to load. Example: "Help me refactor this view into a class-based admin." The `django-admin` skill might load automatically.

A command is "I know what I want, give me a shortcut." A skill is "Here's what I'm trying to do, figure out how."

## Directory layout

A command is a directory with a markdown entry point and frontmatter:

```
flush-toilet/
└── COMMAND.md
```

```markdown
---
name: flush-toilet
description: Prints ASCII art of a flushing toilet.
---

Print this ASCII art verbatim:

```
  _____
 |     |
 |  ~  |
 |_____|
```
```

Commands typically stay small — most are under 1k tokens. Heavy behavior belongs in a skill the command can reference.

## Arguments

Commands can take arguments from the user. The client parses `/command-name <args>` and passes the rest of the line into the command's prompt as a variable (Claude Code uses `$ARGUMENTS`, Cursor and GitHub Copilot have analogous mechanisms).

A command that accepts a branch name might look like:

```markdown
---
name: review
description: Review the named branch for bugs, quality, and architecture issues.
---

Run a senior-architect review of branch `$ARGUMENTS`. Check:
1. Correctness bugs
2. Performance regressions
3. ...
```

## Creating a command

Same as any asset: home-page assistant, **Create → Command**, or `sx add ~/.claude/commands/flush-toilet`.

## Client compatibility

Commands are first-class in Claude Code (as slash commands under `.claude/commands/`), Cursor, GitHub Copilot, Gemini CLI, Cline (as workflows), Kiro, and Codex. Each client renders commands in its own picker or slash menu.

## Discoverability

Commands show up in the client's slash menu on install. The description field is what the user sees when typing `/`; write it as a command-line helper would — short, in imperative form, says what you get.
