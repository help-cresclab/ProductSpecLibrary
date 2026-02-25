# Journey node v2\[X]

This page documents Node Categories, Triggers, Conditions, Rules, Actions, Attributes, Filters and related settings. Content preserved from original.

***

## Node categories (summary)

* Trigger (for starting point)
* Condition (for filter & Rule)
* Filter / Mechanism
* Attribute / Segment
* Rule (branching, waiting, exit)
* Action (channels and message/operation types)
* Member attributes / LINE friend status
* Integrations / Others

***

## Triggers (for starting point)

{% stepper %}
{% step %}
### Tagged event

* Type: Event
* Trigger type: Tagged event
* item content-layer1: {tagA}
* Timespan: -
* Phase: P1-1
{% endstep %}

{% step %}
### GA event — page view

* Type: GA event
* Trigger: page view
  * has viewed any page → Phase: P1-1
  * has viewed specific page: {pagelink} → Phase: P1-1
  * has viewed specific page ≥ {#} times → Phase: P1-1
  * has viewed specific page ≥ {#} secs & ≥ {#} times → Phase: Future
{% endstep %}

{% step %}
### GA event — purchase

* Trigger: purchase
  * has purchase any item → Phase: P1-1
  * has purchase specific item: {itemlink} → Phase: P1-1
{% endstep %}

{% step %}
### GA event — Cart-drop

* Trigger: Cart-drop
  * has added...to cart (specific item {itemlink}) → Phase: P1-2
  * has added...to cart any item → Phase: P1-2
{% endstep %}

{% step %}
### LINE Event — Join / Unblock / Block OA

* Join OA: {has joined} LINE OA → Phase: P2
* Unblocked LINE OA: {has unblocked} LINE OA → Phase: P2
* Block OA: {has blocked} LINE OA → Result: - {未授權} LINE OA → Phase: P4
{% endstep %}

{% step %}
### LINE Event — Open / Click message

* Open message:
  * has opened any broadcast → Phase: P2
  * has opened specific broadcast: {broadcast name/id} → Phase: P2
* Click message:
  * has clicked any broadcast → Phase: Future
  * has clicked specific broadcast: {broadcast name/id} → Phase: Future
{% endstep %}

{% step %}
### Binding event

* Completed binding → Phase: P2
{% endstep %}

{% step %}
### CAAC chat status change

* e.g., resolved → Phase: P4
{% endstep %}

{% step %}
### Integration (EC, etc.)

* Integration with EC...etc. → Phase: P5
{% endstep %}

{% step %}
### Segment attribute trigger

* Segment is {segmentA} → Phase: Future
{% endstep %}
{% endstepper %}

***

## Filter / Mechanism

* match all = AND (choose "is not / has not" instead of "exclude") → Phase: P1-1
* match any = OR → Phase: P1-1
* Note: Branch condition cannot be used with Filter for Phase1.

***

## Condition (for filter & Rule)

Maximum 5 conditions in 1 filter (unless noted).

{% stepper %}
{% step %}
### Tags

* is specific tag: {tagA} → Phase: P2
  * no multi-select: use multiple conditions for multiple tags ({tagA}, {tagB}, {tagC})
* is not specific tag: {tagA} → Phase: P2
* with any tag → Phase: P2
* without any tag → Phase: P2
{% endstep %}

{% step %}
### GA — page view data

Time windows supported: past 7 / 15 / 30 / 90 days (specified time)

* has viewed any page → Phase: Future
* has viewed specific page {pagelink}
  * with >= {#} secs → Phase: Future
  * with >= {#} times → Phase: Future
  * with >= {#} secs AND >= {#} times → Phase: Future
* has not viewed any page (within specified time) → Phase: Future
* has not viewed specific page {pagelink}
  * with >= {#} secs → Phase: Future
  * with >= {#} times → Phase: Future
  * with >= {#} secs AND >= {#} times → Phase: Future
{% endstep %}

{% step %}
### GA — purchase data

* has purchase any item (specified time window: past 7/15/30/90 days) → Phase: Future
* has purchase specific item {itemlink} (same windows) → Phase: Future
* has not purchase any item → Phase: Future
* has not purchase specific item {itemlink} → Phase: Future
{% endstep %}

{% step %}
### GA — cart-drop data

* has added...to cart any item (specified time windows) → Phase: Future
* has added...to cart specific item {itemlink} (specified windows) → Phase: Future
* has not added...to cart any/specific item → Phase: Future
{% endstep %}

{% step %}
### Member attribute conditions

* Customer ID: has data / no data → Phase: P3
* Gender: is Man / Female / Other → Phase: P3
  * single select; no "all gender" or "no data"
* Engagement Level: is Level 1–5 → Phase: P3
  * single select; no "all level"
* Phone: has data / no data → Phase: P3
* Email: has data / no data → Phase: P3
* Birthday:
  * is {YYYY/MM/DD} → Phase: P3
  * is between {specific date-start} and {specific date-end} → Phase: P3
{% endstep %}

{% step %}
### LINE friend status

* is Active / Blocked / Auth → Phase: P3
{% endstep %}
{% endstepper %}

***

## Rules

{% stepper %}
{% step %}
### Branching

* yes/no branch → with Branch condition (cannot have Filter for Phase1) → Phase: P1-1
* multi-branch → with Branch condition → Phase: P3
* Percentage split → with Branch condition → Phase: Future
* A/B testing → with Branch condition → Phase: Future
{% endstep %}

{% step %}
### Waiting time

* format: {Number} (Hours / Days) → Phase: P1-1
{% endstep %}

{% step %}
### Exit

* Exit node → Phase: P1-1
{% endstep %}
{% endstepper %}

***

## Actions (Channel / Action content type / Message type / Settings)

Note: "Phase" references original P1-1 / P1-2 / P1-3 / P2 / P3 / P4 / P5 / Future designations kept.

{% stepper %}
{% step %}
### LINE — Send Message (normal message)

* Action content types:
  * Send message to LINE — normal message
    * Action setting: {Send message}\_directly
    * Phase: P1-1
  * Smart sending (Sending\_Smarting sending)
    * Smart sending setting:
      * YYYY/MM/DD (will send on that date; time not specified)
      * Timezone: Taiwan timezone
    * Phase: P1-1
{% endstep %}

{% step %}
### LINE — Send cart-drop message

* Action content: cart-drop message
* Action setting: {Send message}\_directly
* Phase: P1-2
{% endstep %}

{% step %}
### LINE — DPM message

* Action content: DPM message
* Action setting: {Send message}\_directly
* Phase: P1-3
{% endstep %}

{% step %}
### PNP (third-party) — Send message

* Action content: [Case 1\~9](https://crescendolab.zendesk.com/hc/zh-tw/articles/4414003024025-%E9%80%9A%E7%9F%A5%E5%9E%8B%E8%A8%8A%E6%81%AF%E5%90%84%E6%83%85%E5%A2%83%E4%BD%BF%E7%94%A8%E8%A6%8F%E7%AF%84)
* Action setting: {Send message}\_directly
* Phase: P4
{% endstep %}

{% step %}
### SMS — Send message

* Action setting: {Send message}\_directly
* Phase: P4
{% endstep %}

{% step %}
### MAAC — Tag operations

* Add tag: {add tag}\_directly → tags: {tagA}, {tagB}, {tagC} → Phase: P3
* Remove tag: {remove tag}\_directly → tags: {tagA}, {tagB}, {tagC} → Phase: P3
{% endstep %}

{% step %}
### Update attribute (direct)

* update attribute\_directly for:
  * Customer ID → Phase: P3
  * Gender → Phase: P3
  * Engagement Level → Phase: P3
  * Phone → Phase: P3
  * Email → Phase: P3
  * Birthday → Phase: P3
{% endstep %}

{% step %}
### CAAC — send LINE message (customer care)

* CAAC chat template examples:
  * 售後關懷 (after-sales care) — for interaction with end user → Phase: P4
  * 當月壽星 (this month's birthday) — (template listed)
{% endstep %}

{% step %}
### Integration / Others

* Integration with more channels (e.g., WhatsApp) → Phase: P5
{% endstep %}

{% step %}
### Show web widget

* Action: {Show widget}\_directly
* item: {website widget name}
* Phase: Future
{% endstep %}
{% endstepper %}

***

## Notes / Memo

* Many nodes reference phases P1-1, P1-2, P1-3, P2, P3, P4, P5 or Future — preserved from original.
* Where the original indicated "Future", features or behaviors are not yet available (kept as-is).
* Links kept unchanged (example: PNP Case link).

***

If you want, I can:

* Export this as a single cleaned markdown table instead of steppers.
* Break Actions into a cards block for clickable internal pages.
* Convert numbered lists elsewhere into stepper blocks similarly.
