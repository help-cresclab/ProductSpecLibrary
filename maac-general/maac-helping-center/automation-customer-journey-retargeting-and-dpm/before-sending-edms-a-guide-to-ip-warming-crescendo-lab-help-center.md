# Before Sending EDMs: A Guide to IP Warming – Crescendo Lab Help Center

Before launching large-scale email marketing (EDM) via MAAC, establishing a high-quality sending reputation is a crucial step to ensuring marketing effectiveness. IP Warm-up can significantly improve email deliverability. Maintaining a good email reputation not only protects brand image but also ensures your brand messages accurately reach customer inboxes, bringing significant conversion rates to marketing automation.

"Please read this guide carefully. With the assistance of Crescendo Lab, complete the '14-Day Email IP Warm-up Process' together to lay a solid foundation for the Omnichannel Customer Journey."

## Background Knowledge

Before starting, understanding the basic operating mechanisms of email helps you understand the necessity of warming up.

The email ecosystem is dominated by Internet Service Providers (ISPs, such as Gmail, Yahoo, Microsoft Outlook). The primary task of these providers is to protect their users' inboxes from spam and malware.

* **Reputation System:** ISPs score every IP address and domain that sends email. The higher the score, the easier it is for emails to enter the "Inbox"; if the score is too low, they will be thrown into the "Spam Folder" or rejected directly.
* **Risk Assessment of New IPs:** For ISPs, any new IP address without a historical sending record represents a potential risk. ISP systems default to imposing strict traffic limits and monitoring on unfamiliar sources.
* **Industry Standard:** IP Warm-up is a universal standard procedure in global email marketing, not a limitation of a specific platform. No matter which marketing tool you use, as long as a new sending IP is enabled, you must go through this procedure to "introduce" yourself, thereby gaining the trust of ISPs.

***

## IP Warm-up

**IP Warm-up** is a standard procedure for building sending reputation, which is a "gradually increasing Email sending plan". By gradually increasing the sending volume during the initial use of the Email IP, you prove to ISPs that you are a high-quality sender sending compliant content, achieving optimal deliverability (avoiding being marked as spam). Crescendo Lab will assist in this stage.

IP Warm-up only needs to be performed once. By increasing the Email sending volume daily, gradually scale up until the warm-up is completed:

| Days         | Daily Email Volume (Cap)   | Execution Strategy and Coordination (Assisted by Crescendo Lab)                                                   |
| ------------ | -------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Day 1**    | **Internal Team List**     | First send to the \[Internal Personnel] list (used to establish positive interaction signals)                     |
| **Day 2**    | **500 emails**             | Officially start sending to external members, prioritizing high-engagement audiences (if any).                    |
| **Day 3**    | **700 emails**             | Previous day's basis +40%. Start observing open and bounce data.                                                  |
| **Day 4**    | **1,000 emails**           | Previous day's basis +40%. Continue monitoring ISP acceptance of the new IP.                                      |
| **Day 5-13** | **Increment sequentially** | Increase the sending quota by 40% daily based on the previous day's basis.                                        |
| **Day 14**   | **Target volume achieved** | **Warm-up completed**: Target sending scale achieved. The Crescendo Lab team will send a completion notification. |

Note: The sending volume is a system-calculated cap. If data during the period (Spam Rate / Hard Bounce Rate) triggers security mechanisms leading to suspension, you will need to clean the list before starting the process.

> ⚠️ Key Actions: Please ask internal employees to cooperate by **Opening emails** (Open), **Clicking links** (Click), and if emails enter the spam folder, be sure to manually **"Report as not spam"** and move them back to the inbox.

If this step is skipped and large-scale sending is performed directly, ISP security algorithms will very likely judge your emails as a spam attack, causing damage to reputation.

***

## Getting Started

At the beginning, please assist in preparing the following operations to facilitate collaboration with the Crescendo Lab team:

{% stepper %}
{% step %}
### Ensure the Email channel is successfully activated

Please follow the onboarding guide:

[Onboarding Guide | How to Enable Email Channels and Import Contacts](https://crescendolab.zendesk.com/hc/en-us/articles/53570915864089-Onboarding-Guide-How-to-Enable-Email-Channels-and-Import-Contacts)
{% endstep %}

{% step %}
### Import Email Contacts (including tags)

The list for the initial stage of warm-up must be screened. Please import a contact list containing specific tags (Tags) for batch processing. Divide into #Internal Team and #External List tags and #High Engagement tags (if any). The naming convention of tags can follow brand habits, as long as internal and external audiences can be identified.

Images:

* https://crescendolab.zendesk.com/hc/article\_attachments/54667407608857
* https://crescendolab.zendesk.com/hc/article\_attachments/54667300394521
{% endstep %}

{% step %}
### Create a Warm-up Email Template (Warm-up Email Template)

Please create an Email template dedicated to warm-up in MAAC's Template Library and provide it for the Crescendo Lab team to perform Warm-up.

[Feature Guide | Email Omnichannel Journeys & Editor Tutorial](https://crescendolab.zendesk.com/hc/en-us/articles/53567465248537-Feature-Guide-Email-Omnichannel-Journeys-Editor-Tutorial#h_01KCX6CCYT4JZN7K9R605AX1CG)

Image:

* https://crescendolab.zendesk.com/hc/article\_attachments/54667407609625
{% endstep %}

{% step %}
### Contact the Customer Success Manager

Inform the CSM that "Contact Import & Tagging" and "Warm-up Email Template" are completed. Contact the CSM through the channel used when activating Email. After notification, the Crescendo Lab team will assist your brand in performing automated Email warm-up, scheduling sends based on the tags you set.
{% endstep %}
{% endstepper %}

|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Warm-up Email Content Guidelines**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| <p>- <strong>Format Standardization:</strong> Emails must conform to standard and legal formats. Avoid using excessive exclamation marks, all-caps headlines, or an overly high ratio of images to prevent being marked as spam.<br>- <strong>Content Guidelines:</strong> It is recommended that warm-up email content focus on <strong>brand announcements, member rights notifications, or service-oriented messages</strong>. Avoid sending high-intensity promotional or highly inducive content during the warm-up period to reduce the risk of being marked as spam or unsubscribed by users.<br>- <strong>Functional Links (CTA):</strong> Include functional links in the content. User click behavior (Clicks) can significantly improve sending reputation.</p> |

⚠️ Note: Do not start any "Automated Marketing Journeys (Journey)" before the 14-day warm-up procedure is completed. Starting too early may cause automated emails to go directly to the spam folder due to unstable IP reputation, thereby affecting overall domain health.

***

## FAQ

<details>

<summary>Does using email aliases "alias+1" (e.g., user+1@gmail.com) for testing help with warm-up?</summary>

No, it does not help. Email warm-up relies on interactions with "diverse and independent" mailboxes to build reputation. Sending a large number of emails to the same mailbox (even using aliases) is of no value because ISPs track the overall interaction patterns under their network. Repetitive behavior from a single mailbox cannot represent extensive recipient trust.

</details>

<details>

<summary>If the Sender Domain already has a reputation, is warm-up still needed when changing IPs?</summary>

Yes. Sending reputation is bound to the combination of "IP Address + Domain". Since the new IP has no established historical association with your domain, ISPs will view it as a suspicious source. You must re-execute the warm-up procedure to establish ISP trust in this new combination and avoid emails being marked as suspicious activity.

</details>

***

### Related articles

* [Onboarding Guide | How to Enable Email Channels and Import Contacts](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkOafO4MDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlKY962MToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJoL2hjL2VuLXVzL2FydGljbGVzLzUzNTcwOTE1ODY0MDg5LU9uYm9hcmRpbmctR3VpZGUtSG93LXRvLUVuYWJsZS1FbWFpbC1DaGFubmVscy1hbmQtSW1wb3J0LUNvbnRhY3RzBjsIVDoJcmFua2kG--135f60d98336547541ce4e4854eedf75a04ffa39)
* [Feature Guide | Email Omnichannel Journeys & Editor Tutorial](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBnXvCW4MDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlKY962MToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJfL2hjL2VuLXVzL2FydGljbGVzLzUzNTY3NDY1MjQ4NTM3LUZlYXR1cmUtR3VpZGUtRW1haWwtT21uaWNoYW5uZWwtSm91cm5leXMtRWRpdG9yLVR1dG9yaWFsBjsIVDoJcmFua2kH--9a10940c395d02892ba2b3f6a2d74d1164a069d3)
* [Tutorials | How to Upload Product Feed Data?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkP8pFoMDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlKY962MToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJQL2hjL2VuLXVzL2FydGljbGVzLzUzMjI1NjgzMjkyMDU3LVR1dG9yaWFscy1Ib3ctdG8tVXBsb2FkLVByb2R1Y3QtRmVlZC1EYXRhBjsIVDoJcmFua2kI--1fab889b2865eea923a18d4921efc29b1ce828aa)
* [Tutorials｜AI Agent Set Up](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBn4y9HqLjoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlKY962MToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJAL2hjL2VuLXVzL2FydGljbGVzLzUxNTg2MDc3MDMwNDI1LVR1dG9yaWFscy1BSS1BZ2VudC1TZXQtVXAGOwhUOglyYW5raQk%3D--8de745d1dba1b8edd6d0e0327e574705ca51511f)
* [Tutorials｜Retargeting](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJlJxx4LLDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlKY962MToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI8L2hjL2VuLXVzL2FydGljbGVzLzQ4NDI2MjcyNjM5Mzg1LVR1dG9yaWFscy1SZXRhcmdldGluZwY7CFQ6CXJhbmtpCg%3D%3D--2824d6a900bcec1544d7e3d65dffd385f556520d)
