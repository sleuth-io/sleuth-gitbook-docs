---
description: Parts of the Sleuth GQL API currently in a deprecated state
---

# Deprecation information

This page lists all the fields in our GQL API that have been marked as deprecated along with suggestions on possible alternatives.

We will try to keep all these fields available for at least 3 months after they've been tagged deprecated. You're highly encouraged to update any code still using them to avoid issues once the deprecation period runs out and the fields are removed.

## 2022-05-23

Field `health` on `ChangeType` has been marked as deprecated.

To get detailed information on specific deploy health, you can use the `healthTimeBreakdown` field on that same object.

To get the health state of an environment, you can use the `currentHealth` field on `Environment` objects.

## 2022-04-26

Mutation fields `create_nr_integration` and `create_dd_integration` have been marked as deprecated.

This was just a rename, those same fields are now available as `create_newrelic_integration` and `create_datadog_integration`.
