# Tutorials | Deeplink – Crescendo Lab Help Center

Deeplink can help you identify the most effective channel that attracts friends to join your LINE OA, whether it is online (Facebook, Instagram, EDM, official website...) or offline (store, counter, sign, DM...) — deeplink helps track channels effectively!

#### 💁🏻‍♀️ Advantages

* Create different deeplink for different channels to generate specific link or QR code
* Provide different message for new member and existing member
* Use deeplink as special event's entrance
* Can immediately use the generated link or QR code as specific channel entrance

▶︎ Setting : Create single deeplink

{% stepper %}
{% step %}
### Create a single deeplink — Step 1

After clicking "create" button on the upper right corner, enter deeplink's name and description (optional).
{% endstep %}

{% step %}
### Create a single deeplink — Step 2

Set up tags that can identify this channel (up to 10 tags maximum, friends will be tagged by these tags after joining this channel)

![dd.jpg](https://crescendolab.zendesk.com/hc/article_attachments/8391071516697/dd.jpg)
{% endstep %}

{% step %}
### Create a single deeplink — Step 3

Optional: enable “When members click the link again, messages will still be triggered“.\
If enabled, friends will receive the message multiple times based on how many times they click the link (LINE will charge fees for sending the message).
{% endstep %}

{% step %}
### Create a single deeplink — Step 4

Optional: turn on/off the toggle to give different messages to new members (never joined the OA) / existing members (already joined the OA).
{% endstep %}

{% step %}
### Create a single deeplink — Step 5

When toggle is on, click "Edit" to open the message editor and edit the message. Click "create" after completing the message.

![dd-1.jpg](https://crescendolab.zendesk.com/hc/article_attachments/8391071512217/dd-1.jpg)
{% endstep %}
{% endstepper %}

#### ▶︎ Setting Redirect URL (redirect\_url)

If your brand wants users to automatically jump to a specific page after clicking a deeplink (such as a LINE Official Account, campaign page, or your own website), you can configure a redirect\_url.

This feature is useful for acquisition and conversion tracking scenarios, such as:

* Directing the deeplink to a LINE Official Account invitation page to track successful friend additions
* Directing the deeplink to a campaign or coupon page to boost conversions
* Redirecting users to your brand’s own landing page and integrating with SDK for user identification

System Flow

| Step | System Behavior                                                                                                                 |
| ---- | ------------------------------------------------------------------------------------------------------------------------------- |
| 1    | The user clicks the Deeplink URL                                                                                                |
| 2    | The Deeplink LIFF opens and creates a contact in MAAC (including authorization status)                                          |
| 3    | The Deeplink LIFF automatically redirects to the configured **redirect\_url** (e.g. LINE OA link https://line.me/R/ti/p/123456) |
| 4    | When the user adds the LINE OA, MAAC counts the conversion as successful                                                        |

🔔 Note: To enable this feature, please contact your Crescendo Lab Customer Success Manager.

Important Notes

* If the redirect URL points to a LINE Official Account invitation link (e.g. https://line.me/R/ti/p/xxxxx), ensure the binding and tracking logic are correctly configured.
* Incorrect or invalid URLs may cause redirect failures; test before use.
* The redirect\_url only works in mobile environments (LINE App / mobile browser). On desktop, a QR Code will be displayed, and clicks will not be counted.

#### ▶︎ Setting : Create deeplink by batch (high speed)

By clicking the "Batch Management" button on the upper right corner, you can create, edit or export multiple deeplinks by batch. Features include: Batch create deeplinks, Batch edit existing deeplinks, Export deeplink setting files, Export deeplink QR code.

This section demonstrates the "Batch create deeplinks" feature using the CSV template, explains each CSV column, and shows the final output on MAAC.

{% stepper %}
{% step %}
### Batch create deeplinks — Step 1

Click "Batch Management" button.
{% endstep %}

{% step %}
### Batch create deeplinks — Step 2

Choose "Batch create deeplinks".

![dd-3.jpg](https://crescendolab.zendesk.com/hc/article_attachments/8391365062297/dd-3.jpg)
{% endstep %}

{% step %}
### Batch create deeplinks — Step 3

Download the template file (CSV).
{% endstep %}

{% step %}
### Batch create deeplinks — Step 4

Fill out the template and click "Upload file".
{% endstep %}

{% step %}
### Batch create deeplinks — Step 5

Confirm the file format is accurate, and click "Create".

![dd-4.jpg](https://crescendolab.zendesk.com/hc/article_attachments/8391425386009/dd-4.jpg)
{% endstep %}

{% step %}
### Batch create deeplinks — Step 6

Check the upload result from the "Notification" icon on the upper right corner.
{% endstep %}

{% step %}
### Batch create deeplinks — Step 7

Click "More" to check the result status.

Hint: You can track the error message from here if the deeplink failed to create.

![dd-5.jpg](https://crescendolab.zendesk.com/hc/article_attachments/8391427768729/dd-5.jpg)
{% endstep %}
{% endstepper %}

**➤ Batch create deeplinks — CSV template explanation**

![d1.jpg](https://crescendolab.zendesk.com/hc/article_attachments/8040876547737/d1.jpg)

* name: enter deeplink's name
* description: enter deeplink's description (optional)
* tag: Set up tags that can identify this channel (up to 5 tags maximum; system will automatically create new tag if there's no such tag in MAAC)
* triggered\_again: When members click the link again, messages will still be triggered. LINE will charge fee for sending the message. Instruction: enter TRUE if allowed; enter FALSE if not allowed.
* new\_member\_message\_switch: new member message (enter TRUE to enable; enter FALSE to disable)
* new\_member\_message\_template\_id: new member message's template id
* existing\_member\_message\_switch: existing member message (enter TRUE to enable; enter FALSE to disable)
* existing\_member\_message\_template\_id: existing member message's template id

Reminder:

* For message template IDs (new\_member\_message\_template\_id & existing\_member\_message\_template\_id): create the message in "Template library" first, then copy and paste the template id into this column. Leave empty if you did not enable the feature, or if you want to edit messages directly in the deeplink message editor one by one.

**➤ Batch create deeplinks — output demo**

{% stepper %}
{% step %}
### Output demo — Name

After successful CSV upload, the names you filled in appear as created deeplinks, along with generated links and QR codes.

![dd6.jpg](https://crescendolab.zendesk.com/hc/article_attachments/8391698158489/dd6.jpg)
{% endstep %}

{% step %}
### Output demo — Description

If you left description empty in CSV, there will be no description.
{% endstep %}

{% step %}
### Output demo — Tag

Tags will automatically show on the deeplink.

![dd7.jpg](https://crescendolab.zendesk.com/hc/article_attachments/8391720873113/dd7.jpg)
{% endstep %}

{% step %}
### Output demo — triggered\_again

If you filled FALSE, the checkbox will not be checked.
{% endstep %}

{% step %}
### Output demo — new\_member\_message\_switch

If you filled TRUE, it will enable the new member message toggle button.

![dd8.jpg](https://crescendolab.zendesk.com/hc/article_attachments/8391698464793/dd8.jpg)
{% endstep %}

{% step %}
### Output demo — new\_member\_message\_template\_id

If you filled the template id in the CSV, the specific message template will appear in the message editor.

![dd9.jpg](https://crescendolab.zendesk.com/hc/article_attachments/8391698486809/dd9.jpg)
{% endstep %}
{% endstepper %}

#### ▶︎ Setting : Export by batch - high speed

![dd10.jpg](https://crescendolab.zendesk.com/hc/article_attachments/8391761519129/dd10.jpg)

* Can use keyword to search for specific deeplink.\
  Hint: Keyword search is case sensitive. If the deeplink is called "Test", searching "test" will not find it.
* Can select single deeplink or multiple deeplink at once by checking the checkbox.

Attention:

* If you used the message editor in the deeplink to edit messages directly, the "new\_member\_message\_template\_id" and "existing\_member\_message\_template\_id" columns will be empty in exported settings. To have template IDs in the export, download the "Batch edit existing deeplinks" CSV template, fill in the template IDs, upload it, then export the settings.
* Export deeplink setting files as CSV.
* Export deeplink QR codes as ZIP.

#### ▶︎ Performance

* Keyword search is supported. Reminder: keyword search is case sensitive.
* Each deeplink performance shows "Total clicks" and "Acquired members".
* Duplicate the link or download the QR code from the icons beside the link. Insert the link or QR code into online/offline channels. Use "Batch management" to export multiple links or QR codes at once.
* Click the report icon to see detailed performance results for the deeplink.
* Click the ⋯ icon to edit or archive the deeplink.

Hint: Deeplink can only be archived, not deleted.

![dd-1.jpg](https://crescendolab.zendesk.com/hc/article_attachments/8404899129753/dd-1.jpg)

* On the performance page, adjust the performance calendar to check specific periods.
* Hover the mouse on histogram to see acquired members counts for new/existing members.
* Open the message preview to see the deeplink message.

![dd-2.jpg](https://crescendolab.zendesk.com/hc/article_attachments/8404899144601/dd-2.jpg)

#### ▶︎ Precautions

* When a new member's message is triggered the first time, it is free; existing member messages will be charged by LINE whether it is the first time or subsequent triggers.
* If you want to use the MAAC generated link in any campaign, copy and paste it directly into the channel you want to expose; the link will be invalid if mixed with other characters.
* Use one of the following methods to import CSV and prevent garbled or invalid data:
  * Method 1: Convert the file to UTF-8 format if you use Excel, then import the file into MAAC.
  * Method 2: Download the CSV template, import to Google Sheets first and fill in the form, then export to CSV and import into MAAC.
* When a user clicks a Deeplink on a mobile device, it will be counted as a valid click. Clicks on desktop that display a QR code will not be counted, to avoid duplicate tracking.

<details>

<summary>📊 How to Read Click Stats from Deeplinks</summary>

When analyzing traffic performance, keep in mind the difference between daily and multi-day stats:

* Daily users: Unique users who clicked the redirect link on a specific day. Useful for tracking daily engagement.
* Multi-day (period total) users: Unique users across the entire date range. A person is counted only once even if they visit multiple times.

Reminder:

* Do not add up daily user counts to calculate the total. This will overestimate due to repeat visits.
* Want total reach? Refer to multi-day total.
* Want to track daily performance? Use daily users.

</details>

<details>

<summary>❓ Why is the number of new friends via Deeplink in “Insights > Acquisition” different from the “Deeplink Report”?</summary>

Both “Insights > Acquisition” and the Deeplink Report can be used to evaluate how many contacts became friends through Deeplink, but they use different data sources and logic, which can cause discrepancies for the same date range.

Example:

* Insights > Acquisition shows: 9,997 users
* Deeplink Report shows: 8,125 users

Comparison:

| Source                                    | Data Logic                                                               | Update Frequency   | Note                                 |
| ----------------------------------------- | ------------------------------------------------------------------------ | ------------------ | ------------------------------------ |
| Insights > Acquisition (Deeplink section) | Based on member\_source in CDH, aggregated daily                         | Daily batch update | For trend observation                |
| Deeplink Report                           | Based on actual clicks and successful LINE friend additions via Deeplink | Near real-time     | Recommended as an accurate reference |

</details>

#### ▶︎ What message will friends receive when they join the OA through a deeplink?

* Scenario 1: New member A\
  New members (never joined the OA before) will receive a new member "Welcome message" from MAAC and the LINE OA platform (if both are set). The deeplink's "New member" message will also be sent if configured.
* Scenario 2: Existing member\
  Existing members will receive the "Existing member" message set up in the deeplink.
* Scenario 3: Blocked member

***

Related articles

* [Tutorials｜Customer Journey ✨ New ✨](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkQ8ocDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnloYgDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJEL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMTIyMDExMTMtVHV0b3JpYWxzLUN1c3RvbWVyLUpvdXJuZXktTmV3BjsIVDoJcmFua2kG--43264bb2d67ec41a69bd18c5dedaa8ae3ed74d45)
* [Tutorials｜ MAAC x SurveyCake Form](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkr5rYDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnloYgDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJGL2hjL2VuLXVzL2FydGljbGVzLzQ0MTM5OTk5NTA3NDUtVHV0b3JpYWxzLU1BQUMteC1TdXJ2ZXlDYWtlLUZvcm0GOwhUOglyYW5raQc%3D--de7a80ee5529633836b0bfb1a5ea8214045ec13c)
* [Tutorials｜MAAC Message Module & Template Library](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkb49oDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnloYgDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJUL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQ2MDM3Mjk2ODktVHV0b3JpYWxzLU1BQUMtTWVzc2FnZS1Nb2R1bGUtVGVtcGxhdGUtTGlicmFyeQY7CFQ6CXJhbmtpCA%3D%3D--275fac660e9d27393068329f0d90edc9b70ef333)
* [Tutorials｜Game Interaction](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBlM0QcdBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnloYgDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJAL2hjL2VuLXVzL2FydGljbGVzLzQ1MjI3MzE3MTk3MDUtVHV0b3JpYWxzLUdhbWUtSW50ZXJhY3Rpb24GOwhUOglyYW5raQk%3D--a0eb38fe2e5c04305353e7b5fb95b440d7601803)
* [How to share LINE OA platform, LINE Developers, GA(UA) / GA4 access to Crescendo Lab?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmp1FFgBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnloYgDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ1L2hjL2VuLXVzL2FydGljbGVzLzgxMTAyNzExNDYzOTMtSG93LXRvLXNoYXJlLUxJTkUtT0EtcGxhdGZvcm0tTElORS1EZXZlbG9wZXJzLUdBLVVBLUdBNC1hY2Nlc3MtdG8tQ3Jlc2NlbmRvLUxhYgY7CFQ6CXJhbmtpCg%3D%3D--ffa7870f57d40ebe6ae7e9a7cde1e5cef5bc7199)
