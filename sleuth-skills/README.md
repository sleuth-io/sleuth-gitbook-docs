---
description: >-
  Sleuth Skills is a hosted vault for your team's AI assets — skills, rules,
  agents, commands, hooks, MCP servers, and Claude Code plugins. Manage them in
  the web UI at skills.new; distribute them with the sx CLI; govern them with
  a central audit log and usage metrics.
---

# Welcome to Sleuth Skills

Your best engineers have figured out how to make AI assistants incredibly productive — custom skills, agents, MCP configs, coding rules. But that knowledge usually lives on one laptop. Sleuth Skills ([skills.new](https://skills.new)) turns those private discoveries into team assets that everyone inherits automatically.

<figure><img src="../.gitbook/assets/skills/home.png" alt=""><figcaption><p>The Skills.new home screen, organized around Manage, Distribute, and Govern</p></figcaption></figure>

## How Sleuth Skills is organized

Everything in the product falls into one of three workflows, and the left-hand navigation reflects that split:

| Workflow | What you do here | Where it lives |
|----------|------------------|----------------|
| **Manage** | Create, edit, version, and review AI Assets (skills, rules, agents, commands, hooks, MCP servers, Claude Code plugins). | `AI Assets`, `Change Requests` |
| **Distribute** | Choose _who_ gets each asset: your whole organization, specific repositories, teams, bots, or an individual person. | `Installed`, `Organization`, `Bots`, `Teams`, `Repositories`, `Personal` |
| **Govern** | See what is being adopted, by whom, and on which repositories — plus an append-only audit trail of every install and team change. | `Audit Log`, `AI Metrics`, `Adoption`, `Usage`, `Leaderboards` |

Sleuth Skills is the hosted vault; the [`sx`](https://github.com/sleuth-io/sx) CLI is the distribution runtime. Users run `sx install` in their project directory and `sx` resolves what should be installed for them — based on the scopes configured in Skills.new — and writes the right files into `.claude/`, `.cursor/`, or any other supported client's directory.

## Where to go next

* **New here?** Start with the [Quick Start Guide](quick-start.md) — create an asset, install it, verify it's running.
* **Setting up distribution?** Read [Installation Targets](installation-targets/README.md) to pick the right scope for each asset.
* **Creating assets?** See [Assets](assets/README.md) for the structure and metadata each type expects.
* **Tracking adoption?** Jump to [Governance](governance/README.md) for the audit log and usage dashboards.

## Supported AI clients

Sleuth Skills is client-agnostic. Assets are distributed through `sx`, which writes to the directory each client expects. Current support matrix:

| Client | Asset types supported |
|--------|-----------------------|
| Claude Code | All |
| Cursor | Skills, rules, commands, MCP servers, hooks |
| GitHub Copilot | Skills, rules, commands, agents, MCP servers, local hooks |
| Gemini (CLI / VS Code) | Skills, rules, commands, MCP servers, hooks |
| Gemini (JetBrains) | Rules, MCP servers |
| Codex | Skills, commands, MCP servers |
| Cline | Skills, rules, workflows, MCP servers, hooks |
| Kiro | Skills, rules, commands, MCP servers |
