---
description: >-
  Admin Center API design for Email/EDM channel onboarding. Includes sender
  domains, sender profiles, validation, and channel status rules.
---

# 202510 EDM in Journey onboaring (admin center)

### Overview

This doc captures the **Admin Center** side of **Email/EDM onboarding**.

It defines the **Email channel** endpoints and response shapes used to display and validate:

* sender domains (DNS authentication)
* sender profiles
* email channel status (`not_set`, `connected`, `warning`, `suspended`)

{% hint style="info" %}
**Keywords**: Admin Center, EDM onboarding, email channel, sender domain, sender profile, SendGrid validation, channel status, hard bounce, spam rate
{% endhint %}

Related:

* [202510 EDM (Email) in Customer Journey — Architecture, Token Exchange, and API Design](202510-edm-email-in-customer-journey-architecture-token-exchange-and-api-design.md)
* [202510 EDM in Journey onboaring contact management\_](202510-edm-in-journey-onboaring-contact-management_.md)

### Endpoint index

* `GET /api/v1/channels/{channel_id}/sender-domains`
* `GET /api/v1/channels/{channel_id}/sender-profiles`
* `POST /api/v1/channels/{channel_id}/sender-domains/{domain_id}/validate`
* `GET /api/v1/channels`

## GET /api/v1/channels/{channel\_id}/sender-domains

Success Response (200 OK):

```json
[
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
    "status": "failed",
    "mail_cname_status": "fail",
    "dkim1_status": "fail",
    "dkim2_status": "fail",
    "dmarc_status": "pass",
    "created_at": "2024-01-01T00:00:00Z",
    "updated_at": "2024-01-01T00:00:00Z"
  }
]
```

<details>

<summary>Error Responses</summary>

| Status Code | Error Code          | Description                                                  |
| ----------- | ------------------- | ------------------------------------------------------------ |
| 400         | BAD\_REQUEST        | Invalid request                                              |
| 401         | UNAUTHORIZED        | Missing or invalid JWT token                                 |
| 404         | CHANNEL\_NOT\_FOUND | Channel does not exist or doesn't belong to the organization |

</details>

***

## GET /api/v1/channels/{channel\_id}/sender-profiles

Description

Get all sender profiles for a specific email channel

Path Parameters

* channel\_id (integer, required): The ID of the email channel

Response

Success (200 OK)

```json
[
  {
    "id": 2,
    "name": "Aaren test",
    "from_email": "aaren@marketing.cresclab.site",
    "reply_to": "aaren@marketing.cresclab.site",
    "status": "verified",
    "created_at": "2025-11-15T03:12:33.606Z",
    "updated_at": "2025-11-15T03:12:33.606Z"
  }
]
```

<details>

<summary>Error Responses</summary>

| Status Code | Error Code          | Description                                                |
| ----------- | ------------------- | ---------------------------------------------------------- |
| 401         | UNAUTHORIZED        | User is not authorized                                     |
| 404         | CHANNEL\_NOT\_FOUND | Channel not found or doesn't belong to user's organization |

</details>

***

## POST /api/v1/channels/{channel\_id}/sender-domains/{domain\_id}/validate

URL Parameters

| Parameter   | Type    | Required | Description      |
| ----------- | ------- | -------- | ---------------- |
| channel\_id | integer | Yes      | Email channel ID |
| domain\_id  | integer | Yes      | Sender domain ID |

Body

No request body required.

Response

Success Response (200 OK)

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

<details>

<summary>Error Code Reference</summary>

| Status Code | Error Code                 | Description                                                     |
| ----------- | -------------------------- | --------------------------------------------------------------- |
| 404         | CHANNEL\_NOT\_FOUND        | Channel doesn't exist or doesn't belong to the organization     |
| 404         | SENDER\_DOMAIN\_NOT\_FOUND | Sender domain doesn't exist or doesn't belong to the channel    |
| 400         | INVALID\_REQUEST           | Domain is missing required configuration (external\_domain\_id) |
| 502         | EXTERNAL\_SERVICE\_ERROR   | External service error (see body)                               |

Example External Service Error (SendGrid):

```json
{
  "code": "EXTERNAL_SERVICE_ERROR",
  "message": "[SendGrid API Error] {原始錯誤訊息}"
}
```

Example configuration error (e.g., missing API key):

```json
{
  "code": "INVALID_REQUEST",
  "message": "Channel XX does not have SendGrid API key configured"
}
```

</details>

Behavior

{% stepper %}
{% step %}
### Validates DNS records

Calls SendGrid API to check domain authentication.
{% endstep %}

{% step %}
### Updates database

Stores the latest DNS validation results.
{% endstep %}

{% step %}
### Calculates status

Automatically computes overall domain status.
{% endstep %}

{% step %}
### Returns result

Sends updated domain information to frontend.
{% endstep %}
{% endstepper %}

***

## GET /api/v1/channels

Success (200 OK)

```json
{
  "channels": [
    {
      "id": 1,
      "organization_id": 1,
      "uuid": "431c1b10-af57-4402-ad3e-df7da3cb0e2a",
      "name": "EDM_test",
      "type": "email",
      "status": "connected",
      "external_channel_id": "cresclab.site",
      "channel_information": {
        "sender_domains": [
          {
            "id": 1,
            "domain": "marketing.cresclab.site",
            "status": "verified"
          }
        ],
        "sender_profiles": [
          {
            "id": 2,
            "from_email": "aaren@marketing.cresclab.site",
            "status": "verified"
          }
        ]
      }
    }
  ]
}
```

Email channel status codes (email channel status code 會有的值)

| Status    | 值         | 觸發原因                                                                      |
| --------- | --------- | ------------------------------------------------------------------------- |
| NOT\_SET  | not\_set  | 沒有任何已驗證的 sender profile                                                   |
| CONNECTED | connected | 有至少一個已驗證的 sender profile 且指標正常                                            |
| WARNING   | warning   | Hard Bounce: rate > 2% AND count > 10 OR Spam: rate > 0.3% AND count > 5  |
| SUSPENDED | suspended | Hard Bounce: rate > 5% AND count > 20 OR Spam: rate > 0.5% AND count > 10 |

規則：

* WARNING → SUSPENDED: 可自動升級
* WARNING / SUSPENDED → CONNECTED: 不會自動恢復，需手動處理
* SUSPENDED: 最終狀態，需要人工介入才能恢復
