---
name: Send an airtime top-up
description: Send a pre-paid airtime top-up to a phone number and track top-up history and balance via the engageSPARK API.
api: openapi/engagespark-openapi-original.yml
operations: [getOrgBalance, sendOrgTopup, getOrgTopupsList, getOrgTopups]
---

# Send an airtime top-up

Base URL `https://api.engagespark.com`. Auth header `Authorization: Token <personal_access_token>`.

1. Check funds: `getOrgBalance` — `GET /v1/organizations/{orgId}/balance.json`.
2. Send top-up: `sendOrgTopup` — `POST /v1/organizations/{orgId}/topup/`. A `202` means accepted/queued; `200` completed; `402` means insufficient balance.
3. List: `getOrgTopupsList` — `GET /v1/organizations/{orgId}/topups/`, paginate with `page`+`size`.
4. Read one: `getOrgTopups` — `GET /v1/organizations/{orgId}/topups/{topupId}/`.

Errors: `400`, `401`, `404`. See `errors/engagespark-problem-types.yml`.
