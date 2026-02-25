---
description: >-
  Design notes for supporting CDH tag conditions in Customer Journey rules.
  Covers condition schema changes, tag source (MAAC/CAAC), and related API
  payload updates.
---

# 202410 CDH tag journey rule

Authors: @XXXX, @YYYY

### Overview

This doc tracks the **Customer Journey rule** change needed to support **CDH tags**.

The core change is adding a **tag source** (e.g. `maac` / `caac`) into **condition objects** and **node settings**, so rule evaluation and UI can stay consistent across tag origins.

{% hint style="info" %}
**Keywords**: CDH tag, Customer Journey rule, tag source, MAAC, CAAC, condition object, filters.conditions, trigger, Tag Added, API payload
{% endhint %}

### Quick links

* Journey context:
  * [Customer Journey feature overview](/broken/spaces/GBP3mPdNeU7kBvG5sba7/pages/xC1cwyTuPbT1BMR0eCkC)
  * [202302 Journey Architecture & Design](202302-journey-architecture-and-design.md)
  * [20250619 Journey node performance](20250619-journey-node-performance.md)
* Tagging + channel scope:
  * [202302 Customer Journey FE Scoping](202302-customer-journey-fe-scoping.md) (Tag trigger/editor fields)
  * [202510 EDM in Journey onboarding contact management\_](202510-edm-in-journey-onboaring-contact-management_.md)
* Email journey integration (often touches tags + contact identity):
  * [202510 EDM (Email) in Customer Journey — Architecture, Token Exchange, and API Design](202510-edm-email-in-customer-journey-architecture-token-exchange-and-api-design.md)

### References

* PRD:
  * [PRD Omnichnnel Customer Journey (LINE\_SMS\_EDM)](../product-specifications/prd-omnichannel-customer-journey-line-sms-edm.md)
  * [Customer Journey PRD\_Phase 1 1](../product-specifications/customer-journey-prd_phase-1-1.md)
  * [Source Links](/broken/spaces/GBP3mPdNeU7kBvG5sba7/pages/B99ZFI3sN0c0pk65shzL)
* ERD: TBD

Doc file name: `yyyymm(created_time)` (e.g. `202010`)

## Overview / Background

Current state:

* Journey rules can reference tags.
* CDH may contain tags from different sources.
* The rule engine and UI need a stable way to disambiguate the tag source.

## Problem

Without a source field:

* UI cannot reliably filter / render tags from MAAC vs CAAC.
* Backend condition evaluation can become ambiguous.
* Debugging triggers becomes harder (same tag ID/name across systems).

## Goal / Requirement

* Add a `source` (or equivalent) field into condition objects.
* Keep backward compatibility for existing journeys.
* Make the new shape discoverable in API payload examples.

## Proposed Solution(s)

How would you do this, what resources you’d need. Technical details.

Solution 1

Solution 2 (if any)

Decision, and why

* API Condition object data structure adjustment

| new field | type   | note                    |
| --------- | ------ | ----------------------- |
| source    | string | either ‘maac’ or ‘caac’ |
|           |        |                         |
|           |        |                         |

* object example

{% code title="Condition object example (JSON)" %}
```json
{
  "condition": "tag",
  "op": "with",
  "value": 14887,
  "extra": {"source": "maac"}
}
```
{% endcode %}

* PATCH endpoint

{% code title="PATCH /journey/v1/node/{node_id}/ (payload example)" %}
```json
{
  "type": "tag_added",
  "settings": {
    "tag_id": 4388,
    "tag_source": "maac"
  },
  "filters": {
    "match": "all",
    "conditions": [
      {
        "condition": "tag",
        "op": "with",
        "value": 14887,
        "extra": {
          // new field
          "source": "maac"
        }
      }
    ]
  }
}
```
{% endcode %}

* PATCH response example

<details>

<summary>Response (click to expand)</summary>

{% code title="PATCH response example (JSON)" %}
```json
{
  "id": 27397,
  "journey_id": 6439,
  "name": null,
  "type": "tag_added",
  "category": "trigger",
  "settings": {
    "tag_id": 4388,
    "tag_source": "maac"
  },
  "filters": {
    "match": "all",
    "conditions": [
      {
        "condition": "tag",
        "op": "with",
        "value": 14887,
        "extra": {
          "source": "maac"
        }
      }
    ]
  },
  "branch_settings": {},
  "created_at": "2024-10-17T09:36:51.704553+08:00",
  "updated_at": "2024-10-17T10:55:08.716110+08:00"
}
```
{% endcode %}

</details>

* GET endpoint

{% code title="GET /journey/v1/journey/{journey_id}" %}
```http
GET /journey/v1/journey/{journey_id}
```
{% endcode %}

* GET response example

<details>

<summary>Response (click to expand)</summary>

{% code title="GET response example (JSON)" %}
```json
{
  "id": 6439,
  "bot_id": 83,
  "name": "test 1017",
  "schedule_start_at": null,
  "schedule_end_at": null,
  "repeat_journey_times": null,
  "line_message_quota": null,
  "sleep_start_time": null,
  "sleep_end_time": null,
  "status": "draft",
  "created_at": "2024-10-17T09:36:51.693771+08:00",
  "updated_at": "2024-10-17T10:00:00.509858+08:00",
  "nodes": [
    {
      "id": 27397,
      "journey_id": 6439,
      "name": null,
      "type": "tag_added",
      "category": "trigger",
      "settings": {
        "tag_id": 4388,
        "tag_source": "maac"
      },
      "filters": {
        "match": "all",
        "conditions": [
          {
            "condition": "tag",
            "op": "with",
            "value": 14887,
            "extra": {
              "source": "maac"
            }
          }
        ]
      },
      "branch_settings": {},
      "created_at": "2024-10-17T09:36:51.704553+08:00",
      "updated_at": "2024-10-17T10:55:08.716110+08:00"
    },
    {
      "id": 27398,
      "journey_id": 6439,
      "name": null,
      "type": "exit",
      "category": "rule",
      "settings": {},
      "filters": {},
      "branch_settings": {},
      "created_at": "2024-10-17T09:36:51.710827+08:00",
      "updated_at": "2024-10-17T09:36:51.710855+08:00"
    },
    {
      "id": 27399,
      "journey_id": 6439,
      "name": "test 1017",
      "type": "send_line_message",
      "category": "action",
      "settings": {
        "name": "test 1017",
        "messages": [
          {
            "data": {
              "text": "測試成功！"
            },
            "module_id": 1,
            "parameters": [],
            "quick_reply": {
              "items": []
            }
          }
        ]
      },
      "filters": {},
      "branch_settings": {},
      "created_at": "2024-10-17T09:59:18.768913+08:00",
      "updated_at": "2024-10-17T09:59:46.870018+08:00"
    }
  ],
  "paths": [
    {
      "id": 34139,
      "source_node_id": 27397,
      "target_node_id": 27399,
      "index": 0
    },
    {
      "id": 34140,
      "source_node_id": 27399,
      "target_node_id": 27398,
      "index": 0
    }
  ]
}
```
{% endcode %}

</details>

## Tasks

Items no larger than 1 day. If there’s any, break it down smaller.

* Component 1
* Feature A (2 hr)
* Feature B (2 hr)
* Component 2
* DB change (4 hr)
* External API (1 day)
* Help from sales

Total time required + buffer: 2.5 days

## Measurement

* How do you define/measure success?
* How do you monitor/test the health of this projects?

## Feedback

Section for others to leave feedback and questions. Example:

@George

This is great, but we may need to change the DB schema...
