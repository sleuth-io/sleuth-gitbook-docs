---
description: >-
  Sleuth Skills exposes both a REST API and a GraphQL API at app.skills.new.
  Use them to drive the same actions your engineers take in the web app —
  authoring assets, resolving installs, downloading bundles, and recording
  usage.
---

# API

Sleuth Skills ([skills.new](https://skills.new)) is API-first. Every action you can take in the web UI — listing the assets installed for a user, downloading a skill bundle, creating a bot, recording a usage event — is also available over HTTP.

There are two surfaces:

| Surface | Base URL | Use it for |
|---------|----------|------------|
| **REST** | `https://app.skills.new/api/skills/` | Asset distribution: lock-file resolution, version listing, bundle download, upload, profile selection, usage reporting. This is what `sx` calls. |
| **GraphQL** | `https://app.skills.new/graphql` | Everything else: managing assets, bots, profiles, installations, change requests, audit log, AI metrics. This is what the web UI calls. |

Both surfaces share the same authentication model — an org-scoped credential identifies the caller, and the credential type (user OAuth token, organization API key, or bot API key) determines what the caller can see and do.

## Quick orientation

* **Bot API keys** are the recommended credential for unattended automation. Issue one per bot, scope it to that bot's teams, and rotate without downtime. See [Authentication](authentication.md).
* **`sx` itself is just a REST client.** Everything `sx install`, `sx update`, and `sx vault` do is a documented call against the REST API on this page — see [REST API](rest.md).
* **GraphQL is introspectable.** Open [https://app.skills.new/graphql](https://app.skills.new/graphql) while signed in to explore the full schema in GraphiQL. See [GraphQL API](graphql.md) for the high-level shape.

## Where to go next

* [Authentication](authentication.md) — API keys, bot keys, and how to pass them.
* [REST API](rest.md) — every endpoint `sx` and CI agents use.
* [GraphQL API](graphql.md) — the management surface for assets, bots, profiles, and metrics.

{% hint style="info" %}
This API is for the **Sleuth Skills** product at skills.new. If you're looking for the DORA / deployment-tracking API at app.sleuth.io, see [Sleuth API](../../sleuth-api/README.md) instead.
{% endhint %}
