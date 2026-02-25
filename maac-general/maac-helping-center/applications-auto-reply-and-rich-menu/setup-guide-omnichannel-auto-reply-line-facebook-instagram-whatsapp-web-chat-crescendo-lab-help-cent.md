# Setup Guide｜Omnichannel Auto-Reply (LINE / Facebook / Instagram / WhatsApp / Web Chat) – Crescendo Lab Help Center

#### Prerequisite

Below is the complete setup process for Auto-reply, applicable to LINE, Facebook, Instagram, WhatsApp and WebChat channels:

* https://crescendolab.zendesk.com/hc/en-us/articles/47179966498841
* https://crescendolab.zendesk.com/hc/en-us/articles/47357535190937
* https://crescendolab.zendesk.com/hc/en-us/articles/44652331569945/live\_preview/01KEY4SJ73N7J29K4JKT93RHT5
* https://crescendolab.zendesk.com/hc/en-us/articles/42290656017945-Tutorials-Set-an-Official-Webpage-Interaction-Tool-Web-Chat-Widget-and-Connect-to-CAAC
* https://crescendolab.zendesk.com/hc/en-us/articles/43405131619481

{% stepper %}
{% step %}
### Go to Auto-Reply Page

Navigate to \[Application Center > Auto-Reply], then click "Create Auto-Reply".
{% endstep %}

{% step %}
### Name the Rule & Select a Reply Type

Choose from the following types:

* New Contact Welcome Message\
  Note: Whether it is LINE, Facebook Messenger, Instagram, WhatsApp and WebChat only one "Welcome Message" type of Auto-reply can be enabled per platform at a time.
* Keyword Reply\
  Each Auto-reply can only be set with one keyword. The content entered by the user must exactly match the set keyword to trigger.
* General Reply\
  "General Reply" is a time-based automated reply mechanism. When a user sends a message within the "specific time period" you set, and the message does not match any keywords, the system will automatically send this reply.

🚨 Reply type cannot be changed after creation. Please create a new one if needed.

Definition of "First Interaction" (for Welcome Message trigger):

![](../../../.gitbook/assets/54237229788953)
{% endstep %}

{% step %}
### Set Trigger Schedule & Frequency

📌 Note: The maximum frequency limit for Auto-reply is 30 days.

Keyword Reply: Can be scheduled with start/end date.

* Within the specified schedule, contacts will receive a unified reply to any message sent.
* You can set "Trigger at most once per contact every N hours / days".

![](../../../.gitbook/assets/54237258305177)

General Reply: Supports daily, monthly, business hours, or non-business hours.

📌 Schedule Priority: Monthly > Business/Non-business Hours > Daily

📌 Overlapping schedules cannot be enabled simultaneously. The system will prompt you to adjust.

Example: Two daily general replies both set from 12:00 to 13:00 → Only one can be active at a time.

![](../../../.gitbook/assets/54237229808025)

Welcome Message: Automatically sent when a contact joins and interacts for the first time

When a user interacts with the brand via a communication channel for the "first time", the system will automatically send the default welcome content.

| Platform                   | Definition of First Interaction                                                                       | Notes                                                                                                                                                                                              |
| -------------------------- | ----------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| LINE                       | Contact joins the brand's LINE Official Account for the first time (Friendship established)           | If unblocked and rejoined, the welcome message will be triggered again                                                                                                                             |
| Facebook Messenger         | Contact sends a message to the brand's Facebook Page for the first time                               | Clicking an ad without actively sending a message is not considered an interaction                                                                                                                 |
| Instagram Business Account | Contact sends a DM to the brand's IG or replies to a story for the first time                         | Only supports triggers from IG chat or story interactions; comments, likes, etc. are not included                                                                                                  |
| WhatsApp Business Account  | Contact proactively sends a message to the brand account for the first time.                          | The user must proactively send the first message and not yet exist in the Crescendo system to trigger the welcome message; simply opening the window without sending a message will not trigger it |
| Web Chat Widget            | When a visitor enters the website chat room (opens the chat window), it is considered an interaction. | As soon as the visitor opens or enters the Web Chat widget, the system automatically triggers the welcome message.                                                                                 |

![](../../../.gitbook/assets/54237258309657) ![](../../../.gitbook/assets/54237258313113)
{% endstep %}

{% step %}
### Select Channel

You can select up to four platforms (limit one account each): LINE, Facebook Page, Instagram Business Account, WhatsApp Business Account and Web Chat Widget.

You can bind up to one account per platform, and a maximum of three accounts total:

* LINE Official Account
* Facebook Page
* Instagram Business Account

Each channel supports up to 10 tags.

📌 Only connected channels will appear in the list.

![](../../../.gitbook/assets/54905476050457)
{% endstep %}

{% step %}
### Edit Message Content

You can configure separate messages for bound and unbound contacts.

| Platform                  | Supported Format                                                                | Notes                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ------------------------- | ------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| LINE                      | Text, Image, Flex, Quick Reply, Dynamic Variables                               | Recommend using short links + GA4                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Facebook Messenger        | Text, Image, Generic Template, Quick Reply                                      | GA4 tracking supported                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Instagram Business        | Text, Image, Generic Template, Quick Reply                                      | GA4 tracking supported                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| WhatsApp Business Account | Text, Image (5MB), Document (100MB), Card Message, List Messages, Reply Buttons | <p>- Only single message can be sent at a time<br>- Supports GA4 performance tracking</p>                                                                                                                                                                                                                                                                                                                                                                                    |
| Web Chat Widget           | Text, Image, Card Carousel, Quick Reply                                         | <p>Message limits:<br>- Up to 5 message bubbles per rule.<br>Quick Reply:<br>- Up to 10 buttons per message module.<br>- Supports text replies only (clicking a button sends the button text as a message).<br>- Opening URLs is not supported.<br>Card Carousel:<br>- Includes an image, title, description, and buttons.<br>- Supports horizontal scrolling between cards.<br>- Up to 3 buttons per card.<br>- Buttons support both Open URL and Send Message actions.</p> |

📌 Definition of a bound contact: Contact with a Customer ID in MAAC.

Each message editor supports tagging actions, with a limit of 10 tags.

⚠️ Web Chat Card Carousel Module: You can add a Card Carousel, where each card includes an image, title, description, and buttons. Buttons support Open URL and Send Text actions, with up to 3 buttons per card.

![](../../../.gitbook/assets/54905474921241)

⚠️ WhatsApp Business Account Message Module: Supports Text, Media (Image/Document), and Interactive Messages. You can set up "List Messages" to integrate up to 10 menu options or use "Reply Buttons" to guide users to interact with a single click.

![](../../../.gitbook/assets/54237258319513) ![](../../../.gitbook/assets/54237229818521)

Format and Limit Reminders:

* Single Bubble Only: Due to official WhatsApp regulations, only one chat bubble can be sent per auto-reply.
{% endstep %}

{% step %}
### Save & Activate

After saving, go back to the list and manually enable the rule.

If schedules overlap, the system will prompt you to turn off conflicting rules.
{% endstep %}
{% endstepper %}

#### Duplicate Auto-Reply

Click “Duplicate” to copy an existing rule and speed up your setup. Messages and settings will be prefilled and can be adjusted freely.

***

After completing the above settings, your brand is equipped with automated service capabilities across LINE, Facebook, Instagram, WhatsApp and Web Chat.

Through the Auto-tagging feature, the system not only helps you respond to customers instantly during off-hours but also automatically identifies and tags high-potential visitors, accumulating a precise list for future Broadcasts or Customer Journeys.

It is recommended to regularly visit the "Report" page to review trigger counts and click data for each channel, continuously optimizing your auto-reply strategy to maximize customer service efficiency and marketing conversion!

#### WhatsApp Opt-in / Compliance (stepper)

{% stepper %}
{% step %}
### Technical Definition of Opt-in

According to Meta's technical specifications, brands must obtain explicit authorization actions from users before the system can mark the contact status as OPTED\_IN.

* Prerequisite for Reach: Only for users with OPTED\_IN status does the brand have the authority to proactively send "Marketing Template Messages" in the future.
* Authorization Action: Users must proactively send specific keywords (e.g., Subscribe / START) or click interactive buttons to complete authorization.
{% endstep %}

{% step %}
### Risk Management: Opt-out and Account Permissions

Meta strongly requires brands to provide an easy opt-out method.

* Compliance Impact: Sending messages without consent or lacking a clear opt-out method will lead users to click "Report" or "Block," which may lower the account's quality rating or even lead to permanent suspension.
* System Mechanism: MAAC has built-in compliance keyword detection (e.g., Unsubscribe / STOP), which takes precedence over all custom reply logic to ensure brand operations comply with communication regulations.
{% endstep %}

{% step %}
### Practical Application in Auto-Reply

To optimize the compliance process, it is recommended to use the "WhatsApp Link Generator" so that users automatically send a subscription message immediately upon opening the chat to complete subscription authorization, combined with the "Auto-tagging" feature for data tracking.

Complete Guide: https://crescendolab.zendesk.com/hc/en-us/articles/54186983648281
{% endstep %}
{% endstepper %}

#### Related articles

* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkXVgOzKzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkBXdwcLDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSIBey9oYy9lbi11cy9hcnRpY2xlcy80ODA0Nzg1NTExNDEzNy1GZWF0dXJlLU92ZXJ2aWV3LU9tbmljaGFubmVsLUF1dG8tUmVwbHktU3VwcG9ydHMtTElORS1GYWNlYm9vay1JbnN0YWdyYW0tV2hhdHNBcHAtV2ViQ2hhdAY7CFQ6CXJhbmtpBg%3D%3D--38dd4ff9b60ba0bbc8e1b5fc582926a1f27fca89
* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkb49oDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkBXdwcLDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJUL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQ2MDM3Mjk2ODktVHV0b3JpYWxzLU1BQUMtTWVzc2FnZS1Nb2R1bGUtVGVtcGxhdGUtTGlicmFyeQY7CFQ6CXJhbmtpBw%3D%3D--bcebf648f8604b8c8a11a27eac44a7f52c522251
* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBnIJPHoKjoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkBXdwcLDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJNL2hjL2VuLXVzL2FydGljbGVzLzQ3MTc5OTY2NDk4ODQxLVR1dG9yaWFscy1Ib3ctdG8tQWRkLUZhY2Vib29rLUNoYW5uZWxzBjsIVDoJcmFua2kI--67d1d62bd4fe55f22419c3fb7c0b8eeaf78cd7d5
* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJn%2FD0kSKzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkBXdwcLDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJQL2hjL2VuLXVzL2FydGljbGVzLzQ3MzU3NTM1MTkwOTM3LVR1dG9yaWFscy1Ib3ctdG8tQWRkLWFuLUluc3RhZ3JhbS1DaGFubmVsBjsIVDoJcmFua2kJ--a8eb99f2eed64f0ba8a8b330998fbb3c42f1bb92
* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJlcQs60KzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkBXdwcLDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJTL2hjL2VuLXVzL2FydGljbGVzLzQ4MDU1NTU0NTYzMjI1LVNldHVwLUd1aWRlLVNpbXBseUJvb2stbWUtUmVzZXJ2YXRpb24tTW9kdWxlBjsIVDoJcmFua2kK--2e0313eb1a074011dc8ec7c7625ebaa60d9e490a
