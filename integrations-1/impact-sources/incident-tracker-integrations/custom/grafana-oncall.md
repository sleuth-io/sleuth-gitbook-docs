---
description: >-
  If you are using Grafana OnCall to manage your alerts, you can use its
  Outgoing Webhooks feature to send data directly to a Custom Incident Impact
  Source in Sleuth.
---

# Grafana OnCall

{% hint style="info" %}
Please note that this is just one possible scenario on how you could use Grafana to feed Incident information to Sleuth. If you have a different process, you might need to adjust the steps/settings.&#x20;
{% endhint %}

## Registering a new Incident

Within your **Grafana OnCall** dashboard, navigate to the **Outgoing webhooks** page and click **+ New Outgoing Webhook**:

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

In the next step, select **Advanced** to ensure you can customize your webhook as much as possible:

* Provide a (_preferably descriptive_) name for your webhook, e.g. `Sleuth - New Incident`.
* Select a **Trigger Type** from the dropdown. For the purpose of this example, we're choosing `Alert Group Created`.
* Set the **HTTP Method** to `POST`.
* Copy the **Impact registration POST URL** from Sleuth's Custom Impact Source setup modal and paste it into the **Webhook URL** field in Grafana.
*   Enter the following into the **Webhook Headers** field in Grafana:

    ```json
    {
      "Content-Type": "application/json"
    }
    ```
*   Specify the **Data** you want Grafana to send Sleuth, leveraging the 5 fields the impact registration endpoint is currently able to accept:

    ```json
    {
      "type": "triggered",
      "id": "{{alert_group_id}}",
      "title": "{{alert_payload.oncall.message}}",
      "date": "{{alert_group.created_at}}",
      "url": "{{alert_group.permalinks.web}}"
    }
    ```

{% hint style="warning" %}
Please make sure to **deactivate** **the** `Forward All` **toggle** to ensure only your custom payload is sent to Sleuth's impact registration endpoint.
{% endhint %}

## Closing an Incident

The process is mostly the same as for registering a new Incident, with the difference being the **Name** of the webhook, the **Trigger Ty**pe, which needs to be set to `Resolved`, and the content of the **Data** field, which only needs to contain the following:

* Provide a (_preferably descriptive_) name for your webhook, e.g. `Sleuth - Incident Resolved`.
* Select a **Trigger Type** from the dropdown. For the purpose of this example, we're choosing `Resolved`.
* Set the **HTTP Method** to `POST`.
* Copy the **Impact registration POST URL** from Sleuth's Custom Impact Source setup modal and paste it into the **Webhook URL** field in Grafana.
*   Enter the following into the **Webhook Headers** field in Grafana:

    ```json
    {
      "Content-Type": "application/json"
    }
    ```
*   Specify the **Data** you want Grafana to send Sleuth, leveraging the 5 fields the impact registration endpoint is currently able to accept:

    ```json
    {
      "type": "resolved",
      "id": "{{alert_group_id}}",
      "title": "{{alert_payload.oncall.message}}",
      "date": "{{alert_group.created_at}}",
      "url": "{{alert_group.permalinks.web}}"
    }
    ```

{% hint style="warning" %}
Please make sure to **deactivate** **the** `Forward All` **toggle** to ensure only your custom payload is sent to Sleuth's impact registration endpoint.
{% endhint %}

{% hint style="info" %}
Both above examples use Grafana's response's default data structure to extract data that correspond to fields for Sleuth's custom incident events. The only mandatory field **is`type`**, all others are optional and can thus be omitted from the response definition.

Without a unique identifier in both payloads, however, Sleuth will not be able to match the **`triggered`** and **`resolved`** events belonging to the **same incident**, and upon receiving a webhook with `resolved`, will **resolve all active Incidents** for that impact source.
{% endhint %}

