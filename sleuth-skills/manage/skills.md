---
description: >-
  Skills are named capabilities with a prompt, metadata, and optional bundled
  reference files. The AI client loads a skill when its description matches
  the user's goal.
---

# Skills

A **skill** is the most common asset type in Sleuth Skills. It is a self-describing capability that the AI client can load on demand when the user's request matches the skill's description.

## Directory layout

A skill is a directory containing at least one file — `SKILL.md` — with YAML frontmatter:

```
my-skill/
├── SKILL.md
└── references/
    ├── advanced-patterns.md
    ├── common-mistakes.md
    └── verification.md
```

The `SKILL.md` frontmatter is required:

```markdown
---
name: django-admin
description: >-
  Use this skill when creating or modifying Django admin interfaces, adding
  custom admin actions, configuring filters for large datasets, or debugging
  admin-related issues.
---

# Django Admin

## Prerequisites

- Model exists in `sleuth/apps/yourapp/models.py`
- Admin module exists or needs to be created at ...

## Quick Start
...
```

Reference files under `references/` (or any subdirectory) are not loaded into context by default — they're documents the skill can point the model to via Read. This keeps the skill's on-load token footprint small while leaving rich material available when needed.

## Writing an effective description

The `description` in the frontmatter is the single most important part of a skill. The client reads it when deciding whether to load the skill for a given user request; a vague description means the model will skip a perfectly applicable skill.

Good descriptions:

* **Lead with the trigger.** Start with "Use this skill when..." or "Triggered when...".
* **List concrete verbs.** "creating", "modifying", "debugging", not "working with".
* **Name the domain objects.** "Django admin interfaces", "GraphQL mutations", "webhook retries" — specific nouns help the model decide.
* **State boundaries.** If the skill is _only_ for Python or _only_ for a specific repo, say so.

Bad descriptions read like marketing copy: "A powerful skill for handling complex Django scenarios." That tells the model nothing.

## Creating a skill in Sleuth Skills

Three ways:

1. **Home-page assistant.** Describe what you want the skill to do; the assistant drafts `SKILL.md`, frontmatter, and any reference files.
2. **Create → Skill** from the top-right button.
3. **`sx add`** from the CLI:

   ```bash
   sx add ~/.claude/skills/django-admin
   ```

   `sx` detects the skill type from the presence of `SKILL.md`, bundles the directory into a `.zip`, and uploads it to the vault.

## Publishing

New skills start in **Draft**. When you're ready, open the asset detail page and set status to **Published**. Only published skills resolve during `sx install`.

## How the client loads a skill

When `sx install` places a skill in `.claude/skills/<name>/`, Claude Code discovers it on the next session and surfaces it in the skill picker. The client evaluates the frontmatter description against the user's prompt and loads the skill when the match is strong enough.

Other clients use the same directory layout where supported — see the [Welcome page](../README.md#supported-ai-clients) for the full compatibility matrix.

## Token cost

The asset detail page shows a **Token count** — the number of tokens the skill's `SKILL.md` contributes when loaded. References under `references/` are not counted because they load on demand.

Keep `SKILL.md` tight; stash detail in references. A 50k-token skill is expensive to load on every session where its description matches.
