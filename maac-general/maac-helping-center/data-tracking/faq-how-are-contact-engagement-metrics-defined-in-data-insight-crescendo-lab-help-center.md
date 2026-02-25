# FAQ｜How Are Contact Engagement Metrics Defined in Data Insight? – Crescendo Lab Help Center

{% stepper %}
{% step %}
### What is the basis for the calculation of these indicators?

Contact engagement metrics (e.g., Open Rate, Click Rate) are calculated using the following logic:

* Based on MAAC system records of broadcast messages sent.
* The system tracks contact interactions after broadcasts are sent.
* Contacts are marked as "engaged" only if they have interacted with at least one broadcast message.

{% hint style="warning" %}
These metrics only reflect interaction behavior after a broadcast.

If a contact hasn't received any broadcasts, they won't be included in the analysis.
{% endhint %}
{% endstep %}

{% step %}
### Definition of each indicator

| Metric              | Definition                                                                                                                                      |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Open Rate**       | The percentage of users who opened any broadcast message (read receipt enabled)                                                                 |
| **Click Rate**      | The percentage of users who clicked on any MAAC short link in a broadcast message                                                               |
| **Conversion Rate** | The percentage of users who performed a defined conversion action (e.g., page view, form submission) after clicking a short link in a broadcast |
{% endstep %}

{% step %}
### Where does the data come from?

All engagement data is collected through:

* MAAC's **Broadcast** module
* MAAC's **Short Link** service
* MAAC's **Tracking Pixel** for conversions

Only data from broadcast campaigns sent via MAAC is included in this analysis.
{% endstep %}

{% step %}
### What Is "Engagement Level"?

#### For: Basic Plan, Growth Plan (no GA4 integration)

The system categorizes contacts into 3 levels based on how recently they have actively interacted with the LINE Official Account:

| Level       | Definition                                                                                             |
| ----------- | ------------------------------------------------------------------------------------------------------ |
| **Level 3** | LINE contacts who have actively interacted with the Official Account **within the past 30 days**       |
| **Level 2** | LINE contacts whose **last active interaction** was **31–90 days ago**                                 |
| **Level 1** | LINE contacts who have **not had any active interaction** in the past 90 days (includes blocked users) |

{% hint style="info" %}
This classification is calculated based on MAAC internal interaction data and does not require GA4 integration.
{% endhint %}

This classification helps users:

* Re-engage users who haven't interacted in a while
* Prioritize marketing campaigns for highly active users
* Monitor overall engagement trends in the contact database

***

#### For: Professional Plan or users with eCommerce feature enabled (GA4 integration required)

Contacts are classified into 5 levels based on both LINE and website behavior tracked via Google Analytics:

| Level       | Definition                                                                                                                                                     |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Level 5** | LINE contacts who, within the last 60 days, were tracked by GA as having browsed the website in depth or made a purchase                                       |
| **Level 4** | LINE contacts who, within the last 60 days, were tracked by GA as having clicked multiple links, browsed frequently, or made a purchase                        |
| **Level 3** | LINE contacts who actively interacted with the Official Account within 30 days (see note below); and within 60 days clicked a link or possibly made a purchase |
| **Level 2** | LINE contacts whose last active interaction with the Official Account was between 31–90 days ago                                                               |
| **Level 1** | LINE contacts with no active interaction in the past 90 days (includes blocked users)                                                                          |

**Definition of "active interaction" includes:**

* Sending messages to the Official Account
* Triggering auto-replies by entering keywords
* Tapping rich menus that display text
* Clicking images/buttons that trigger a response
* Adding the account as a friend
* Unblocking a previously blocked account
* Clicking inbound links (e.g., BindLink)

If you are integrated with a supported eCommerce platform and have completed binding, old contacts who click on order links or BindLinks will also be tracked.

Note:

* Level 4 and Level 5 are classified based on a proprietary Crescendo Lab model that considers interactions across LINE and your website, including triggered events, clicks, and message exchanges.
  * Level 5 represents highly engaged contacts with strong interactions across both platforms.
  * Level 4 includes slightly less engaged, but still active, contacts.
{% endstep %}
{% endstepper %}

### Related articles

* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmh8YcDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkft4gDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI4L2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMTIxNzI2OTctVHV0b3JpYWxzLUluc2lnaHRzBjsIVDoJcmFua2kG--ee7af49aa7d6c73cebf048c3af218ef98594d459
* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkzBMgDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkft4gDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI%2BL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQyODcxMzE0MTctVHV0b3JpYWxzLVJhcGlkLVJlZmVycmFsBjsIVDoJcmFua2kH--5d1561588695649ef527387a1640d00d4b0fdd8c
* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmp1FFgBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkft4gDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ1L2hjL2VuLXVzL2FydGljbGVzLzgxMTAyNzExNDYzOTMtSG93LXRvLXNoYXJlLUxJTkUtT0EtcGxhdGZvcm0tTElORS1EZXZlbG9wZXJzLUdBLVVBLUdBNC1hY2Nlc3MtdG8tQ3Jlc2NlbmRvLUxhYgY7CFQ6CXJhbmtpCA%3D%3D--28ede3b8cf498fc3d9bd903d7efc26a38d103987
* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJn6ysBcBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkft4gDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJgL2hjL2VuLXVzL2FydGljbGVzLzgwOTQ5NTI5MTM1NjEtVHV0b3JpYWwtQ0FBQy1Db25kdWN0LUNvbnZlcnNhdGlvbi1hbmQtQ29udGFjdC1JbmZvcm1hdGlvbgY7CFQ6CXJhbmtpCQ%3D%3D--ab2bdcb86814b151ff86bdc021b8f773ef9f4c81
* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBldJIkDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJkft4gDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSIBiy9oYy9lbi11cy9hcnRpY2xlcy80NDEzMjMyMjc0NzEzLVdoYXQtaXMtdGhlLW5vdGlmaWNhdGlvbi10ZXh0LVdoYXQtaXMtdGhlLWRpZmZlcmVuY2UtYmV0d2Vlbi1ub3RpZmljYXRpb24tdGV4dC1tZXNzYWdlLXByZXZpZXctYW5kLW1lc3NhZ2UGOwhUOglyYW5raQo%3D--939c58b94ec41aa2d8c2a1890941aa6aa5a62062
