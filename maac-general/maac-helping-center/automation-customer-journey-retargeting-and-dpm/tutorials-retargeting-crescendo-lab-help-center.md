# Tutorials｜Retargeting – Crescendo Lab Help Center

Retargeting can be configured using different data source modes. Please ensure your brand has completed the required integrations and prerequisites before following the setup steps below.

For feature details, please refer to: https://crescendolab.zendesk.com/hc/en-us/articles/41771536572825

{% stepper %}
{% step %}
### Step 1: Prerequisite Checks — GA4-only Mode

* MAAC e-commerce feature is enabled, and GA4 integration is complete. For GA4 setup and permissions, refer to: https://crescendolab.zendesk.com/hc/en-us/articles/22490379797273
* GA4 must include cart-related event data:
  * Go to GA4 Admin → Lifecycle → Monetization → E-commerce Purchases → Click “Shopping Behavior”, and verify that the “Adds-to-Carts” event shows numbers, and each product has corresponding data.
  * Image: https://crescendolab.zendesk.com/hc/article\_attachments/48426794329881
* Retargeting campaigns must use MAAC tracking links with UTM parameters, or use MAAC’s audience segment tool with UTM settings applied.

{% hint style="warning" %}
Only mobile-originated traffic can be linked back to LINE UID; desktop clicks cannot be tracked. UTM must include utm\_term.\
Example UTM: https://www.cresclab.com/utm\_campaign=tracelink\_xxxx\&utm\_source=line\&utm\_medium=message\&utm\_term=lm%3A5
{% endhint %}
{% endstep %}

{% step %}
### Step 1: Prerequisite Checks — GA4 + SDK Mode

* In addition to GA4 requirements, Web SDK must be installed.
* Setup instructions: SDK installation instructions
{% endstep %}

{% step %}
### Step 1: Prerequisite Checks — SDK-only Mode

* Retargeting is based solely on Web SDK user behavior tracking.
* To disable SDK tracking while keeping Web Channel connected:\
  Go to Admin Center > Tool Settings > Web Footprint Tracking and turn it off.

Access path: Retargeting > Setting > Website Behavior Tracking > Setting > Channel Settings > Connected Websites > Web Tools > Web Footprint Tracking
{% endstep %}
{% endstepper %}

### Step 2: Configure Retargeting

Go to: MAAC > Automation > Retargeting > Settings.\
Image: https://crescendolab.zendesk.com/hc/article\_attachments/48494263202329

#### Define Trigger Conditions

* Set a delay time for when the reminder is sent after the cart event (e.g., 4 hours).\
  Recommendation for GA4 mode: set a delay of over 24 hours (ideally 36 hours) to avoid delivery issues due to data latency.
* Additional settings you can configure:
  * Do-not-disturb Interval: Prevent duplicate sends within a set number of days.
  * Sleep Hours: Avoid sending during night hours.

### Step 3: Create Retargeting Message

Go to: MAAC > Automation > Retargeting > Create\
Image: https://crescendolab.zendesk.com/hc/article\_attachments/48494293381785

{% stepper %}
{% step %}
#### Message contents

* Use the “Unpaid Items” Dynamic Message Template, which automatically pulls up to 10 product entries (image, name, price).

{% hint style="warning" %}
Each retargeting message can include only one dynamic cart module.
{% endhint %}
{% endstep %}

{% step %}
#### Set UTM tracking

* Ensure all redirect links include UTM parameters to enable performance tracking.
* Dynamic Message will auto-map to corresponding product URLs from the Product Feed.
{% endstep %}

{% step %}
#### Save & Schedule

* You may save the message as a draft and return to edit it later.
* Set a scheduled send time. The system will deliver the message automatically at the chosen time.\
  Image: https://crescendolab.zendesk.com/hc/article\_attachments/48494263207577
{% endstep %}
{% endstepper %}

### Performance Reports

You can access performance metrics for all Cart Retargeting messages via the MAAC backend dashboard. Use the reporting tools to evaluate each campaign and refine your strategies.

Key performance metrics include: Delivery count, Open rate, Click rate, Order count, Revenue. Click the report icon to view product-level click details and card previews. Use the export function to download performance data for specific periods.

#### Data Sources

* GA4
  * Data comes from UTM-marked traffic reported to Google Analytics 4.
  * 24–72 hour data latency. Best for historical analysis.
  * May differ from SDK data.\
    Image: https://crescendolab.zendesk.com/hc/article\_attachments/48494293383577
* SDK
  * Data is reported in real-time (usually < 1 hour).
  * Tracks:
    * Number of interactions (e.g., clicks, cart adds)
    * Number of unique users who triggered interactions
  * Best for real-time campaign monitoring and dynamic message tracking.\
    Image: https://crescendolab.zendesk.com/hc/article\_attachments/48494293385881
* GA4 + SDK
  * The system provides tabs to switch between GA4 and SDK metrics within the report dashboard.
  * We recommend using both to cross-validate data and optimize campaigns.

#### Data Comparison Summary

| Data Source | Technology Used           | Data Latency    | Dynamic Message Support |
| ----------- | ------------------------- | --------------- | ----------------------- |
| GA4         | UTM tagging & GA4 backend | 24–72 hours     | Yes                     |
| SDK         | Embedded tracking script  | Real-time (<1h) | Yes                     |

Note: GA4 and SDK use different data collection methods. Metrics may vary. Choose the appropriate mode based on your retargeting goals.

### Related articles

* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBlDGXN0FDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJlJxx4LLDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJDL2hjL2VuLXVzL2FydGljbGVzLzQxNzcxNTM2NTcyODI1LUZlYXR1cmUtT3ZlcnZpZXctUmV0YXJnZXRpbmcGOwhUOglyYW5raQY%3D--fb27857cea2f103486a4e0f8221f8e7dac655804
* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBlDGXN0FDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJlJxx4LLDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ0L2hjL2VuLXVzL2FydGljbGVzLzIyNDkwMzc5Nzk3MjczLUhvdy10by1zaGFyZS1HQTQtYWNjZXNzLWFuZC1Qcm9kdWN0LWZlZWQtd2l0aC1DcmVzY2VuZG8tTGFiLXRvLWVuYWJsZS1FQy1wbGFuBjsIVDoJcmFua2kH--a0e92250c7dacfe172ab779ef66c8c78e8b115ef
* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJk0ii%2BuJToYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJlJxx4LLDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJOL2hjL2VuLXVzL2FydGljbGVzLzQxNDMwMDUyMTIzODAxLVR1dG9yaWFsLVNESy1XZWItQmVoYXZpb3ItVHJhY2tpbmctVG9vbAY7CFQ6CXJhbmtpCA%3D%3D--c6b42bfa7134a6fbf0f2a9f5c9ccbb50bf86f09a
* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkQ8ocDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJlJxx4LLDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJEL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMTIyMDExMTMtVHV0b3JpYWxzLUN1c3RvbWVyLUpvdXJuZXktTmV3BjsIVDoJcmFua2kJ--4799212be7674f30d18f546987152d3781dc285a
* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkNOwV6KzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJlJxx4LLDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJkL2hjL2VuLXVzL2FydGljbGVzLzQ3ODAzMDczNzYwNTM3LUZlYXR1cmUtT3ZlcnZpZXctU21hcnQtUmVkaXJlY3QtVG9vbC1Qcm9maWxlLVVuaWZpY2F0aW9uLUxpbmsGOwhUOglyYW5raQo%3D--0d6d879dc2ec1dde7ada4cefcacf0af10b51edd1
