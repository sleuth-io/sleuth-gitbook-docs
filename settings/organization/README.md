# Organization settings

{% hint style="warning" %}
Only Owners and Administrators and Billing users can access Organization settings.
{% endhint %}

The following settings can be configured for the Sleuth organization:

| Setting                       | Description                                               |
| ----------------------------- | --------------------------------------------------------- |
| [**Details**](details.md)     | General information about the organization                |
| [**Authentication**](signup/) | Set the email domain for auto-joining by new members      |
| [**Members**](members.md)     | Manage invitations and member roles for your organization |
| ****[**Teams**](teams.md)**** | Manage teams, sub-teams, and team membership              |
| [**Billing**](billing.md)     | Choose a new Sleuth plan for your organization            |

Owners and Administrators (see [Access Control](../access-control.md) for more information about roles) in Sleuth can make changes to the organization, which affects all users and projects that belong to that organization.

Some integrations allow project- and user-level settings to be made, such as the [Slack integration](../../integrations-1/slack.md). For example, a project could generate a Slack message when a deploy occurs, but a user might only want to receive a Slack message if the deploy is **not** healthy.
