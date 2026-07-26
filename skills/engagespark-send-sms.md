---
name: Send and track an SMS
description: Send an SMS to a known contact or a raw phone number via the engageSPARK API and check delivery, using safe-retry de-duplication.
api: openapi/engagespark-openapi-original.yml
operations: [sendSmsContact, sendSmsPhonenumber, getSmsList, getSms, getOrgBalance]
---

# Send and track an SMS

Base URL `https://api.engagespark.com`. Auth: `Authorization: Token <personal_access_token>` (the literal word `Token` must prefix the token).

1. (Optional) Check funds with `getOrgBalance` — `GET /v1/organizations/{orgId}/balance.json`. A send with no funds returns `402`.
2. Send:
   - To a saved contact: `sendSmsContact` — `POST /v1/sms/contact`.
   - To a raw phone number (E.164): `sendSmsPhonenumber` — `POST /v1/sms/phonenumber`.
   Set a unique `clientDedup` string per logical message. On a network retry, resending the same `clientDedup` is safe: engageSPARK will not send twice and returns `409` with the original response fields.
3. List history with `getSmsList` (`GET /v1/organizations/{orgId}/messages/`, paginate with `page`+`size`) or fetch one with `getSms` (`GET /v1/organizations/{orgId}/messages/{messageId}/`).

Errors: `400` bad request, `401` bad/absent token, `402` insufficient balance, `409` duplicate clientDedup (treat as success). Envelope is `application/json`. See `errors/engagespark-problem-types.yml` and `conventions/engagespark-conventions.yml`.
