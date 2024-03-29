# SaaS Logs

Panther supports pulling logs directly from SaaS platforms such as Okta, OneLogin, and more.

The two mechanisms used are direct integrations (by querying APIs) and AWS EventBridge.

## Direct

Supported direct SaaS integrations include:

* [1Password](1password.md)
* [Atlassian](https://docs.runpanther.io/data-onboarding/saas-logs/atlassian)
* [Box](box.md)
* [CrowdStrike](crowdstrike.md)
* [Duo](duo.md)
* [G Suite](gsuite.md)
* [Github](github.md)
* [Okta](okta.md)
* [OneLogin](onelogin.md)
* [Salesforce](salesforce.md)
* [Slack](slack.md)
* [Microsoft 365](microsoft.md)
* [Zendesk](zendesk.md)
* [Zoom](zoom.md)
* More coming soon!

{% hint style="info" %}
By default, we poll for new logs every minute.
{% endhint %}

## EventBridge

Panther has direct support for pulling log data from AWS EventBridge, enabling real-time streaming and simple ingestion of [supported SaaS integrations](https://aws.amazon.com/eventbridge/integrations/).

* [OneLogin](onelogin.md)
* _(Coming soon!)_ Auth0
* _(Coming soon!)_ NewRelic
