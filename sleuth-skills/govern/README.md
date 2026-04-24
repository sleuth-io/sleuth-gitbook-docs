---
description: >-
  Sleuth Skills keeps an append-only audit log of every install and team
  change, plus pre-built dashboards that show what your org is actually using.
---

# Govern

Once you have assets published and distributed, the question becomes: _is anyone actually using them, and can I reconstruct what happened?_ Sleuth Skills answers both through the **Govern** pillar.

<figure><img src="../../.gitbook/assets/skills/home.png" alt=""><figcaption><p>The Govern section — Audit Log, AI Metrics, Adoption, Usage, and Leaderboards.</p></figcaption></figure>

## The two governance surfaces

| Surface | Question it answers | Page |
|---------|---------------------|------|
| [Audit log](audit-log.md) | _Who changed what, and when?_ | Installs, uninstalls, team and bot changes, asset publications — every mutation. Append-only. |
| [Usage metrics](metrics.md) | _Who is actually using these assets?_ | Pre-built dashboards for adoption, top assets, per-team rollups, leaderboards. |

The audit log is the compliance record — it's what you reach for during an incident review or a security question. The usage dashboards are the adoption signal — they tell you which assets are earning their keep.

## Pre-built and custom dashboards

Under **Usage metrics**, Sleuth Skills ships four pre-built dashboards — **AI Metrics**, **Adoption**, **Usage**, and **Leaderboards** — plus a fifth **Start from scratch** option for building your own. You can clone any preset into a new custom dashboard and extend it, add widgets backed by PQL queries, or ask the assistant to generate persistent charts and tables from a natural-language prompt. See [Usage metrics](metrics.md#custom-dashboards) for the full walkthrough.

## Why both matter

Governance often means "compliance checkbox," but in Sleuth Skills the two surfaces work together to support real engineering decisions:

* A skill has low usage in the dashboard. Check the audit log — was it actually installed for the people who would benefit?
* A new rule went out org-wide and errors spiked. The audit log tells you when and who; the usage dashboard tells you whether engineers are bypassing or following it.
* Someone reports a surprising behavior. The audit log reconstructs the exact set of installs at that moment.

## Default filters

Every Govern surface defaults to the organization scope and the last 30 days. You can narrow to a specific team, repository, user, or asset type using the **Add filter** control at the top of each page. The dashboards respond immediately; the audit log supports the same filters plus free-text event search.

## Export

Both the audit log and dashboard data can be exported. The audit log has an **Export CSV** button in its header; dashboard widgets can be exported as CSV or cloned into a custom dashboard for sharing.

The CLI counterpart — `sx audit --json` and `sx stats --json` — returns the same data for git and path vaults; the Skills.new hosted vault delegates those commands to the server's aggregation API.
