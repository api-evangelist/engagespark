---
name: Manage contacts
description: Create, read, update, delete, and search an organization's contacts in the engageSPARK API.
api: openapi/engagespark-openapi-original.yml
operations: [listContacts, createContact, getContact, updateContact, deleteContact]
---

# Manage contacts

Base URL `https://api.engagespark.com`. Auth header `Authorization: Token <personal_access_token>`. All paths are scoped to `{orgId}`.

1. Create: `createContact` — `POST /v1/organizations/{orgId}/contacts/`.
2. List / search: `listContacts` — `GET /v1/organizations/{orgId}/contacts/`. Filter with `search`, `phonenumber`+`region`, `groupid`, etc.; paginate with `page` (starts at 1) and `size`.
3. Read one: `getContact` — `GET /v1/organizations/{orgId}/contacts/{contactId}/`.
4. Update: `updateContact` — `PUT /v1/organizations/{orgId}/contacts/{contactId}/`.
5. Delete: `deleteContact` — `DELETE /v1/organizations/{orgId}/contacts/{contactId}/`.

Errors: `400`, `401`, `404` (unknown contact), `500`. See `errors/engagespark-problem-types.yml`.
