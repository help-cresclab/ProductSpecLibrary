# FAQs｜Smart Redirect Tool – Website Redirect and Identity Integration – Crescendo Lab Help Center

### Product Overview

The **Smart Redirect Tool** is a self-configurable web widget that helps brands redirect anonymous visitors to their LINE Official Account and complete identity integration. Through this tool, brands can effectively **convert website traffic into identifiable and interactive LINE contacts**, achieving data unification between their official website and social media channels.

When visitors click on the Smart Redirect Tool and complete identity binding, the system automatically integrates their LINE ID with website visit records (User Unification), further establishing a **complete Full-context Profile**. This enables brands to:

* Precisely execute remarketing campaigns and audience segmentation with tags
* Connect customer service journeys to improve service efficiency
* Enhance cross-channel personalized interactions and conversion performance

The Smart Redirect Tool serves as a key bridge connecting "website traffic" and "social media management," helping brands transform "anonymous visitors" into "familiar contacts" while comprehensively improving interaction depth and operational efficiency.

### ⚠️ Web Widget Sunset Notice - Upgrade Recommended

To ensure brands continue receiving optimal interaction benefits and technical support, **we plan to fully discontinue the legacy Web Widget service in Q4 2025**.

#### 📌 We recommend that you:

* Complete the Web SDK upgrade and implement the new Smart Redirect Tool as soon as possible
* Convert existing Web Widget settings to the Smart Redirect Tool
  * [How to Upgrade from Legacy Web Widget to Smart Redirect Tool](https://crescendolab.zendesk.com/hc/en-us/articles/48048484309785-How-to-Upgrade-from-Legacy-Web-Widget-to-Smart-Redirect-Tool)
* Avoid impacting redirect functionality and the accuracy and completeness of identity integration

***

<details>

<summary><strong>Q1: Will contacts complete identity integration just by joining the LINE Official Account?</strong></summary>

**A: No.**

Completing identity integration requires more than just joining the LINE Official Account. When contacts are redirected to LINE OA through the Smart Redirect Tool, the system will **automatically populate an identity integration message** in the chat input field.

Contacts **must actively send that message** for the system to successfully bind their website identity with their LINE identity.

If contacts only add as friends but do not send the message, integration cannot be completed.

![](../../../.gitbook/assets/48063211632409) ![](../../../.gitbook/assets/48063197710105)

</details>

<details>

<summary><strong>Q2: Why are two widget tools showing on my website?</strong></summary>

**A:** This usually occurs when both the old and new redirect tools are active. Please check the following:

Check if you have activated two Web WidgetsFor example, if both the legacy Web Widget 1.0 and the new Smart Redirect Tool (SRT) are enabled at the same time.Check if the old Web Widget code is still embedded on your websiteIf the old Web Widget 1.0 code remains on your website while the LINE Binding Module in the Admin Center is also enabled, both widgets may appear simultaneously.How to find the Admin center?MAAC Smart Redirect Tool > Install > Admin center > Channels > Web channel

Recommendation:

Please remove the old widget code or disable the legacy configuration to ensure only the Smart Redirect Tool is active, preventing duplicate widgets from affecting the user experience.

</details>

<details>

<summary><strong>Q3: How can I tell whether a redirect link is created by the Smart Redirect Tool or the legacy Web Widget?</strong></summary>

**A:** In the MAAC interface, you can identify the tool type by checking the “Link Type” field:

* If the link type is **Profile unification link**, it was created by the **Smart Redirect Tool**.
* If the link type is **Deeplink**, it was created by the **Web Widget** (legacy version).

![](../../../.gitbook/assets/48048071242905)

</details>

<details>

<summary><strong>Q4: After publishing the Smart Redirect Tool, can I still add the legacy Web Widget?</strong></summary>

**A: No.** After you install the new **Smart Redirect Tool** SDK code on your website:

* The MAAC backend only supports creating the **new Smart Redirect Tool (identity integration links)**
* The legacy Web Widget will no longer appear in the creation process and cannot be added
* If your website still has Web Widget code embedded, the legacy widget may still display temporarily in the short term, but support will gradually be discontinued

#### 📌 Important Notice: Web Widget planned for complete sunset in Q4 2025

* Legacy Web Widget functionality will be deprecated, including all existing redirect link settings and interaction styles will stop being supported
* We recommend completing the transition to the new Smart Redirect Tool as soon as possible to ensure stable functionality
* The system will continue providing report viewing functionality, but existing campaigns cannot be edited or reused

For upgrade instructions or assistance with implementing the new redirect process, please contact Crescendo Lab partners for support.

</details>

<details>

<summary><strong>Q5: Can I still edit legacy Web Widgets I've already created?</strong></summary>

**A:** Currently during the Smart Redirect Tool promotion period, legacy Web Widgets can still be edited, but after the Web Widget functionality is sunset, modifications will no longer be possible.

#### During the Promotion Period:

You can continue editing existing legacy redirect links (Web Widgets), such as updating redirect messages or adjusting display conditions.

#### After Web Widget Functionality Sunset (planned for complete sunset in Q4 2025):

* Existing **legacy Web Widget** redirect links will **no longer be editable**
* Redirect functionality will stop displaying on websites, with only **report query functionality** retained for brands to review historical data

**We recommend completing the upgrade to the new Smart Redirect Tool as soon as possible to ensure continuous redirect functionality and enjoy the new version's identity integration and performance tracking advantages.**

</details>

<details>

<summary><strong>Q6: After completing identity integration in MAAC through the Smart Redirect Tool, will it also sync to CAAC?</strong></summary>

**A: Yes.**

When brands enable the **CDH (Customer Data Hub) functionality**, the system automatically connects user data across MAAC, CAAC, and Web Chat, achieving **three-way identity integration** across products.

#### Practical Scenario Explanations

**Scenario 1: Completing Identity Integration During First Interaction**

* User A visits the brand website for the first time and **interacts with the brand through Web Chat**. The system identifies them as " **Anonymous Visitor A**"
* Next, A clicks the **Smart Redirect Tool** on the webpage and completes **LINE Official Account identity binding**
* At this point, A will be recorded as " **New Contact A**" in MAAC

Integration Results:

* Because the brand has enabled **CDH (Customer Data Hub) functionality**, the system automatically connects identities
* Anonymous Visitor A's Web Chat conversation records will automatically integrate with New Contact A in MAAC, forming complete cross-channel user data

This process ensures brands can complete social identity integration during the user's first interaction, facilitating consistent subsequent broadcasts and customer service.

**Scenario 2: Returning After Time Gap, Re-integrating Identity**

* After more than 30 days, User A visits the brand website again and **interacts with the brand through Web Chat**. The system will mark them as " **Anonymous Visitor B**"
* If A clicks the Smart Redirect Tool again and completes **LINE binding**, the system will recognize them as " **Existing Contact A**" in MAAC

![](../../../.gitbook/assets/48067858588569)

Integration Results:

* In **CAAC**, both "Anonymous Visitor A" and "Anonymous Visitor B" Web Chat conversation records will be retained
* However, both anonymous visitors' contact information will **integrate with the same Contact A in MAAC**, achieving cross-time, cross-identity continuity and identification

This process ensures:

* **Visitor journeys remain uninterrupted**, even across devices and time periods when using the website and LINE
* Customer service representatives in CAAC can access users' past MAAC interaction records and tag information when viewing conversations

![](../../../.gitbook/assets/48067854850329)

</details>

### Related Links

* For detailed feature descriptions, please refer to: [Feature Overview｜Smart Redirect Tool - Profile Unification Link](https://crescendolab.zendesk.com/hc/en-us/articles/47803073760537)
* For setup tutorials, please refer to: [Setup Tutorial | Smart Redirect Tool - Website Redirect and Identity Integration](https://crescendolab.zendesk.com/hc/en-us/articles/47925134609305-Tutorials-Smart-Redirect-Tool-Profile-Unification-Link)

### Related articles

* [Feature Overview｜Smart Redirect Tool - Profile Unification Link](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkNOwV6KzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBll3HSWKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJkL2hjL2VuLXVzL2FydGljbGVzLzQ3ODAzMDczNzYwNTM3LUZlYXR1cmUtT3ZlcnZpZXctU21hcnQtUmVkaXJlY3QtVG9vbC1Qcm9maWxlLVVuaWZpY2F0aW9uLUxpbmsGOwhUOglyYW5raQY%3D--bd90fdbead5313b8a28e6a81d6481a95e6148d28)
* [Tutorials｜Smart Redirect Tool - Profile Unification Link](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJnLn3CWKzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBll3HSWKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJdL2hjL2VuLXVzL2FydGljbGVzLzQ3OTI1MTM0NjA5MzA1LVR1dG9yaWFscy1TbWFydC1SZWRpcmVjdC1Ub29sLVByb2ZpbGUtVW5pZmljYXRpb24tTGluawY7CFQ6CXJhbmtpBw%3D%3D--69b1d7fac8c0eeebbd59ae0b84734709706ea3b5)
* [How to Upgrade from Legacy Web Widget to Smart Redirect Tool](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBnb1iizKzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBll3HSWKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJjL2hjL2VuLXVzL2FydGljbGVzLzQ4MDQ4NDg0MzA5Nzg1LUhvdy10by1VcGdyYWRlLWZyb20tTGVnYWN5LVdlYi1XaWRnZXQtdG8tU21hcnQtUmVkaXJlY3QtVG9vbAY7CFQ6CXJhbmtpCA%3D%3D--f9b3af64438c53706052e1a15bc6862be6129fa5)
* [Tutorials｜Retargeting](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJlJxx4LLDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBll3HSWKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI8L2hjL2VuLXVzL2FydGljbGVzLzQ4NDI2MjcyNjM5Mzg1LVR1dG9yaWFscy1SZXRhcmdldGluZwY7CFQ6CXJhbmtpCQ%3D%3D--fb23f5f6f4cacbbb98563a85423c4e52c3454f2a)
* [Feature Overview｜SMS+ API (Supports Event Tracking)](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkrw9wDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBll3HSWKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJWL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQ2MzUxOTExOTMtRmVhdHVyZS1PdmVydmlldy1TTVMtQVBJLVN1cHBvcnRzLUV2ZW50LVRyYWNraW5nBjsIVDoJcmFua2kK--eaca8a4882fadb7cbdc311cc24d2be12bec2f8f9)
