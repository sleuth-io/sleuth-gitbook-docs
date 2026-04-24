---
description: >-
  MCP servers package Model Context Protocol server definitions so the client
  can launch and talk to them. Use them to give AI clients structured access
  to internal APIs, databases, and custom tools.
---

# MCP servers

An **MCP server** asset packages a [Model Context Protocol](https://modelcontextprotocol.io) server definition — how to launch it, what tools it exposes, and any credentials or configuration it needs. When installed, the client picks up the server definition and can call the server's tools from any session.

MCP is how you extend the AI client's tool set beyond the built-ins: give Claude Code structured access to your internal incident tracker, your feature-flag system, your staging database, or anything else you can wrap in an MCP server.

## Directory layout

An MCP asset is a directory with an `MCP.md` (or `MCP.json`) manifest:

```
hi-dylan/
└── MCP.md
```

```markdown
---
name: hi-dylan
description: This MCP server returns the greeting "Hi Dylan!" when invoked.
type: stdio
command: node
args: ["server.js"]
env:
  NODE_ENV: production
---
```

Or the JSON form for the same thing:

```json
{
  "name": "hi-dylan",
  "type": "stdio",
  "command": "node",
  "args": ["server.js"],
  "env": {
    "NODE_ENV": "production"
  }
}
```

`type` is one of:

* `stdio` — the client launches the server as a subprocess and talks over stdin/stdout.
* `http` — the client connects to an HTTP endpoint.
* `sse` — server-sent events over HTTP.

## Installing an MCP server

An installed MCP asset is written to the client's MCP config (Claude Code: `.claude/mcp.json` or `~/.claude/mcp.json` for org scope). The client will launch or connect on the next session.

## Credentials

Most interesting MCP servers need credentials — an API token, a database password, an OAuth token. Sleuth Skills treats the MCP manifest as a template; user-scope credentials should come from the invoker's environment (env vars, credential helpers) rather than being baked into the asset. The manifest can reference required env vars:

```markdown
---
name: incident-tracker
type: stdio
command: incident-mcp
env:
  INCIDENT_TOKEN: "${INCIDENT_TOKEN}"
---
```

`sx install` substitutes env var references at install time against the user's environment. Missing env vars produce a warning — the install still succeeds, but the server may fail to launch.

## Experimental status

MCP support in `sx` and Sleuth Skills is marked **experimental** in the `sx` roadmap: the spec is young, client implementations vary, and the Sleuth Skills ingestion surface is still evolving. Expect the packaging format to tighten over the next few releases; early adopters should pin to specific asset versions and watch the changelog.

## Client compatibility

MCP is supported in Claude Code, Cursor, GitHub Copilot, Gemini (CLI / VS Code / JetBrains, Android Studio with HTTP-only transport), Codex, Cline, and Kiro. The transport support per-client is noted in the compatibility table on the [Welcome page](../README.md#supported-ai-clients).

## Discovering servers

[skills.sh](https://skills.sh) lists community MCP servers alongside skills and rules. `sx add --browse` will surface them with the same metadata.
