# Feature Overview｜Retargeting – Crescendo Lab Help Center

Retargeting allows brands to re-engage contacts who have added items to their shopping cart on the website but did not complete the checkout within a predefined time frame. This feature is designed to increase conversion rates and overall e-commerce revenue.

Below is a feature overview. For setup instructions, please refer to： [Tutorials｜Retargeting](https://crescendolab.zendesk.com/hc/en-us/articles/48426272639385)

#### 🙋 Who Should Use Retargeting?

* **E-commerce Platforms**: To boost conversion rates.
* **Custom Websites**: For multi-channel marketing.
* **Marketers**: To drive effective campaigns with actionable insights.

MAAC's retargeting supports three flexible data integration modes, enabling brands to select the best-suited triggering mechanism based on their technical readiness and marketing needs. Each method has its own trade-offs between data freshness and message trigger speed:

{% stepper %}
{% step %}
### GA4 + SDK Hybrid Mode

* Integrates both GA4 and the Web SDK.
* SDK captures real-time user behavior to compensate for GA4 latency.
* Suitable for brands needing both historical analytics and real-time engagement, such as during major promotions.
* For SDK setup, refer to: [SDK installation instructions](https://crescendolab.zendesk.com/hc/en-us/articles/41430052123801)
{% endstep %}

{% step %}
### SDK-only Mode

* Relies solely on the Web SDK to track user actions (e.g., cart adds) on the website.
* Enables message triggering within \~1 hour.
* Ideal for conversion-driven or time-sensitive campaigns.
{% endstep %}

{% step %}
### GA4-only Mode

* Utilizes cart event data collected via Google Analytics 4 (GA4).
* Best for brands that do not require real-time triggering, as GA4 data updates every 48–72 hours.
* In GA4-only mode, retargeting can only be triggered for users redirected via LINE click.
* For GA4 setup and permissions, refer to: [How to share GA4 access and Product feed with Crescendo Lab to enable EC plan?](https://crescendolab.zendesk.com/hc/en-us/articles/22490379797273)
{% endstep %}
{% endstepper %}

| Mode      | Method                                                                                                                                 | Data Latency                   | Dynamic Card Support | Best Use Case                                       | Setup Reference                                                                                    |
| --------- | -------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------ | -------------------- | --------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| SDK Only  | Only relies on Web SDK to detect user behavior in real-time for quick retargeting triggers, but performance reports are not available. | \~1 hr                         | Yes                  | Real-time campaigns, flash sales                    | [SDK installation instructions](https://crescendolab.zendesk.com/hc/en-us/articles/41430052123801) |
| GA4 + SDK | Hybrid of GA4 + SDK                                                                                                                    | SDK: \~1 hr / GA4: \~48–72 hrs | Yes                  | Real-time & historical analytics (e.g., promotions) | [SDK installation instructions](https://crescendolab.zendesk.com/hc/en-us/articles/41430052123801) |
| GA4 Only  | Cart events via GA4                                                                                                                    | \~48–72 hrs                    | Yes                  | History-based push, low urgency                     | [How to share GA4 access](https://crescendolab.zendesk.com/hc/en-us/articles/22490379797273)       |

⚠️ Note: Cart Retargeting Trigger Logic

* When using both GA4 and SDK, the system prioritizes SDK data for triggering retargeting. Even if GA4 event data is available, it will not trigger the retargeting message.
* If using GA4 + SDK mode or SDK-only mode and the SDK code is not properly installed on the website, retargeting messages cannot be triggered.
* If using GA4-only mode but the required product data (Product Feed) is not uploaded in the correct format, messages cannot be generated or sent.

#### ✨ Feature Highlights

* Personalized & Dynamic Messages
  * The system automatically pulls product names, prices, and images from the user's cart into visually engaging Dynamic Card messages to improve click-through and conversion rates.
  * Dynamic Messages Example: ![](../../../.gitbook/assets/48741432629785)
* Automated Product Sync
  * MAAC's Retargeting integrates with major e-commerce platforms via Product Feed. It ensures real-time updates of product details, eliminating the need for manual updates.
  * ⚠️ This feature requires a properly formatted Product Feed. Brands must provide updated data to the Crescendo Lab team for integration.
* Multi-Channel Triggers via Identity Unification (Only supported in SDK + GA4 mode and SDK-only mode)
  * By enabling the Identity Unification feature of the Smart Redirect Tool, the system can bind anonymous website visitors to their corresponding LINE UID. This enables cross-channel retargeting triggers based solely on website activity.
  * Once the binding is complete, users no longer need to enter the website via a LINE OA link. Simply browsing or interacting on the site is sufficient to trigger cart retargeting messages.
  * For more details, refer to: [Feature Overview｜Smart Redirect Tool - Profile Unification Link](https://crescendolab.zendesk.com/hc/en-us/articles/47803073760537)
* Performance Dashboard & Insights
  * Dashboards include click-through and conversion rates, order breakdowns and revenue attribution, and campaign effectiveness. These insights allow marketers to continuously optimize retargeting strategies.

#### Common Retargeting Use Cases

| Use Case                            | Description                                                                   |
| ----------------------------------- | ----------------------------------------------------------------------------- |
| Abandoned Cart Reminder             | Automatically remind users who added items to the cart but did not check out. |
| Product Recommendations / Upselling | Suggest related products based on previous behavior.                          |
| Flash Sale Reminder                 | Push limited-time discounts to accelerate purchases.                          |
| Product View Without Purchase       | Engage users who viewed products but didn’t add to cart.                      |

#### Data Requirements & Limitations

1. Product Data Fields

Dynamic Cards require the following fields from the product page or product feed:

* `link` (URL to the product page)
* `image_link` (Image URL for card display)

2. Product Feed Format

Required for SDK and dynamic templates. Feed must include:

* Unique product ID (e.g., SKU)
* Name, price, link, image link

Reference: 《 [How to share GA4 access and Product feed with Crescendo Lab to enable EC plan?](https://crescendolab.zendesk.com/hc/en-us/articles/22490379797273)》

⚠️ Note:

If the system cannot detect essential product data (e.g., SDK fails to capture data or the Product Feed is incomplete), it will activate an automatic fallback mechanism to prevent abnormal card displays.

The fallback mechanism is as follows:

* If a product lacks an “image” or “product link,” that product card will not be displayed.
* If all products in the user’s cart are missing either “image” or “product link,” the entire retargeting message will not be sent.
* If a product is missing the “price,” the card will display “Check the price” as a fallback.

This mechanism ensures the message content remains well-presented even when some data is missing, without requiring manual intervention.

3. Identity Binding Conditions

If the Identity Unification feature of the Smart Redirect Tool is enabled, anonymous visitor actions can be logged and associated with a LINE UID upon binding.

> Without the Smart Redirect Tool, retargeting is limited to users who arrived via a LINE OA click.

#### Frequently Asked Questions (FAQ)

<details>

<summary>Q1. Retargeting messages have been created, but no retargeting messages are being sent.</summary>

Please check first:

* Is your brand using SDK or GA4 settings?
* Only one method can trigger retargeting messages at a time.

When Admin Center > Web Channel > Web Tracking is enabled (SDK activated), the system will prioritize SDK data as the retargeting trigger source.

Even if there is event data in GA4, retargeting messages will not be triggered.

</details>

<details>

<summary>Q2. SDK setup is completed, but no retargeting messages are being sent.</summary>

Possible reasons:

* Web Tracking is not enabled in Admin Center > Web Channel.
* The SDK code is not correctly installed on the website, or the placement is incorrect.
* Required product information fields (e.g., product\_id, price, image) are missing on product pages.

Solutions:

* Go to Admin Center > Web Channel and confirm Web Tracking is enabled.
* Confirm with the website administrator that the SDK code is correctly installed on all pages or via GTM.
* Ensure product pages contain all required product information fields.

</details>

<details>

<summary>Q3. GA4 is set up, but messages are delayed or not triggered.</summary>

Possible reasons:

* GA4 access has not been shared with Crescendo Lab.
* The Product Feed file has not been provided or is incorrectly formatted.
* GA4 data has a normal delay of 48–72 hours before triggering retargeting messages.

Solutions:

* Confirm GA4 access is shared with Crescendo Lab’s designated account.
* Make sure the Product Feed file follows MAAC format requirements and has been successfully uploaded.
* Wait 48–72 hours after setup, then check message performance and report data.

</details>

<details>

<summary>Q4. Can I manually disconnect the Web Channel?</summary>

Not recommended. Doing so disables SDK features and reverts messages to static templates, losing real-time event tracking.

</details>

<details>

<summary>Q5. How can I properly disable SDK-based retargeting?</summary>

Go to: Admin Center > Tool Settings > Web Footprint Tracking and turn it off. This disables SDK tracking while keeping Web Channel connected.

Access path: Retargeting >Setting > Website Behavior Tracking > Setting > Channel Settings > Connected Websites > Web Tools > Web Footprint Tracking

![](../../../.gitbook/assets/48492224310937)

</details>

<details>

<summary>Q6. Can SDK and GA4 be configured simultaneously?</summary>

Yes, both can be configured, but retargeting will prioritize SDK events as the main trigger source. Please ensure the SDK is correctly installed and configured to guarantee proper message delivery.

Important notes:

* This applies to both scenarios: users who add products to the cart via LINE click and users who add products directly on the website.
* For website cart actions, the user must first complete SRT identity unification so the system can recognize the LINE UID and trigger messages correctly.
* In GA4-only mode, retargeting can only be triggered for users redirected via LINE click.

</details>

#### 📘 Terminology Glossary

| Term                     | Definition                                                                                                |
| ------------------------ | --------------------------------------------------------------------------------------------------------- |
| Admin Center             | Manages MAAC & CAAC settings including SDK status and channel configuration.                              |
| Dynamic Card Message     | Auto-generated message with product visuals and info based on the user's cart. (SDK only, up to 10 items) |
| GA4 (Google Analytics 4) | Google's tracking tool for site and cart activity; 48–72 hour data delay.                                 |
| LINE UID                 | Unique identifier for a LINE user. Used for message targeting in MAAC.                                    |
| Product Feed             | Structured product data used to generate Dynamic Cards. Must include name, price, image link, and URL.    |
| ROAS                     | Return on Ad Spend; measures revenue-to-cost ratio of campaigns.                                          |
| UTM Parameters           | Tracking tags (e.g., utm\_source) to attribute traffic and behavior.                                      |
| Web Channel Status       | Shows SDK connection status: Connected/Disconnected. Needed for real-time/dynamic features.               |
| Web SDK                  | JavaScript code embedded on the website to detect user behavior and sync with MAAC.                       |
| Retargeting              | Marketing to users who abandoned their carts, aiming to increase conversion and repeat sales.             |

Related articles

* [Tutorial | SDK Web Behavior Tracking Tool](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJk0ii%2BuJToYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJlhmbH9JToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJOL2hjL2VuLXVzL2FydGljbGVzLzQxNDMwMDUyMTIzODAxLVR1dG9yaWFsLVNESy1XZWItQmVoYXZpb3ItVHJhY2tpbmctVG9vbAY7CFQ6CXJhbmtpBg%3D%3D--78e2e5a58c842d2193b2b93694bd955268511bf8)
* [Tutorials｜ MAAC x SurveyCake Form](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkr5rYDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJlhmbH9JToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJGL2hjL2VuLXVzL2FydGljbGVzLzQ0MTM5OTk5NTA3NDUtVHV0b3JpYWxzLU1BQUMteC1TdXJ2ZXlDYWtlLUZvcm0GOwhUOglyYW5raQc%3D--9e9456141f5e6ad0033d7dfb9e0c976530065b23)
* [Tutorials｜Rapid Referral](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkzBMgDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJlhmbH9JToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI%2BL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQyODcxMzE0MTctVHV0b3JpYWxzLVJhcGlkLVJlZmVycmFsBjsIVDoJcmFua2kI--8d32a0a39d3bc88515ffc182ccb61dde56e130b0)
* [Tutorials｜Game Interaction](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBlM0QcdBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJlhmbH9JToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJAL2hjL2VuLXVzL2FydGljbGVzLzQ1MjI3MzE3MTk3MDUtVHV0b3JpYWxzLUdhbWUtSW50ZXJhY3Rpb24GOwhUOglyYW5raQk%3D--e2c9b3fabf3740c7689aa43a31b818ebc8747118)
* [Feature Overview｜SMS+ API (Supports Event Tracking)](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkrw9wDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJlhmbH9JToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJWL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQ2MzUxOTExOTMtRmVhdHVyZS1PdmVydmlldy1TTVMtQVBJLVN1cHBvcnRzLUV2ZW50LVRyYWNraW5nBjsIVDoJcmFua2kK--019b21d3e806b1c6e7655983542106cff02775dc)
