---
description: >-
  API proposals for Customer Journey node performance reporting. Compares v1
  node-only endpoint vs v2 combined journey + node report design.
---

# 20250619 Journey node performance

### Overview

This doc proposes API designs for **Customer Journey performance reporting**, with a focus on **node-level performance**.

It compares:

* a **v1 node report endpoint** (node-only response)
* a **v2 report endpoint** that returns both **journey summary + per-node metrics** (preferred)
* an option to extend the existing **Get Journey** API with optional date params

{% hint style="info" %}
**Keywords**: journey node performance, journey report API, message sent, open count, click metrics, transactions, revenue, date range, v1, v2
{% endhint %}

Related:

* [202302 Journey Architecture & Design](202302-journey-architecture-and-design.md)
* [Journey Troubleshooting Knowledge Base](../troubleshooting-and-faq/journey-troubleshooting-knowledge-base.md)

### Problem

We need a consistent API to support:

* **Journey Report** (overall performance)
* **Node performance** (per-node cards / canvas overlay)
* a clear **date range filter** with stable metric definitions

### Goal

* Avoid multiple round trips for journey + node metrics.
* Reduce UI inconsistency risk (time gaps between APIs).
* Keep the payload shape easy to cache and index.

### Proposed solutions

{% stepper %}
{% step %}
### Proposal 1 — Separate Node Performance API

Get Journey Node Performance Data API (new api)

Description: This API retrieves performance metrics for each node in a specified journey within a given date range. Metrics include message sends, opens, clicks, transactions, and revenue.

Endpoint GET /journey/v1/journey/{journey\_id}/nodes/report/

Query Parameters

| Name        | Type   | Required | Description                                | Example    |
| ----------- | ------ | -------- | ------------------------------------------ | ---------- |
| start\_date | string | Yes      | Start date (inclusive), format: YYYY-MM-DD | 2025-06-09 |
| end\_date   | string | Yes      | End date (inclusive), format: YYYY-MM-DD   | 2025-06-20 |

Example Request

GET /journey/v1/journey/123/nodes/report/?start\_date=2025-06-09\&end\_date=2025-06-20

Success Response (200 OK)

```json
[
  {
    "id": 1,
    "message_sent": 0,
    "message_pushed": 0,
    "open_count": 0,
    "clicks": 0,
    "unique_clicks": null,
    "adds_to_cart": 0,
    "transactions": 0,
    "transaction_revenue": 0.0,
    "clicks_of_share": null,
    "unique_clicks_of_share": null,
    "traffic_count": 0,
    "last_updated_at": "2025-06-19T16:00:46.776942Z"
  }
]
```

Response Fields

| Field                     | Type     | Description                         | Note                                      |
| ------------------------- | -------- | ----------------------------------- | ----------------------------------------- |
| id                        | integer  | Node ID                             |                                           |
| message\_sent             | integer  | Number of messages sent             |                                           |
| message\_pushed           | integer  | Number of messages pushed           |                                           |
| open\_count               | integer  | Number of message opens             |                                           |
| clicks                    | integer  | Number of total clicks              |                                           |
| unique\_clicks            | integer  | Number of unique users who clicked  |                                           |
| adds\_to\_cart            | integer  | Items added to cart                 |                                           |
| transactions              | integer  | Number of transactions              |                                           |
| transaction\_revenue      | float    | Total revenue from transactions     |                                           |
| clicks\_of\_share         | integer  | Clicks from shared messages         | not used (copied from journey report api) |
| unique\_clicks\_of\_share | integer  | Unique clicks from shared messages  | not used (copied from journey report api) |
| traffic\_count            | integer  | Total traffic count                 |                                           |
| last\_updated\_at         | datetime | Last update time in ISO 8601 format | not used (copied from journey report api) |

Error Responses

| Status Code | Description       | Example                                                     |
| ----------- | ----------------- | ----------------------------------------------------------- |
| 400         | Bad request       | {"detail": "start\_date is required."}                      |
| 404         | Journey not found | {"detail": "Journey not found."}                            |
| 401         | Unauthorized      | {"detail": "Authentication credentials were not provided."} |
{% endstep %}

{% step %}
### Proposal 2 — Journey Performance Data API (v2) \[Preferred]

Get Journey Performance Data API (new v2 api)

Description: This API retrieves performance metrics for both journey and node in a specified journey within a given date range. Metrics include message sends, opens, clicks, transactions, and revenue.

Endpoint GET /journey/v2/journey/{journey\_id}/report/

Query Parameters

| Name        | Type   | Required | Description                                | Example    |
| ----------- | ------ | -------- | ------------------------------------------ | ---------- |
| start\_date | string | Yes      | Start date (inclusive), format: YYYY-MM-DD | 2025-06-09 |
| end\_date   | string | Yes      | End date (inclusive), format: YYYY-MM-DD   | 2025-06-20 |

Example Request

GET /journey/v1/journey/123/report/?start\_date=2025-06-09\&end\_date=2025-06-20

Success Response (200 OK)

```json
{
  "message_sent": 0,
  "open_count": 3,
  "clicks": 3,
  "unique_clicks": null,
  "adds_to_cart": 0,
  "transactions": 0,
  "transaction_revenue": 0.0,
  "traffic_count": 2,
  "last_updated_at": "2025-06-19T16:00:46.776942Z",
  "node": [
    {
      "id": 1,
      "message_sent": 0,
      "open_count": 2,
      "clicks": 0,
      "unique_clicks": null,
      "adds_to_cart": 0,
      "transactions": 0,
      "transaction_revenue": 0.0,
      "traffic_count": 2
    },
    {
      "id": 2,
      "message_sent": 0,
      "open_count": 1,
      "clicks": 3,
      "unique_clicks": null,
      "adds_to_cart": 0,
      "transactions": 0,
      "transaction_revenue": 0.0,
      "traffic_count": 1
    }
  ]
}
```

Response Fields

| Field                | Type     | Description                         | Note |
| -------------------- | -------- | ----------------------------------- | ---- |
| id                   | integer  | Node ID                             |      |
| message\_sent        | integer  | Number of messages sent             |      |
| open\_count          | integer  | Number of message opens             |      |
| clicks               | integer  | Number of total clicks              |      |
| unique\_clicks       | integer  | Number of unique users who clicked  |      |
| adds\_to\_cart       | integer  | Items added to cart                 |      |
| transactions         | integer  | Number of transactions              |      |
| transaction\_revenue | float    | Total revenue from transactions     |      |
| traffic\_count       | integer  | Total traffic count                 |      |
| last\_updated\_at    | datetime | Last update time in ISO 8601 format |      |

Error Responses

| Status Code | Description       | Example                                                     |
| ----------- | ----------------- | ----------------------------------------------------------- |
| 400         | Bad request       | {"detail": "start\_date is required."}                      |
| 404         | Journey not found | {"detail": "Journey not found."}                            |
| 401         | Unauthorized      | {"detail": "Authentication credentials were not provided."} |

Rationale for preferring proposal 2:

* Journey performance is the sum of node performance; returning both journey and node data in one API is more efficient and avoids repetitive calculations.
* Using one API reduces risk of time gaps between separate APIs causing UI data inconsistency.
{% endstep %}

{% step %}
### Proposal 3 — Extend Get Journey API with optional dates

Get Journey API endpoint: GET /journey/v2/journey/{journey\_id}/

Query Parameters

| Name        | Type   | Required | Description                                | Example    |
| ----------- | ------ | -------- | ------------------------------------------ | ---------- |
| start\_date | string | False    | Start date (inclusive), format: YYYY-MM-DD | 2025-06-09 |
| end\_date   | string | False    | End date (inclusive), format: YYYY-MM-DD   | 2025-06-20 |

Example Response (excerpt)

```json
{
  "id": 22656,
  "bot_id": 1,
  "name": "gideon only",
  ...
  "nodes": [
    {
      "id": 115155,
      "journey_id": 22656,
      "type": "tag_added",
      "performance": {
        "message_sent": 0,
        "open_count": 2,
        "clicks": 0,
        "unique_clicks": null,
        "adds_to_cart": 0,
        "transactions": 0,
        "transaction_revenue": 0.0,
        "traffic_count": 2,
        "unique_contact_count": 5,
        "unique_url_click_count": 10
      }
    }
  ],
  "paths": [
    {
      "id": 146939,
      "source_node_id": 115157,
      "target_node_id": 115156,
      "index": 0,
      "performance": {
        "traffic_count": 60,
        "traffic_ratio": 0.6,
        "unique_contact_count": 60,
        "unique_contact_ratio": 0.6,
        "type": "send_message"
      }
    }
  ],
  "performance": {
    "message_sent": 0,
    "open_count": 2,
    "clicks": 0,
    "unique_clicks": null,
    "adds_to_cart": 0,
    "transactions": 0,
    "transaction_revenue": 0.0,
    "traffic_count": 2,
    "unique_contact_count": 5,
    "unique_url_click_count": 10,
    "last_updated_at": "2025-05-26T15:22:42.945223+08:00"
  }
}
```

Notes about data structure differences:

* Different node types have different performance data:
  * trigger node: traffic\_count
  * send message: traffic\_count, message\_sent, open\_count, clicks, transactions, transaction\_revenue
  * yes/no branch: traffic\_count
  * time interval nodes: traffic\_count
  * exit node: traffic
* There is a question whether some stats should be shown on paths/edges rather than nodes; follow-up required.
{% endstep %}
{% endstepper %}

### Decision

Prefer proposal 2.

Reasons:

* Journey performance equals the sum of node performance, so one API that returns both avoids repetitive calculations.
* Single API reduces the possibility of time gaps between two separate API responses leading to UI data inconsistency.

### Next steps (TODO)

<details>

<summary>Open items</summary>

* Confirm metric definitions with data pipeline (unique click, unique open).
* Confirm whether path/edge performance is required in v2.
* Decide caching strategy for report payload (per journey + date range).

</details>
