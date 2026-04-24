---
description: >-
  The core domain model of Sleuth Skills. An installation target answers
  "who gets this asset?" — Organization, Team, Repository, Bot, or Personal.
---

# Installation Targets

Every asset in Sleuth Skills is published once and then _installed_ to one or more **targets**. A target is the entity an installation attaches to; when someone runs `sx install`, the CLI resolves the set of assets that apply to them based on these targets.

## The five targets

Sleuth Skills has five installation targets, visible as five entries under the **Distribute** section of the left navigation.

| Target | Who it applies to | Typical use |
|--------|-------------------|-------------|
| [Organization](organization.md) | Every member of the vault. | Coding standards, company-wide rules, a shared code-reviewer agent. |
| [Teams](teams.md) | All members of a named team, plus its member bots and repositories. | Role-specific assets — the SRE team's runbook skill, the Frontend team's React review rules. |
| [Repositories](repositories.md) | Anyone running `sx install` inside a clone of the specified repository. | Repo-specific skills: Django admin patterns for the monolith, Terraform rules for infra. |
| [Bots](bots.md) | A service account that can be a member of teams and have assets installed directly. | CI agents, scheduled cleanup bots, review bots. |
| [Personal](personal.md) | A single user. Does not affect teammates. | Your own experimental skills before sharing them with the team. |

## The hierarchy

Teams are the only target that composes other targets:

```
Organization
└── Teams
    ├── Members (users)
    ├── Bots
    └── Repositories
```

When you install an asset to a **team**, `sx` flattens that into installs for every member, every bot, and every repository on the team. This makes teams the natural unit of distribution once you move past "global" and "one repo."

## Resolution order

`sx install` asks: _given this user, this repo, and this session, which assets apply?_ The answer walks the targets in this order:

1. **Organization** — always applied. Writes to the user's global client directory (e.g. `~/.claude/`).
2. **Team** (via membership) — applied if the user is a member of a team that has the asset installed. Flattens to repo-scoped installs for each of the team's repositories.
3. **Repository** — applied if `sx install` is run inside a clone of a repository that has the asset installed. Writes to `<repo>/.claude/`.
4. **Path** (subset of repository) — applied if the current directory is under one of the paths configured in the install. Writes to `<repo>/<path>/.claude/`. Useful for monorepos.
5. **Personal (user scope)** — applied to the caller's global client directory when their git identity matches the configured user email.

If an asset has no active install on any of these targets, `sx install` will not write it.

## Changing targets

Every target change — adding a user to a team, switching an asset from org-wide to repo-scoped, promoting a member to admin — is recorded in the [Audit Log](../governance/audit-log.md). Target changes are also idempotent: re-adding an existing member or re-installing with the same scope is a silent no-op that does not rewrite state or emit noise into the audit trail.
