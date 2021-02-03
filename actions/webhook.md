# Webhook Action

The `webhook` action will send an HTTP POST to the URL of your choosing. The body contains information about the
deployment, and a signature to verify the webhook is valid and originated at Sleuth.

## Body

The body of the webhook will look something like this:

    {
      "organization": {
        "slug": "myorg"
      },
      "name": "791f0e0",
      "on": "2021-02-03T00:35:09.823706+00:00",
      "branch": "master",
      "revision": "791f0e0ce8612717da226d73caac7790e0de4032",
      "environment": {
        "slug": "production"
      },
      "changeSource": {
        "slug": "sleuth-test"
      },
      "health": "healthy",
      "author": {
        "email": "nobody@example.com"
      }
    }

## Signature

The webhook will contain two headers you can use to safely validate the message:

* `X-SLEUTH-TIMESTAMP` - The unix timestamp, in seconds, of when the webhook was created
* `X-SLEUTH-SIGNATURE` - The signature of the timestamp and request body, signed with the API key

The signature follows the format Slack uses to validate their webhooks. For more information how it works and how to 
validate the signature, see (the Slack docs)[https://api.slack.com/authentication/verifying-requests-from-slack]

The only difference is Sleuth uses the API key from your Sleuth [organization](../settings/organization/details.md) as 
the signing key.