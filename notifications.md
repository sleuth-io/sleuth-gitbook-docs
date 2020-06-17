# Notifications

In addition to the available [Chat Ops](integrations-1/chat-ops/) integrations, Sleuth can notify you and your team when something happens with your source of change, including sending targeted messages for your entire team or just yourself. You can notify all team members on every deploy or just yourself once a week. You can also 

### Setting up Slack notifications

Before you set up project-level Slack notifications, the [Slack integration](integrations-1/chat-ops/slack.md#about-the-integration) must be made the Sleuth organization level first. Once that's done, you can configure who and how those notifications are sent and who receives them. 

#### To set up Slack change notifications for the project

1. Select a project in the sidebar, then click **Project Settings**. 
2. Click **Slack Notifications**. 
3. In the _Slack channel_ dropdown, start typing the name of the Slack channel that will receive change notifications. If the channel is private, you will need to invite the _Sleuth bot_ to the channel first.  ![](.gitbook/assets/slack-config-channels.png) 
4. Click **Save**. 

At this point you can notify users in your Slack organization that a notifications channel for this project has been set up and that they should join it to receive any and all change notifications that occur in that project. 

#### To set up custom Slack notifications for yourself 

In the previous section you created a project-level Slack notification. Team members will only receive change notifications if they join the corresponding Slack channel. However, you might want customized notifications sent directly to yourself. You can do this by configuring your user-level Slack notifications preferences: 

1. Select your username in the bottom of the sidebar, then click **Manage Account**. 
2. Click **Notifications**. 
3. Any [email notifications]() you've already setup will be displayed here. Enable the **Slack notifications** toggle. 
4. You can enable or disable **Deployed code** and/or **Impact of your Code**:
   * **Deployed code**: Selecting **All** means you will receive a Slack notification every time code in which you are the author is deployed.  Selecting **Exclude my deployments** notifies you of all deployments except those in which you're the author. This option is great if you're up to speed on your own code but want to keep tabs on how the rest of your team's deployments are doing. 
   * **Impact of your Code**: Selecting **All** means you will always receive a Slack notification about the impact of your code on the rate of production errors.  Selecting **Exclude healthy** sends a notification only if a deployment occurs in which the impact of your code on productions errors is anything except _Healthy;_ this includes _Unhealthy_, _Ailing_, or _Improved_.   ![](.gitbook/assets/notifications-slack-notifications-setup.png) 

### Setting up email notifications 

Email notifications are sent at the frequency you select, and can be configured individually at the project and change source level. 

#### To set up at the project level

1. Select a project in the sidebar. 
2. Click **My Notifications** in the upper-right corner of the Dashboard.   ![](.gitbook/assets/slack-my-notifications.png) 
3. Select a notification frequency in the dropdown. More than one can be selected.  

#### To set up at the change source level

1. Select a project in the sidebar. The project's dashboard is displayed. 
2. Select a change source in the [_Change sources_ section](dashboard.md) and click on its title link. The dashboard for the change source is displayed.   ![](.gitbook/assets/change-source.png) ![](.gitbook/assets/screen-shot-2020-06-17-at-4.35.45-pm.png)  
3. Click **My Notifications** in the upper-right corner of the dashboard.   ![](.gitbook/assets/slack-my-notifications.png)
4. Select a notification frequency in the dropdown. More than one can be selected. 
