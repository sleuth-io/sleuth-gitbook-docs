---
description: >-
  Sleuth Skills is where your team creates, reviews, and governs the AI assets
  — skills, rules, agents, commands, hooks, MCP servers, and Claude Code
  plugins — that make every engineer more productive.
---

# Welcome to Sleuth Skills

Your best engineers have figured out how to make AI assistants incredibly productive — custom skills, agents, MCP configs, coding rules. But that knowledge usually lives on one laptop. Sleuth Skills ([skills.new](https://skills.new)) turns those private discoveries into team assets that everyone inherits automatically.

<figure><img src="../.gitbook/assets/skills/home.png" alt=""><figcaption><p>The Skills.new home screen, organized around Manage, Distribute, and Govern</p></figcaption></figure>

Sleuth Skills is the **application your team works in every day** — a web app at [skills.new](https://skills.new) where you author assets, review your teammates' edits, target who receives what, and see what's actually being used. It's where the whole asset lifecycle lives: from "someone wrote a useful skill" to "the right engineers are using it and we can prove it."

## How Sleuth Skills is organized

Everything in the product falls into one of three workflows, and the left-hand navigation reflects that split:

| Workflow | What you do here | Where it lives |
|----------|------------------|----------------|
| **Manage** | Create, edit, version, and review AI Assets (skills, rules, agents, commands, hooks, MCP servers, Claude Code plugins). Configure RBAC and approve Change Requests. | `AI Assets`, `Change Requests` |
| **Distribute** | Choose _who_ gets each asset: your whole organization, specific repositories, teams, bots, or an individual person. | `Installed`, `Organization`, `Bots`, `Teams`, `Repositories`, `Personal` |
| **Govern** | See what is being adopted, by whom, and on which repositories — plus an append-only audit trail of every install and team change. | `Audit Log`, `AI Metrics`, `Adoption`, `Usage`, `Leaderboards` |

For the **Distribute** side, Sleuth Skills uses the [`sx`](https://github.com/sleuth-io/sx) CLI as its delivery runtime. When an engineer runs `sx install` in a project, `sx` talks to Skills.new, resolves what should be installed for that user and that repository, and writes the right files into `.claude/`, `.cursor/`, or the relevant client directory.

## Where to go next

* **New here?** Start with the [Quick Start Guide](quick-start.md) — create an asset, install it, verify it's running.
* **Creating or editing assets?** See [Manage](manage/README.md) for RBAC, asset lifecycle, and each asset type.
* **Setting up distribution?** Read [Distribute](distribute/README.md) to pick the right installation target for each asset.
* **Tracking adoption?** Jump to [Govern](govern/README.md) for the audit log and usage dashboards.

## Supported AI clients

Sleuth Skills is client-agnostic and works in two modes:

* **CLI-installed clients** use [`sx install`](https://github.com/sleuth-io/sx) to write assets into the client's configuration directory on the developer's machine. This covers every local or IDE-based client.
* **Web clients** (claude.ai and chatgpt.com) can't be written to from the CLI. Instead, Sleuth Skills exposes your org's assets to them through a hosted **MCP shim** — configure the shim once in the web client's MCP settings and your assets are available in every conversation.

| Client | Delivery | Asset types supported |
|--------|----------|-----------------------|
| Claude Code | `sx` | All |
| claude.ai | MCP shim | Skills, agents, commands, MCP tool calls |
| chatgpt.com | MCP shim | Skills, agents, commands, MCP tool calls |
| Cursor | `sx` | Skills, rules, commands, MCP servers, hooks |
| GitHub Copilot | `sx` | Skills, rules, commands, agents, MCP servers, local hooks |
| Gemini (CLI / VS Code) | `sx` | Skills, rules, commands, MCP servers, hooks |
| Gemini (JetBrains) | `sx` | Rules, MCP servers |
| Codex | `sx` | Skills, commands, MCP servers |
| Cline | `sx` | Skills, rules, workflows, MCP servers, hooks |
| Kiro | `sx` | Skills, rules, commands, MCP servers |
