# retargeting\_asana\_history\_knowledge\_base\_final

## Investigation of Cart Retargeting Message Delivery Failure

**Metadata**

* **Feature:** MAAC-Retargeting
* **Created At:** 2026-01-26
* **Asana Task ID:** [1212970282944318](https://app.asana.com/1/1184020052539844/task/1212970282944318)
* **Ticket Priority:** P3
* **Client Name:** 博士倫
* **Resolution Owner:** Tracy, YH
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported not receiving cart retargeting messages. The add-to-cart event was recorded on 1/23 at 12:10, but the expected follow-up message was not triggered.

### 2. Context & Details

* **Environment:**
  * Channel Type: LINE
  * MAAC org id: 1596
  * MAAC bot/channel id: 1307
  * Affected contact id: \[REDACTED\_ID]
* **User Actions:**
  * Item added to cart on 1/23 at 12:10.
* **Reproduction Steps:**
  * Check SDK event logs for add-to-cart actions.
  * Verify product ID "BIO-047530PK" in the product feed.
* **Expected vs Actual Behavior:**
  * Expected: Cart retargeting message should be sent after add-to-cart event.
  * Actual: No message was received by the client.
* **Additional Information:**
  * Product feeds available at:
    * \[Product Feed 1]\(https://platform.cresclab.com/applications/product-feeds/\[REDACTED\_PATH]
    * \[Product Feed 2]\(https://platform.cresclab.com/applications/product-feeds/\[REDACTED\_PATH]

### 3. Root Cause & Solution

* **Root Cause:**
  * The product ID in the SDK event did not match the product feed. Additionally, the SDK event lacked essential "image\_link" and "link" data. The system operated as designed due to these data discrepancies.
* **Solution:**
  * **Customer Actions:** Ensure the SDK "product\_id" aligns with the product feed and include "image\_link" and "link" in SDK events.
  * **Product Team:** Add to backlog the development of a UI feature for verifying event receipt.
  * **Engineering Team:** Add to backlog the enhancement of the SDK to automatically capture image and link data.
* **Status:** Actionable (Customer integration update needed; backlogs created)

***

## Investigation of Retargeting Event Trigger Failure

**Metadata**

* **Feature:** MAAC-Retargeting
* **Created At:** 2026-01-12
* **Asana Task ID:** [1212733573655785](https://app.asana.com/1/1184020052539844/task/1212733573655785)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client configured retargeting but no events were triggered. The admin center shows successful integration, and page view events are received in Metabase. However, the "add to cart" event is not being received. Guidance is needed on how to adjust the SDK settings.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org id: 6394
  * MAAC bot/channel ID: 6468
* **User Questions:**
  * How to adjust SDK settings to ensure event triggering?
* **Reproduction Steps:**
  * Configuration of retargeting in the admin center.
  * Verification of event reception in Metabase.
* **Expected vs Actual Behavior:**
  * Expected: "Add to cart" events should be received in Metabase.
  * Actual: "Add to cart" events are not being received.

### 3. Root Cause & Solution

* **Root Cause:**
  * The tracking code (SDK or GA4-formatted data layer events) has not been correctly implemented by the customer. The platform requires properly formatted GA4 data layer events.
* **Solution:**
  * The customer's IT team must verify and correctly implement the tracking code to ensure GA4 e-commerce events are pushed to the data layer. Awaiting verification from the customer's IT team.

***

## Investigation of Cart Re-Engagement Trigger Failure

**Metadata**

* **Feature:** MAAC-Retargeting
* **Created At:** 2025-12-30
* **Asana Task ID:** [1212613584339567](https://app.asana.com/1/1184020052539844/task/1212613584339567)
* **Ticket Priority:** P3
* **Client Name:** 博士倫
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported that the cart re-engagement messages were not triggered as expected.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 1596
  * MAAC bot/channel ID: 1307
* **User Actions:**
  * The client attempted to trigger cart re-engagement using SDK version 2.0.
  * A test was conducted where items were added to the cart at 14:52, but no re-engagement message was received by 18:58.
* **Reproduction Steps:**
  1. Add items to the cart using the SDK.
  2. Wait for the cart re-engagement message.
* **Expected vs Actual Behavior:**
  * **Expected:** Cart re-engagement messages should be sent after items are added to the cart.
  * **Actual:** No messages were sent.

### 3. Root Cause & Solution

* **Root Cause:**
  * The product IDs in the SDK `add_to_cart` events were inconsistent with those in the product feeds, preventing proper correlation.
  * Missing `image_link` and `link` fields in SDK events, along with products not present in the feeds, also contributed to the issue.
* **Solution:**
  * Product Management (PM) will add UI prompts to guide clients in uploading or updating product feeds.
  * The engineering team will evaluate the optimization of the e-commerce data layer to improve SDK data collection.
  * Clients are advised to ensure consistency in product IDs across all platforms.

***

## Investigation of Cart Retargeting Trigger Failure

**Metadata**

* **Feature:** MAAC-Retargeting
* **Created At:** 2025-11-26
* **Asana Task ID:** [1212151114663202](https://app.asana.com/1/1184020052539844/task/1212151114663202)
* **Ticket Priority:** P2
* **Client Name:** Kanebo
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The cart retargeting feature did not trigger as expected, with the trigger count reported as zero during the specified operational period.

### 2. Context & Details

* **Environment Conditions:**
  * GA4 integration is functioning correctly.
  * SDK is not integrated; reliance is on GA4 events.
* **Operational Period:**
  * October 28, 2025, 15:30 to November 3, 2025, 23:29.
* **User Observations:**
  * Retargeting push notifications included cart data.
* **Reproduction Steps:**
  * Enable "Website Tracking" in Admin Center.
  * Attempt to trigger cart retargeting without SDK installation.
* **Expected vs Actual Behavior:**
  * Expected: Cart retargeting triggers based on GA4 events.
  * Actual: No triggers occurred due to missing SDK events.

### 3. Root Cause & Solution

**Root Cause:** The root cause was identified as a system design issue where the "Website Tracking" feature was enabled, designating the SDK as the trigger source. However, the SDK was not installed, preventing the platform from receiving necessary events.

**Solution:**

* The customer should either correctly install the SDK or disable "Website Tracking" if the SDK is not intended for use.
* It is recommended that the Product/Engineering team implement enhanced UI guidance or a warning mechanism. For instance, a message should indicate that if the SDK tracking code is not embedded but "Website Tracking" is enabled, the feature may not trigger.

***

## Investigation of Missing Abandoned Cart Retargeting Events

**Metadata**

* **Feature:** MAAC-Retargeting
* **Created At:** 2025-11-26
* **Asana Task ID:** [1212148501035856](https://app.asana.com/1/1184020052539844/task/1212148501035856)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Jalex
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The customer reported that there were no data or messages triggered for abandoned cart retargeting.

### 2. Context & Details

* **Environment Conditions:**
  * SDK has been updated and the web tracking module is enabled.
  * Admin center integration appears normal.
  * Metabase shows mapping for UID and add\_to\_cart events.
  * The retargeting page displays "Tracked by GA4," which is unexpected.
* **User Questions:**
  * Why are there no retargeting messages being sent?
* **Reproduction Steps:**
  * Update and install the SDK.
  * Enable the web tracking module.
  * Verify integration in the admin center.
  * Check event mapping in Metabase.
* **Expected vs Actual Behavior:**
  * **Expected:** Abandoned cart events should trigger retargeting messages.
  * **Actual:** No messages are being sent despite the setup.

### 3. Root Cause & Solution

* **Root Cause:**
  * The add\_to\_cart events sent via the Web SDK were missing critical product\_link and product\_image\_link information. Additionally, the MAAC product feed lacked corresponding product IDs to complete the data. Without these necessary product details, the retargeting logic was unable to process the cart event and send messages.
* **Solution:**
  * The client needs to correct their Web SDK implementation for add\_to\_cart events to include product\_link and product\_image\_link for each item. This will ensure that the retargeting logic can process the events and send the appropriate messages.

***

## Investigation of Retargeting Trigger Failure Without SDK Usage

**Metadata**

* **Feature:** MAAC-Retargeting
* **Created At:** 2025-11-21
* **Asana Task ID:** [1212010637368974](https://app.asana.com/1/1184020052539844/task/1212010637368974)
* **Ticket Priority:** P3
* **Client Name:** PORTER INTERNATIONAL
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported that retargeting campaigns on their website are being triggered through Google Analytics instead of the MAAC SDK, despite the system checks indicating proper integration.

### 2. Context & Details

* **Environment Conditions:**
  * SDK integration is complete and connections are normal.
  * Website tracking is enabled.
  * The shopping cart content does not require a product feed as it is not checkout-related.
  * Django backend checks are active and functioning.
* **Reproduction Steps:**
  * Navigate to the retargeting page.
  * Observe the triggering mechanism for retargeting campaigns.
* **Expected vs Actual Behavior:**
  * **Expected:** Retargeting campaigns should trigger via the MAAC SDK.
  * **Actual:** Campaigns are triggered via Google Analytics.
* **Additional Information:**
  * MAAC org ID: 3461
  * MAAC bot ID: 3652
  * Feature ID: Cart Retargeting ID: 3238

### 3. Root Cause & Solution

* **Root Cause:** The add-to-cart event sent from the client's website via the MAAC SDK is missing required data fields: `product_link` (items.link) and `product_image_link` (items.image\_link). These fields are essential for the MAAC cart retargeting mechanism to function correctly.
* **Solution:** This issue is due to a client-side SDK integration gap, not a product bug. The client's development team needs to update their SDK implementation to ensure that `product_link` and `product_image_link` are included in the add-to-cart event. The issue is resolved by identifying this gap, and the client is expected to update their implementation accordingly.

***

## Investigation of Low Data Transmission in Cart Retargeting

**Metadata**

* **Feature:** MAAC-Retargeting
* **Created At:** 2025-11-13
* **Asana Task ID:** [1211931864921428](https://app.asana.com/1/1184020052539844/task/1211931864921428)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** N/A
* **Result Breakdown:** Fix Problems

### 1. Issue Description

During the promotional period from November 1 to November 12, the cart retargeting feature sent only 37 messages. Previously, over a three-day promotional period, more than 80 messages were sent. Despite a downturn in e-commerce performance this year, the decrease should not be this significant. Persistent issues with cart data necessitated a review by the product and engineering teams.

### 2. Context & Details

* **Environment:** The issue occurred during the Double 11 promotional period.
* **User Questions:** Why was there a significant drop in the number of messages sent after SDK integration?
* **Reproduction Steps:**
  * Compare message counts before and after SDK integration.
  * Analyze message sending patterns during similar promotional periods.
* **Expected vs Actual Behavior:**
  * **Expected:** Message count should be consistent with previous promotional periods, adjusted for current e-commerce performance.
  * **Actual:** Message count was approximately one-fifth of the expected number.

### 3. Root Cause & Solution

* **Root Cause:** A backend data retrieval logic error, specifically incorrect date range partitioning, led to some data being excluded, resulting in underestimated reporting.
* **Solution:** The data processing logic for calculating sent messages was corrected. A migration was performed for all clients to update the reported sent message count to the accurate figure (91 messages for this case). No further action is required for this specific data discrepancy.

***

## Verification of Retargeting Logic in Delayed Data Ingestion Scenarios

**Metadata**

* **Feature:** MAAC-Retargeting
* **Created At:** 2025-11-11
* **Asana Task ID:** [1211907397205677](https://app.asana.com/1/1184020052539844/task/1211907397205677)
* **Ticket Priority:** P2
* **Client Name:** MCJeans
* **Resolution Owner:** Jalex
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

Clarification is requested regarding the timing of retargeting message triggers when GA4 data ingestion experiences delays. Specifically, the concern is whether the retargeting logic uses the original event timestamp from GA4 or the system's data ingestion timestamp.

### 2. Context & Details

* **Environment Conditions:**
  * Retargeting is set up to be triggered by GA4 only, without using an SDK.
  * A 24-hour wait time is configured for retargeting.
  * A customer adds an item to the cart at 12 PM.
  * Data ingestion by CL occurs with a 5-hour delay.
* **User Questions:**
  * When will the customer receive the retargeting message given the data ingestion delay?
* **Reproduction Steps:**
  1. Set up retargeting to be triggered by GA4.
  2. Configure a 24-hour wait time.
  3. Simulate a customer adding an item to the cart at a specific time.
  4. Introduce a delay in data ingestion.
* **Expected vs Actual Behavior:**
  * **Expected:** The retargeting message should be triggered based on the original event timestamp.
  * **Actual:** Confirmation needed on whether the system uses the original event timestamp or the ingestion timestamp.

### 3. Root Cause & Solution

* **Root Cause:** There is confusion regarding whether the retargeting system uses the original GA event timestamp or the system's data ingestion timestamp for triggering messages.
* **Solution:** The system correctly uses the original contact event timestamp from GA4 for retargeting triggers, irrespective of data ingestion delays. No changes to the system are necessary. It is recommended to conduct internal knowledge sharing sessions for Customer Success Managers (CSMs) to ensure clarity on this functionality.

***

## Investigation of Anomalies in Cart Retargeting Data

**Metadata**

* **Feature:** MAAC-Retargeting
* **Created At:** 2025-11-10
* **Asana Task ID:** [1211897774167545](https://app.asana.com/1/1184020052539844/task/1211897774167545)
* **Ticket Priority:** P2
* **Client Name:** One Boy
* **Resolution Owner:** Aaren, Jalex
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The client observed anomalies in cart retargeting data during the Double 11 sales period. Despite receiving retargeting notifications, the dashboard's send data significantly differed from the number of broadcast messages sent during this period.

### 2. Context & Details

* **Environment:**
  * MAAC org ID: 4555
  * MAAC bot ID: 3652
* **User Actions:**
  * Broadcast messages sent from 11/6 to 11/10.
  * Cart retargeting 2.0 enabled using image card message templates.
* **Reproduction Steps:**
  * Compare data from 7/15-7/22 with 11/6-11/10.
  * July data used "open in external browser" for cart messages; November did not.
* **Expected vs Actual Behavior:**
  * Expected: Retargeting send counts should align with broadcast numbers.
  * Actual: Significant discrepancy in retargeting trigger counts (only 30+ times).

### 3. Root Cause & Solution

* **Root Cause:**
  * System Design: MAAC report query date aggregation mismatch between UTC+8 (WHERE) and UTC+0 (GROUP BY) led to data misaggregation.
  * Bug: Client's SDK misconfigured, failing to send transaction/revenue events since 2025/10/16.
* **Solution:**
  * Fixed MAAC retargeting report logic and migrated historical data for all clients.
  * Customer Success to guide the client in correcting SDK configuration to ensure transaction/revenue events are sent.

***

## Investigation of Cart Retargeting Trigger Failure in Product Feed

**Metadata**

* **Feature:** MAAC-Retargeting
* **Created At:** 2025-10-28
* **Asana Task ID:** [1211765809261366](https://app.asana.com/1/1184020052539844/task/1211765809261366)
* **Ticket Priority:** P2
* **Client Name:** One Boy
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The Product Feed file was successfully uploaded, but the cart retargeting message module for "Unpurchased Items" failed to trigger for LINE friends.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 4555
  * MAAC bot ID: 3652
  * Feature ID: Cart Retargeting ID: 3213
* **User Questions:**
  * The client inquired about IP whitelisting for their Product Feed URL.
* **Reproduction Steps:**
  * Attempt to trigger cart retargeting messages using the "Unpurchased Items" module.
* **Expected vs Actual Behavior:**
  * Expected: Messages should trigger for LINE friends.
  * Actual: No messages were triggered.

### 3. Root Cause & Solution

* **Root Cause:**
  * For clients using the Web SDK, dynamic product feed re-engagement requires users to complete identity binding via the Smart Redirect Tool (SRT). Without SRT, the system cannot link website activity to a specific LINE user to populate dynamic product data, even if SDK events are received.
* **Solution:**
  * The client must enable and properly implement SRT for identity binding to allow dynamic product feed messages to trigger. It is recommended to review documentation and UI prompts for SDK-based dynamic content to clearly state SRT requirements.

***

## Investigation of Blurry Product Images in Cart Retargeting Messages

**Metadata**

* **Feature:** MAAC-Retargeting
* **Created At:** 2025-10-08
* **Asana Task ID:** [1211584676786043](https://app.asana.com/1/1184020052539844/task/1211584676786043)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** JY, Noel
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The unexpected situation involves consumers seeing blurry product images in cart retargeting messages.

### 2. Context & Details

* **Client Information:**
  * MAAC org ID / CAAC org ID: 4894
  * MAAC bot / CAAC channel ID: 3904
* **Feature Information:**
  * The issue has occurred previously.
  * Reproduction: Similar issues have been reported.
  * Reference Task: [Link](https://app.asana.com/1/1184020052539844/project/1201173638593204/task/1210596667924046?focus=true)
* **Attachments:**
  * [Screenshot/Screen Record](https://app.asana.com/app/asana/-/get_asset?asset_id=1211584676786055)

### 3. Root Cause & Solution

* **Root Cause:**
  * The system captures low-resolution product images directly from checkout pages during add-to-cart events. These images are used without quality validation or fallback to the Product Feed, which is the current design expectation.
* **Solution:**
  * Proposed enhancement includes implementing resolution checks for event payload images. If images are low-resolution, the system should fallback to the Product Feed to retrieve higher quality images. This enhancement is under review for prioritization by the Product and Engineering teams.

***

## Investigation of Data Discrepancy Between SDK and GA4 in Retargeting Reports

**Metadata**

* **Feature:** MAAC-Retargeting
* **Created At:** 2025-09-30
* **Asana Task ID:** [1211504611161164](https://app.asana.com/1/1184020052539844/task/1211504611161164)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Noel
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The client activated SDK web tracking on 2025/08/12. They observed discrepancies in retargeting report data between SDK and GA4 for the period 2025/08/14 to 2025/09/30. Specifically, the SDK showed zero attributions while GA4 displayed data.

### 2. Context & Details

* **Environment:**
  * SDK and GA4 are used concurrently by the client.
  * The issue was noted in the retargeting report for the specified period.
* **User Questions:**
  * Why is there a discrepancy between SDK and GA4 data?
* **Reproduction Steps:**
  * Review the retargeting report for the specified period.
  * Compare SDK and GA4 data outputs.
* **Expected vs Actual Behavior:**
  * Expected: Consistent data between SDK and GA4.
  * Actual: SDK shows zero attributions; GA4 shows data.

### 3. Root Cause & Solution

* **Root Cause:**
  * A dataLayer plugin update around 10/22 caused the SDK to incorrectly process or fail to receive purchase events, leading to zero attribution. The MAAC UI also failed to differentiate between an actual zero value and no data.
* **Solution:**
  * A fix for the dataLayer plugin was deployed.
  * Monitor SDK attribution data post-deployment.
  * Enhance MAAC UI to distinguish "no data" from an actual "zero value".
  * Educate the client on MAAC/GA4 attribution differences.

***

## Investigation of Cart Retargeting Trigger Failure

**Metadata**

* **Feature:** MAAC-Retargeting
* **Created At:** 2025-09-05
* **Asana Task ID:** [1211254887927848](https://app.asana.com/1/1184020052539844/task/1211254887927848)
* **Ticket Priority:** P2
* **Client Name:** GNC
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The cart retargeting message was not triggered as expected for a user who logged in and added items to the cart on the website.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org id / CAAC org id: 5943
  * MAAC bot / CAAC channel ID: 4858
  * Happened time: 2025/09/04
  * Reproducibility: No
* **Event Timeline:**
  * 2025/09/01: Cart retargeting setup completed.
  * 2025/09/02: Internal GNC personnel accessed the website and logged in as a member (non-anonymous).
  * 2025/09/03: Reported that cart retargeting was not triggered. Conditions for triggering were communicated (user must be logged in and items must remain in the cart for 48 hours).
  * 2025/09/04: Reported again before end of day that retargeting was still not triggered.
  * 2025/09/05: Customer Success Manager checked and confirmed the issue persisted.
* **Reproduction Steps:**
  * User logs in to the website.
  * User adds items to the cart.
  * Wait for 48 hours to see if retargeting message is triggered.
* **Expected vs Actual Behavior:**
  * **Expected:** Retargeting message should be triggered after 48 hours if conditions are met.
  * **Actual:** No retargeting message was triggered.

### 3. Root Cause & Solution

* **Root Cause:** The client initially used GA4 for tracking. GA4-based cart retargeting requires users to enter the website via a LINE link for proper tracking and user identification. The user accessed the website directly, bypassing the necessary LINE-linked entry point.
* **Solution:** The client was advised to install the SDK for website tracking. After the SDK installation was completed on 2025/09/16, the issue was resolved, and no further reports of untriggered cart retargeting have occurred. No additional product or engineering action is required at this time.

***

## Investigation of Missing "Add to Cart" and "Purchase" Events in SDK Implementation

**Metadata**

* **Feature:** MAAC-Retargeting
* **Created At:** 2025-08-11
* **Asana Task ID:** [1211019487637979](https://app.asana.com/1/1184020052539844/task/1211019487637979)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Noel
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The system did not receive "addtocart" and "purchase" events from the client's website, only "pageview" events, despite the client having embedded the SDK and configured event names to standard formats on their live site.

### 2. Context & Details

* The client implemented the SDK the previous week.
* Initial checks using Metabase showed only "pageview" events were received.
* The client's development team confirmed the SDK was correctly embedded.
* Google Analytics on the client's side showed receipt of cart data.
* The client requested assistance to verify if there were any implementation errors preventing the receipt of "addtocart" and "purchase" events.
* Web Channel domains:
  * Production: https://shopping.gamania.com
  * Development: https://dev-www.shopping.gamania.com

### 3. Root Cause & Solution

**Root Cause:** The client's dataLayer format includes an additional "ecommerce" layer, which prevents our system from recognizing and processing the "addtocart" and "purchase" event data, even though the event names themselves are standard. Our system expects a different dataLayer structure.

**Solution and Suggested Actions:** The client's dataLayer format needs to be adjusted to align with the structure our system is configured to receive. The client's engineering team reported challenges in making this change due to impacts on their architecture. Internally, modifying our system to support the client's current dataLayer format has been identified as technically feasible but would require custom development.
