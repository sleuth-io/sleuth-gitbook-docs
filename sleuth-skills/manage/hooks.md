---
description: >-
  Hooks are shell commands the client runs in response to lifecycle events —
  before a prompt, after a tool call, on session exit, and similar.
---

# Hooks

A **hook** is automation wired to a client lifecycle event. When the event fires, the client runs the hook's configured shell command. Hooks are how you integrate the AI client with the rest of your developer workflow — start a dev server before a session, log tool usage to an external system, enforce pre-commit checks before a write.

## Events

The exact event catalog is client-specific; Claude Code's hooks (the reference implementation) include:

* `UserPromptSubmit` — fires when the user submits a prompt.
* `PreToolUse` / `PostToolUse` — fires before/after a tool call (Read, Edit, Bash, etc.).
* `SessionStart` / `SessionEnd` — session lifecycle.
* `Stop` — the assistant stopped producing output.

Other clients expose comparable events; Sleuth Skills maps hook definitions to each client's native format at install time.

## Directory layout

A hook is a directory with a `HOOK.md` (or `HOOK.json`) descriptor and optional helper scripts:

```
greeter/
├── HOOK.md
└── greet.sh
```

```markdown
---
name: greeter
description: Logs a greeting message to log.txt on every prompt submission.
events:
  - UserPromptSubmit
command: bash .claude/hooks/greeter/greet.sh
---
```

The `command` is run by the client's shell; it has access to the session's environment variables and whatever files the hook bundles.

## When to use a hook (and when not to)

Good hook use cases:

* Logging tool calls to a central observability pipeline.
* Running a lightweight lint or format check after the assistant writes a file.
* Enforcing a check before a destructive tool call (exit 1 blocks the call).

Avoid hooks for:

* **Long-running work.** Hooks block the event they're attached to. A five-second hook on `UserPromptSubmit` means a five-second delay on every prompt.
* **Anything the user can do from a command.** If a user might want to skip the behavior, a slash command is a better fit.

## Creating a hook

The usual three entry points: home-page assistant, **Create → Hook**, or `sx add ~/.claude/hooks/greeter`.

## Security

Hooks run arbitrary shell commands on the user's machine. Treat hook installs as code review:

* Prefer hooks with scripts bundled in the asset over hooks that `curl | bash` at runtime.
* Limit org-wide hook installs to well-reviewed assets.
* Use the [Audit Log](../govern/audit-log.md) to watch for hook installs you didn't authorize.

Hooks are one of the sharpest tools in the Sleuth Skills set; lock them down like you would any other shared piece of automation.
