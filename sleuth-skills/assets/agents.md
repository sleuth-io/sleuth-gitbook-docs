---
description: >-
  Agents are autonomous AI workers with a specific goal — reviewing a branch,
  writing tests, investigating a bug. Published agents become invokable from
  any installed client.
---

# Agents

An **agent** is a self-contained autonomous worker packaged as a Sleuth Skills asset. Agents have a clear goal, the tools they need to pursue it, and an entry-point prompt that defines their persona and constraints. Where a skill is a capability the model _can_ load, an agent is something you _invoke_ to do a piece of work end-to-end.

## Typical agents

From the home page's Popular list you can see what teams actually deploy:

* **reviewer** — Reviews code changes on a branch with senior-architect rigor. Catches bugs, enforces quality, validates architecture.
* **fix-pr** — Takes a failing PR and walks its review comments, build failures, and planned fixes until it's ready to merge.
* **test-writer** — Writes a missing or failing test for a piece of code.

## Directory layout

An agent is a directory with an `AGENT.md` entry point and any supporting files:

```
reviewer/
├── AGENT.md
├── checklist.md
└── examples/
```

The frontmatter describes when the agent should be available:

```markdown
---
name: reviewer
description: >-
  Reviews code changes on a branch with senior architect rigor. Catches bugs,
  enforces quality, validates architecture, and blocks security/performance
  regressions before merge.
tools: [Read, Grep, Bash]
---

# Reviewer agent

You are a senior architect reviewing a branch. Goals:
1. Identify correctness bugs.
2. Flag performance and security regressions.
...
```

`tools` optionally restricts which tools the agent is allowed to use — useful for locking a review agent to read-only operations, or a fix-pr agent to a specific subset.

## Agents vs skills

Both are discovered via their `description`, but the contract is different:

* A **skill** adds a capability to the main session. The model decides when to load it and uses it as one tool among many.
* An **agent** is spawned as its own session with a narrow goal. It has its own context window, its own system prompt, and returns a result to the caller.

Pattern to remember: _skill = reference manual; agent = hired contractor._

## Invoking an agent

Claude Code exposes installed agents through the `Agent` tool — the calling session picks an agent by name and hands off the task. Other clients expose agents via their own mechanisms (subagent spawning, task-runner flows).

You can also invoke an agent directly from the Sleuth Skills home-page assistant — it routes "use the reviewer agent on branch X" to the appropriate invocation.

## Tools, permissions, and context

An agent's `tools` list is a floor, not a ceiling: the invoking session can further restrict what the agent can do based on its own permission mode. Keep the `tools` list as narrow as the agent needs — an agent that doesn't write files should not list `Edit` or `Write`.

## Token economics

Agents burn their own context window on every invocation, which can be expensive. Three habits help:

* Keep the agent's `AGENT.md` lean — push long reference material into files the agent can Read on demand.
* Scope each agent to one goal. A "do everything" agent is hard to prompt well and wastes tokens.
* Use `sx stats` (CLI) or the **AI Metrics** dashboard (UI) to spot agents with lots of invocations but low output signal — those are candidates for pruning or rewriting.
