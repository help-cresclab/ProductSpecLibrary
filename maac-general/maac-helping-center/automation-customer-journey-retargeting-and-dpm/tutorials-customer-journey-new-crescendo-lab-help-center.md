# Tutorials｜Customer Journey ✨ New ✨ – Crescendo Lab Help Center

## Feature Overview

Customer Journey (Journey) is MAAC’s marketing automation flow design tool that allows brands to build multi-stage, personalized communication journeys based on contact behavior and conditions, improving engagement and conversion rates.

This feature supports cross-channel message delivery (e.g., LINE, SMS), tag management (add/remove), and behavior tracking.

Common use cases include:

* New customer welcome journey (via LINE / SMS)
* Real-time reaction triggers (e.g., block, add friend)
* High-value customer tagging and behavior maintenance

Through a visual editor, you can connect the following nodes:

* Define trigger conditions (e.g., friend added, blocked, page viewed)
* Send messages (LINE, SMS), add delay timers, and create behavior splits
* Add/remove tags, control frequency and quiet hours
* Track node engagement and conversion performance (open rate, CTR, revenue, etc.)

## Setup Guide

{% stepper %}
{% step %}
### Create a Journey

* Go to the “Customer Journey” page and click **\[Create New Journey]**
* Enter the journey name
* Decide whether to enable a schedule (e.g., run daily at 9:00 AM)
* Set the number of times each contact can enter (default: unlimited)
* Configure **message send limit** (e.g., max 1 SMS per person)
* Set **Quiet Hours** (e.g., do not send between 00:00–08:00)

{% hint style="warning" %}
Once the message limit is enabled, you can only increase the cap — you cannot remove or disable it.

To reset, use the **\[Duplicate Journey]** function.
{% endhint %}

{% hint style="info" %}
Unified Contact Definition: Contacts across different channels are matched by Unify Key (e.g., phone number, email) and merged into a single True Contact identity.
{% endhint %}
{% endstep %}

{% step %}
### Set Trigger Conditions (Choose One)

Each journey can only have one trigger source, including:

* **Website Events** (requires SDK or GA4): Page view, add to cart, purchase, etc.
* **LINE Events**: Add friend, block, open message
* **Attribute Change**: Add tag

{% hint style="info" %}
Default Limitations:

* Same tag trigger: each True Contact can trigger once per hour
* GA event trigger: once per day
{% endhint %}
{% endstep %}

{% step %}
### Design Journey Nodes

Each node supports the following actions:

* Send Message: LINE, SMS
* Add / Remove Tags
* Branch Conditions: Based on tags, web events, or reachability
* Delay: Minute / hour / day / week interval control

{% hint style="info" %}
Before using SMS: SMS sending requires prior activation by Crescendo Lab and sufficient MAAC point balance. Insufficient balance or unactivated SMS will cause delivery failure.

For details, see: [Feature Description｜MAAC Point Deduction and Recharge Mechanism](https://crescendolab.zendesk.com/hc/en-us/articles/4414010746393)
{% endhint %}

Node limitations:

* Each journey supports up to 30 nodes (including exit nodes).
* Each action can add/remove up to 5 tags, and the processing order is not guaranteed.
{% endstep %}

{% step %}
### Publish & Activate

After completing the design, click **\[Publish]** to activate the journey. You can monitor performance via “Journey Overview” and “Node Performance Report.”

{% hint style="info" %}
SMS Delivery Note: If SMS delivery fails in a node, you can download the failed delivery list from the journey’s settings page. Delivery logs for the past 2 months are available.
{% endhint %}
{% endstep %}
{% endstepper %}

## Metrics & Reporting

### Performance Metrics by Channel

| Metric                   | Calculation                                                     | Description                                        |
| ------------------------ | --------------------------------------------------------------- | -------------------------------------------------- |
| Messages Sent            | Total messages sent                                             | All successfully delivered messages (LINE and SMS) |
| Open Rate                | LINE: Daily Unique opens / Sent messages                        | Only supported for LINE; SMS has no open data      |
| Click-Through Rate (CTR) | <p>LINE: Total clicks / Opens<br>SMS: Total clicks / Sent</p>   | Calculated per channel; combined CTR available     |
| Unique Click Rate        | <p>LINE: Unique clicks / Opens<br>SMS: Unique clicks / Sent</p> | Requires GA4 + UTM tracking                        |
| Add to Cart              | GA4 add\_to\_cart events                                        | Requires GA4 integration                           |
| Orders                   | GA4 purchase events                                             | Requires GA4 integration                           |
| Revenue                  | GA4 revenue value                                               | Requires GA4 integration                           |

### Node Performance Report Metrics

Data updates hourly. Report export is currently not supported.

| Metric            | Description                                                     |
| ----------------- | --------------------------------------------------------------- |
| Message Name      | Corresponds to the node name in the journey                     |
| Sent Count        | Total successfully sent messages                                |
| Opens             | LINE only; SMS displays as N/A                                  |
| Open Rate         | LINE: Unique opens / Sent messages                              |
| Clicks            | Total clicks via MAAC short links                               |
| CTR               | <p>LINE: Clicks / Opens<br>SMS: Clicks / Sent</p>               |
| Unique Clicks     | Unique clicks tracked via GA4 + UTM                             |
| Unique Click Rate | <p>LINE: Unique clicks / Opens<br>SMS: Unique clicks / Sent</p> |
| SMS Units         | Billing units calculated by message length (SMS only)           |
| Add to Cart       | GA4 add\_to\_cart events attributed to this node                |
| Orders            | GA4 purchase events attributed to this node                     |
| Revenue           | Total GA4 revenue attributed to this node                       |

## FAQ

<details>

<summary>Feature Availability &#x26; Limits — Do I need to enable Node Report?</summary>

Only journeys created after Aug 11, 2025, support node reporting.

</details>

<details>

<summary>Feature Availability &#x26; Limits — How many journeys can I create per account?</summary>

Up to 350 journeys (subject to plan limits).

</details>

<details>

<summary>Feature Availability &#x26; Limits — Can I set multiple triggers?</summary>

No. Each journey supports only one trigger source. To cover multiple triggers, create separate journeys or use conditional branches.

</details>

<details>

<summary>Feature Availability &#x26; Limits — Any limits for SDK or GA triggers?</summary>

Web SDK Triggers:

* Each True Contact can trigger once per hour
* Real-time triggers suitable for shopping or interaction events
* Recognizes users from LINE/SMS if SDK includes identifiers

GA Triggers:

* Only for contacts entering the site via LINE
* Delay of approx. 24–48 hours
* Once per day per True Contact

</details>

<details>

<summary>Feature Availability &#x26; Limits — Are there system-wide send limits?</summary>

No overall send frequency limit across channels, but you can configure per-channel limits (e.g., LINE, SMS).

</details>

<details>

<summary>Contacts &#x26; Frequency — Can the same user trigger a journey from different channels?</summary>

By default, each True Contact can trigger once per hour (GA triggers once per day). Even if multiple actions occur simultaneously, only one trigger will be processed.

</details>

<details>

<summary>Contacts &#x26; Frequency — What is a True Contact?</summary>

A unified identity created by matching multiple channel profiles (e.g., LINE + phone number). Triggers are managed per True Contact.

</details>

<details>

<summary>Contacts &#x26; Frequency — If a tag is added to multiple channel contacts, will it sync?</summary>

Yes. Tags sync instantly across all channels within the same True Contact and appear in the contact detail view with source “MAAC Tag.”

</details>

<details>

<summary>Contacts &#x26; Frequency — If a LINE account is linked to multiple phone numbers, which one is used?</summary>

The system prioritizes the contact record with the most recent activity.

</details>

<details>

<summary>Sending &#x26; Node Control — What’s the max number of nodes per journey?</summary>

30 nodes (including exit).

</details>

<details>

<summary>Sending &#x26; Node Control — What happens if SMS balance runs out?</summary>

The node will stop, and subsequent nodes won’t execute. The system displays a warning icon and sends a notification email to the MAAC admin.

</details>

<details>

<summary>Sending &#x26; Node Control — How to control channel priority?</summary>

Use the “Reachability Branch” node to set fallback logic (e.g., if LINE unavailable → send SMS).

</details>

<details>

<summary>Editing &#x26; Versioning — Can I edit a live journey?</summary>

You can modify existing node settings (e.g., message content, delay) but cannot add or delete nodes. Pause the journey before editing.

</details>

<details>

<summary>Editing &#x26; Versioning — Are previous versions stored?</summary>

No. Please record your own changes and timestamps.

</details>

<details>

<summary>Data &#x26; Reports — How often does the Node Report update?</summary>

Every hour.

</details>

<details>

<summary>Data &#x26; Reports — Can reports be exported?</summary>

Not supported currently.

</details>

<details>

<summary>Data &#x26; Reports — How is Unique Click calculated?</summary>

Requires GA4 + UTM. Multiple clicks from the same contact are deduplicated — only the first counts.

</details>

{% hint style="warning" %}
SDK events (e.g., page\_view, purchase) are not reflected in CTR, revenue, or order metrics. Use GA4 UTM tracking to measure conversions.
{% endhint %}

## SDK Integration Notes

1. Web SDK installation required
2. Supported events:
   * `page_view`: Page view
   * `add_to_cart`: Add to cart
   * `purchase`: Purchase completed
3. SDK affects “Journey Entry” and “Branch Conditions” only, not CTR/revenue reports
4. Each True Contact can trigger one SDK event per hour
5. You can filter by “Web Channel” in triggers (up to 5 sources)

See setup guide: [Setup Guide｜Web SDK Installation](https://crescendolab.zendesk.com/hc/en-us/articles/41430052123801)

## Use Case Examples

For detailed scenarios, please refer to: [Use Cases｜Journey Feature Application Guide](https://crescendolab.zendesk.com/hc/en-us/articles/49575668897305)

### Related articles

* [Tutorials｜MAAC Message Module & Template Library](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkb49oDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkQ8ocDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJUL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQ2MDM3Mjk2ODktVHV0b3JpYWxzLU1BQUMtTWVzc2FnZS1Nb2R1bGUtVGVtcGxhdGUtTGlicmFyeQY7CFQ6CXJhbmtpBg%3D%3D--e262e4e33959fa5f44a8e1a7919ee31417dd967d)
* [Tutorials｜ MAAC x SurveyCake Form](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkr5rYDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkQ8ocDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJGL2hjL2VuLXVzL2FydGljbGVzLzQ0MTM5OTk5NTA3NDUtVHV0b3JpYWxzLU1BQUMteC1TdXJ2ZXlDYWtlLUZvcm0GOwhUOglyYW5raQc%3D--4e3ecca793c5d99cd21604dfcdce13a8fb54ddbe)
* [Feature Description｜MAAC Contact Import and Update](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBnqhYkDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkQ8ocDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJYL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMzg2Njc4MDEtRmVhdHVyZS1EZXNjcmlwdGlvbi1NQUFDLUNvbnRhY3QtSW1wb3J0LWFuZC1VcGRhdGUGOwhUOglyYW5raQg%3D--d5516a1e409b88ceae27a9e685d4b8bc657f9d11)
* [Tutorials｜CAAC Users](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJnaVfz6BjoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkQ8ocDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI6L2hjL2VuLXVzL2FydGljbGVzLzc2NzUwNDUwNzU2MDktVHV0b3JpYWxzLUNBQUMtVXNlcnMGOwhUOglyYW5raQk%3D--b671a391e510d96746f63a5eb3462f6f1f05dce2)
* [How to share LINE OA platform, LINE Developers, GA(UA) / GA4 access to Crescendo Lab?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmp1FFgBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkQ8ocDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ1L2hjL2VuLXVzL2FydGljbGVzLzgxMTAyNzExNDYzOTMtSG93LXRvLXNoYXJlLUxJTkUtT0EtcGxhdGZvcm0tTElORS1EZXZlbG9wZXJzLUdBLVVBLUdBNC1hY2Nlc3MtdG8tQ3Jlc2NlbmRvLUxhYgY7CFQ6CXJhbmtpCg%3D%3D--6a41dd16c79e0514eeb9feb8377a0777300bbf80)
