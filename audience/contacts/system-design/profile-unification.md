# Profile unification

## PRD & Design Links

* PRD: https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit#heading=h.7z5imn1sorpi
* Figma: https://www.figma.com/file/k0XwP83RAV16nVdyFx7crb/Omnichannel-inbox?type=design\&node-id=4765-42620\&mode=design\&t=jsndVG6TFALc1cog-0

This project mainly involves 2 tasks:

{% stepper %}
{% step %}
### Profile unification in CAAC

See "CAAC part" below for API details, web socket events, and the unification process.
{% endstep %}

{% step %}
### Application page

See "Admin Center part" below for Admin Center APIs and CDH integration endpoints.
{% endstep %}
{% endstepper %}

***

## API

### CAAC part

#### New API

For unify key setting: The CRUD API for unify key setting follows the practice of CDH: https://www.notion.so/Unification-on-CDH-e437d717897c4fcf910df984cb5a84ee?pvs=21

*   Create org unify key setting (4hr)

    * URL: POST /api/v1/orgs/:org\_id/organization/unify-scope-setting
    * Body example:

    ```json
    {
      "unify_keys": [
        {"attribute":"line_id","is_distinct":false},
        {"attribute":"custom_id","is_distinct":false}
      ]
    }
    ```
*   Update org unify key (4hr)

    * URL: PUT /api/v1/orgs/:org\_id/organization/unify-scope-setting/unify-keys
    * Body example:

    ```json
    {
      "unify_keys": ["display_mobile","custom_id"]
    }
    ```

    * Errors: CDH\_ALREADY\_CONNECTED
* Delete org unify key (4hr)? (TBD)
*   Get Org Unify scope setting (4hr)

    * URL: GET /api/v1/orgs/:org\_id/organization/unify-scope-setting
    * Response example:

    ```json
    {
      "unify_scope_id": 1,
      "is_cdh_connected": true,
      "orgs": [
        {"id":1, "source": "maac"},
        {"id":1, "source": "caac"}
      ],
      "unify_keys": ["display_email","external_member_id","display_mobile"]
    }
    ```

    * Note: "is\_cdh\_connected": true if len(orgs) > 1; "unify\_keys" is \[] if no keys
*   Get org merge state (4hr)

    * URL: GET /api/v1/orgs/:org\_id/organization/unify-scope-setting/merge-state
    * Behavior: retrieve org merge state from cache; on cache miss → update; else → updating
    * Response example:

    ```json
    {
      "org_id": 1,
      "is_finished": true
    }
    ```

For profile usage:

* Ticket: https://app.asana.com/0/1204010721938900/1206344489487084/f
* Get unify profile (4hr) (endpoint/details TBD)
* Update contact unify key (4hr)
  * Use CDH API (referenced in Asana)
  * Endpoint: /api/v1/orgs/:org\_id/chat/members/:member\_id/uni
  * Request/response details: TBD
*   Change channel entity unification (4hr)\
    Use case: when user knows a specific contact should be unified with another contact. Flow:

    1. Lookup unify\_key for the org
    2. Modify the channel entity's all unify\_key to NULL
    3. Modify the channel entity's all editable columns to NULL
    4. Modify the channel entity's `unify_key` to some value (e.g. {"unify\_key":"mobile", "value":"0988..."})

    * URL: POST /api/v1/orgs/:org\_id/chat/members/:member\_id/change-unification
    * Request example:

    ```json
    {
      "unify_key": "display_email",
      "value": "kevin.tsai@cresclab.com.tw"
    }
    ```
* Cancel channel entity unification (4hr)\
  Cancel Unification flow:
  1. Lookup unify\_key for the org
  2. Modify all unify\_key of channel entity to be NULL
  3. (CDH is going to de-unify)
  * URL: POST /api/v1/orgs/:org\_id/chat/members/:member\_id/cancel-unification
*   Get Member Unification

    * URL: GET /api/v1/orgs/:org\_id/chat/members/:member\_id/unification
    * Response example:

    ```json
    {
      "member_id": 1,
      "unify_members": [
        {
          "source": "caac",
          "channel_id": 2,
          "channel_name": "unify channel 1",
          "type": "fb",
          "member_id": 2,
          "original_name": "member_original_name_2",
          "external_member_id": "U29893540562c1227b119f425d962f0ce",
          "last_message_at": "2024-01-31 12:25:27.743019+00"
        },
        {
          "source": "maac",
          "channel_id": null,
          "channel_name": null,
          "type": null,
          "member_id": 2,
          "original_name": null,
          "external_member_id": null,
          "last_message_at": null
        }
      ]
    }
    ```

For unification process:

* Unification subscriber (8hr) — ticket: https://app.asana.com/0/1199607007611227/1206359985962905/f
* Get channel entity merge state (4hr) — retrieve channel entity merge state in cache; if cache miss → update else → updating

For redirect to platform:

*   Get jwt token

    * URL: POST /api/v1/platform/token
    * Request example:

    ```json
    {
      "org_id": 1
    }
    ```

    * Response example:

    ```json
    {
      "org_id": 1,
      "token": "jwt token"
    }
    ```

    * Note: token is a JWT for the platform; default expiry after 300s

#### Updated API

For profile usage:

* Partial update member profile (6hr)\
  Introduce logic:
  1. Check if updated attribute is a unify key or not
  2. If true: call CDH process (reference): https://www.notion.so/cresclab/Unification-on-CDH-e437d717897c4fcf910df984cb5a84ee?pvs=4#828d303a5d034876af09dad3580c9ccf

### Web socket event

* Profile updated event (4hr)\
  Reference: https://www.notion.so/Real-Time-Web-Notification-7643cb44c55249eea3c1b7f6b27bde7a?pvs=21\
  (+ PubSub subscription added)

***

### Admin Center part

#### New API

For unify key setting: The CRUD API for unify key setting follow the practice of CDH: https://www.notion.so/Unification-on-CDH-e437d717897c4fcf910df984cb5a84ee?pvs=21

*   Get unify scope setting (6hr)

    * URL: GET /api/v1/applications/cdh/unify-scope-setting
    * Response example:

    ```json
    {
      "unify_scope_id": 17,
      "orgs": [
        {
          "id": 1,
          "source": "caac",
          "name": "org name",
          "uuid": "org uuid"
        }
      ],
      "unify_keys": [
        {"attribute": "connect_id","is_distinct": false},
        {"attribute": "custom_id","is_distinct": false}
      ],
      "is_cdh_connected": false,
      "distinct_key": null
    }
    ```
*   Update org unify keys (6hr)

    * URL: PUT /api/v1/applications/cdh/unify-scope-setting/unify-keys
    * Body example:

    ```json
    {
      "unify_keys": ["display_mobile","custom_id"]
    }
    ```

    * Response example:

    ```json
    {
      "unify_scope_id": 17,
      "orgs": [
        {"id": 1, "source": "caac"}
      ],
      "unify_keys": [
        {"attribute": "connect_id","is_distinct": false},
        {"attribute": "custom_id","is_distinct": false}
      ],
      "is_cdh_connected": false,
      "distinct_key": null
    }
    ```
*   Update org unify key (6hr)?

    * URL: PUT /api/v1/orgs/:org\_id/organization/unify-keys/:unify\_key\_id
    * Body example:

    ```json
    {
      "unify_key_attribute": "display_email",
      "is_distinct": true
    }
    ```
* Delete org unify key (6hr)? (TBD)
*   Integrate CDH (6hr) — follow rules in ref: https://www.notion.so/Unification-on-CDH-e437d717897c4fcf910df984cb5a84ee?pvs=21

    * URL: POST /api/v1/applications/cdh/integrate
    * Body example:

    ```json
    {
      "unify_keys": ["custom_id","display_mobile"]
    }
    ```

    * Response example:

    ```json
    {
      "unify_scope_id": 348,
      "orgs": [
        {"id": 11, "source": "caac", "name": null, "uuid": null},
        {"id": 1275, "source": "maac", "name": null, "uuid": null}
      ],
      "unify_keys": [
        {"attribute": "custom_id","is_distinct": false},
        {"attribute": "display_mobile","is_distinct": false}
      ],
      "is_cdh_connected": true,
      "distinct_key": null
    }
    ```
* Disconnect CDH (6hr)
  * URL: POST /api/v1/applications/cdh/disconnect
  * Response: 204
* Unification subscriber (8hr) — ticket: https://app.asana.com/0/1199607007611227/1206359985962905/f
*   Get org merge state (6hr)

    * URL: GET /api/v1/application/cdh/unify-scope-setting/merge-state
    * Response example:

    ```json
    {
      "unify_scope_id": 1,
      "is_finished": false
    }
    ```
*   Get organizations

    * URL: GET /api/v1/application/cdh/organizations
    * Response example:

    ```json
    [
      {
        "id": 11,
        "source": "caac",
        "name": "Test[Sta]-CS-CrescendoLab",
        "uuid": "48919660-0d39-4714-a183-b042bfae1143"
      },
      {
        "id": 1275,
        "source": "maac",
        "name": "Test[St]-CS-TW",
        "uuid": "48919660-0d39-4714-a183-b042bfae1143"
      }
    ]
    ```

Related reference: https://www.notion.so/d5092de991da4a0cb2b638a7920fbc50?pvs=21

***

If you want, I can:

* Extract the endpoints into a machine-readable OpenAPI/Swagger draft.
* Produce example requests/responses for the TBD endpoints (Get unify profile, Update contact unify key) if you provide expected fields.
