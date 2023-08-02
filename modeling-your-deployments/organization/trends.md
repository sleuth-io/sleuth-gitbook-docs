# Trends

Sleuth's **Trends** dashboard allows you spot how your initiatives (projects, labels, or teams) are trending over time.

![](<../../.gitbook/assets/image (25) (1).png>)

You can use the date filter to see trends over the last two weeks, month, quarter or any custom date range you desire.&#x20;

Each of the four DORA metrics can be drilled into to see how each metric has broken down. If your MTTR is trending up over the period use the drill-downs to discover if it's an increase in Incidents, Rollbacks or some other cause.

Using the Trends dashboard coupled with [Labels](labels.md) and [Teams](../teams.md) allows you to see trends across any taxonomy within your Organization.

{% hint style="info" %}
Trends for all projects is available on all plans. Filtering by specific projects, labels, or teams requires being on an Enterprise plan.
{% endhint %}

### How is Failure rate calculated?

Each of the four bars represents a period. For each of the 4 periods Sleuth calculates failure rate across all projects. Assume for period 3 one has three projects with corresponding failure rates

* Project A: 30%
* Project B: 0%
* Project C: 0%

The resulting average for the period is somewhere around 10%. You can see this by hovering over independent bars.

![](<../../.gitbook/assets/image (85).png>)

The final number at the bottom represents the average across all four periods

![](<../../.gitbook/assets/image (86).png>)



## Further Reading

For additional information on how Sleuth calculates and "percent change" for the Trends dashboard and for other dashboards and views, see [Interpreting "Percent Change" in Sleuth](../../accelerate-metrics/how-we-calculate.md#interpreting-percent-change).
