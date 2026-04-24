---
description: >-
  Claude Code plugins bundle skills, commands, hooks, and MCP configs into a
  single installable unit. Use them when a product feature needs all four
  types deployed together.
---

# Claude Code plugins

A **Claude Code plugin** is a bundle. It packages multiple asset types — skills, commands, hooks, MCP servers — into one installable unit, so engineers can pick up the whole feature in a single install rather than chasing four separate assets.

This is the shipping format for anything that feels like "a product feature" rather than "a single capability."

## When to use a plugin

* You're shipping a themed set: a Django plugin that includes `django-admin`, `django-models`, `django-migrations`, plus a `/django-shell` command and an MCP server for querying the staging DB.
* You want one audit event per install, not one per bundled asset.
* You're mirroring a Claude Code community plugin that ships this way upstream.

If your bundle is only one type deep — all skills, all commands — consider whether you really need the wrapping, or whether publishing the individual assets with sensible names is cleaner.

## Directory layout

A plugin is a directory with a `plugin.json` (or `PLUGIN.md` with YAML frontmatter) at the root, plus the bundled assets in subdirectories:

```
devtools/
├── plugin.json
├── skills/
│   ├── code-review/
│   │   └── SKILL.md
│   └── test-writer/
│       └── SKILL.md
├── commands/
│   └── review/
│       └── COMMAND.md
├── hooks/
│   └── pre-commit/
│       └── HOOK.md
└── mcp/
    └── staging-db/
        └── MCP.md
```

```json
{
  "name": "devtools",
  "description": "Team-wide dev tools: code review, test writing, pre-commit checks, staging DB access.",
  "version": "1.2.0"
}
```

## Installation

Installing a plugin installs every bundled asset. The audit log records a single plugin install event plus one install event per bundled asset, so you can see both the high-level and detailed views.

`sx install <plugin-name>` resolves to the same scope rules as any other asset — you can target an org, a team, a repo, a path, a bot, or a personal install.

## Discovering plugins

Claude Code has an official plugin ecosystem. Sleuth Skills can mirror plugins from Claude's plugin registry:

```bash
sx add code-review@claude-plugins-official
```

This pulls the plugin into your vault at its current version and makes it available for installation with your scope rules.

## Versioning

Plugins are versioned as a unit. Bumping the plugin version typically also bumps the bundled assets' versions. The asset detail page shows the plugin's active version; each bundled asset inherits that version for its own installation record.

## When to split a plugin back into pieces

Plugins are convenience, not magic. If half your team loves the skills in a plugin but never uses the MCP server, consider extracting the MCP server as a standalone asset and letting teams install it separately. The **Adoption** dashboard is the best signal — if the plugin's aggregate usage is good but individual bundled assets are wildly imbalanced, that's a sign to decompose.
