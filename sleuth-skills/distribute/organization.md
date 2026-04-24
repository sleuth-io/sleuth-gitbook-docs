---
description: >-
  The root installation target. Every member of your Sleuth Skills vault
  belongs to exactly one organization; org-scoped installs reach everyone.
---

# Organization

The **Organization** is the outermost container in Sleuth Skills. It is created automatically when you first sign in and owns every other entity — users, bots, teams, repositories, assets, and the audit log.

<figure><img src="../../.gitbook/assets/skills/organization.png" alt=""><figcaption><p>The Organization page shows aggregate asset usage, the most popular assets, and the repositories connected to the org.</p></figcaption></figure>

## What you can do here

From the **Organization** entry in the Distribute section of the left nav you can:

* See aggregate asset usage over a time window (default: last 30 days).
* Browse the most popular assets across the whole org.
* Review connected repositories.
* Install an asset org-wide with **Install asset**.

## Org-wide installs

An asset installed at the organization level reaches every member of the vault, regardless of which repo they're working in.

Under the hood, an org install is equivalent to `sx install <asset> --org`. `sx` writes the asset to the user's _global_ client directory (`~/.claude/`, `~/.cursor/`, etc.), so it's available in every project they touch.

Use org installs for assets that are truly universal: company-wide coding standards, a shared code reviewer agent, or an MCP server that authenticates against internal services everyone uses.

## When not to use org scope

Org-scope is the wrong answer when:

* **The asset only applies to one codebase.** Org-scope pollutes every project's context with prompts that aren't relevant there. Use a [repository-scoped](repositories.md) install instead.
* **The asset is role-specific.** Frontend-focused rules don't belong in every backend engineer's global directory. Use a [team-scoped](teams.md) install so only the relevant people receive it.
* **You're still iterating.** Keep the asset as a [personal](personal.md) install until it's ready to share.

## Organization-level governance

Because the Organization is the root of the audit log and every usage metric, the **Govern** section of the left nav always shows organization-wide data by default. You can filter each dashboard down to a specific team, repository, or user from there.
