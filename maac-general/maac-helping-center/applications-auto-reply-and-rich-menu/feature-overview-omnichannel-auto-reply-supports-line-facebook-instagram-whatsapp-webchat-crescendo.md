# Feature Overview｜Omnichannel Auto-Reply (Supports LINE / Facebook / Instagram/ WhatsApp/WebChat) – Crescendo Lab Help Center

#### Overview & Use Cases

**Omnichannel rule integration**

Create a single auto-reply rule that applies to multiple platforms—LINE, Facebook, Instagram, WhatsApp and WebChat—allowing unified content and tagging for streamlined management.

{% stepper %}
{% step %}
### New Contact Welcome Message

* **Trigger:** When a contact first interacts with the brand account (e.g. sends a message or replies to an IG story).
* **Benefit:** Creates a strong first impression and starts the customer journey.
* **Note:** Only sent once—re-following does not re-trigger.

Definition of “first interaction” by platform:

| Platform                      | First Interaction Definition                                                                          | Notes                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ----------------------------- | ----------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| LINE                          | User starts a friend relationship with the LINE OA                                                    | Unblocking and re-adding will re-trigger the welcome message                                                                                                                                                                                                                                                                                                                                                                                                   |
| Facebook Messenger            | User sends a message to the brand’s Facebook Page                                                     | Clicking an ad without messaging does not count                                                                                                                                                                                                                                                                                                                                                                                                                |
| Instagram (Business)          | User sends the first DM or replies to an IG Story                                                     | Comments or likes do not trigger                                                                                                                                                                                                                                                                                                                                                                                                                               |
| **WhatsApp Business Account** | Contact proactively sends a message to the brand account for the first time.                          | <p><strong>The user must proactively send the first message and not yet exist in the Crescendo system</strong> to trigger the welcome message; simply opening the window without sending a message will not trigger it<br>👉 <strong>Click here for the complete guide:</strong> <a href="https://crescendolab.zendesk.com/hc/en-us/articles/54186983648281-Guide-WhatsApp-Opt-in-Opt-out-Mechanisms">Tutorial | WhatsApp Opt-in and Opt-out Mechanism</a></p> |
| **Web Chat Widget**           | When a visitor enters the website chat room (opens the chat window), it is considered an interaction. | As soon as the visitor opens or enters the Web Chat widget, the system automatically triggers the welcome message.                                                                                                                                                                                                                                                                                                                                             |
{% endstep %}

{% step %}
### Keyword Reply

* **Trigger:** Message exactly matches a predefined keyword (case-insensitive).
* **Benefit:** Automatically answers common questions, guides to product info, and reduces manual workload.
{% endstep %}

{% step %}
### General Reply

* **Trigger:** All messages within a specified time window.
* **Benefit:** Provides consistent responses outside business hours or during high-traffic periods.
* **Tip:** Use for all-day coverage, e.g., directing users to a form or support when the team is offline.
{% endstep %}
{% endstepper %}

***

#### Core Benefits & Marketing Applications

* **Reduce cross-platform operational costs:** A single setup covers LINE, FB, IG, and WhatsApp, significantly saving time and resources.
* **Precision marketing & tagging:** Use tagging rules to segment users and drive automated campaigns.
* **24/7 auto support:** Ensures consistent interaction and improves brand image.
* **Personalized content:** Tailor messages based on whether a user is linked.
* **Ecosystem integration:** Works seamlessly with MAAC journey automation and messaging tools.

***

#### Important Usage Notes

* **Keyword Matching:** Currently only supports **exact match** for a single keyword (case-insensitive).
* **Keyword Priority:** If a user enters a **keyword** during non-business hours, the system will **prioritize triggering "Keyword Reply"** over "General Reply".
* **Frequency Limit:** The frequency limit for Auto-reply is **30 days**.
* **Account Binding:** Each auto-reply rule can **only be bound to one brand account** per platform.
  * For example: One LINE Official Account, one Facebook Page, one Instagram Business Account, one WhatsApp Business Account and one Web Chat Widget. You can bind accounts from up to four different platforms simultaneously, but only one per platform.
* **IG Story Reply Validity:** Must select a story that has **not expired within 24 hours**. Even if expired, the rule will not automatically deactivate but will fail to trigger.
* **Welcome Message Logic:** Triggered only when a contact interacts with the brand for the **first time**; it will not be sent repeatedly.

CAAC Co-usage Reminder: If both MAAC and CAAC keyword features are enabled, **please avoid setting the same keywords** to prevent functional conflicts.

***

#### Special Feature: Instagram Story Auto-Reply

* **Supported types:** Keyword or generic reply targeting specific IG story.
* **Trigger limit:** Must be within 24 hours.
* **Expiration behavior:** Story expiration stops triggering; system keeps rule active but nonfunctional.
* **Highlights (Pinned Stories):** Works beyond 24 hrs if story is pinned.
* **Priority:** Story replies always override other reply types when multiple rules match.

#### Special Reply Type: WhatsApp Interactive Messages

WhatsApp supports more structured interaction methods to improve click-through conversion:

* **Reply Buttons:** Configure up to **3** quick reply buttons at the bottom of the message.
* **List Messages:** Supports a menu interface with up to **10** options, ideal for guiding through FAQs or service items.
* **CTA URL Buttons:** Configure a single button to guide users to click an external link.

***

#### Comparison of Auto-Reply Types

| Reply Type      | Scheduling Options                                | Keyword Support                | Frequency Limit | Notes                                                       |
| --------------- | ------------------------------------------------- | ------------------------------ | --------------- | ----------------------------------------------------------- |
| Welcome Message | —                                                 | —                              | ✅               | Only once per platform rule, based on first interaction.    |
| Keyword Reply   | Date range or always-on scheduling                | Exact match (case-insensitive) | ✅               | Unique keywords; duplicates block CAAC triggers.            |
| Generic Reply   | Daily, monthly, during support/off-business hours | —                              | ✅               | Only one can be active at a time for overlapping schedules. |

#### Auto-Reply Trigger Priority

If a user message matches multiple response conditions, the system will determine which rule to trigger based on the following priority order:

1. Instagram Story Replies
2. Keyword Replies
3. General Replies (daily, monthly, within/outside response time windows)

Notes:

* Once an Instagram Story expires, it will no longer trigger auto-replies. However, the rule itself will remain active and is not automatically disabled.
* The New Contact Welcome Message is triggered only once and is not affected by the priority rules above.

***

#### Data & Performance Tracking

You can view trigger counts, message clicks, and link clicks for each auto-reply through the **MAAC Auto-Reply Report**, including:

* Quick reply button clicks
* Clicks on triggered messages or keywords

Multiple clicks from the same user are counted cumulatively, subject to anti-spam and interval control rules.

![](../../../.gitbook/assets/54902275965849)

***

#### FAQ

<details>

<summary>In WhatsApp Auto-reply, can I set up multiple chat bubbles like in LINE?</summary>

No. Each auto-reply only supports a **single message bubble**. This is due to WhatsApp's official API specifications, which do not allow "packaging" multiple contents (such as text and images) to be sent simultaneously. It is highly recommended to use **"Interactive Reply Buttons"** or **"Interactive List Messages"** to consolidate your information into one cohesive message.

</details>

<details>

<summary>If a user sends "STOP" (an opt-out keyword), will it trigger my custom keyword auto-reply?</summary>

No. The system is designed to **prioritize compliance keywords** (such as "STOP" or "UNSUBSCRIBE") over any custom marketing rules. The **compliance action (Opt-out) takes precedence** to ensure legal compliance is not blocked, so your custom auto-replies will not interfere with this official process.

</details>

<details>

<summary>Does keyword matching support fuzzy or multi-keyword triggers?</summary>

No. Only exact single-keyword matching is supported (case-insensitive, trimmed).

</details>

<details>

<summary>Why isn’t IG Story auto-reply triggering?</summary>

Only stories within 24 hrs can be selected. If the story is expired, the rule won’t work. Please select a new active story.

</details>

<details>

<summary>My auto-reply didn’t send—what could be wrong?</summary>

Please ensure:

* The rule is enabled.
* The input matches the exact keyword.
* The schedule is active.
* Only one rule of the same type is enabled if schedules overlap.

</details>

<details>

<summary>Will deleting/re-following trigger the welcome message again?</summary>

No. Once triggered, the welcome message won’t send again, even after unfollowing and refollowing.

</details>

<details>

<summary>Does IG Story auto-reply update automatically?</summary>

No. You need to manually re-select a new story after the previous one expires.

</details>

<details>

<summary>How do I view auto-reply performance?</summary>

Check MAAC’s analytics list for triggers, sends, clicks, orders, and revenue. Ensure GA tracking is correctly integrated.

</details>

<details>

<summary>Can I set up auto-replies for FB, IG, LINE, WhatsApp, and Web Chat at the same time?</summary>

Yes. Auto-replies support binding a single rule to multiple platforms. Each platform can be connected with one account only (e.g., one LINE Official Account, one Facebook Page, one Instagram Business Account, one WhatsApp Business Account, and one Web Chat).

You can customize the message content for each platform independently.

</details>

<details>

<summary>What is the difference between Unbound and Bound contacts in Web Chat auto-replies?</summary>

The difference lies in whether the system can identify the visitor’s member identity (i.e., whether a customer\_id exists). This typically depends on whether you have integrated CDH (Customer Data Hub) and completed data merging.

* Bound: The visitor has a customer\_id in the system (usually indicating the user is logged in or has been identified).
* Unbound: The visitor does not have a customer\_id and is considered an anonymous visitor.

You can configure different auto-reply messages for each status (for example, guiding unbound visitors to register or log in).

</details>

<details>

<summary>If I use a tracked link in an auto-reply button, will the performance data appear in the auto-reply report?</summary>

No. The auto-reply report currently only shows trigger counts and message-level click data.

To view detailed performance metrics for tracked links (such as conversions or unique clicks), please go to Analytics > TraceLink in the admin dashboard.

</details>

<details>

<summary>When a visitor triggers an auto-reply in Web Chat (e.g., a welcome message or keyword reply), will CAAC also receive the message?</summary>

This depends on whether the visitor’s message is intercepted by MAAC:

* If the message matches a MAAC keyword: MAAC will handle and send the auto-reply directly, and the message will not appear in the CAAC inbox.
* If the message does not match any keyword: The message will be routed to CAAC, where customer service agents can view and respond to it.

</details>

***

Related articles

* [Setup Guide｜Omnichannel Auto-Reply (LINE / Facebook / Instagram / WhatsApp / Web Chat)](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkBXdwcLDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkXVgOzKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJzL2hjL2VuLXVzL2FydGljbGVzLzQ4NTAyNDY3Nzg5MjA5LVNldHVwLUd1aWRlLU9tbmljaGFubmVsLUF1dG8tUmVwbHktTElORS1GYWNlYm9vay1JbnN0YWdyYW0tV2hhdHNBcHAtV2ViLUNoYXQGOwhUOglyYW5raQY%3D--d8c689500ea6cd2bf23555ce3bff547158f7ba63)
* [Feature Overview｜Reservation Module (SimplyBook.me)](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkXQM20KzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkXVgOzKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJYL2hjL2VuLXVzL2FydGljbGVzLzQ4MDU1NTM3NjM3MjczLUZlYXR1cmUtT3ZlcnZpZXctUmVzZXJ2YXRpb24tTW9kdWxlLVNpbXBseUJvb2stbWUGOwhUOglyYW5raQc%3D--b666b2e0e898ea7b0f64d1e68d95e28a4025b508)
* [Tutorials｜How to Add an Instagram Channel](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJn%2FD0kSKzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkXVgOzKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJQL2hjL2VuLXVzL2FydGljbGVzLzQ3MzU3NTM1MTkwOTM3LVR1dG9yaWFscy1Ib3ctdG8tQWRkLWFuLUluc3RhZ3JhbS1DaGFubmVsBjsIVDoJcmFua2kI--e8d8ae866cbb61d3240cfe842d3ce2e1ee04f519)
* [Tutorial｜Using Facebook Channel in CAAC](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBnG6aHpKjoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkXVgOzKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJOL2hjL2VuLXVzL2FydGljbGVzLzQ3MTgyOTMyMTk4OTM3LVR1dG9yaWFsLVVzaW5nLUZhY2Vib29rLUNoYW5uZWwtaW4tQ0FBQwY7CFQ6CXJhbmtpCQ%3D%3D--c85b8cfeb16d5901c7e3bd7d0302d0c7d01a2957)
* [How to share LINE OA platform, LINE Developers, GA(UA) / GA4 access to Crescendo Lab?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmp1FFgBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkXVgOzKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ1L2hjL2VuLXVzL2FydGljbGVzLzgxMTAyNzExNDYzOTMtSG93LXRvLXNoYXJlLUxJTkUtT0EtcGxhdGZvcm0tTElORS1EZXZlbG9wZXJzLUdBLVVBLUdBNC1hY2Nlc3MtdG8tQ3Jlc2NlbmRvLUxhYgY7CFQ6CXJhbmtpCg%3D%3D--9085281b8f7212928656820791823100791a0357)

For setup steps, please refer to 👉 [Setup Guide｜Omnichannel Auto-Reply](https://crescendolab.zendesk.com/hc/en-us/articles/48502467789209-Setup-Guide-Omnichannel-Auto-Reply-LINE-Facebook-Instagram-WhatsApp)
