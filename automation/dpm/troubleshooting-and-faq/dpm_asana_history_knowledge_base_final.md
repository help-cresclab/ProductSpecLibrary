# dpm\_asana\_history\_knowledge\_base\_final

## Why Are Uploaded Product Feeds Not Displaying in DPM?

**Metadata**

* **Feature:** MAAC-DPM
* **Created At:** 2026-01-27
* **Asana Task ID:** [1212990129456272](https://app.asana.com/1/1184020052539844/task/1212990129456272)
* **Ticket Priority:** P2
* **Client Name:** TelemedicineSCH
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The product feed was successfully uploaded via the Admin Center, but the uploaded files did not appear in the list when creating DPM. The user attempted logging out and refreshing several times without success.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 4956
  * Issue reproducibility: Not specified
* **User Actions:**
  * Uploaded product feed via Admin Center
  * Attempted to view uploaded files in DPM
  * Logged out and refreshed the page multiple times
* **Expected vs Actual Behavior:**
  * **Expected:** Uploaded product feed should appear in the DPM list.
  * **Actual:** Uploaded files are not visible in the DPM list.
* **Attachments:**
  * [Screenshot 1](https://app.asana.com/app/asana/-/get_asset?asset_id=1213001687353297)
  * [Screenshot 2](https://app.asana.com/app/asana/-/get_asset?asset_id=1213001687353298)

### 3. Root Cause & Solution

* **Root Cause:** The MAAC system lacks a deletion mechanism, causing deleted feeds to still appear in the DPM.
* **Solution:** Feeds were re-synced, and a deletion sync feature has been added to the product backlog for future implementation.

***

## How to Enable Comma Separation in DPM Price Display

**Metadata**

* **Feature:** MAAC-DPM
* **Created At:** 2026-01-22
* **Asana Task ID:** [1212908659038893](https://app.asana.com/1/1184020052539844/task/1212908659038893)
* **Ticket Priority:** P3
* **Client Name:** TelemedicineSCH
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

Clients observed that the price in the product feed file is set with commas for digit separation, but the DPM card does not display these commas. They requested the ability to enable comma separation for better readability.

### 2. Context & Details

* **Environment:**
  * Channel Types: LINE, Web, WhatsApp, EDM, Facebook, Instagram
  * Affected contact ID: \[REDACTED\_ID]
* **Reproduction Steps:**
  * Set a price with commas in the product feed file.
  * Observe the price display on the DPM card.
* **Expected vs Actual Behavior:**
  * **Expected:** The DPM card should display the price with commas as set in the product feed.
  * **Actual:** The DPM card does not display commas, affecting readability.

### 3. Root Cause & Solution

* **Root Cause:** The absence of comma separation in the DPM card is due to the current system design and product specifications. This behavior is expected and not a result of a bug or data error.
* **Solution:** No immediate fix is required as the system is functioning as designed. A product enhancement request will be submitted to consider adding comma separators or other formatting options to improve price readability in the DPM display.

***

## Investigation of Product Recommendation Message for Discontinued Items

**Metadata**

* **Feature:** MAAC-DPM
* **Created At:** 2025-12-26
* **Asana Task ID:** [1212595175811570](https://app.asana.com/1/1184020052539844/task/1212595175811570)
* **Ticket Priority:** P3
* **Client Name:** 美津濃
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The unexpected situation involved the delivery of product recommendation messages for items that had already been discontinued. Specifically, messages were sent for the following products:

* Women's Long Sleeve Polo Shirt
* GATE SKY PLUS 4 Badminton Shoes

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 5809
  * MAAC bot ID: 4702
  * LINE UID: \[REDACTED\_ID] / \[REDACTED\_PHONE]
* **Reproduction Steps:**
  * The issue was reported when the client noticed that discontinued products were still being included in recommendation messages.
* **Expected vs Actual Behavior:**
  * **Expected:** Discontinued products should not appear in recommendation messages.
  * **Actual:** Discontinued products were included in the messages sent to customers.

### 3. Root Cause & Solution

* **Root Cause:**
  * The root cause was identified as an error in the customer's product feed. The feed incorrectly listed the products as 'in stock'. MAAC's Dynamic Product Message (DPM) logic functions correctly by excluding products marked 'out of stock' from the feed during message preparation and sending. The system operated as designed based on the provided data.
* **Solution:**
  * The customer has updated their product feed with the correct inventory statuses. It is crucial to ensure that customers understand the direct correlation between their uploaded product feed data, particularly the 'availability' status, and the products delivered via MAAC DPMs. The issue is now resolved.

***

## How to Display Decimals in DPM Card Messages

**Metadata**

* **Feature:** MAAC-DPM
* **Created At:** 2025-10-20
* **Asana Task ID:** [1211692480064245](https://app.asana.com/1/1184020052539844/task/1211692480064245)
* **Ticket Priority:** P2
* **Client Name:** Buymed
* **Resolution Owner:** Tracy
* **Result Breakdown:** Product Optimization

### 1. Issue Description

The DPM card messages were displaying prices as integers, rounding down the values, despite the product feed containing prices with two decimal places. For example, a price of $76.52 in the product feed was displayed as $76 in the card message.

### 2. Context & Details

* **Environment Conditions:**
  * The issue was observed in the DPM system.
  * The product feed from the client included prices with two decimal places.
* **Reproduction Steps:**
  1. Upload a product feed containing prices with decimals to the DPM system.
  2. Observe the card message displaying the price.
* **Expected vs Actual Behavior:**
  * **Expected:** Prices should display with two decimal places if present in the product feed.
  * **Actual:** Prices were rounded down and displayed as integers.

### 3. Root Cause & Solution

* **Root Cause:** The DPM system was originally designed to display prices as integers, which was the expected behavior according to the previous code configuration.
* **Solution:** The DPM system has been updated to display prices with up to two decimal places if they are present in the source product feed. If the price is an integer, it will display as such. This update has been released to production, and all Customer Success Managers will be notified of this specification change.

***

## Investigation of Delayed Message Broadcast in IKEA's Campaign

**Metadata**

* **Feature:** MAAC-DPM
* **Created At:** 2025-07-18
* **Asana Task ID:** [1210828414791514](https://app.asana.com/1/1184020052539844/task/1210828414791514)
* **Ticket Priority:** P2
* **Client Name:** IKEA
* **Resolution Owner:** TY
* **Result Breakdown:** Fix Problems

### 1. Issue Description

On 2025-07-17, IKEA's DPM\_4334 broadcast campaign for product recommendations was stuck in a "preparing" status and failed to send messages. The product recommendation list for this campaign was not successfully generated. The "Prepare Task" completed, and "Misterioso" was triggered, but "Rubato" did not receive a callback, resulting in broadcast failure. This issue is intermittent.

### 2. Context & Details

* **Environment:**
  * Region: TW
  * Date and Time: 2025-07-17 20:45:01
* **User Questions:**
  * Delays in message receipt during high traffic periods were reported.
* **Reproduction Steps:**
  * The issue occurred during the execution of a long-running task for product recommendations.
* **Expected vs Actual Behavior:**
  * Expected: Timely broadcast of product recommendations.
  * Actual: Broadcast was delayed and not completed.

### 3. Root Cause & Solution

* **Root Cause:**
  * The product recommendation list for DPM\_4334 was not successfully generated due to an Out-Of-Memory (OOM) event and subsequent service restart. This likely occurred when the DPM long-running task for product recommendations and an API server's gender calculation request ran concurrently, exceeding current memory limits. The failure of "Misterioso" to call back "Rubato" is a consequence of this system instability.
* **Solution:**
  * Immediate incident resolution involved restarting the affected services and monitoring memory usage to prevent concurrent tasks from exceeding memory limits. Further investigation and optimization of memory allocation for long-running tasks are recommended to prevent recurrence.
