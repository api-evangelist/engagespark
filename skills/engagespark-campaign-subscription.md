---
name: Subscribe a contact to a campaign
description: Subscribe and unsubscribe a contact to an engageSPARK voice/SMS campaign (engagement).
api: openapi/engagespark-openapi-original.yml
operations: [subscribeContact, unsubscribeContact, listContacts]
---

# Subscribe a contact to a campaign

Base URL `https://api.engagespark.com`. Auth header `Authorization: Token <personal_access_token>`.

1. Identify or create the contact (`listContacts`) and note the campaign (`{campaignId}`).
2. Subscribe: `subscribeContact` — `POST /v1/organizations/{orgId}/engagements/{campaignId}/subscribe`. This starts the voice/SMS engagement for the contact.
3. Unsubscribe: `unsubscribeContact` — `POST /v1/organizations/{orgId}/engagements/{campaignId}/unsubscribe`.

Errors: `400`, `401`, `500`. Campaign/survey responses are delivered back to your server via the Campaign Action Webhook (see `asyncapi/engagespark-webhooks.yml`).
