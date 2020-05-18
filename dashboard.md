---
description: 'Get a 30,000-foot view of your DevOps environment on the Sleuth Dashboard.'
---

# Dashboard

The **Dashboard** is Sleuth's command central. Sleuth aggregates all of the data your disparate tools generate and presents it to you in a clean, easy-to-use interface, as shown below. 

![](.gitbook/assets/dashboard-with-size.png)

All the data Sleuth collects about your code deployments is displayed in the Dashboard. The Dashboard is composed of the following elements: 

* **Sidebar** 🇦 

  The Sidebar provides quick access to your projects \(if you have more than one\), code deployments, feature flags, and impacts. 

* **Trend Graph** 🇧 

  A visual representation of the changes that have have been made over the selected time range.

* **Size/Leaderboard** 🇨 

  The [**Size**](integrations-1/terminology.md#size) graph gives you a quick way to see the average size of your deployments. The [**Leaderboard**](integrations-1/terminology.md#leaderboard) gamifies a team's deployment frequency, motivating you and your peers to make smaller deployments faster. 

* **Deploy Card** 🇩 

  A running list of your deploys, shown in chronological order. Direct links are provided to the corresponding repos, allowing you to quickly see what changes were made. The size of the deploy is also displayed. Collectively, the size of your deploys over the displayed time range impacts the size graph. Clicking on the commit hash will display more detailed information about all the events leading up to the deploy. [Learn more](integrations-1/terminology.md#deploy-cards) about deploy cards. 

* **Change Sources** 🇪 All of the sources of change connected to your project are displayed here. Collectively, all of the change sources combined drive the data shown in the main Trend Graph🇧.

