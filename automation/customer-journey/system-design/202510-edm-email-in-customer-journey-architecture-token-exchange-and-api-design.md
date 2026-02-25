---
description: >-
  System design for EDM/Email actions in Customer Journey (MAAC + Email
  Extension + MDS). Covers boundaries, token exchange, campaign CRUD, message
  build/send flow, and key APIs.
---

# 202510 EDM (Email) in Customer Journey — Architecture, Token Exchange, and API Design

## Overview

This doc covers **EDM (Email) sending inside Customer Journey**. It describes the **Journey email action node** design across **MAAC**, **Email Extension service (Epistola)**, and **MDS**. It also documents **token exchange**, **campaign CRUD APIs**, and the **message build + send flow**.

{% hint style="info" %}
**Keywords**: EDM, email, Customer Journey, Journey node, action node, MAAC, MDS, Rubato, Email Extension, iframe editor, token exchange, JWT, SendGrid
{% endhint %}

### Related docs

* Email onboarding APIs
  * [202510 EDM in Journey onboaring contact management\_](202510-edm-in-journey-onboaring-contact-management_.md)
  * [202510 EDM in Journey onboaring (admin center)](202510-edm-in-journey-onboaring-admin-center.md)
* Tag trigger rule changes (often touches identity + tag source)
  * [202410 CDH tag journey rule](202410-cdh-tag-journey-rule.md)

***

## Action node v2 boundary (EDM / Email in Journey)

### **MAAC**

* journey
  * Journey graph 管理與渲染
  * Member progress 在節點間的移動
  * Progress 狀態改變（READY/RUNNING/WAITING/ENDED）
  * 呼叫 Email Extension / email service 發送訊息
  * 接收 webhook forward 取得發送結果（via MDS）
  * 儲存 MAAC metadata（channel 也在 MAAC）
  * 儲存 channel raw message（Email content / template metadata）
* member
  * Member API for outsource (PII / member profile)
* access management
  * Generate token for iframe (短效 token / exchange token)

### **Email Extension service**

* iframe editor FE (drag-and-drop / HTML editor)
* Node configuration
  * raw message verification
  * message preview
* Build message
  * member + message → personalized built message

### **MDS**

* Channel adaptor for sending
* Channel webhook processing + forward

***

## Design notes

### Design & discussion

* Email Extension FE + BE are in the same repo (monorepo).
* Tech stack
  * FE: iframe
  * BE:
    * python (fastAPI)
    * serverless (cloud run)
    * stateless (no db)
* Template for CI/CD and infra
* Scalable URL domain (?)
  * subdomain vs. domain
* 認證機制

### EDM provider survey (SendGrid)

* sendgrid: [https://www.notion.so/cresclab/Send-emails-through-SendGrid-API-2558ce158938805d867fd081cb7eea64#2558ce158938805d867fd081cb7eea64](https://www.notion.so/cresclab/Send-emails-through-SendGrid-API-2558ce158938805d867fd081cb7eea64#2558ce158938805d867fd081cb7eea64)

***

## System architecture diagrams

### System chart

TBD. Use the component chart below as the current reference.

### Component chart (editor + message builder)

![](<../../../.gitbook/assets/Unknown image (11)>)

extension FE: editor

extension BE: message builder

***

## Authentication: token exchange (iframe editor)

### Token exchange sequence diagram

* short-lived token: jwt (expires in 30s)
* long-live token: jwt for now (org level)
  * option 1: jwt (for now)
  * option 2: open api
    * user\_id is required in header for audit log (specific prefix for system)

![](<../../../.gitbook/assets/Unknown image (12)>)

***

## Journey campaign editing flow

### Campaign edit sequence diagram

![](<../../../.gitbook/assets/Unknown image (13)>)

Extension calls Rubato API for message storage.

* PATCH /extension/v1/campaign/{campaign\_id} → build campaign layer message

```json
{
  "ref_type": "journey_node",
  "metadata": {
    "name": "gideon_test"
  },
  "raw_message": {
    "sender_profile_id": 1,
    "subject": "string",
    "member_name_default_value": "string",
    "message_editor_type": "drag-and-drop",
    "json": {},
    "html": "string"
  },
  "built_message": {
    "sender_profile_id": 1,
    "subject": "string",
    "member_name_default_value": "string",
    "message_editor_type": "drag-and-drop",
    "json": {},
    "html": "string"
  },
  "channel_id": 1
}
```

* GET /extension/v1/campaign/{id}/?ref\_type=journey\_node

```json
{ "ref_type": "journey_node" }
```

Response:

```json
{
  "ref_type": "journey_node",
  "ref_id": 100,
  "metadata": {
    "name": "string"
  },
  "raw_message": {
    "json": {},
    "html": "string"
  },
  "built_message": {
    "json": {},
    "html": "string"
  }
}
```

* DELETE /extension/v1/campaign/{pk}

```json
{ "ref_type": "journey_node" }
```

***

## Message build and send flow (EDM / Email)

### Campaign message send flow

![](<../../../.gitbook/assets/Unknown image (14)>)

Rubato calls extension API for message building.

* POST /api/email/v1/build\_message payload

```json
{
  "receiver_entity_ids": [1],
  "built_message": {
    "sender_profile_id": 1,
    "subject": "string",
    "member_name_default_value": "string",
    "message_editor_type": "drag-and-drop",
    "json": {},
    "html": "string"
  }
}
```

Response:

```json
{
  "data": [
    {
      "entity_id": 1,
      "recipient_id": "receiver_email",
      "personalized_message": {}
    }
  ]
}
```

### Journey flow (email action execution)

![](<../../../.gitbook/assets/Unknown image (15)>)

### **Email Extension Repo**

[https://github.com/chatbotgang/Epistola](https://github.com/chatbotgang/Epistola)

***

## API design (EDM / Email in Journey)

This section focuses on **searchable endpoint keywords** and **integration points**. Keep endpoint names consistent in other docs to improve discoverability.

### External service → MAAC BE (journey trigger)

* /api/v1/journey/trigger

```json
{
  "channel_type": "email",
  "channel_external_id": 123,
  "channel_entity_external_id": 456,
  "journey_id": 789
}
```

### MAAC FE → MAAC BE (CRUD)

* GET Sender profiles Same response as the [definition](https://www.notion.so/202510-EDM-in-journey-2878ce158938804f9ae5ceed1bcd4c47?pvs=21)
* POST /journey/v1/node/

```json
{
  "id": "string",
  "name": "string",
  "sender_profile_id": 1,
  "...": {}
}
```

#### Token minting (short-lived)

* POST /accounts/v1/token

```json
{ "expiration": 30 }
```

Response:

```json
{ "token": "abc" }
```

### MAAC BE → Extension BE / Email service

#### Sender profile

* GET /extension/v1/email/sender\_profile/ (query: sender\_profile\_id)

```json
[
  {
    "id": 1,
    "reply_to": "string",
    "from_email": "string",
    "from_name": "string",
    "status": "valid",
    "channel_id": 1
  }
]
```

#### Campaign list (email)

* GET /campaign/v1/campaign/?channel\_type=email

```json
[
  {
    "ref_type": "journey_node",
    "ref_id": 123,
    "metadata": {
      "name": "string",
      "journey_name": "string"
    },
    "raw_message": {
      "sender_profile_id": 1,
      "subject": "string",
      "member_name_default_value": "string",
      "message_editor_type": "drag-and-drop",
      "json": {},
      "html": "string"
    },
    "channel_id": 1
  }
]
```

### Template API (email message templates)

* POST /email/v1/message/template/

```json
{
  "name": "123123",
  "subject": "string",
  "member_name_default_value": "string",
  "message_editor_type": "drag-and-drop",
  "json": {},
  "html": "string"
}
```

* PATCH /email/v1/message/template/{id}/

```json
{
  "name": "123123",
  "subject": "string",
  "member_name_default_value": "string",
  "json": {},
  "html": "string"
}
```

* DELETE /email/v1/message/template/{id}/
* POST /email/v1/message/template/search/ (params)
  * offset
  * limit
  * name\_q

Response:

```json
{
  "count": 48,
  "results": [
    {
      "id": 9527,
      "name": "123123",
      "subject": "string",
      "member_name_default_value": "string",
      "message_editor_type": "drag-and-drop",
      "json": {},
      "html": "string"
    }
  ]
}
```

* GET /email/v1/message/template/{id}/

```json
{
  "id": 9527,
  "name": "123123",
  "subject": "string",
  "member_name_default_value": "string",
  "message_editor_type": "drag-and-drop",
  "json": {},
  "html": "string"
}
```

***

## Iframe integration (MAAC FE → Extension FE)

### Open the extension FE in an iframe

```
{extension_editor_url}?lang={maac_ui_language}&messageFor=journey&nodeId=9527
```

### URL query parameters (keywords: iframe, editor URL, messageFor, nodeId)

* `lang` (optional, default: `en`)
  * Align Extension FE language with MAAC UI language.
* `messageFor` (required)
  * Which MAAC feature is using the extension.
  * Affects rendered input fields and called APIs.
  * Example: `journey`
* `nodeId` (conditionally required)
  * Target Journey node ID the message belongs to.
  * Required when `messageFor=journey`.
* `usedFor` (required)
  * Product identifier.
  * Values: `maac`, `caac`

### Extension FE → MAAC FE (postMessage events)

Mutation notification. When PATCH or DELETE happens in Extension FE, notify MAAC FE to refetch node detail.

```json
{
  "type": "EMAIL_EDITOR_CONTENT_SAVED",
  "payload": { "node_id": 123 }
}
```

```json
{
  "type": "EMAIL_EDITOR_CONTENT_DELETED",
  "payload": { "node_id": 123 }
}
```

```json
{
  "type": "EMAIL_EDITOR_CLOSE_REQUESTED",
  "payload": { "node_id": 123 }
}
```

***

## Extension API (iframe editor → Extension BE): raw message CRUD

### PATCH /api/v1/node/{node\_id} (drag-and-drop)

```json
{
  "name": "string",
  "metadata": { "name": "string" },
  "sender_profile_id": 1,
  "message_editor_type": "drag-and-drop",
  "raw_message": {
    "subject": "string",
    "member_name_default_value": "string",
    "json": {},
    "html": "string"
  }
}
```

### PATCH /api/v1/node/{node\_id} (HTML editor)

```json
{
  "name": "string",
  "sender_profile_id": 1,
  "message_editor_type": "html",
  "raw_message": {
    "subject": "string",
    "member_name_default_value": "string",
    "json": null,
    "html": "string"
  }
}
```

* GET /api/v1/node/{node\_id}/

Response:

```json
{ "json": {}, "html": "string" }
```

* DELETE /api/v1/node/{node\_id}

***

## Additional APIs (reference)

This section keeps the remaining endpoints in a consistent format. Some endpoint naming is legacy and may change.

### Campaign API (general)

Used for storing or retrieving email campaign content for a Journey node.

* PATCH `/api/campaign/v1`

```json
{
  "ref_type": "journey_node",
  "ref_id": 123,
  "metadata": { "name": "string" },
  "raw_message": {
    "sender_profile_id": 1,
    "subject": "string",
    "member_name_default_value": "string",
    "message_editor_type": "drag-and-drop",
    "json": {},
    "html": "string"
  }
}
```

* GET `/api/campaign/v1?ref_type=journey_node&ref_id=123`
* DELETE `/api/campaign/v1`

```json
{ "ref_type": "journey_node", "ref_id": 123 }
```

### Email sender profiles

* GET `/api/email/v1/sender_profile`

```json
[
  {
    "id": 1,
    "reply_to": "no-reply@example.com",
    "from_email": "marketing@example.com",
    "from_name": "Example Company",
    "status": "verified",
    "channel_id": 1
  }
]
```

### Channels

Same as MAAC `/channel/v1/channel`.

* GET `/api/channel/v1`

```json
[
  {
    "id": 1,
    "uuid": "string",
    "name": "string",
    "type": "email",
    "enable": true,
    "status": "valid",
    "channel_information": { "brand_domain": "string" }
  }
]
```

### Google Analytics settings

* GET `/api/ga/v1/settings`

```json
[
  { "website_url": "https://example.com", "view_id": "123456" }
]
```

### CDP tags

* GET `/api/cdp/v1/tags?source=maac`

```json
[
  { "id": 1563072, "name": "Tag name", "source": "maac" }
]
```

### Email templates (legacy)

* GET `/api/email/v1/template`
* POST/PATCH `/api/email/v1/template`

```json
{
  "name": "string",
  "raw_message": {
    "sender_profile_id": 1,
    "subject": "string",
    "member_name_default_value": "string",
    "message_editor_type": "drag-and-drop",
    "json": {},
    "html": "string"
  }
}
```

### Send test email

* POST `/api/email/v1/send` (test email)

```json
{
  "to": ["user1@example.com", "user2@example.com"],
  "raw_message": {
    "sender_profile_id": 1,
    "subject": "Hello, this is a test email",
    "member_name_default_value": "Default member name",
    "message_editor_type": "drag-and-drop",
    "json": {},
    "html": "..."
  }
}
```

### Member search (PII)

* POST `/api/member/v1/search`

```json
{ "email": "user@example.com" }
```

### Token exchange (short-lived → long-lived)

* POST `/api/token/v1/exchange`

```json
{ "exchange_token": "short_lived_jwt" }
```

```json
{ "token": "long_lived_jwt" }
```

### Extension service testing

* POST `/api/extension/{channel}/test_message`

```json
{
  "receiver_entity_ids": [1943, 393],
  "raw_message": {}
}
```

### MDS callback handling (Journey email delivery results)

API details live here: https://chatbotgang.slack.com/docs/T4TDRKSG4/F09KPV86S9F

***

## Admin Center: message template schema

message template (admin center)

|                  | **data type**     |   |
| ---------------- | ----------------- | - |
| id               | big int           |   |
| name             | text              |   |
| channel\_type    | text              |   |
| message\_type    | text              |   |
| message          | json              |   |
| organization\_id | int (foreign key) |   |
