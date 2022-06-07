---
description: Parts of the Sleuth GQL API currently in a deprecated state
---

# Deprecation information

This page lists all the fields in our GQL API that have been marked as deprecated along with suggestions on possible alternatives.

We will try to keep all these fields available for at least 3 months after they've been tagged deprecated. You're highly encouraged to update any code still using them to avoid issues once the deprecation period runs out and the fields are removed.

## 2022-06-07

* Field `impactHistory` was deprecated from object type `Environment`. Use field `healthEvents` instead.
* Field `impactHistory` was deprecated from object type `ChangeModelType`. Use field `healthEvents` instead.

## 2022-05-23

* Field `health` was deprecated from object type `ChangeType`. Use field `currentHealth` on type `Environment` instead.

## 2022-04-26

* Mutation `create_nr_integration` was deprecated. Use mutation `create_newrelic_integration` instead.
* Mutation `create_dd_integration` was deprecated. Use mutation `create_datadog_integration` instead.
