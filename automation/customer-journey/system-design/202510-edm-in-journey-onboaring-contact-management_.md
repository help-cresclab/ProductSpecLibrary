---
description: >-
  Email (EDM) onboarding contact management APIs for Customer Journey. Covers
  sender domains, sender profiles, and DNS validation flow.
---

# 202510 EDM in Journey onboaring contact management\_

### Overview

This doc captures the **Email/EDM onboarding APIs** used by Customer Journey to manage **sender domains** and **sender profiles**.

It focuses on the **contact management** slice of onboarding, including **DNS validation** (SendGrid domain authentication) and the expected response shapes.

{% hint style="info" %}
**Keywords**: EDM onboarding, email channel, sender domain, sender profile, domain validation, DNS, DKIM, DMARC, SendGrid, Customer Journey API
{% endhint %}

Related:

* [202510 EDM (Email) in Customer Journey — Architecture, Token Exchange, and API Design](202510-edm-email-in-customer-journey-architecture-token-exchange-and-api-design.md)
* [202510 EDM in Journey onboaring (admin center)](202510-edm-in-journey-onboaring-admin-center.md)

### Endpoint index

* `GET /api/v1/channels/{channel_id}/sender-domains`
* `GET /api/v1/channels/{channel_id}/sender-profiles`
* `POST /api/v1/channels/{channel_id}/sender-domains/{domain_id}/validate`

## GET /api/v1/channels/{channel\_id}/sender-domains

Success Response (200 OK)

{% code title="Response (application/json)" %}
```json
{
  "sender_domains": [
    {
      "id": 1,
      "domain": "example1.com",
      "status": "verified",
      "mail_cname_status": "pass",
      "dkim1_status": "pass",
      "dkim2_status": "pass",
      "dmarc_status": "pass",
      "created_at": "2024-01-01T00:00:00Z",
      "updated_at": "2024-01-01T00:00:00Z"
    },
    {
      "id": 2,
      "domain": "example2.com",
      "status": "warning",
      "mail_cname_status": "pass",
      "dkim1_status": "fail",
      "dkim2_status": "pass",
      "dmarc_status": "pass",
      "created_at": "2024-01-01T00:00:00Z",
      "updated_at": "2024-01-01T00:00:00Z"
    },
    {
      "id": 3,
      "domain": "example3.com",
      "status": "not_set",
      "mail_cname_status": "fail",
      "dkim1_status": "fail",
      "dkim2_status": "fail",
      "dmarc_status": "pass",
      "created_at": "2024-01-01T00:00:00Z",
      "updated_at": "2024-01-01T00:00:00Z"
    }
  ]
}
```
{% endcode %}

Error Responses

| Status Code | Error Code          | Description                                                  |
| ----------- | ------------------- | ------------------------------------------------------------ |
| 400         | BAD\_REQUEST        | Invalid request                                              |
| 401         | UNAUTHORIZED        | Missing or invalid JWT token                                 |
| 404         | CHANNEL\_NOT\_FOUND | Channel does not exist or doesn't belong to the organization |

***

## GET /api/v1/channels/{channel\_id}/sender-profiles

Description Get all sender profiles for a specific email channel

Path Parameters

* channel\_id (integer, required): The ID of the email channel

Response

Success (200 OK)

{% code title="Response (application/json)" %}
```json
{
  "sender_profiles": [
    {
      "id": 1,
      "from_name": "Marketing Team",
      "from_email": "marketing@example.com",
      "reply_to": "reply@example.com",
      "status": "verified",
      "created_at": "2025-01-15T10:30:00Z",
      "updated_at": "2025-01-15T10:30:00Z"
    }
  ]
}
```
{% endcode %}

Error Responses

| Status Code | Error Code          | Description                                                |
| ----------- | ------------------- | ---------------------------------------------------------- |
| 401         | UNAUTHORIZED        | User is not authorized                                     |
| 404         | CHANNEL\_NOT\_FOUND | Channel not found or doesn't belong to user's organization |

***

## POST /api/v1/channels/{channel\_id}/sender-domains/{domain\_id}/validate

URL Parameters

| Parameter   | Type    | Required | Description      |
| ----------- | ------- | -------- | ---------------- |
| channel\_id | integer | Yes      | Email channel ID |
| domain\_id  | integer | Yes      | Sender domain ID |

Body No request body required.

Response

Success Response (200 OK)

{% code title="Response (application/json)" %}
```json
{
  "id": 1,
  "domain": "example.com",
  "status": "verified",
  "mail_cname_status": "pass",
  "dkim1_status": "pass",
  "dkim2_status": "pass",
  "dmarc_status": "pass",
  "created_at": "2025-01-15T10:00:00Z",
  "updated_at": "2025-01-15T10:30:00Z"
}
```
{% endcode %}

Error Code Reference

| Status Code | Error Code                 | Description                                                     |
| ----------- | -------------------------- | --------------------------------------------------------------- |
| 404         | CHANNEL\_NOT\_FOUND        | Channel doesn't exist or doesn't belong to the organization     |
| 404         | SENDER\_DOMAIN\_NOT\_FOUND | Sender domain doesn't exist or doesn't belong to the channel    |
| 400         | INVALID\_REQUEST           | Domain is missing required configuration (external\_domain\_id) |

Behavior

{% stepper %}
{% step %}
### Validate DNS records

Calls SendGrid API to check domain authentication.
{% endstep %}

{% step %}
### Update database

Stores the latest DNS validation results.
{% endstep %}

{% step %}
### Calculate status

Automatically computes overall domain status.
{% endstep %}

{% step %}
### Return result

Sends updated domain information to frontend.
{% endstep %}
{% endstepper %}
