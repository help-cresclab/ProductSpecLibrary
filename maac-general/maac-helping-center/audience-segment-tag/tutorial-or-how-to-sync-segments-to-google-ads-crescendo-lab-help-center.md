# Tutorial | How to Sync Segments to Google Ads – Crescendo Lab Help Center

### Feature Introduction

MAAC has launched the "Segment with Ad Platforms" feature, solving three major pain points for marketers:

* Automated process, saving time: No more need to manually download and upload segment CSVs, significantly reducing the labor cost and time for cross-platform data processing.
* Automatic segment synchronization: The system performs daily scheduled updates, dynamically excluding converted users or updating high-potential audiences in real-time, ensuring the timeliness of ad targeting.
* Cross-platform integration: Supports one-click synchronization of data to Google Ads, easily achieving precise Re-marketing.

![](../../../.gitbook/assets/54480140728857)

***

#### Step 1: Preparation

Before using the segment sync feature, you must complete the ad account integration authorization in Admin Center.

If you haven't completed the integration, please read the following setup process first: [Tutorial | How to integrate Google Ads?](https://crescendolab.zendesk.com/hc/zh-tw/articles/54306264020505-%E6%95%99%E5%AD%B8-%E5%A6%82%E4%BD%95%E4%B8%B2%E6%8E%A5-Google-Ads)

#### Step 2: How to sync segments to ad platforms?

You have two ways to perform synchronization: set it up when creating a new segment, or sync existing segments.

Create a new segment and sync:

{% stepper %}
{% step %}
### Create Segment

Go to MAAC > Audience > Segment, and click "+ Create" in the top right corner.

![](../../../.gitbook/assets/54480441729049)

{% hint style="info" %}
Tip: You can use filters or the latest AI Segment feature to quickly create audiences using text descriptions (e.g., "Users who clicked but did not purchase in the past 30 days").
{% endhint %}
{% endstep %}

{% step %}
### Turn on sync, select ad account

After setting the segment conditions, enable the "Sync to Ad Platform" feature at the bottom of the segment settings. Then, select the ad platform and ad account you want to sync.

![](../../../.gitbook/assets/54480441731609)
{% endstep %}

{% step %}
### Complete creation

Click "Create". The system will start calculating the audience size and automatically upload the list to the designated ad platform.
{% endstep %}
{% endstepper %}

Sync existing segments:

{% stepper %}
{% step %}
### Select Segment

Find the target segment in the segment list.
{% endstep %}

{% step %}
### Turn on sync

Click "Edit", enable the "Sync to Ad Platform" feature and select the ad account on the settings page, then click "Update" to sync the existing segment list to the ad platform.
{% endstep %}
{% endstepper %}

#### Step 3: How to manage and view sync status?

After the feature launch, an ad platform status column has been added to the Segment List interface:

![](/broken/files/48e048be59bf3e44aad6dae799221601d238ce1b)

* Sync status lights: Please check the "Sync to Ad Platform" column in the list.
  * 🟢 Synced (Green light): Sync successful, the list has been updated to the ad backend.
  * 🔴 Failed (Red light): Sync failed (usually due to expired authorization or insufficient permissions; hover over the icon to see the error reason).
* View details: You can view the synced ad account name, ID, and last synced time.
* Auto-update mechanism: The system defaults to automatically recalculating the segment size at 4:00 AM local time daily, and syncing the updated list to the ad platform. If you manually edit the segment conditions, the system will also trigger an update immediately after the calculation is complete.
* Manual update: If you need to use the audience on the ad platform immediately, click the "..." menu on the right side of the segment list and select "Update" to manually trigger synchronization, pushing the latest list to the ad backend immediately.

![](../../../.gitbook/assets/54480599830937)

### Use Cases

After successfully setting up ad platform synchronization, you can try the following high-ROI marketing strategies:

* Exclude purchased users to save budget: Create a "Purchased in past 30 days" segment and sync it to the ad platform. When setting up ad audiences, set this list to "Exclude" to avoid repeatedly showing ads to people who just made a purchase.
* Wake up high-value dormant customers: Filter members in MAAC who have "no interaction for over 90 days" but "high historical spending (VIP)", and sync them to Meta or Google. Targeting this group with exclusive "repurchase offers" or "new product notifications" is more effective than casting a wide net.

### FAQ

<details>

<summary>Q: What does the red light (Failed) status in the segment list mean? How can I troubleshoot it?</summary>

A red light indicates that the segment failed to sync to the ad platform. Hover your mouse over the "warning" error icon (⚠️) to view the specific error message. You can troubleshoot using the following three common causes:

* Authentication failure or connection lost: Go to Admin Center > Applications to check the connection status of the corresponding platform (e.g., Google Ads). If the status is disconnected, please re-authorize the connection. Refer to: [Tutorial | How to integrate Google Ads?](https://crescendolab.zendesk.com/hc/zh-tw/articles/54306264020505-%E6%95%99%E5%AD%B8-%E5%A6%82%E4%BD%95%E4%B8%B2%E6%8E%A5-Google-Ads)
* Insufficient ad account permissions: The MAAC Service Account may have lost access permissions. Please check your ad platform settings and ensure the MAAC account has Standard access or higher.
* Empty Segment: If the segment criteria are too strict, resulting in a count of 0, the system will return a failure. Please adjust your criteria to ensure the list contains at least 1 valid contact.

If the above steps do not resolve the issue, please record the error message and contact the Crescendo Lab Support Team.

</details>

### Related articles

* [Tutorial｜How to Connect to Google Ads?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBl2kylkMToYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnPGJCHMToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJML2hjL2VuLXVzL2FydGljbGVzLzU0MzA2MjY0MDIwNTA1LVR1dG9yaWFsLUhvdy10by1Db25uZWN0LXRvLUdvb2dsZS1BZHMGOwhUOglyYW5raQY%3D--c6443237c64cd4de439a7549de18e1cbbe0bb890)
* [Before Sending EDMs: A Guide to IP Warming](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBlKY962MToYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnPGJCHMToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJQL2hjL2VuLXVzL2FydGljbGVzLzU0NjYxNDg0ODU3ODgxLUJlZm9yZS1TZW5kaW5nLUVETXMtQS1HdWlkZS10by1JUC1XYXJtaW5nBjsIVDoJcmFua2kH--166eaf0311cf3c80ca353ad79a4df7bd332f342e)
* [Tutorial | SDK Web Behavior Tracking Tool](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJk0ii%2BuJToYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnPGJCHMToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJOL2hjL2VuLXVzL2FydGljbGVzLzQxNDMwMDUyMTIzODAxLVR1dG9yaWFsLVNESy1XZWItQmVoYXZpb3ItVHJhY2tpbmctVG9vbAY7CFQ6CXJhbmtpCA%3D%3D--24147617f40d089004443672f97daf0f95d97724)
* [Onboarding Guide | How to Enable Email Channels and Import Contacts](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkOafO4MDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnPGJCHMToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJoL2hjL2VuLXVzL2FydGljbGVzLzUzNTcwOTE1ODY0MDg5LU9uYm9hcmRpbmctR3VpZGUtSG93LXRvLUVuYWJsZS1FbWFpbC1DaGFubmVscy1hbmQtSW1wb3J0LUNvbnRhY3RzBjsIVDoJcmFua2kJ--5842a4d9ce2ccc58cf5851aebaf5646aaaf8c079)
* [Feature Guide | Email Omnichannel Journeys & Editor Tutorial](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBnXvCW4MDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnPGJCHMToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJfL2hjL2VuLXVzL2FydGljbGVzLzUzNTY3NDY1MjQ4NTM3LUZlYXR1cmUtR3VpZGUtRW1haWwtT21uaWNoYW5uZWwtSm91cm5leXMtRWRpdG9yLVR1dG9yaWFsBjsIVDoJcmFua2kK--8ac3bc771a7db61b8e945851ebb92a354d898bf3)
