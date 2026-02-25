# Feature Guide | Email Omnichannel Journeys & Editor Tutorial – Crescendo Lab Help Center

This article will guide you on how to integrate Email (EDM) channels into the MAAC Customer Journey to achieve cross-channel automated marketing communication.

## ＃Feature Introduction

The Omnichannel Customer Journey now integrates Email as a core communication channel, enabling brands to move beyond the limitations of a LINE-only environment. With this added email capability, marketers can flexibly orchestrate LINE, SMS, and Email messages within a single journey canvas, based on user behaviors and preferences.

Key updates include:

* **Email Channel Integration**: Officially supports adding Email sending nodes in the Customer Journey, allowing you to seamlessly connect LINE, SMS, and Email on the same canvas for a more complete communication strategy.
* **New Email Editor:** Provides an intuitive Drag & Drop interface with built-in design elements. No coding background required to quickly create beautiful responsive Emails.
* **Reachability**: The system automatically determines if a user is "reachable" on each channel and performs smart routing based on your priority settings (e.g., try lower-cost Email first, if unreachable then send LINE).
* **Cross-channel Interaction Trigger**: Supports setting Email interactions (such as Open, Click Link, Unsubscribe) as trigger conditions or filter thresholds for the journey, making marketing responses more immediate and precise.

⚠️ Note before use Currently, Email channel activation requires assistance from the Crescendo Lab operation team and cannot be done entirely via self-service. If you have not yet completed channel activation or contact import, please prioritize reading and completing the following steps: 👉 [Setting Tutorial | How to enable Email channel and import contacts?](https://crescendolab.zendesk.com/hc/en-us/articles/53570915864089)

![](../../../.gitbook/assets/53663962489753)

## ＃Feature Advantages

1. **Cost Optimization and Waterfall Strategy:** Use the "Channel Reachability" node to establish priorities. For example: prioritize sending lower-cost Emails; if the user does not open or is unreachable, automatically switch to sending LINE messages, and finally use higher-cost SMS to maximize marketing budget efficiency.
2. **Rich Information Delivery:** Use Email for content requiring complete text and image explanations (such as event details, newsletters), while using LINE or SMS for short, immediate reminders.
3. **Cross-channel Remarketing:** When a user blocks the LINE Official Account, the system can automatically detect this and switch to Email or SMS channels to win back key customers.
4. **Unified Data Management**: No need to switch between multiple platforms; view cross-channel sending performance and user footprints directly in MAAC.

![](../../../.gitbook/assets/53663963494937)

## ＃Setup Tutorial | Create Omnichannel Customer Journey

For basic tutorials on creating a Customer Journey, please refer to: [Feature Description | Customer Journey ✨New Upgrade✨](https://crescendolab.zendesk.com/hc/en-us/articles/4413212201113)

After setting the trigger conditions for the Customer Journey, you can now add a "Send Email" node to the journey:

![](../../../.gitbook/assets/53663993484825)

#### Add Email Message Node

{% stepper %}
{% step %}
### Sender Profile

Select a verified Email channel, choose a sender, enter the Email subject, and click "Next".
{% endstep %}

{% step %}
### Message

Click to enter the editor and drag design elements (e.g., text, images) to design the Email.
{% endstep %}
{% endstepper %}

![](../../../.gitbook/assets/53664033634713) ![](../../../.gitbook/assets/53663996732569)

**⚠️ What are "From (Sender)" and "Reply-To"?**

When setting up Email sending, you will see a "Sender Profile", which contains two key email addresses with different purposes in email mechanisms and marketing strategies:

* From Address (Sender): This is the "Sender Source" that recipients see first in their inbox list, representing the brand's identity. To ensure good sender reputation and deliverability, this address must use a Sender Domain that has completed DNS verification.
* Reply-To Address: The address where the email will actually be sent when a recipient clicks "Reply", used to receive customer inquiries or feedback. It is usually recommended to set this to a real, managed customer service email, such as service@yourbrand.com or support@yourbrand.com

Tip: If you need to change an existing reply-to address, or add other sender identities, please contact your Customer Success Manager (CSM) for assistance.

#### Set "Reachability" Branching

Use this node to determine if a user is in a "reachable" status for a specific channel and branch accordingly based on the result.

* Setup Method: Select a channel you want to check (e.g., Email) in the node.
* Logic: The system checks if the user is eligible to receive messages on this channel:
  * Reachable: The user can receive messages via this channel and will enter this path (can proceed to send messages for this channel).
  * Unreachable: The user cannot receive messages via this channel and will enter this path (can proceed to check other channels or end the journey).

![](../../../.gitbook/assets/53664036285977)

#### Set Email Related Triggers

You can use Email interaction behaviors as "Triggers" for the journey:

* Email Open: When a contact opens the email (Note: Due to privacy policies, there may be discrepancies in open event tracking and triggering).
* Email Click: When a contact clicks a maac.io short link inside the email.
* Email Unsubscribe: When a contact unsubscribes.

![](../../../.gitbook/assets/53664604503065)

#### Enable Website User Identification

If you plan to use website behavior events (such as Add to Cart or Page View) to trigger Email automation journeys, please make sure this setting is enabled.

* Setting location: Go to Admin Center > Channels > Web Channel, click the Edit button on the right side of your website channel, then switch to the Tools tab.
* Feature status: This feature is Disabled by default. Please enable Website User Identification.

For security and access control reasons, the system will only receive and process identity identification requests from the Web SDK (e.g. identify(email)) when this toggle is enabled. If it is not enabled, the system will ignore Email binding requests even if the Web SDK has already been installed on your website.

How it works: Once enabled, when a customer performs an identity-confirming action on your website—such as logging in or completing checkout—the Web SDK can associate the current browser session with a known Email contact. This allows the customer’s on-site behavior to be correctly attributed, enabling it to trigger subsequent EDM marketing journeys.

![](../../../.gitbook/assets/53791284879385)

## ＃Data and Performance Tracking

In the Customer Journey report, you can view detailed data for omnichannel and individual channels. For the Email channel, the following metrics are added:

* Bounced & Bounce rate: The sum of "Hard Bounce" and "Soft Bounce".
* Complaints & Complaint rate: The number of times recipients marked your email as spam. This is the most serious metric affecting domain reputation.
* Unsubscribes & Unsubscribe rate: The number of times recipients clicked the unsubscribe link.
* Delivery failures: The number of emails that failed to send. If this value is not zero, a link to "Download Failure Report" will be provided on the node for you to check specific reasons (e.g., insufficient balance, system block, etc.).

***

## ＃Operation Tutorial | Using Email Editor

Operation Guide

The Email Editor currently supports a Drag & Drop editor. You can:

* Drag Images, Text, Buttons, Dividers, etc., to the preview page on the right.
* Insert Personalization Variables: {contact\_name} (Default value can be set if no name exists).
* Set Tracking Links: The system automatically converts links to maac.io short URLs to track clicks, GA/SDK website events (UTM), and auto-tagging.

**Demo 1: Drag text to Email preview page**

To start designing an Email, drag content blocks (such as text, images, buttons) from the "Elements" on the left to the preview page on the right to edit content or adjust image sizes.

⚠️ The Email design page must include an "Unsubscribe" link or button to successfully save the Email.

![](../../../.gitbook/assets/53664600186649)

**Demo 2: Edit object styles and attributes**

After clicking an object on the preview page, you can adjust "Global Attributes" (such as line height, block size) via the left panel; if you need to configure "local text" (such as font, color, link), simply select that text segment directly on the preview page.

![](../../../.gitbook/assets/53664604508441)

**Demo 3: Set "Unsubscribe" link**

To comply with Email sending regulations, every Email must include an "Unsubscribe" link or button. If the email does not have an unsubscribe mechanism set, the Email cannot be saved or sent. You can set unsubscribe in the editor in two ways:

* Button Module: Select and set the "Unsubscribe" link in the button (please refer to the video below, click the \</> button)

![](../../../.gitbook/assets/53664751920665)

* Text Paragraph: Insert an "Unsubscribe" link in the text content (please refer to the video below, click "Short link", click the \</> button)

![](../../../.gitbook/assets/53664797884825)

Note: Currently, only the editor's built-in "Unsubscribe" link is supported. Adding your own brand or external unsubscribe links is not supported at this time.

**Demo 4: Set Email Column Layout**

Drag "Structure Blocks" (e.g., 1 column, 2 columns) from the left "Elements" panel to the preview page to easily complete multi-column paragraph layout.

![](../../../.gitbook/assets/53664901301913)

**Demo 5: Use Layer function to adjust Email layout**

Open the "Layers" panel on the left and drag objects up or down to quickly adjust the order of text or images.

![](../../../.gitbook/assets/53665000149529)

Necessary Regulations

{% stepper %}
{% step %}
### Unsubscribe Link

* Mandatory: Every email content must contain the {unsubscribe\_link} variable.
* If the system detects a missing "Unsubscribe Link", the node cannot be saved. This is to comply with international anti-spam regulations.
{% endstep %}

{% step %}
### File and Content Limits

* Image Size: Single image suggested to be less than 1 MB, width suggested 600px - 800px. Supports JPG, PNG, GIF.
* Subject Length: Suggested to be within 50 characters to avoid truncation on mobile.
{% endstep %}

{% step %}
### Test Sending

* Before officially going live, please be sure to use the "Send Test Email" function. The test email subject will automatically add Test -.
* Test recipients must be contacts already existing in MAAC. If you need to send to yourself or internal colleagues for preview, please make sure to import these Emails into the system contact list first.
{% endstep %}
{% endstepper %}

## ＃FAQ

<details>

<summary>I. Operation and Setup — Q: Why can't I save Email content in the journey?</summary>

This is usually because the content is missing an unsubscribe link. To maintain good sending reputation and comply with international regulations, MAAC mandates that every marketing email must include an unsubscribe mechanism. Please use the variable function in the editor to insert `{unsubscribe_link}` into the email body.

</details>

<details>

<summary>I. Operation and Setup — Q: Why am I unable to select "Email Unsubscribed," "Email Opened," or "Email Clicked" when setting up triggers in the Customer Journey?</summary>

This is because your Email Channel has not been fully activated, or valid Sender Profiles have not yet been established.

Since the system cannot find trackable entities, the options will appear disabled or unselectable. Specific reasons:

* For "Email Unsubscribed": This trigger relies on the Brand Domain configuration. The system must confirm that your brand's root domain (e.g., `brand.com`) has been verified before it can associate and track unsubscribe events for that domain.
* For "Email Opened" and "Email Clicked": These two triggers rely on the Sender Profile. According to the system design, you must specify which sender identity to monitor. If you have not created any valid Sender Profiles, the system will not find any targets for you to select.

How to solve: Please check the status in Admin Center > Channels > Email. If it displays as Not Set or shows a grey indicator, it means your domain verification or sender setup is incomplete. Please contact your CSM (Customer Success Manager) to assist with Email Channel activation and Sender Profile creation. Once the backend verification and configuration are complete, you will be able to select these options in the Journey normally.

</details>

<details>

<summary>II. Journey Logic — Q: What happens if SMS or Email credits run out?</summary>

Messages for that channel will not be sent, but other actions in the journey (such as tagging, sending LINE messages) will continue to execute. The system will send an alert email to the administrator when insufficient balance is detected, and display a warning icon in the journey list.

</details>

<details>

<summary>II. Journey Logic — Q: If the same customer has data in both LINE and Email, will the same journey be triggered repeatedly?</summary>

Please go to Admin Center > Customer Data Hub settings first and set Email as the Unify Key. The system can then integrate identities from different channels into the same user and calculate trigger limits for the "Unified Contact" to avoid repeated disturbance.

Special Note: The Email field in the Contact Profile does not equal valid Email sending eligibility. The user must be imported into the Email Channel (Brand Domain) and have agreed to subscribe to be capable of receiving Emails.

</details>

<details>

<summary>II. Journey Logic — Q: Will tags applied in an Email journey be visible when viewing LINE contact profiles?</summary>

Tags are applied to the "Unified Contact". However, in interface presentation, if the tag was applied via the Email channel, when viewing identity information for other channels (like LINE), these synced tags will be displayed under the Customer Data Hub (CDH) tab.

</details>

<details>

<summary>II. Journey Logic — Q: Can Email short URLs (maac.io) track website behavior?</summary>

As long as your website has the MAAC SDK installed and the link carries UTM parameters, the system can track subsequent website behavior events after the user clicks the `maac.io` short URL in the email.

</details>

### Related articles

* [Onboarding Guide | How to Enable Email Channels and Import Contacts](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkOafO4MDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnXvCW4MDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJoL2hjL2VuLXVzL2FydGljbGVzLzUzNTcwOTE1ODY0MDg5LU9uYm9hcmRpbmctR3VpZGUtSG93LXRvLUVuYWJsZS1FbWFpbC1DaGFubmVscy1hbmQtSW1wb3J0LUNvbnRhY3RzBjsIVDoJcmFua2kG--be720bc15508276dafb902b1e8ba1092440c6b36)
* [Tutorials｜Customer Journey ✨ New ✨](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkQ8ocDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnXvCW4MDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJEL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMTIyMDExMTMtVHV0b3JpYWxzLUN1c3RvbWVyLUpvdXJuZXktTmV3BjsIVDoJcmFua2kH--3a4074b18a6ddc3cfd7b44a9c119575b1021cc7f)
* [Feature Introduction | WhatsApp Broadcast: Overview & Setup Guide](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBnkY4fRMDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnXvCW4MDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJjL2hjL2VuLXVzL2FydGljbGVzLzUzNjc2NDc3NzY4NzI5LUZlYXR1cmUtSW50cm9kdWN0aW9uLVdoYXRzQXBwLUJyb2FkY2FzdC1PdmVydmlldy1TZXR1cC1HdWlkZQY7CFQ6CXJhbmtpCA%3D%3D--c0012edd9e470cd2a57b33a5d94de4663e51eda4)
* [Feature Description｜MAAC Contact Import and Update](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBnqhYkDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnXvCW4MDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJYL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMzg2Njc4MDEtRmVhdHVyZS1EZXNjcmlwdGlvbi1NQUFDLUNvbnRhY3QtSW1wb3J0LWFuZC1VcGRhdGUGOwhUOglyYW5raQk%3D--17eccccfba0b571b4ef7ddd6cfcc81c694ce6654)
* [Tutorials | How to Upload Product Feed Data?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkP8pFoMDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnXvCW4MDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJQL2hjL2VuLXVzL2FydGljbGVzLzUzMjI1NjgzMjkyMDU3LVR1dG9yaWFscy1Ib3ctdG8tVXBsb2FkLVByb2R1Y3QtRmVlZC1EYXRhBjsIVDoJcmFua2kK--85f95c55bb2df0cdae6419e95a7499753ed7315b)
