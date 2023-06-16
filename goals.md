# Goals

Sleuth's **Goals** dashboard, available for Standard an Enterprise plans, helps teams set, track and achieve their efficiency goals by:

* Allowing them to set actionable goals for Coding time, Review lag time, Review time, and Deploying time
* Automatically notifying PR owners and reviewers in real-time as they begin to drift from their goals
* Providing ongoing visibility into their progress toward achieving their goals over time

<figure><img src=".gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

### Sleuth-suggested goals

By default, the Goals dashboard is pre-populated with suggested goals that Sleuth calculates based on your team's historical performance. Suggested goals are calculated by taking your average performance for the selected time period and reducing it by 10% in order to drive improvement. &#x20;

Suggested goals are presented along with your historical metrics on greyed-out charts, and they will not send notifications to any users until you explicitly enable them.

### Enabling goals

To enable or modify a suggested goal, perform the following steps:

*   Click **Set goal.** A modal appears with the suggested goal pre-populated &#x20;

    <figure><img src=".gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>
* To modify the suggested goal, simply enter your own goal using the **Days**, **Hours**, and **Minutes** fields.
* To learn more about how to set up "nudge" notifications for a goal, refer to [Setting up "nudge" notifications](goals.md#setting-up-nudge-notifications-for-goals)
* Click **Save** to enable the goal. Once enabled, the goal chart appears in color, and the goal line updates from a dashed line to a solid line, indicating that the goal is now enabled.

### Interpreting goal charts

<figure><img src=".gitbook/assets/image (21).png" alt=""><figcaption><p>Enabled goals are color-coded to highlight the days on which the goal was or wasn't achieved</p></figcaption></figure>

In the screen shot above, the enabled goal is represented by the solid grey line.&#x20;

Each column on a goal chart represents the average value for the specific metric (in our example, Coding time) for all of the items that deployed on that day, and the columns are colored red or green according to whether or not the goal was achieved for that day.&#x20;

The main heading on the top-left of the chart summarizes the daily pass/fail data as an overall percentage of days passing in the selected period, and the sub-heading presents your overall average across the entire period in relation to the goal.

The chart also displays a solid blue line representing your trend over the selected time period, and the chart's footer provides commentary on how the direction of that trend compares to your overall average for the period.&#x20;

The Goals dashboard aims to answer the question "How have we been doing against the goals we've set?" Since each column on the goal charts represents the average for items that _deployed_ on that day, the Goals dashboard is inherently backward-looking. However, Sleuth continuously evaluates individual PRs against your goals in real-time, and if you've [set up "nudge" notifications](goals.md#setting-up-nudge-notifications-for-goals) for a goal, Sleuth will notify teams in real-time as PRs begin to approach the thresholds you've defined.&#x20;

### Setting up "nudge" notifications for goals

One of the most powerful features of Goals is the ability to set up automated Slack notifications that "nudge" teams as their individual PRs begin to approach the goals they've set. Goals do not include notifications by default, but you can easily set them up by performing the following steps:

*   For an already-enabled goal, click the ellipsis in the top-right of the chart and select "Edit goal". For a goal that has not yet been enabled, click "Set goal." Either action will present the settings modal for that goal:\


    <figure><img src=".gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>
* Expand the **Notification type** drop-down and select either "Smart escalations" or "Custom schedule"
  *   **Smart escalations:** This option will automatically send 2 progressively escalating notifications to the selected Slack channel. The first notification is sent at 75% of goal and doesn't specifically mention anyone. The second notification is sent at 90% of goal and @mentions the authors or reviewers on the PR (whichever is appropriate to the specific goal). \


      <figure><img src=".gitbook/assets/image (84).png" alt=""><figcaption></figcaption></figure>
  *   **Custom schedule:** This option allows you to schedule up to 5 notifications. Specify the elapsed **Days**, **Hours**, and **Minutes** when the first notification should be sent (this value must be less than the goal value, as the notification is intended to warn teams _before_ the goal has passed).To add additional notifications to the schedule, click **+ Add another notification**. \


      <figure><img src=".gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

The formatting for individual notifications varies slightly depending the goal type and whether they include @mentions or an @channel, but they all generally align to the following examples:

<figure><img src=".gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

### Disabling and re-enabling goals

Disabling a goal turns it back to grey-scale and pauses any notifications that have been set for it while preserving any goal or notification settings you've already specifie. This allows you to easily re-enable a goal with a single click.&#x20;

To disable a goal, click on the ellipsis and select **Disable goal**.

<figure><img src=".gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

To re-enable a disabled goal, click **Enable goal**.

<figure><img src=".gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

### Resetting goals and generating new suggestions

While disabling a goal preserves your goal settings, **Reset to default** generates a fresh goal suggestion and puts the goal back into its "default" state. Note that when a goal is in the default state, Sleuth will regenerate a fresh suggestion for that goal each time you load the Goals dashboard!
