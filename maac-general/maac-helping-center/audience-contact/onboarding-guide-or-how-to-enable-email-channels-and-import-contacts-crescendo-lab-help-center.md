# Onboarding Guide | How to Enable Email Channels and Import Contacts – Crescendo Lab Help Center

To enable the Email feature in a Customer Journey, you must go through two stages: "Channel Activation" and "Journey Settings". Currently, Email channel activation is assisted by the Crescendo Lab Ops team and cannot be done entirely via self-service. Please follow these steps:

## Phase 1: Email Channel Activation

To activate the Email Channel, please prepare your domain information and complete the application form here: [MAAC Email Channel Activation Request](https://tally.so/r/81Z4El)

⚠️ Initial setup includes DNS verification and channel configuration. Please allow **10 business days** for activation, followed immediately by a **15-day** Email Warm-up process.

{% stepper %}
{% step %}
### Provide Domain Information

Please provide the following information to your CSM:

* **Brand Domain**: Usually your official website's main domain (e.g. brand.com).
*   **Sender Domain**: We recommend using a subdomain (e.g. `marketing.brand.com`).

    _❗️The root domain of the Sender Domain must match the "Brand Domain"._
*   **Sender Profile**: The sender name and email address you want customers to see (e.g. Brand News [news@marketing.brand.com](mailto:news@marketing.brand.com)).

    _❗️Under one Brand Domain, multiple Sender Domains and Sender Profiles are supported, allowing you to distinguish sender identities based on different business needs (such as marketing newsletters, transaction notifications)._
* **Reply-To Address**: The email address for customers to reply to. It **must be a real, receiving email address** (e.g. [support@brand.com](mailto:support@brand.com)).
{% endstep %}

{% step %}
### Configure DNS Records (IT Collaboration)

Crescendo Lab will provide a set of DNS values (including SPF, DKIM records). Ask your IT staff to add these values to your domain hosting backend. This is a critical step to ensure email deliverability and domain reputation.
{% endstep %}

{% step %}
### Verify and Enable

After DNS settings are complete, notify your CSM. Once verified, you will see the Email channel status displayed as **Connected** in Admin Center > Channel settings.

![](<../../../.gitbook/assets/53662972392601 (1)>)
{% endstep %}
{% endstepper %}

Email Channel Status

In the Email channel list in Admin Center, you can view the current health status of the Email channel. The system displays one of the following four states based on **sender setting completeness** and **sending health (past 24 hours data)**.

| **Channel Status** | **Status Description**                                                                                                                   | **System Behavior**                                                                |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Connected**      | Indicates the Email channel is operating normally. At least one Sender Profile in the system has completed verification and is "Active". | You can normally set and send Emails in Customer Journeys.                         |
| **Not Set**        | Indicates there are currently no Active Sender Profiles, so sending tasks cannot be executed.                                            | Emails in Customer Journeys will not be sent.                                      |
| **Suspended**      | Indicates the channel has been temporarily forced shut by the system's "Automatic Suspension Policy" to protect sending reputation.      | All Email sending will be **stopped immediately**.                                 |
| **Warning**        | Indicates incomplete sender domain settings or declining sending health, presenting potential risks.                                     | Usually still **allows sending**, but a risk warning will appear on the interface. |

👉 Learn more: [Email Channel Status and Common Solutions](onboarding-guide-or-how-to-enable-email-channels-and-import-contacts-crescendo-lab-help-center.md#h_01KD10QB6MHQ5BA73H6VYEK9GT)

## Phase 2: Import Email Channel Contacts

In the "Contact" page, you can now see the Email status for each contact. This helps you identify at a glance who can receive Emails and who has unsubscribed.

![](<../../../.gitbook/assets/53662972394009 (1)>)

Contact Status Definitions

Before sending, please understand the three states of Email contacts:

| **Status Display** | **Definition**                                                                                                                                                                                                      | **Can Send** |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| **Subscribed**     | Customer agreed to receive emails, and the mailbox is normal.                                                                                                                                                       | Yes ✅        |
| **Unsubscribed**   | Customer clicked the "Unsubscribe" link.                                                                                                                                                                            | No ❌         |
| **Suppressed**     | <p>Includes past occurrences of:<br>- Hard Bounce<br>- Multiple Soft Bounce<br>- Spam Report<br>- Invalid Domain (Hygiene invalid)<br>*The system will automatically block sending to protect domain reputation</p> | No ❌         |

CSV Import Tutorial and Important Rules

If you have an existing list of member Emails, you can batch import them into MAAC via CSV file:

{% stepper %}
{% step %}
### Import contacts via CSV — Steps

* Go to "Audience" > Click "Contacts" > Click "Import"
* Click "Import data manually"
* Select the Email channel to import
* Select key value "Email"

![](<../../../.gitbook/assets/53663186524825 (1)>)

![](<../../../.gitbook/assets/53663139496345 (1)>) ![](<../../../.gitbook/assets/53663139496985 (1)>)
{% endstep %}

{% step %}
* Click "Next"
* Download the dedicated CSV template
* Fill in the Email and messaging\_status fields in the CSV template (Required)
* Click "Import" to upload the CSV file

After import is complete, you can view the results in the notification center at the top right and return to the contact list to view the imported Email contacts.

* _Reminder: Do not attempt to change unsubscribed users to subscribed via import; the system will automatically ignore this change._

![](<../../../.gitbook/assets/53663139497497 (1)>) ![](<../../../.gitbook/assets/53663186527257 (1)>)
{% endstep %}
{% endstepper %}

Important Import Restrictions

To comply with **international anti-spam laws and protect domain reputation**, MAAC has a strict **"Irreversible Status"** rule:

🚫 **You cannot change "Unsubscribed" or "Suppressed" contacts back to "Subscribed" via CSV import.**

* If you attempt to change Unsubscribed to Subscribed in the CSV, the system will **ignore the status update** and only update other fields (such as name, phone number). This prevents accidental sending to mailboxes that have explicitly refused or are invalid, avoiding your brand being blacklisted.

Automatic Suspension Policy

To maintain sending quality for all users, the system has an automatic monitoring mechanism. If your sending domain exhibits the following conditions, the system will **automatically suspend** your sending function:

* Trigger Conditions (within the past 24 hours):
  * **Hard Bounce**: Sent to too many non-existent mailboxes, count **exceeds 20 and bounce rate > 5%**.
  * **Spam Report**: Too many users marked your emails as spam, count **exceeds 10 and report rate > 0.5%**.
* How to restore?
  * You must first use a third-party tool to clean your Email list and exclude invalid lists.
  * Import the cleaning results into MAAC to update contact statuses.
  * Notify your CSM to assist in applying for restoration. It will be manually restored from the backend after **manual review**.

**⚠️** Email (EDM) channel functions use shared IPs; one abnormal sender can damage all clients. Clients must only use consented, subscribed lists. Do not use purchased or scraped lists.

## Common Questions (FAQ)

#### I. Operation and Settings

<details>

<summary>Q. I have a large Email list but I'm unsure how many are invalid. Will importing and sending directly cause my account to be locked?</summary>

To protect your sending reputation, the system performs basic checks during import (such as domain MX records), but if sending results in a high "Hard Bounce" rate after import, the automatic suspension mechanism will still be triggered.

* Suggested Action: If your list hasn't been maintained for a long time, it is recommended to use a third-party Email cleaning tool to filter invalid mailboxes first, or test send a small amount to active members who have interacted recently to ensure list health.

</details>

<details>

<summary>Q. DNS settings are too complicated for me, and I don't have IT staff. Can I provide my account and password for you to set it up?</summary>

For information security reasons, we cannot ask for your DNS hosting platform account and password to operate on your behalf.

* Suggested Action: We will provide a complete **DNS setting value table**. You just need to pass this document to the vendor managing the domain or IT staff and ask them to "copy and paste" to complete the setting.

</details>

<details>

<summary>Q. Why can't I change "Unsubscribed" users back to "Subscribed" when importing CSV?</summary>

This is a system security mechanism designed to comply with international anti-spam regulations and protect your sending reputation. If a user has expressed they do not wish to receive emails, forcibly resetting the status may lead to high report rates and domain blocking.

</details>

#### II. Email Channel Status

<details>

<summary>Q: Why does my Email channel show "Not Set" and I can't send Emails in the journey?</summary>

This status indicates the system currently **has not detected any valid sender profiles (Active Sender Profile)**. A usable sender profile must meet both "Profile Created" and "Domain Verification (DNS) Successful" conditions. As long as there is no valid Profile, the system will automatically block Email sending nodes in the journey.

Common Reasons:

* Profile not yet created (you may not have applied to CSM/Ops to create sender information).
* Domain verification failed (e.g. SPF or DKIM verification failed).

How to handle:

* Contact your CSM: Confirm if complete sender information has been submitted (Brand Domain, Sender Domain, Sender Email, Sender Name, Reply-to Address).
* Check DNS settings: If you have received the DNS settings file, pass it to your IT department to complete the settings. Once done, notify CSM/Ops to perform "Re-check DNS".

</details>

<details>

<summary>Q: Why does my Email channel show "Suspended" and all emails have stopped sending?</summary>

This status indicates your Email channel has triggered the system's **Automatic Suspension Policy** to protect domain reputation and shared IP health.

Trigger Conditions (Within the past 24 hours):

* **Hard Bounce**: Quantity exceeds **20 emails** AND bounce rate exceeds **5%**.
* **Spam Report**: Quantity exceeds **10 emails** AND report rate exceeds **0.5%**.

How to handle:

1. Use third-party Email Hygiene Tools to clean your contact list and remove invalid or high-risk Emails.
2. Import the cleaned invalid list into MAAC and update their status to "Suppressed".
3. Contact your CSM or Ops to apply for restoration. Ops will review and may manually restore the channel status to "Connected" after confirmation.

</details>

<details>

<summary>Q: What does it mean when the Email channel shows "Warning"? Can I still send emails?</summary>

"Warning" indicates sender domain settings are incomplete or recent sending health is declining. The system usually still **allows Email sending**, but this is a strong warning that should be addressed to avoid delivery issues or suspension.

Common Reasons:

* Domain verification missing (e.g. SPF passed but DKIM failed).
* Health decline (past 24 hours):
  * **Hard Bounce**: Quantity exceeds **10 emails** AND bounce rate exceeds **2%**.
  * **Spam Report**: Quantity exceeds **5 emails** AND report rate exceeds **0.3%**.

How to handle:

* If it's a verification issue: contact your IT department to check DNS records (SPF/DKIM).
* If it's a health issue:
  * Consider suspending high-risk campaigns.
  * Review recent lists and content quality.
  * Consider list cleaning to remove low-engagement or invalid contacts.

</details>

<details>

<summary>Q: Why is the Email channel settings page "Read-only" and uneditable?</summary>

The Email channel is managed in a "Managed Service" mode. Settings involve DNS verification and third-party sending service integration and must be configured/verified by the Crescendo Lab Ops team. The Admin Center's Email settings page is view-only.

If you need modifications (add/modify sender info, add sender domain, request DNS re-verification), contact your Customer Success Manager (CSM) for assistance.

</details>

#### III. Email Function Billing

<details>

<summary>Q. Why can't I use the "Send Email" node in the journey, and the button shows Upgrade?</summary>

This means your Email channel has not completed the activation process. Email activation requires domain verification (DNS) and sender settings managed by the Ops team. Contact your CSM to apply for activation and complete the backend settings to unlock this feature.

</details>

<details>

<summary>Q. How is the Email sending function charged? Is there a free quota?</summary>

The Email function uses a **"Plan Quota + Overage Pay-per-use"** model:

* Plan Quota: Monthly free sending quota based on your subscription plan.
* Overage Billing: Excess beyond the free quota is charged per-email.

(For detailed quotas and unit prices, consult your CSM or the quotation.)

</details>

<details>

<summary>Q. How are overage fees deducted? Is a separate top-up required?</summary>

Overage fees are **directly deducted from MAAC points**, sharing the balance with SMS/MMS. Email overage fees use the same **MAAC Points Pool (CL Points Pool)** as SMS/MMS. If the balance is insufficient, top-up per the existing process is required.

</details>

<details>

<summary>Q. If email delivery fails (e.g., recipient address does not exist), will I still be charged?</summary>

The system has a **"Hard Bounce Credit-back"** mechanism. Points are deducted at send time, but if an email is determined to be a **Hard Bounce** within **24 hours**, the system will automatically refund the fee for that email.

</details>

When you complete the above channel activation and contact import, you can go to Customer Journey to start sending emails. For Email editor operations and journey node settings, please refer to: 👉 [Feature Guide | Email Omnichannel Journeys & Editor Tutorial](https://crescendolab.zendesk.com/hc/en-us/articles/53567465248537)

### Related articles

* [Feature Guide | Email Omnichannel Journeys & Editor Tutorial](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBnXvCW4MDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkOafO4MDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJfL2hjL2VuLXVzL2FydGljbGVzLzUzNTY3NDY1MjQ4NTM3LUZlYXR1cmUtR3VpZGUtRW1haWwtT21uaWNoYW5uZWwtSm91cm5leXMtRWRpdG9yLVR1dG9yaWFsBjsIVDoJcmFua2kG--354e0d03e0df69fe11e0195fb3ce3e7a01ece2e0)
* [Tutorials｜Customer Journey ✨ New ✨](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkQ8ocDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkOafO4MDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJEL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMTIyMDExMTMtVHV0b3JpYWxzLUN1c3RvbWVyLUpvdXJuZXktTmV3BjsIVDoJcmFua2kH--880c82a842d68bb4549cfddc0615685de88cb5a4)
* [Tutorials | How to Upload Product Feed Data?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkP8pFoMDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkOafO4MDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJQL2hjL2VuLXVzL2FydGljbGVzLzUzMjI1NjgzMjkyMDU3LVR1dG9yaWFscy1Ib3ctdG8tVXBsb2FkLVByb2R1Y3QtRmVlZC1EYXRhBjsIVDoJcmFua2kI--4930eb8a2257df8d21f42018e7cf2cae4436684a)
* [Feature Introduction | WhatsApp Broadcast: Overview & Setup Guide](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBnkY4fRMDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkOafO4MDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJjL2hjL2VuLXVzL2FydGljbGVzLzUzNjc2NDc3NzY4NzI5LUZlYXR1cmUtSW50cm9kdWN0aW9uLVdoYXRzQXBwLUJyb2FkY2FzdC1PdmVydmlldy1TZXR1cC1HdWlkZQY7CFQ6CXJhbmtpCQ%3D%3D--b662f812a079685271e4f26722dce51907203c49)
* [Tutorial | SDK Web Behavior Tracking Tool](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJk0ii%2BuJToYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkOafO4MDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJOL2hjL2VuLXVzL2FydGljbGVzLzQxNDMwMDUyMTIzODAxLVR1dG9yaWFsLVNESy1XZWItQmVoYXZpb3ItVHJhY2tpbmctVG9vbAY7CFQ6CXJhbmtpCg%3D%3D--ef6f5f7ce2e3bd16ea792bb037904835684eb5d2)
