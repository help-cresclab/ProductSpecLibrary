# Onboarding Guide | How to Enable Email Channels and Import Contacts – Crescendo Lab Help Center

## Phase 1: Email Channel Activation

To enable the Email feature in a Customer Journey, you must complete two stages: Channel Activation and Journey Settings. Email channel activation requires Crescendo Lab Ops assistance (not self-service).

{% stepper %}
{% step %}
### Prepare and Submit Activation Request

Complete the application form here: [MAAC Email Channel Activation Request](https://tally.so/r/81Z4El)

Initial setup includes DNS verification and channel configuration. Allow **10 business days** for activation, followed by a **15-day** Email warm-up process.
{% endstep %}

{% step %}
### Provide Domain & Sender Information (to your CSM)

Provide the following to your CSM:

* Brand Domain (e.g. brand.com)
* Sender Domain (recommended as a subdomain, e.g. `marketing.brand.com`)\
  &#xNAN;_&#x54;he root domain of the Sender Domain must match the Brand Domain._
* Sender Profile (sender name and email shown to recipients, e.g. Brand News [news@marketing.brand.com](mailto:news@marketing.brand.com))\
  &#xNAN;_&#x55;nder one Brand Domain, multiple Sender Domains and Sender Profiles are supported._
* Reply-To Address (must be a real receiving email, e.g. [support@brand.com](mailto:support@brand.com))
{% endstep %}

{% step %}
### Configure DNS Records (IT collaboration)

Crescendo Lab will provide DNS values (including SPF, DKIM). Ask your IT staff or DNS vendor to add these records to your domain hosting backend to ensure deliverability and domain reputation.
{% endstep %}

{% step %}
### Verify and Enable

After DNS settings are added, notify your CSM. Once Crescendo Lab verifies, the Email channel status will display as **Connected** in Admin Center > Channel settings.
{% endstep %}
{% endstepper %}

![](../../../.gitbook/assets/53662972392601)

Email Channel Status

In Admin Center > Email channel list, the system shows one of four states based on sender setting completeness and sending health (past 24 hours):

| Channel Status | Status Description                                                               | System Behavior                                           |
| -------------- | -------------------------------------------------------------------------------- | --------------------------------------------------------- |
| **Connected**  | At least one Sender Profile is verified and Active.                              | You can set and send Emails in Customer Journeys.         |
| **Not Set**    | No Active Sender Profiles detected.                                              | Emails in Customer Journeys will not be sent.             |
| **Suspended**  | Channel forcibly suspended by Automatic Suspension Policy to protect reputation. | All Email sending is stopped immediately.                 |
| **Warning**    | Incomplete sender domain settings or declining sending health.                   | Usually still allows sending, but a risk warning appears. |

👉 Learn more: [Email Channel Status and Common Solutions](onboarding-guide-or-how-to-enable-email-channels-and-import-contacts-crescendo-lab-help-center.md#h_01KD10QB6MHQ5BA73H6VYEK9GT)

***

## Phase 2: Import Email Channel Contacts

In the Contacts page you can view each contact’s Email status to identify who can receive emails or has unsubscribed.

![](../../../.gitbook/assets/53662972394009)

### Contact Status Definitions

| Status Display   | Definition                                                                                                                                          | Can Send |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| **Subscribed**   | Customer agreed to receive emails; mailbox is normal.                                                                                               | Yes ✅    |
| **Unsubscribed** | Customer clicked the unsubscribe link.                                                                                                              | No ❌     |
| **Suppressed**   | Includes past Hard Bounce, multiple Soft Bounce, Spam Report, Invalid Domain (hygiene invalid). System blocks sending to protect domain reputation. | No ❌     |

### CSV Import Tutorial and Important Rules

{% stepper %}
{% step %}
### Start Import

* Go to Audience > Contacts > Import
* Click "Import data manually"
* Select the Email channel to import
* Select key value "Email"
{% endstep %}

{% step %}
### Prepare CSV

* Click "Next"
* Download the dedicated CSV template
* Fill in the Email and messaging\_status fields in the CSV template (Required)
{% endstep %}

{% step %}
### Upload

* Click "Import" to upload the CSV file
* After import completes, view results in the notification center (top right) and check the contact list for imported Email contacts

Reminder: Do not attempt to change Unsubscribed users to Subscribed via import; the system will ignore such changes.
{% endstep %}
{% endstepper %}

![](../../../.gitbook/assets/53663186524825)

![](../../../.gitbook/assets/53663139496345) ![](../../../.gitbook/assets/53663139496985)

![](../../../.gitbook/assets/53663139497497) ![](../../../.gitbook/assets/53663186527257)

#### Important Import Restrictions

To comply with international anti-spam laws and protect domain reputation, MAAC enforces an irreversible status rule:

* You cannot change "Unsubscribed" or "Suppressed" contacts back to "Subscribed" via CSV import.
* If you attempt to change Unsubscribed to Subscribed in the CSV, the system will ignore the status update and only update other fields (e.g., name, phone number).

#### Automatic Suspension Policy

To maintain sending quality, the system monitors recent sending. If your sending domain meets these conditions within the past 24 hours, the system will automatically suspend sending:

* Hard Bounce: count exceeds 20 AND bounce rate > 5%
* Spam Report: count exceeds 10 AND report rate > 0.5%

How to restore:

1. Use a third-party tool to clean your Email list and exclude invalid addresses.
2. Import the cleaning results into MAAC to update contact statuses.
3. Notify your CSM to apply for restoration; Ops will manually review and restore if appropriate.

⚠️ Email channel functions use shared IPs; one abnormal sender can damage all clients. Use only consented, subscribed lists. Do not use purchased or scraped lists.

***

## Common Questions (FAQ)

#### I. Operation and Settings

<details>

<summary>Q. I have a large Email list but I'm unsure how many are invalid. Will importing and sending directly cause my account to be locked?</summary>

The system performs basic checks during import (e.g., domain MX records), but if sending results in a high Hard Bounce rate after import, the automatic suspension mechanism may be triggered.

Suggested action: Use a third-party Email cleaning tool to filter invalid mailboxes first, or test send to a small, recently active subset to ensure list health.

</details>

<details>

<summary>Q. DNS settings are too complicated for me, and I don't have IT staff. Can I provide my account and password for you to set it up?</summary>

For security reasons, Crescendo Lab cannot accept your DNS hosting account credentials.

Suggested action: Crescendo Lab will provide a complete DNS setting value table. Pass this document to your DNS vendor or IT staff to "copy and paste" and complete the settings.

</details>

<details>

<summary>Q. Why can't I change "Unsubscribed" users back to "Subscribed" when importing CSV?</summary>

This is a security mechanism to comply with anti-spam regulations and protect sending reputation. Forcibly resetting users who opted out may cause high report rates and domain blocking.

</details>

#### II. Email Channel Status

<details>

<summary>Q: Why does my Email channel show "Not Set" and I can't send Emails in the journey?</summary>

"Not Set" means no valid Active Sender Profiles detected. A usable profile must have Profile Created and Domain Verified (DNS) Successful. Without a valid profile, Email nodes in journeys are blocked.

How to handle:

1. Contact your CSM to confirm sender information submission (Brand Domain, Sender Domain, Sender Email, Sender Name, Reply-to Address).
2. If you received DNS settings, pass them to IT and notify CSM/Ops to perform "Re-check DNS".

</details>

<details>

<summary>Q: Why does my Email channel show "Suspended" and all emails have stopped sending?</summary>

"Suspended" indicates the Automatic Suspension Policy was triggered (within past 24 hours):

* Hard Bounce: >20 emails AND bounce rate >5%
* Spam Report: >10 emails AND report rate >0.5%

How to handle:

1. Clean the list with third-party Email Hygiene Tools.
2. Import the cleaned invalid list into MAAC and update status to "Suppressed".
3. Contact your CSM/Ops to apply for restoration; Ops will review and manually restore to "Connected" if cleared.

</details>

<details>

<summary>Q: What does it mean when the Email channel shows "Warning"? Can I still send emails?</summary>

"Warning" indicates incomplete domain verification or declining sending health. Sending is usually still allowed but risky.

Common reasons:

* Missing or partial domain verification (e.g., SPF passed, DKIM failed)
* Health decline in past 24 hours:
  * Hard Bounce: >10 emails AND bounce rate >2%
  * Spam Report: >5 emails AND report rate >0.3%

How to handle:

* If verification issue: contact IT to check SPF/DKIM DNS records.
* If health issue:
  * Consider suspending current high-risk campaigns.
  * Review recent lists and content quality.
  * Consider list cleaning to remove low-engagement or invalid contacts.

</details>

<details>

<summary>Q: Why is the Email channel settings page "Read-only" and uneditable?</summary>

Email channel uses a "Managed Service" mode. DNS verification and third-party integration are complex and must be configured/verified by the Crescendo Lab Ops team. The Admin Center page is view-only.

If you need modifications (add/modify sender info, add sender domain, request DNS re-verification), contact your Customer Success Manager (CSM).

</details>

#### III. Email Function Billing

<details>

<summary>Q. Why can't I use the "Send Email" node in the journey, and the button shows Upgrade?</summary>

Your Email channel has not completed activation. Email activation requires domain verification (DNS) and sender settings, and cannot be self-enabled. Contact your CSM to apply for activation.

</details>

<details>

<summary>Q. How is the Email sending function charged? Is there a free quota?</summary>

Charging model: "Plan Quota + Overage Pay-per-use"

* Plan Quota: monthly free sending quota per subscription plan.
* Overage Billing: excess emails beyond plan quota are charged per email.

For detailed quotas and pricing, consult your CSM or the quotation.

</details>

<details>

<summary>Q. How are overage fees deducted? Is a separate top-up required?</summary>

Overage fees are deducted from the shared MAAC Points Pool (CL Points Pool) used by Email and SMS/MMS. No separate account is required. If points are insufficient, top-up per existing process.

</details>

<details>

<summary>Q. If email delivery fails (e.g., recipient address does not exist), will I still be charged?</summary>

The system has a "Hard Bounce Credit-back" mechanism. Points are deducted at send time, but if an email is determined to be a Hard Bounce within 24 hours, the fee for that email will be automatically refunded to your account.

</details>

***

When channel activation and contact import are complete, you can use Customer Journey to send emails. For Email editor operations and journey node settings, see: [Feature Guide | Email Omnichannel Journeys & Editor Tutorial](https://crescendolab.zendesk.com/hc/en-us/articles/53567465248537)

Related articles

* Feature Guide | Email Omnichannel Journeys & Editor Tutorial: https://crescendolab.zendesk.com/hc/en-us/articles/53567465248537
* Tutorials｜Customer Journey ✨ New ✨: https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkQ8ocDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkOafO4MDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJEL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMTIyMDExMTMtVHV0b3JpYWxzLUN1c3RvbWVyLUpvdXJuZXktTmV3BjsIVDoJcmFua2kH--880c82a842d68bb4549cfddc0615685de88cb5a4
* Feature Introduction | WhatsApp Broadcast: Overview & Setup Guide: https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBnkY4fRMDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkOafO4MDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJjL2hjL2VuLXVzL2FydGljbGVzLzUzNjc2NDc3NzY4NzI5LUZlYXR1cmUtSW50cm9kdWN0aW9uLVdoYXRzQXBwLUJyb2FkY2FzdC1PdmVydmlldy1TZXR1cC1HdWlkZQY7CFQ6CXJhbmtpCA%3D%3D--9a2b164a77e0693ec10ed7c776f13f3aec1b96eb
* Tutorials | How to Upload Product Feed Data?: https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkP8pFoMDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkOafO4MDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJQL2hjL2VuLXVzL2FydGljbGVzLzUzMjI1NjgzMjkyMDU3LVR1dG9yaWFscy1Ib3ctdG8tVXBsb2FkLVByb2R1Y3QtRmVlZC1EYXRhBjsIVDoJcmFua2kJ--5afc9d4d7b28f24019d73e38049e3d644639c5a3
* Tutorial | SDK Web Behavior Tracking Tool: https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJk0ii%2BuJToYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkOafO4MDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJOL2hjL2VuLXVzL2FydGljbGVzLzQxNDMwMDUyMTIzODAxLVR1dG9yaWFsLVNESy1XZWItQmVoYXZpb3ItVHJhY2tpbmctVG9vbAY7CFQ6CXJhbmtpCg%3D%3D--ef6f5f7ce2e3bd16ea792bb037904835684eb5d2)
