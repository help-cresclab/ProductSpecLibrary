# Feature Introduction | WhatsApp Broadcast: Overview & Setup Guide – Crescendo Lab Help Center

**This article explains how to use the new mechanism for WhatsApp Broadcast in MAAC.** By integrating Meta's WhatsApp Business Account (WABA), you can send approved Template Messages and combine them with MAAC’s omnichannel data tracking to enhance marketing effectiveness.

## Feature Overview

The WhatsApp Broadcast feature allows brands to send marketing or notification messages to WhatsApp users within the MAAC interface. This feature combines precise reach with omnichannel tracking, offering core values including:

* Effective Reach and Segmentation: The system filters for "Reachable" valid users by default, helping you concentrate marketing resources on audiences willing to interact. This mechanism helps maintain account health scores while maximizing delivery effectiveness.
* Omnichannel Performance Tracking: Fully supports MAAC short URL conversion tracking. When users click a template link, the system not only records the number of clicks but also integrates with GA4/SDK parameters to deeply track subsequent actions such as Add to Cart and revenue contribution.
* Automated Compliance Management: Built-in standardized Opt-in (START) / Opt-out (STOP) keyword processes. The system automatically interprets and processes subscription status, reducing manual management costs.
* Seamless Customer Service Integration: Equipped with a smart routing feature. Except for subscription keywords, general user replies will be automatically directed to the CAAC inbox, ensuring that live agents can immediately follow up on business opportunities.

![](../../../.gitbook/assets/53801075108249)

Before starting segment filtering and creating broadcasts, please ensure you have added the WhatsApp Business Account (WABA) channel to the Admin Center. If you haven't completed the integration, please refer to this tutorial to complete the setup:👉 [Tutorial | Adding a WhatsApp Channel](https://crescendolab.zendesk.com/hc/en-us/articles/44652331569945)

## Contact Status Definitions

To protect account quality and comply with Meta regulations, MAAC categorizes WhatsApp contacts into two statuses:

| Status         | Definition                                                                  | System Field: Reachability | Description                                                                                                                                               |
| -------------- | --------------------------------------------------------------------------- | -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Opted-in       | Users who proactively subscribe or are marked as subscribed through import. | Reachable                  | The system will not automatically block the broadcast, but you must bear the risk of being blocked. A risk consent prompt must be checked before sending. |
| Not Subscribed | Users who have not yet expressed an intention to subscribe.                 | Not Reachable              |                                                                                                                                                           |
| Opted-out      | Users who have replied STOP to unsubscribe.                                 | Not Reachable              | The system will automatically block the broadcast to avoid violations.                                                                                    |

_Due to user privacy considerations, Meta does not return "User blocked business account" events, therefore MAAC will not display a "Blocked" status._

## Preparation

{% stepper %}
{% step %}
### Confirm Compliance Settings

Go to Admin Center > WhatsApp Channel > Compliance

* In this section, you can view the system's default Opt-in/Opt-out keywords (e.g., START, STOP) and auto-reply content.
* Note: To ensure legal compliance, the content in this section supports multiple languages but cannot be customized or edited.

![](../../../.gitbook/assets/53801170573465)

![](../../../.gitbook/assets/53801117066521)
{% endstep %}

{% step %}
### Import WhatsApp Contacts

Go to Audience > Import > Manual Import, and select the identifier (Key) as WhatsApp phone number.

* CSV Format Specifications:
  * WhatsApp\_mobile (Required): Must be a full phone number including the country code.
  * Status (Required): Enter opted\_in if the list has been authorized; enter not\_subscribed if unconfirmed or not yet subscribed; enter opted\_out for those who unsubscribed (do not leave blank).

⚠️ Gender (Important Note): Since the official WhatsApp API does not provide user gender data, if you want to segment by gender later, you must manually enter data in the gender field of the CSV; the system cannot capture this automatically.

![](../../../.gitbook/assets/53801298779801) ![](../../../.gitbook/assets/53801298781081)
{% endstep %}
{% endstepper %}

## Setup Tutorial

### Phase 1: Create Templates in the WhatsApp Manager (WABA)

Due to Meta policy restrictions, please go to Meta's WhatsApp Manager to create templates.

Please read the following article first to create WhatsApp message templates: [Tutorial | How to create and submit WhatsApp message templates for approval?](https://crescendolab.zendesk.com/hc/en-us/articles/44810965515417-%E6%95%99%E5%AD%B8-%E5%A6%82%E4%BD%95%E5%BB%BA%E7%AB%8B-WhatsApp-%E8%A8%8A%E6%81%AF%E7%AF%84%E6%9C%AC%E4%B8%A6%E9%80%81%E5%AF%A9#h_01KDJMVGXD7C55B98ZA27EDY3X)

![](../../../.gitbook/assets/53801397413913)

⚠️ To ensure successful delivery and performance tracking through MAAC, please check these 3 points when creating a template:

* Category Selection: You must select the Marketing category and choose the Custom layout to send broadcasts.
* Variable Format: The body only supports numerical variables (e.g., \{{1\}}). It does not support named variables (e.g., \{{name\}}).
* Tracking Settings (Important): To track clicks and revenue, the URL button settings must be filled in according to the values below:
  * Type of action: Visit Website
  * Button type: Dynamic
  * Website URL: https://maac.io/

Why must the Website URL be set to https://maac.io/?

This acts as a "tracking relay point." Entering https://maac.io/ in the WABA backend serves as a "Base URL," intended to give the MAAC system control. When you return to the MAAC editor to send a message, the system will provide a field for you to enter your actual "Destination URL."

In this way, the system can automatically convert your long URL into a "short URL with UTM parameters and Tags" and dynamically insert it into the button, thereby enabling performance tracking.

### Phase 2: Create and Send Broadcasts in MAAC

{% stepper %}
{% step %}
### Prepare Target Audience List

Before sending a broadcast, please confirm that you have created the target audience you intend to reach. When creating a WhatsApp segment, the system will default to filtering for "Reachable" contacts to help maintain account quality and delivery effectiveness.

For full instructions and the new logic, please refer to: [Feature Description | Creating Segments](https://crescendolab.zendesk.com/hc/en-us/articles/4413222974233)

Data Logic Explanation:

* Engagement Level: An activity metric calculated by the system based on the "frequency" and "timing" of user interaction with the brand. In the WhatsApp channel, valid interaction behaviors include: users proactively sending messages (Inbound) or clicking links (Clicks).
* Last Engaged: Includes user-sent messages (Inbound), Quick Reply clicks, or link clicks (Clicks).

Note: Simple "Read" events are not counted as interaction time.
{% endstep %}

{% step %}
### Edit and Send

{% stepper %}
{% step %}
#### Step: Create Broadcast

Go to Broadcast > Select WhatsApp Channel > Select "Create"

![](../../../.gitbook/assets/54186225797273)
{% endstep %}

{% step %}
#### Step: Select Audience and Risk Control

* Standard Operation: Select Reachable users.
* Risk Operation: If the segment includes Not Reachable users and you insist on sending, the system will display a risk consent form. You must check to confirm that you "acknowledge this may lead to the WABA account being blocked or downgraded" before the system allows delivery.

![](../../../.gitbook/assets/53801573843737)
{% endstep %}

{% step %}
#### Step: Sync Templates

Select a template with an Approved status. The system automatically syncs every 12 hours by default. If you don't see a newly created template, please click "Refresh templates" manually.

![](../../../.gitbook/assets/53801520092313)
{% endstep %}

{% step %}
#### Step: Edit Content and Tracking Settings

* Variable Settings: You can map \{{1\}} to a "Short Link," "Customer Name," or custom text.

![](../../../.gitbook/assets/53801695041945)

* Short Link Settings: For Dynamic URL buttons, the editor will display a "Destination URL" field. Enter the full URL here and enable UTM parameters; the system will automatically generate a tracking short URL.

![](../../../.gitbook/assets/53801695044633)

⚠️ Note: Currently only URL button tracking is supported. Clicks on "Quick Reply" buttons are not yet supported for tracking.
{% endstep %}

{% step %}
#### Step: Sending Limits and Scheduling

* Tier Sending Limit Mechanism (Warn then Fail): The system will check your WABA account Tier. If the sending volume exceeds Meta's daily limit, the excess messages will fail immediately, and the system will not automatically queue them for retry.

![](../../../.gitbook/assets/53801695047961)
{% endstep %}
{% endstepper %}
{% endstep %}
{% endstepper %}

## Report Metric Definitions

After sending, you can view performance data under "Interaction" or download a "Failure Report."

![](../../../.gitbook/assets/53801720329369)

| Metric                     | Definition                                                                    | Notes                                                                        |
| -------------------------- | ----------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| Delivered                  | The number of times a message was successfully sent to the user's phone.      | Meta returns delivered status                                                |
| Read                       | The number of times a user opened and viewed the message.                     | Meta returns read status                                                     |
| Clicks                     | The total number of times users clicked the maac.io short URL in the message. | /                                                                            |
| Unique Clicks (Count/Rate) | The number of unique users who clicked the short URL.                         | /                                                                            |
| Failed                     | The number of messages that could not be successfully delivered.              | Common causes: exceeding sending limit, invalid number, user not subscribed. |

You can also [integrate GA4 settings](https://crescendolab.zendesk.com/hc/en-us/articles/22490379797273) to view conversion tracking for e-commerce data.

| Metric              | Definition                                                                                             |
| ------------------- | ------------------------------------------------------------------------------------------------------ |
| Items added to cart | The number of Add to Cart events generated after users click the broadcast link and enter the website. |
| Orders              | The total number of completed orders attributed to the broadcast campaign.                             |
| Revenue             | The total attributed order amount generated by the broadcast campaign.                                 |

If delivery fails, the system provides a "Failure Report" for download. The report provides a specific reason for each failure; common reasons include:

* Message limit reached: Daily WhatsApp sending limit has been reached.
* User not opted-in: User is not subscribed or has unsubscribed.
* Invalid phone number: Phone number format is incorrect or is a dead number.

## Frequently Asked Questions (FAQ)

<details>

<summary>Q1: Why has the number of people in my SMS or LINE segments decreased?</summary>

A: This is because the system’s segmentation logic was upgraded, and all existing segments now automatically include a "Reachability = Reachable" filter condition.

This change primarily filters out the following two categories that have phone numbers but are considered inactive subscriptions:

* LINE blocked users with phone numbers: They have phone numbers but are in a blocked state according to LINE's definition.
* SMS contacts with only a phone number: Refers to lists in the system that only contain phone numbers without other channel identities.

Recommendation: If your segment was originally intended for sending SMS to all users, please go to the segment editing page and manually change the Reachability condition back to "All".

</details>

<details>

<summary>Q2: Can I turn off the automated compliance keyword feature?</summary>

No. The system currently only supports standardized default keywords (e.g., START, STOP) and fixed multi-language reply content; customization is not yet available.

</details>

<details>

<summary>Q3: Can I customize keywords or auto-reply content?</summary>

No. To ensure legal compliance and unify compliance management, the built-in subscription (e.g., START) and unsubscription (e.g., STOP) keywords and reply messages are fixed. They support Traditional Chinese, English, Japanese, and Thai, and cannot be customized.

</details>

<details>

<summary>Q4: Why can't I find or select the template I just created in WABA within MAAC?</summary>

If you cannot find the template in the list or if the template is grayed out and unselectable, please check the following in order:

1. Confirm Status: First, confirm in the [WABA Admin](https://business.facebook.com/latest/whatsapp_manager/message_templates) whether the template status is "Approved."
2. Confirm Category: Only Marketing or Utility categories under the Custom type are supported.
3. Check Format: Check if the template contains unsupported formats (e.g., location information Header, or named variables like `{{name}}`). Such templates will appear in the list but will be grayed out and unselectable.

⚠️ If you have confirmed the above settings, we recommend clicking the "Refresh templates" button in the editor; the system will immediately fetch the latest template data from Meta.

</details>

<details>

<summary>Q5: Will sending WhatsApp broadcasts incur conversation charges?</summary>

Yes. Sending marketing template messages will open a marketing conversation, and Meta will charge you based on local pricing policies. MAAC only provides the delivery functionality and does not handle these fees.

</details>

<details>

<summary>Q6: How should I handle it if the broadcast shows "Failed" messages?</summary>

You can download a "Failure Report" on the broadcast performance report page. The report will list the reasons for failure. If the reason is "Message limit reached," it means you have triggered Meta's daily sending limit; we recommend sending in batches or upgrading your account tier.

</details>

<details>

<summary>Q7: Can I use AI segments to filter for "Not Reachable (unsubscribed)" users and try to win them back?</summary>

No. AI segments and Customer Data Hub (CDH) segments default to including only "Reachable (subscribed)" users in their system logic. If you need to perform actions targeting Not Reachable users, you must use standard MAAC filter conditions for your settings.

</details>

### Related articles

* [Tutorial｜How to Create and Submit a WhatsApp Message Template](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJl8rl3BKDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnkY4fRMDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJkL2hjL2VuLXVzL2FydGljbGVzLzQ0ODEwOTY1NTE1NDE3LVR1dG9yaWFsLUhvdy10by1DcmVhdGUtYW5kLVN1Ym1pdC1hLVdoYXRzQXBwLU1lc3NhZ2UtVGVtcGxhdGUGOwhUOglyYW5raQY%3D--2550ceb9da67aa8bc1ae56894422ae807e96fb0f)
* [Tutorials｜How to add a WhatsApp channel](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBmTXG6cKDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnkY4fRMDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJOL2hjL2VuLXVzL2FydGljbGVzLzQ0NjUyMzMxNTY5OTQ1LVR1dG9yaWFscy1Ib3ctdG8tYWRkLWEtV2hhdHNBcHAtY2hhbm5lbAY7CFQ6CXJhbmtpBw%3D%3D--7d541691423d613c13f6f0da45803964fd0081ec)
* [Tutorial｜Segment](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBlzlogDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnkY4fRMDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI2L2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMjI5NzQyMzMtVHV0b3JpYWwtU2VnbWVudAY7CFQ6CXJhbmtpCA%3D%3D--49bd1b3564b6f9268152f43870083f123aef4ecf)
* [Onboarding Guide | How to Enable Email Channels and Import Contacts](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkOafO4MDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnkY4fRMDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJoL2hjL2VuLXVzL2FydGljbGVzLzUzNTcwOTE1ODY0MDg5LU9uYm9hcmRpbmctR3VpZGUtSG93LXRvLUVuYWJsZS1FbWFpbC1DaGFubmVscy1hbmQtSW1wb3J0LUNvbnRhY3RzBjsIVDoJcmFua2kJ--8d331dcae89576fe5272bb4562308838bda65cdd)
* [Feature Guide | Email Omnichannel Journeys & Editor Tutorial](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBnXvCW4MDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnkY4fRMDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJfL2hjL2VuLXVzL2FydGljbGVzLzUzNTY3NDY1MjQ4NTM3LUZlYXR1cmUtR3VpZGUtRW1haWwtT21uaWNoYW5uZWwtSm91cm5leXMtRWRpdG9yLVR1dG9yaWFsBjsIVDoJcmFua2kK--00b9bd9b971f79550a42ad45960f55f1b964f468)
