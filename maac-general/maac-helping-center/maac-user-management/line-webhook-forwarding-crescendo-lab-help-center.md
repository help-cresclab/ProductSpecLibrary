# LINE Webhook Forwarding – Crescendo Lab Help Center

### 💁‍♀️ Advance

* To integrate with multiple tools to fulfill the scenarios in LINE without worrying about the LINE webhook forward limitation!
* Utilize Webhook forwarding to seamlessly connect MAAC with various tools, enabling flexible use of LINE messages and webhook events.
* Set up to 10 forwarding sets, allowing your brand to integrate with more third-party applications and scenarios.

![](../../../.gitbook/assets/34581860331033)

### ⬇️ Setting introduction

{% stepper %}
{% step %}
### Ensure Webhook in LINE Developers is pointed to Crescendo Lab

Please ensure that the Webhook setting in your LINE Developers Messaging API Channel is connected to the MAAC backend by Crescendo Lab.\
Webhook URL should be: https://event.cresclab.com/api/webhook/line//events
{% endstep %}

{% step %}
### Open Webhook settings

![](../../../.gitbook/assets/34580519278105)
{% endstep %}

{% step %}
### Provide the Webhook URLs

Provide the Webhook URLs that will receive Webhook events to Crescendo Lab team.
{% endstep %}

{% step %}
### Crescendo Lab will assist

Crescendo Lab team will assist with the setup and inform you upon completion.
{% endstep %}

{% step %}
### Verify at your endpoint

Once the setup is successful, you can verify the relevant data at your specified Webhook receiving endpoint!
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
Please note that this feature is an add-on. If you wish to purchase it, please submit a request to Crescendo Lab team or contact them through the customer service button at the bottom right corner for procurement!

Also note that not all LINE Webhook URLs can be forwarded. Please confirm with the recipient vendor whether they can receive forwarded requests before proceeding.
{% endhint %}

📖 Review: [Why Are the Pre-set Auto-reply and Rich Menu Not Working?](https://crescendolab.zendesk.com/hc/en-us/articles/4413225066137-Why-Are-the-Pre-set-Auto-reply-and-Rich-Menu-Not-Working)

***

### ⬇️ Error notification Email

After Webhook forwards are set, if an error occurs during the process of receiving data, the Crescendo system will send a "system notification letter".

#### Notification Email Subject

\[System Notification] XXXX -- LINE Webhook Forward Failure Reminder

#### Notification Email Example

```
Dear Crescendo Lab Partner:
We have detected that the webhook forward failed.

Official account: Crescendo Lab
Error reason: 404 Not Found
Webhook endpoint URL:  https://example.com.tw/LineServer/index.html

Please check your integration service.Thanks!
```

<details>

<summary>Why did I receive a ‘LINE Webhook Forward Failure Reminder’ letter? What should I do after receiving the letter?</summary>

Crescendo Lab has detected that the brand's request for webhook forwarding of LINE related events to the specified endpoint failed.

Please help us to confirm the following:

* Please check with the relevant team/vendor whether the LINE Webhook Event is received properly.
* If you are no longer using the service of the relevant team/vendor, you can ask our Customer Success team to remove the LINE Webhook forwarding setting.

If you have any questions, please contact CS team! Thank you for your help!

</details>

<details>

<summary>Error Message</summary>

The error message Reason item is provided below. If you receive a system notification email, please check your Webhook endpoint URL Receiver/Receiver Manufacturer settings again.

* 403 Forbidden
* 400 Bad Request
* remote network error
* 404 Not Found
* 500 Internal Server Error
* 502 Bad Gateway
* 405 Method Not Allowed
* 530
* 401 Unauthorized

</details>

<details>

<summary>System notification frequency</summary>

* The Crescendo system will check every week to see if any errors have occurred.
* If an error is detected, a letter will be sent immediately to notify the brand.
* Brands notified within one hour will not be notified again.

</details>

***

### Related articles

* [Tutorials｜Webhook](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJnyT08EBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlukWdzHzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI3L2hjL2VuLXVzL2FydGljbGVzLzQ0MTY1NTcwMTk4MDEtVHV0b3JpYWxzLVdlYmhvb2sGOwhUOglyYW5raQY%3D--77c041b8adc38387cc7911c737007537be73f54f)
* [Why Are the Pre-set Auto-reply and Rich Menu Not Working?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJletogDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlukWdzHzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJeL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMjUwNjYxMzctV2h5LUFyZS10aGUtUHJlLXNldC1BdXRvLXJlcGx5LWFuZC1SaWNoLU1lbnUtTm90LVdvcmtpbmcGOwhUOglyYW5raQc%3D--ece464bb1dac5ba79d7e5fefee22b345496d4e19)
* [Tutorials｜ MAAC x SurveyCake Form](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkr5rYDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlukWdzHzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJGL2hjL2VuLXVzL2FydGljbGVzLzQ0MTM5OTk5NTA3NDUtVHV0b3JpYWxzLU1BQUMteC1TdXJ2ZXlDYWtlLUZvcm0GOwhUOglyYW5raQg%3D--3e8ea72ed0f2df7ab695caba499bc33dc6e9b311)
* [How to share LINE OA platform, LINE Developers, GA(UA) / GA4 access to Crescendo Lab?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmp1FFgBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlukWdzHzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ1L2hjL2VuLXVzL2FydGljbGVzLzgxMTAyNzExNDYzOTMtSG93LXRvLXNoYXJlLUxJTkUtT0EtcGxhdGZvcm0tTElORS1EZXZlbG9wZXJzLUdBLVVBLUdBNC1hY2Nlc3MtdG8tQ3Jlc2NlbmRvLUxhYgY7CFQ6CXJhbmtpCQ%3D%3D--4afb531f3d9dfb6cd8452a45cd107fc4fe5d137b)
* [How to use Helping Center](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJnfgqYYBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlukWdzHzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI%2FL2hjL2VuLXVzL2FydGljbGVzLzQ1MDM5MTkzMjA5ODUtSG93LXRvLXVzZS1IZWxwaW5nLUNlbnRlcgY7CFQ6CXJhbmtpCg%3D%3D--136bc6cfe0287bacf4b1935593a54fdb2e3a3d87)
