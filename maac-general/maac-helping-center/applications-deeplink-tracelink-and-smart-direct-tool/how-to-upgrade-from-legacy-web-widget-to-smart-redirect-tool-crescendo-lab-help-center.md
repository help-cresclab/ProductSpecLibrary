# How to Upgrade from Legacy Web Widget to Smart Redirect Tool – Crescendo Lab Help Center

To provide a better user experience, we recommend upgrading your legacy Web Widget to the new Smart Redirect Tool. Below are the complete upgrade steps.

{% stepper %}
{% step %}
### Step 1: Remove Legacy Web Widget

#### Identify Current Installation Method

First, check how your website currently has Web Widget 1.0 installed:

* Method 1: Direct HTML Code Embedding
  * Check the section of each webpage
  * Look for code similar to the following:

{% code title="Example legacy embed" %}
```html
<!-- Cresclab -->
<script src="//cdn.maac.app/widget/827965af0f814769b0d9266ea0877a65.js" async="async"></script>
```
{% endcode %}

* Check if Web Widget-related tags are configured in your GTM container

#### Completely Remove Legacy Settings

Based on your installation method, perform the corresponding removal steps:

* HTML Embedding: Completely remove the legacy Web Widget JavaScript code from your website's source code
* GTM Installation: Disable or delete all tags related to the legacy Web Widget in GTM

{% hint style="warning" %}
If you enable the new Smart Redirect Tool without completely removing the legacy code, your webpage may display two redirect tools simultaneously, affecting user experience.
{% endhint %}
{% endstep %}

{% step %}
### Step 2: Install New Web SDK

If you have already installed the Web SDK on your website, proceed directly to Step 3 and Step 4.

#### Obtain SDK Code

Please refer to: Software Development Kit (SDK) Installation Guide to get the latest Web SDK code and installation instructions

#### Deploy SDK to Website

Choose one of the following installation methods:

* Direct Embedding: Place the SDK code in your website's section
* Via GTM: Create a new custom HTML tag and embed the SDK code within it
{% endstep %}

{% step %}
### Step 3: Enable LINE Binding Module

In the SDK management dashboard:

* Navigate to the "Connected Websites" settings page
* Find the "Web Tools" section
* Enable the "LINE Binding Module (Identity Integration Tool)" feature

![LINE Binding Module screenshot](../../../.gitbook/assets/48048637921561)
{% endstep %}

{% step %}
### Step 4: Configure Smart Redirect Tool Parameters

After completing the SDK installation, configure the redirect links according to the documentation:

* Tutorials｜Smart Redirect Tool - Profile Unification Link\
  https://crescendolab.zendesk.com/hc/en-us/articles/47925134609305-Tutorials-Smart-Redirect-Tool-Profile-Unification-Link
{% endstep %}
{% endstepper %}

***

### Related Resources

#### 📚 Further Reading

* Feature Overview｜Smart Redirect Tool - Profile Unification Link\
  https://crescendolab.zendesk.com/hc/en-us/articles/47803073760537
* FAQs｜Smart Redirect Tool – Website Redirect and Identity Integration\
  https://crescendolab.zendesk.com/hc/en-us/articles/47925205689625

{% hint style="info" %}
Need Assistance?\
If you encounter any issues during the upgrade process, please contact our technical support team.
{% endhint %}

### Related articles

* Tutorial | SDK Web Behavior Tracking Tool\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJk0ii%2BuJToYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnb1iizKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJOL2hjL2VuLXVzL2FydGljbGVzLzQxNDMwMDUyMTIzODAxLVR1dG9yaWFsLVNESy1XZWItQmVoYXZpb3ItVHJhY2tpbmctVG9vbAY7CFQ6CXJhbmtpBg%3D%3D--20b832a731996c66018986dd4373e2c5bafa275b
* Tutorials｜Smart Redirect Tool - Profile Unification Link\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJnLn3CWKzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnb1iizKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJdL2hjL2VuLXVzL2FydGljbGVzLzQ3OTI1MTM0NjA5MzA1LVR1dG9yaWFscy1TbWFydC1SZWRpcmVjdC1Ub29sLVByb2ZpbGUtVW5pZmljYXRpb24tTGluawY7CFQ6CXJhbmtpBw%3D%3D--b79bdb51ebc37d706f871b1ffe6f92f85d87ae93
* Feature Overview｜Smart Redirect Tool - Profile Unification Link\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkNOwV6KzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnb1iizKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJkL2hjL2VuLXVzL2FydGljbGVzLzQ3ODAzMDczNzYwNTM3LUZlYXR1cmUtT3ZlcnZpZXctU21hcnQtUmVkaXJlY3QtVG9vbC1Qcm9maWxlLVVuaWZpY2F0aW9uLUxpbmsGOwhUOglyYW5raQg%3D--3196c9ce51853987fc984f974323a72b3131d859
* Tutorials | Deeplink\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJnloYgDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnb1iizKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI4L2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMjM3MjQ0NDEtVHV0b3JpYWxzLURlZXBsaW5rBjsIVDoJcmFua2kJ--0e7a866a2be1a1b3e92d9be1e2cc800f90b8824a
* FAQs｜Smart Redirect Tool – Website Redirect and Identity Integration\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBll3HSWKzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnb1iizKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJpL2hjL2VuLXVzL2FydGljbGVzLzQ3OTI1MjA1Njg5NjI1LUZBUXMtU21hcnQtUmVkaXJlY3QtVG9vbC1XZWJzaXRlLVJlZGlyZWN0LWFuZC1JZGVudGl0eS1JbnRlZ3JhdGlvbgY7CFQ6CXJhbmtpCg%3D%3D--c5291a00fc5f529eca1145f06f66112d1538cd10

***

If you would like any sections converted into separate pages, or want the SDK install code block pulled from the referenced SDK Installation Guide into this document (keeping the original links unchanged), tell me which parts to include.
