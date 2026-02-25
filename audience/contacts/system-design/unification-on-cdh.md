# Unification on CDH

## Goal and Requirement

1. Provide unification in Cross-product or Intra-product.
2. CDH, or Customer Data Hub, functions as both a database and a set of workers ingesting and broadcasting events from various applications (i.e., user updated maac member\_id =123 email to be qq@cresclab.com).
3. Unification setting can be based on {unify\_scope\_id, unify\_key} to achieve the different unification result — contact profile.

## Terminology

#### Channel Entity

* A channel entity represents the smallest unit for member within our system. Each channel entity possesses its own unique external member identifier, such as Line\_uid, mobile (SMS), Instagram\_id, or Facebook\_id.

#### Unify Key

* The unify key refers to designated attributes used to differentiate between individuals. In CrescendoLab, we have defined the following attributes as unify keys:
  * custom\_id
  * display\_mobile
  * display\_email
  * line\_uid
  * connect\_id 🆕

#### Contact Profile

* A contact profile is comprised of one or multiple channel entities that share the same unify key.
* For example, if an organization selects {connect\_id} as the unify key, the profile combines the latest valid values from all channel entities who share same unify key.\
  ![Untitled](<../../../.gitbook/assets/Unknown image>)

#### UnifyScope

* The Unify Scope helps define which organizations' channel entities are subject to unification.
* Since the same clients company within CrescendoLab may own different Business Units (BUs) belonging to separate Crescendo Lab organizations, either in MAAC or CAAC, our goal is to unify channel entities across these different orgs.
  * what is scope: the range of a subject covered by some rules.
  * what is UnifyScope: images below show conceptual diagrams.\
    ![Untitled](<../../../.gitbook/assets/Unknown image>)\
    ![Untitled](<../../../.gitbook/assets/Unknown image>)\
    ![Untitled](<../../../.gitbook/assets/Unknown image>)

## Propose solution

### 1. Overview - Architecture

The unification is a streaming processor which processes the WALs from event stores.

![Untitled](<../../../.gitbook/assets/Unknown image>)

* We separate the event stores, event process, and event driven components. This helps to build robust boundaries.

## Database

### DB - tables

#### BQ

**customer\_member\_wal**

| customer\_member\_wal |
| --------------------- |
| member\_id            |
| source                |
| attribute             |
| new\_value            |
| previous\_value       |
| source\_timestamp     |
| arrived\_timestamp    |

* example

| member\_id | source | attribute     | new\_value | previous\_value | source\_timestamp      | arrived\_timestamp     |
| ---------- | ------ | ------------- | ---------- | --------------- | ---------------------- | ---------------------- |
| 123        | maac   | display\_name | TY         | QQTY            | 2024-10-01T00:00:00.00 | 2024-10-01T00:00:00.00 |
| 456        | caac   | birthday      | 1990-01-01 | 2020-01-01      | 2024-10-01T00:00:00.00 | 2024-10-01T00:00:00.00 |

#### PG

**unify\_scope\_setting**

| unify\_scope\_setting |
| --------------------- |
| unify\_scope\_id      |
| name                  |
| updated\_at           |
| created\_at           |

* example

| unify\_scope\_id | name            | updated\_at | created\_at |
| ---------------- | --------------- | ----------- | ----------- |
| 1                | HUBSPOT\_PCHOME |             |             |
| 2                | maac\_2         |             |             |

**unify\_key**

| unify\_key       |
| ---------------- |
| id               |
| attribute        |
| unify\_scope\_id |
| is\_distinct     |

* note: is\_distinct should ALWAYS be False
* example

| id | attribute       | unify\_scope\_id | is\_distinct |
| -- | --------------- | ---------------- | ------------ |
| 1  | line\_id        | 1                | False        |
| 1  | display\_email  | 1                | False        |
| 1  | display\_mobile | 1                | False        |
| 1  | connect\_id     | 1                | False        |
| 1  | custom\_id      | 1                | False        |

**org\_unify\_scope**

| org\_unify\_scope |
| ----------------- |
| org\_id           |
| source            |
| unify\_scope\_id  |

* example

| org\_id | source | unify\_scope\_id |
| ------- | ------ | ---------------- |
| 1       | maac   | 1                |
| 2       | caac   | 1                |

**unification\_graph (unification\_graph\_v2)**

| unification\_graph\_v2      |
| --------------------------- |
| member\_id                  |
| source                      |
| unify\_scope\_id            |
| unify\_attribute            |
| unify\_key\_value           |
| composed\_unify\_key\_value |

* example

| unify\_key\_value                 | unify\_scope\_id | member\_id | source | unify\_attribute | composed\_unify\_key\_value                    |
| --------------------------------- | ---------------- | ---------- | ------ | ---------------- | ---------------------------------------------- |
| U4a17373204a10cb6370b6f1647e5db60 | 1                | 1          | maac   | line\_id         | U4a17373204a10cb6370b6f1647e5db60\_1\_line\_id |
| 0988888888                        | 1                | 2          | caac   | display\_mobile  | 0988888888\_1\_display\_mobile                 |

#### Business domain

* Channel Entity: the basic unit of member in MAAC/CAAC

| name       | type | description                             |
| ---------- | ---- | --------------------------------------- |
| source     | str  | Enum(maac, caac)                        |
| member\_id | int  | the member\_id in its own source system |

* Profile: A dict showing all attributes that belong to either contact or channel\_entity. Example:

```json
{
  "note": "臣亮言：先帝創業未半而中道崩殂，",
  "bot_id": "98",
  "gender": "male",
  "health": "weak",
  "status": "active",
  "line_id": "Ua03e68f82280c2d3c0355b8927ed6a43",
  "birthday": "2022-01-19",
  "location": null,
  "org_uuid": "6e3329e0-38c2-4899-bafe-a85dfab71cdb",
  "custom_id": "customer_DavidChou",
  "channel_id": "1567460013",
  "created_at": "2022-06-24T18:32:06.009655Z",
  "display_name": "羽鵑",
  "last_engaged": "2022-11-14T10:51:10.808274Z",
  "display_email": "qq@email.com",
  "original_name": "David Chou",
  "display_mobile": "0911",
  "original_email": "test_maac@emial.com",
  "last_message_at": "2023-04-21T11:32:15.498047Z",
  "original_mobile": "+8863534134",
  "connect_id": null
}
```

* Unified Channel Entity
  * an array of the Channel Entities meaning the elements share the same unify\_scope\_id and unify\_key. The length of the array could be 1 or more.
  * example:

```json
[
  { "source": "caac", "member_id": 512187 },
  { "source": "maac", "member_id": 2882101 },
  { "source": "caac", "member_id": 512044 },
  { "source": "caac", "member_id": 512175 },
  { "source": "maac", "member_id": 2881552 },
  { "source": "maac", "member_id": 2881553 }
]
```

## 3. Critical Workflow

#### Workers

We have several workers to handle different tasks:

* graph\_maker (unify-member-and-update-profile)
  * When any profile WAL is ingested, CDH upserts the entity’s profile and updates the unification\_graph.
* broadcast-member-update-worker
  * When any profile WAL is ingested by CDH, the worker will broadcast the attribute-based event to its unified channel entities.
* (unified\_work)broadcast-contact-profile-with-unified-entity-worker
  * When any specified unify-key of profile WAL is ingested by CDH, the worker broadcasts the profile-based event to its unified channel entities; broadcasts tag events with inherited label and its unified channel entities; upserts the contact tag for each unified channel entity into the database.
* update-member-tag-worker
  * When tag WAL is ingested by CDH, the worker upserts the profile-tag table for its unified channel entities.

#### Jobs

* UnifyScopeSettingChange:
  * If unified orgs changes:
    * cdh-update-edges-unify-scope updates edges’ unify\_scope\_id on table unification\_graph\_v2.
    * \[cloud run job] cdh-broadcast-contact-profile-under-scope broadcasts (publishes) all edges’ contact profile under the unify\_scope.
  * If unified orgs unchanged but unify\_key changes:
    * cdh-broadcast-contact-profile-under-scope will broadcast all edges’ contact profile under the unify\_scope.
  * Otherwise do nothing.

#### API (influences subgraph)

* MoveSubgraph (deprecated): API that used to clear the entity’s profile and changed its unify\_key attributes. The new flow leaves broadcast-contact-profile-with-unified-entity-worker to handle subgraph changes.

#### Workflow Dependence

* The sequence below indicates worker dependencies (logical influence):
  * graph maker (v2)
  * unified\_channel\_entity
  * initial member/member update broadcaster (would combine the members into one)

![Untitled](<../../../.gitbook/assets/Unknown image>)

#### Graph Maker v2

Process attribute changes on channel entity to unification graph. (Blue line)

![Untitled](<../../../.gitbook/assets/Unknown image>)

Sequence:

```
Application ->> WALs: CUD on channel members of apps
WALs ->> Profile: [GraphMaker] upsert profile in CDH
WALs ->> Unification Graph: [GraphMaker] upsert any edge-changes involved custom_id, mobile, email, or line_id
```

#### Unified Channel Entity Profile Update Broadcaster

The broadcaster broadcasts events about new profile (Green line).

![Untitled](<../../../.gitbook/assets/Unknown image>)

Sequence:

```
Application[CAAC MAAC] ->> CDH: fetch the change event
note right of Application[CAAC MAAC]: Show notification of merging
CDH ->> CDH: update unification
CDH ->> Queue: Send all unified members' profile
Application[CAAC MAAC] -->> Queue: pull events and overwrite profile
note right of Application[CAAC MAAC]: Show notification of merged
```

#### Change Unification Setting (Job)

Broadcaster of command-event:

* Setting: unify key
  * We provide the event-driven job that once we find any org whose unify\_keys ({custom\_id, connect\_id, display\_mobile, display\_email}) are set, we send the member’s unified profile for all involved channel entities.
  * Example message:

```json
{
  "topic": "unified_channel_entity.update",
  "profile": {
    "note": "",
    "bot_id": "47",
    "gender": "female",
    "health": null,
    "status": "active",
    "line_id": "Uecd1fe7455f1eca7300054bf24181a95",
    "birthday": "9999-12-31",
    "location": "",
    "org_uuid": "144529b5-249e-42aa-9bd7-0453ccb4177a",
    "custom_id": "",
    "channel_id": "1577288112",
    "created_at": "2022-06-17 05:57:05.495315+00",
    "display_name": "美惠(_;)",
    "last_engaged": null,
    "display_email": "",
    "original_name": "美惠(_;)",
    "display_mobile": null,
    "original_email": "",
    "last_message_at": "2022-06-17 04:42:13.148+00",
    "original_mobile": ""
  },
  "unified_channel_entities": [
    {"source": "caac", "member_id": 134982}
  ]
}
```

Sequence:

```
Apps ->> CDH: unify_scope change unify key
CDH ->> CDH: update unify_key
CDH ->> Cloud Run Job: trigger job
Cloud Run Job ->> CDH: re-unify the profile (under the unify_scope)
Cloud Run Job -->> Queue: Pull events
```

* Setting: unify scope
  * We provide an event-driven job that once we find any org updated its unify\_scope\_id, we send the member’s unified profile for all channel entities under its unify\_scope\_id.

Sequence:

```
Application[CAAC MAAC platform] ->> CDH: update unify keys (applied)
note right of Application: Show notification of merging
CDH ->> CDH: update unify settings
CDH ->> Queue: Send all influenced unified members' profile
loop pull
Application[CAAC MAAC] -->> Queue: pull events and overwrite profile
end
```

#### Event-driven Job

* Goal: to re-unify or unify the orgs which just updated their unify setting ({unify\_keys, unify\_scope\_id}).
* Job: updates all the channel entities under args — --unify\_scope\_id.
* The job sends event messages to the topic: staging-unified-channel-entity-profile-update-event.

#### Query flow

Sequence:

```
Application ->> API: Request a member profile
API ->> Unify_key: Fetch all Unify_key for the org which the member belongs
Unify_key -->> API: return the {"unify_key_attribute", "is_distinct"}
API ->> Unification: find all unified members based on `unify_key_attribute`
Unification -->> API: Return all unified members {"member_id","source"}
API ->> Profile: Fetch all profiles belongs to all unified members
Profile -->> API: Return the merged profile
API -->> Application: Return the merged profile
```

## API spec

production: https://cdh-production.internal.cresclab.com\
staging: https://cdh-staging.internal.cresclab.com

How to access token: gcloud auth print-identity-token

* In staging, you will need the ID token; we are considering using a simple token instead of the ID token and will notify ASAP if there is any change.
* In production, there is no authentication (production CDH service will only accept internal traffic within the same VPC).

### Endpoints

* GET /member/\{{source\}}/\{{member\_id\}}/unified\_channel\_entity
* GET member/\{{source\}}/unified\_channel\_entities?member\_ids=\{{member\_id\_1\}}\&member\_ids=\{{member\_id\_2\}}

#### Description

Retrieve all channel entities associated with multiple members from CDH.

#### Path parameters

* source (required): the member exists in {maac, caac}

#### Query parameters

* member\_ids (required): the member\_id(s) for the source

#### Request Headers

* Authorization: Bearer {token}

#### Responses

Example request: member/maac/unified\_channel\_entities?member\_ids=1\&member\_ids=2

Success 200

```json
{
  "1": [
    { "source": "maac", "member_id": 1 },
    { "source": "caac", "member_id": 511767 },
    { "source": "caac", "member_id": 512316 }
  ],
  "2": [
    { "source": "maac", "member_id": 2 }
  ]
}
```

Fail 404

```json
{ "detail": "Not Found" }
```

* GET /member/\{{source\}}/\{{member\_id\}}/contact\_profile

#### Description

Retrieve unified profile from one channel entity's unified channel entities.

#### Path parameters

* memberId (required)
* source (required): one of {maac, caac}

#### Request Headers

* Authorization: Bearer {token}

#### Responses

Success 200

```json
{
  "note": "臣亮言：先帝創業未半而中道崩殂，",
  "bot_id": "98",
  "gender": "male",
  "health": "weak",
  "status": "active",
  "line_id": "Ua03e68f82280c2d3c0355b8927ed6a43",
  "birthday": "2022-01-19",
  "location": null,
  "org_uuid": "6e3329e0-38c2-4899-bafe-a85dfab71cdb",
  "custom_id": "customer_DavidChou",
  "channel_id": "1567460013",
  "created_at": "2022-06-24T18:32:06.009655Z",
  "display_name": "羽鵑",
  "last_engaged": "2022-11-14T10:51:10.808274Z",
  "display_email": "qq@email.com",
  "original_name": "David Chou",
  "display_mobile": "0911",
  "original_email": "test_maac@emial.com",
  "last_message_at": "2023-04-21T11:32:15.498047Z",
  "original_mobile": "+8863534134",
  "connect_id": null
}
```

Fail 404

```json
{ "detail": "Not Found" }
```

* PATCH /member/\{{source\}}/\{{member\_id\}}/contact\_profile

#### Description

Update unified profile from one channel entity's unified channel entities.

#### Path parameters

* memberId (required)
* source (required): one of {maac, caac}

#### Request Body

```json
{ "custom_id": "string" | null, "display_email": "string" | null, "display_mobile": "string" | null, "connect_id": "string" | null }
```

Example: {"display\_email": "a@gmail.com"}

#### Request Headers

* Authorization: Bearer {token}

#### Responses

Success 200

```json
{ /* merged profile, same as GET response example */ }
```

Fail 422

```json
{
  "detail": [
    { "loc": ["string",0], "msg": "string", "type": "string" }
  ]
}
```

* GET /unify\_scope\_setting/\{{source\}}/\{{orgId\}}

#### Description

Retrieve unify\_scope\_setting of a specific org. Use to tell whether the org is connected with any other orgs.

#### Path parameters

* orgId (required)
* source (required): {maac, caac}

#### Request Headers

* Authorization: Bearer {token}

#### Responses

Success 200 example:

```json
{
  "unify_scope_id": 1,
  "orgs":[ {"id":1, "source": "maac"}, {"id":1, "source": "caac"} ],
  "unify_keys":[ {"attribute":"line_id","is_distinct":false}, {"attribute":"custom_id","is_distinct":false} ],
  "distinct_key": null
}
```

Fail 404

```json
{ "detail": "Not Found" }
```

* POST /unify\_scope\_setting/

#### Description

Create a brand new unify\_scope for its unify\_key. Use PATCH API to add orgs.

#### Request Body

```json
[
  {"attribute":"line_id","is_distinct":false},
  {"attribute":"custom_id","is_distinct":false}
]
```

#### Request Headers

* Authorization: Bearer {token}

#### Responses

Success 200 example:

```json
{
  "unify_scope_id": 0,
  "orgs": [ { "id": 0, "source": "maac" } ],
  "unify_keys": [ { "attribute": "string", "is_distinct": true } ],
  "distinct_key": "string"
}
```

Fail 404

```json
{ "detail": "Not Found" }
```

* PUT /unify\_scope\_setting/\{{unify\_scope\_id\}}/unify\_keys

#### Description

Update the unify\_scope\_id's unify\_keys.

#### Request Body

Examples:

```json
{ "unify_keys": [ {"attribute":"line_id","is_distinct":false}, {"attribute":"custom_id","is_distinct":false} ] }
```

or

```json
{ "unify_keys": [ {"attribute":"custom_id","is_distinct":false}, {"attribute":"custom_id","is_distinct":false}, {"attribute":"display_mobile","is_distinct":false} ] }
```

#### Request Headers

* Authorization: Bearer {token}

#### Responses

Success 200 example:

```json
{
  "org_id":1,
  "source":"maac",
  "unify_scope_id": 1,
  "uniy_scope_name": "6e3329e0-38c2-4899-bafe-a85dfab71cdb",
  "unify_keys":["external_member_id"],
  "orgs":[ {"org_id":1, "source": "maac"}, {"org_id":1, "source": "caac"} ]
}
```

Fail 404

```json
{ "detail": "Not Found" }
```

* PATCH /unify\_scope\_setting/\{{unify\_scope\_id\}}/orgs

#### Description

Move orgs under unify\_scope\_id.

#### Request Body

```json
{ "orgs": [ {"source":"maac", "id":1}, {"source":"caac", "id":1} ] }
```

#### Request Headers

* Authorization: Bearer {token}

#### Responses

Success 200

```json
{
  "unify_scope_id": {{unify_scope_id}},
  "uniy_scope_name": "6e3329e0-38c2-4899-bafe-a85dfab71cdb",
  "orgs":[ {"org_id":1, "source": "maac"}, {"org_id":1, "source": "caac"} ]
}
```

Fail 404

```json
{ "detail": "Not Found" }
```

* GET /member/\{{source\}}/\{{member\_id\}}/tags

#### Description

Retrieve a channel entity's tags which come from all its contacts. Tags are attached/removed when two channel entities are merged.

#### Path parameters

* memberId (required)
* source (required): {maac, caac}

#### Request Headers

* Authorization: Bearer {token}

#### Responses

Success 200 example:

```json
[
  { "tag_id": 14, "tag_name": "yeshahaha", "source": "caac", "is_attached": true, "source_timestamp": "2023-11-29T06:07:50.563943+00:00" },
  { "tag_id": 4677, "tag_name": "測試測試", "source": "caac", "is_attached": true, "source_timestamp": "2023-06-01T06:28:31.761926+00:00" },
  { "tag_id": 728085, "tag_name": "鵑鵑測試貼標", "source": "caac", "is_attached": true, "source_timestamp": "2022-06-23T14:27:26.742680+00:00" }
]
```

Fail 404

```json
{ "detail": "Not Found" }
```

* POST /member/import/
  * Concurrency import task limit: 1. Clients can poll the task status API to check task status.

Sequence:

```
Client ->> CDH: send Import member request
CDH ->> DB-Task table: Check running and pending tasks with concurrency limit
CDH ->> DB-Task table: Create a pending task
CDH ->> GCS: Upload the import data
CDH ->> Client: return response with task id
Client ->> CDH: check task status
CDH ->> DB-Task table: return status
Worker ->> DB-Task table: update status to running
Worker ->> GCS: retrieve import data
Worker: do import in batch and update progress to db
Worker ->> DB-Task table: update status to complete
```

* GET /org

#### Description

Retrieve orgs

#### Query parameters

* org\_uuid (optional): the uuid of the org in MAAC or CAAC

#### Request Headers

* Authorization: Bearer {token}

#### Responses

Success 200 example:

```json
[
  { "id": 11, "source": "caac", "name": "Test[Sta]-CS-CrescendoLab", "uuid": "48919660-0d39-4714-a183-b042bfae1143" },
  { "id": 1275, "source": "maac", "name": "Test[St]-CS-TW", "uuid": "48919660-0d39-4714-a183-b042bfae1143" }
]
```

* POST /member/{source}/{member\_id}/move\_subgraph

#### Description

Special API for moving a channel entity to a specific contact profile (subgraph).

#### Request Body example

```json
{ "custom_id": "customer_Jin" }
```

Allowed keys: custom\_id, connect\_id, display\_email, display\_mobile

#### Request Headers

* Authorization: Bearer {token}

#### Responses

* Success 204
* Fail 404: { "detail": "Not Found" }
* Fail 400: { "detail": "Bad Request" }

## Event Spec

### Contact profile event — Decoded data format

Example payload:

```json
{
  "metadata": {
    "type": "unify_scope_setting_update",
    "unify_scope_id": 1,
    "orgs": [ { "id": 1, "source": "caac" } ],
    "is_last_batch": false
  },
  "events": [
    {
      "topic": "contact.update",
      "timestamp": "2024-02-20T17:40:32.774210+00:00",
      "profile": { /* profile object */ },
      "unified_channel_entities": [ { "source": "maac", "member_id": 2877075 } ],
      "unification_updated_at": "2020-03-31T15:14:26.577972+00:00"
    },
    { /* another event */ }
  ]
}
```

### Tag Update Event

Example:

```json
{
  "metadata": { "type": "member_tag_update" },
  "events": [
    {
      "timestamp": "2024-04-13T10:43:23.947887+00:00",
      "topic": "member.tag.update",
      "unified_channel_entities": [
        { "member_id": 512249, "source": "caac" },
        { "member_id": 512253, "source": "caac" },
        { "member_id": 2882285, "source": "maac" },
        { "member_id": 2882280, "source": "maac" }
      ],
      "tags": [
        { "tag_id": 123, "source": "caac", "action": "add" },
        { "tag_id": 567, "source": "maac", "action": "add" },
        { "tag_id": 456, "source": "caac", "action": "delete" }
      ]
    }
  ]
}
```

* metadata is dynamic and optional. Examples:
  *   If triggered by updating unification setting:

      ```json
      { "type": "unify_scope_setting_update", "unify_scope_id": 1, "orgs": [ { "id": 1, "source": "caac" } ], "is_last_batch": false }
      ```
  *   If triggered by importing:

      ```json
      { "type": "member_import" }
      ```
  *   Channel entity's unification change:

      ```json
      { "type": "channel_entity_profile_update" }
      ```
  *   Channel entity's tag update:

      ```json
      { "type": "channel_entity_tag_update" }
      ```

#### Security

* We will use JWT (RS256) instead of push auth of Pub/Sub.
  * RS256 decoding benchmark: \~2000–2500 RPS. Slower than HS256 but sufficiently fast and avoids shared secret keys across systems.

## Tasks

### Product

#### All possible settings-tasks

{% stepper %}
{% step %}
### Inter-caac setting: update unify\_keys

* Endpoint: PUT unify\_scope\_setting/\{{unify\_scope\_id\}}/unify\_keys
* Input: unify\_keys
* Following job: broadcast (cdh-broadcast-contact-profile-under-scope)
{% endstep %}

{% step %}
### Enable CDH (connect two orgs with same org\_uuid)

Steps:

1. POST unify\_scope\_setting/ — input: one org
2. GET /org — query\_parameter: org\_uuid
3. PATCH unify\_scope\_setting/\{{unify\_scope\_id\}}/orgs — input: orgs
4. PUT unify\_scope\_setting/\{{unify\_scope\_id\}}/unify\_keys — input: unify\_keys
5. Following job: broadcast
{% endstep %}

{% step %}
### After Enable CDH (operations)

* Update unify\_keys (UI)
  * PUT unify\_scope\_setting/\{{unify\_scope\_id\}}/unify\_keys — input: unify\_keys
  * Following job: broadcast
* Disconnect (UI)
  * POST unify\_scope\_setting/
  * Create each org’s unify\_scope\_setting respectively
  * PATCH unify\_scope\_setting/\{{unify\_scope\_id\}}/orgs
* Add more orgs under unify\_scope\_setting (ticket)
  * PATCH unify\_scope\_setting/\{{unify\_scope\_id\}}/orgs — input: orgs, unify\_keys
{% endstep %}
{% endstepper %}

#### Application Page

* Support the unification setting UI.
* API to display unification setting:
  * unify\_scope\_id
  * unify\_key
* API to create/modify/delete unification settings:
  * unify\_scope\_id
  * unify\_key

#### Profile Usage

* Update the attribute designated as unify\_key for all unified channel entities.
* Cancel unification on a specific channel entity.
* Modify a channel entity to another unified contact.

#### Unification Process

* Leverage WALs to implement the unification graph.
* Broadcaster from profile unify key changes (note: apps only update editable profile fields).

### Apps

* modify member._update\_unification\_graph_:
  * Description: function updates/inserts unification edges when graph\_maker runs.
  * sol1:
    * iterate WALs → if changed attribute ∈ {line\_id, mobile, email, custom\_id, connect\_id} → insert/update row on {member\_id, source} with (uuid, unify\_key\_attribute, member\_id, source) using value of WAL and attribute.
    * Pros: no need to query existing edges; insert all WALs regardless of org’s setting (saves effort when clients update settings).
    * Cons: need to backfill existing uuids in unification graph.
  * sol2:
    * iterate WALs → only insert/update when changed attribute belongs to org’s unify\_key setting → insert/update row with hashed value.
    * Pros: minimizes unification graph volume.
    * Cons: when user changes unify\_key, requires replay of WALs.
* repo.unification\_graph._get\_unify\_key\_subgraphs\_by\_member\_id_
  * Description: given a channel entity (e.g., {"member\_id":123,"source":"maac"}), return a list of connected channel entities.
  * Approach:
    * fetch the unify\_key setting for the org (list of unify keys & is\_distinct flags).
    * fetch all unification\_graph rows where unify\_key\_attribute ∈ that set.
    * traverse nodes and their connected nodes. For distinct-key cases, traverse within distinct key subgraphs.
* repo.profile.unified\_member\_profile
  * Based on nodes returned by fetch\_unified\_members:
    * ignore NULL values
    * take the most recent updated value
* add event\_broker.unified\_event (WIP)
* add a Cloud Run job to update unify\_key attribute (WIP)
* unify\_key value change cases:
  1. Change in one channel\_entity (it may be removed from unified set)
     * CAAC receives the unify\_key value change WAL (always present).
     * CAAC receives the profile WAL only when unify\_key changed.
  2. All channel\_entities change together → contact\_profile level change
     * CAAC receives the profile WAL only when unify\_key changed.

## Test

* Regression test cases:
  * Single rules: line\_id, display\_mobile, display\_email, custom\_id
  * Composed rules: {line\_id, display\_mobile}, {line\_id, display\_mobile, display\_email}, {line\_id, display\_mobile, display\_email, custom\_id}, {display\_mobile, display\_email, custom\_id}, {display\_mobile, custom\_id}
  * Example member records (A..J, H duplicates, etc.) — test merges, splits, null handling.

![Untitled](<../../../.gitbook/assets/Unknown image>)

## Q\&A

<details>

<summary>1. Update unify_key setting (How is this handled?)</summary>

Flow (sequence):

```
Application ->> API: Request CRUD a unify_key to one org.
API ->> Unify_key: Update all Unify_key.
Unify_key -->> API: return
API ->> Unification Graph: Fetch unified edges belonging to the updated `unify_key_attribute`
Unification -->> API: Return all unified members {"member_id","source"}
API -->> Application: Return the unified members
```

Note: This is replaced by the Broadcaster: Change Unification Setting (Job). Instead of returning only channel entities, the broadcaster returns all channel entities’ profiles and triggers events to re-broadcast under the affected unify\_scope.

</details>

## Additional worker / tag flow notes

* Direct Write Tag Worker flow vs Original Flow:
  * OriginalFlow:
    1. fetch all tag WALs (+ bq name)
    2. upsert\_member\_tags
    3. generate: a) broadcast event \[not\_inherited, inherited], b) contact\_wal
    4. upsert contact tag
    5. broadcast events
  * DirectWriteFlow:
    1. fetch original-not-inherited tag
    2. upsert\_member\_tags
    3. generate: a) broadcast event \[not\_inherited, inherited], b) contact\_wal
    4. upsert contact tag
    5. broadcast events
    6. upsert contact tag
    7. broadcast events
* API: POST member/{member\_source}/tag/\_bulk
  * Batch update member tags.
  *   Request Body example:

      ```json
      [
        { "member_id": 1, "tag_id": 1, "tag_name": "Taiwan No.1", "tag_source": "maac", "is_attached": false },
        { "member_id": 1, "tag_id": 2, "tag_name": "QQ Tag", "tag_source": "maac", "is_attached": true }
      ]
      ```
  * Responses: Success 204
* WAL models (examples)
  * MemberTagWALWithName:
    * member\_id: int
    * tag\_id: int
    * is\_deleted: bool
    * source: Source
    * source\_timestamp: ISODatetime
    * tag\_name: str
  * ContactTagWALWithName:
    * member\_id: int
    * tag\_id: int
    * member\_source: Source
    * tag\_source: Source
    * tag\_name: str
    * is\_deleted: bool
    * source\_timestamp: ISODatetime
    * inherited: bool = False
* Upsert + Broadcast steps:
  1. fetch MemberTagWAL-like data
  2. build ContactTagWAL-like data
  3. upsert + broadcast as above

(End of document)
