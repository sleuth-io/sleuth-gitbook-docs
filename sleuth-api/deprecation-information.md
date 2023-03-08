---
description: Parts of the Sleuth GQL API currently in a deprecated state
---

# Deprecation information

This page lists all the fields in our GQL API that have been marked as deprecated along with suggestions on possible alternatives.

We will try to keep all these fields available for at least 3 months after they've been tagged deprecated. You're highly encouraged to update any code still using them to avoid issues once the deprecation period runs out and the fields are removed.

## 2023-03-08

* Field `org` was deprecated from object type `ContextType`. Use field `organization` on root query type instead.

## 2023-03-07

* Field `visibleOrganizations` was deprecated from object type `ContextType`. Use field `organizations` on type `UserType` instead.
* Field `visibleProjects` was deprecated from object type `ContextType`. Use field `projects` on type `OrganizationType` instead.

## 2023-03-06

* Field `user` was deprecated from object type `ContextType`. Use field `user` on root query type instead.
* Field `messages` was deprecated from object type `ContextType`. Use field `flashMessages` on root query type instead.
* Field `baseurl` was deprecated from object type `ContextType`. Use field `baseurl` on root query type instead.

## 2023-03-02

* Field `flags` was deprecated from object type `ContextType`. Use field `flags` on type `OrganizationType` instead.

## 2022-06-24

* Enum `OrderField` 's option `health` is deprecated. Use option `health_time` instead.
* Field `orgChanges` has the following arguments deprecated:&#x20;
  * `healths`, use `health_times` instead
  * `start_date`, use `start` instead
  * `end_date`, use `end` instead
* For the following fields the  arguments `start_date` and `end_date` are deprecated, use `start` and `end` instead:
  * `ProjectType.metricMTTR`&#x20;
  * `ProjectType.metricFrequency`
  * `ProjectType.metricLeadTime`
  * `ProjectType.metricFailureRate`&#x20;
  * `ProjectType.metricRecap`
  * `ProjectType.metricSlowestPrs`
  * `ProjectType.metricBiggestDeploys`
  * `ProjectType.metricTopUnhealthyDeploys`
  * `ProjectType.insights`

## 2022-06-07

* Field `impactHistory` was deprecated from object type `Environment`. Use field `healthEvents` instead.
* Field `impactHistory` was deprecated from object type `ChangeModelType`. Use field `healthEvents` instead.

## 2022-05-23

* Field `health` was deprecated from object type `ChangeType`. Use field `currentHealth` on type `Environment` instead.

## 2022-04-26

* Mutation `create_nr_integration` was deprecated. Use mutation `create_newrelic_integration` instead.
* Mutation `create_dd_integration` was deprecated. Use mutation `create_datadog_integration` instead.
