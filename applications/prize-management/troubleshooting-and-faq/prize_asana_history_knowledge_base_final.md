# prize\_asana\_history\_knowledge\_base\_final

## How to Resolve Inconsistent File Size Limit Display in Prize Management

**Metadata**

* **Feature:** MAAC-Prize management
* **Created At:** 2026-01-16
* **Asana Task ID:** [1212835062606954](https://app.asana.com/1/1184020052539844/task/1212835062606954)
* **Ticket Priority:** P4
* **Client Name:** N/A
* **Resolution Owner:** N/A
* **Result Breakdown:** N/A

### 1. Issue Description

The file size limit description for image settings in the Prize Management section displays inconsistently across different languages. The limit should be uniformly set to 1MB, but some languages incorrectly show a 20MB limit.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC > Prize Management > Coupon Style > Card Message > Image settings
* **User Questions:**
  * Why is the file size limit displayed differently in various languages?
* **Reproduction Steps:**
  * Navigate to the Prize Management section.
  * Check the file size limit description in different language settings.
* **Expected vs Actual Behavior:**
  * **Expected:** All languages should display a file size limit of 1MB.
  * **Actual:**
    * ZH (Chinese): Displays < 1MB (Correct)
    * EN (English): Displays < 1MB (Correct)
    * TH (Thai): Displays < 20MB (Incorrect)
    * JP (Japanese): Displays < 20MB (Incorrect)

### 3. Root Cause & Solution

* **Root Cause:** The issue was due to an outdated or missing translation entry for specific UI text strings in the Thai and Japanese language settings.
* **Solution:** The incorrect translations were identified and updated with the correct copy. The fix has been deployed to production. It is recommended to review and enhance localization processes for new or modified UI texts to prevent similar issues in the future.

***

## Investigation of Prize Management Editing Issue

**Metadata**

* **Feature:** MAAC-Prize management
* **Created At:** 2026-01-16
* **Asana Task ID:** [1212834391682490](https://app.asana.com/1/1184020052539844/task/1212834391682490)
* **Ticket Priority:** P1 - Very High
* **Client Name:** N/A
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Fix Problems

### 1. Issue Description

Customers reported an issue where unexpired prizes could not be edited due to the absence of the edit icon in the user interface.

### 2. Context & Details

* **Environment Conditions:**
  * Occurred on January 16.
  * Affected MAAC organization ID: 5722.
  * Affected MAAC bot/channel ID: 4619.
* **User Questions:**
  * Why is the edit icon missing for unexpired prizes?
* **Reproduction Steps:**
  * Attempt to edit unexpired prizes in the prize management interface.
  * Observe the absence of the edit icon.
* **Expected vs Actual Behavior:**
  * **Expected:** The edit icon should be present and functional for unexpired prizes.
  * **Actual:** The edit icon is missing, preventing edits.

### 3. Root Cause & Solution

* **Root Cause:** A recent code deployment introduced a regression that caused the edit functionality/icon for unexpired prizes to disappear.
* **Solution:** The edit functionality/icon has been restored and deployed to the production environment.

***

## Investigation of "Limit Reached" Message and Prize Non-receipt in MAAC Lottery Poetry

**Metadata**

* **Feature:** MAAC-Prize management
* **Created At:** 2026-01-09
* **Asana Task ID:** [1212713603195744](https://app.asana.com/1/1184020052539844/task/1212713603195744)
* **Ticket Priority:** P2
* **Client Name:** ホテラバ
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

A user reported encountering a "Limit reached" message and was unable to complete the Lottery poetry flow or receive a prize. The user pressed the "Receive" button multiple times, but the process did not complete and returned to the same screen, suggesting the game may have been played without successfully granting a prize.

### 2. Context & Details

* **Environment:**
  * MAAC org ID: 80
  * MAAC bot ID: 79
  * Feature ID: l8qO3Dq7
* **User Actions:**
  * User pressed the "Receive" button multiple times.
* **Reproduction Steps:**
  * Issue could not be reproduced on Android devices.
* **Expected vs Actual Behavior:**
  * Expected: User receives a prize upon completing the game.
  * Actual: User did not receive a prize, and the system displayed a "Limit reached" message.
* **Prize Report Check:**
  * Affected UID: \[REDACTED]
  * No prize records found for the user in the 2026年☆ホテラバおみくじ campaign.

### 3. Root Cause & Solution

* **Root Cause:**
  * System Design: Game logs confirm the user did not win a prize, likely due to insufficient or depleted prizes in the campaign. The current UI lacks clear communication regarding the "no prize" status, leading to user confusion.
* **Solution:**
  * No system action is required for the affected user as logs confirm "no prize" status.
  * The product team is enhancing the UI to clearly display "unowned prize" information, scheduled for release this month, to prevent similar confusion in the future.

***

## Why Did the System Trigger a Low Stock Alert for Prize ID 38798?

**Metadata**

* **Feature:** MAAC-Prize management
* **Created At:** 2026-01-05
* **Asana Task ID:** [1212652484063147](https://app.asana.com/1/1184020052539844/task/1212652484063147)
* **Ticket Priority:** P2
* **Client Name:** iPair
* **Resolution Owner:** Aaren
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client received a low stock alert for prize ID 38798, despite the current inventory being greater than 200 units.

### 2. Context & Details

* **Environment Conditions:**
  * Prize ID: 38798
  * Prize Name: New Year Luck Slot - Universal Badge
  * Inventory threshold set for alerts: below 100 units
  * Current inventory displayed: greater than 200 units
* **User Questions:**
  * Why was a low stock alert triggered when inventory is above the threshold?
* **Reproduction Steps:**
  1. Set a low stock alert threshold for prize inventory below 100 units.
  2. Monitor inventory levels for prize ID 38798.
  3. Observe alert triggered despite inventory being above 200 units.
* **Expected vs Actual Behavior:**
  * **Expected:** No alert should be triggered as inventory is above the threshold.
  * **Actual:** Alert was triggered, causing confusion for the client.

### 3. Root Cause & Solution

* **Root Cause:**
  * The alert system is designed to trigger based on the quantity of PrizeStatus.UNOWNED (unassigned) prizes falling below the threshold of 100. For prize ID 38798, the UNOWNED quantity was 0, which correctly triggered the alert. The client was confused because the MAAC UI only displays the count of "received" prizes, not the unassigned ones.
* **Solution:**
  * The system functioned as intended; there is no bug. The client indeed has zero UNOWNED prizes, which is why the alert was triggered. It is advised to replenish the inventory. Additionally, a UI enhancement is suggested to display both UNOWNED and OWNED counts to improve clarity for users.

***

## Investigation of Incorrect Localization in Prize Status Label

**Metadata**

* **Feature:** MAAC-Prize management
* **Created At:** 2025-12-24
* **Asana Task ID:** [1212577017707300](https://app.asana.com/1/1184020052539844/task/1212577017707300)
* **Ticket Priority:** P4
* **Client Name:** IHG
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The label in the prize report displayed incorrectly in the Thai Language UI. The expected label in English is "Claimed," which should be translated to "เก็บแล้ว" in Thai. However, the current Thai UI uses "ผู้ติดต่อ," meaning "Contact."

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 5938
  * MAAC bot/CAAC channel ID: 4796
* **Reproduction Steps:**
  * Access the prize report in the Thai Language UI.
  * Observe the label for claimed prizes.
* **Expected vs Actual Behavior:**
  * **Expected:** The label should read "เก็บแล้ว" (claimed) in Thai.
  * **Actual:** The label reads "ผู้ติดต่อ" (contact) instead.
* **Additional Information:**
  * The issue can be reproduced consistently.
  * Relevant screenshots and screen records are available:
    * [Screenshot 1](https://app.asana.com/app/asana/-/get_asset?asset_id=1212577017707313)
    * [Screenshot 2](https://app.asana.com/app/asana/-/get_asset?asset_id=1212577017707315)

### 3. Root Cause & Solution

* **Root Cause:** An incorrect localization string was present in the product's Thai language files for the "claim" action related to prizes.
* **Solution:** The incorrect Thai translation has been updated to "เก็บแล้ว" (claimed). No further action is required at this time. The issue is now resolved.

***

## Investigation of Repeated Prize Redemption in JCB Event

**Metadata**

* **Feature:** MAAC-Prize management
* **Created At:** 2025-11-26
* **Asana Task ID:** [1212148507497017](https://app.asana.com/1/1184020052539844/task/1212148507497017)
* **Ticket Priority:** P2
* **Client Name:** JCB
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

JCB conducted a credit card receipt lottery event where users could upload their JCB credit card receipts to enter a draw. The prizes were set in the backend as LINE POINTS of 50 and 10 points. Within a few minutes, a large number of prizes were claimed, indicating an issue with repeated prize redemption.

### 2. Context & Details

* **Event Start:** Large number of prize claims began on 11/17.
* **User Process:**
  1. Open LIFF interface.
  2. Enter form details and upload receipt image.
  3. Backend recognition.
  4. Backend confirmation allows submission.
  5. User submits.
  6. Backend conducts draw and distributes prizes.
* **System Records:** Multiple UIDs showed prize claims without corresponding receipt records.
  * **50 Points UIDs:** \[REDACTED]
  * **10 Points UIDs:** \[REDACTED]
* **Previous Mechanism:** Initially used a message template with a roulette system, which was changed after the LIFF link was shared, allowing unauthorized users to participate and claim prizes.
* **Push API Details:**
  * URL: `https://api.cresclab.com/openapi/v1/direct_message/push/`
  * Header: `Authorization: Bearer {CRESCLAB_API_KEY}`
  * Body: `template_id` for message template ID, varies weekly.

### 3. Root Cause & Solution

**Root Cause:** The client's system logic incorrectly assessed prize eligibility and API call frequency, resulting in repeated API calls to MAAC's message sending service for individual users. MAAC processed these requests as received.

**Solution:** The issue is within the client's internal system. The client needs to revise their prize distribution logic to prevent duplicate API calls. No changes are required on the MAAC side.

**Status:** Investigation concluded. Awaiting client's internal action.

***

## Investigation of Unresponsive Redemption Voucher Click in MAAC-Prize Management

**Metadata**

* **Feature:** MAAC-Prize management
* **Created At:** 2025-10-02
* **Asana Task ID:** [1211530080882418](https://app.asana.com/1/1184020052539844/task/1211530080882418)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

An end-user reported an unresponsive page when attempting to click a redemption voucher for LINE Points in the MAAC capsule machine. The page remained static, leading to a customer complaint.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC Organization ID: 1793
  * MAAC Bot ID: 1453
  * Occurrence Date: 10/2
  * UUID: \[REDACTED\_UUID]
  * Screenshot provided: [Link to asset](https://app.asana.com/app/asana/-/get_asset?asset_id=1211530080882432)
* **User Questions:**
  * The user questioned why the voucher click resulted in no response.
* **Reproduction Steps:**
  * The issue could not be reproduced by the Customer Success Manager (CSM). Attempts to redeem were successful on their end.
* **Expected vs Actual Behavior:**
  * **Expected:** Clicking the voucher should lead to a successful redemption process.
  * **Actual:** The page remained unresponsive, and the user was unable to proceed with the redemption.

### 3. Root Cause & Solution

* **Root Cause:**
  * The root cause remains undetermined as the issue could not be reproduced by the CSM. The specific reason for the redemption failure is unknown due to the lack of user-side data.
* **Solution:**
  * A direct redemption link was provided as a temporary workaround.
  * Further investigation requires a complete screen recording from the end-user to identify the issue.
  * It is noted that the "claimed" status in MAAC does not confirm successful redemption of LINE Points.

Investigation is currently paused, pending resolution through the workaround or additional evidence from the customer.

***

## Investigation of Prize Stock Alert Notifications Despite High Inventory Levels

**Metadata**

* **Feature:** MAAC-Prize management
* **Created At:** 2025-09-10
* **Asana Task ID:** [1211310614292818](https://app.asana.com/1/1184020052539844/task/1211310614292818)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Yio
* **Result Breakdown:** Fix Problems

### 1. Issue Description

Customers received notifications indicating that prize stock levels were low or at zero immediately after creating prize settings and uploading prizes. This occurred despite the MAAC UI displaying a high quantity of prizes available and none being claimed.

### 2. Context & Details

* **Environment:** The issue was reported by Cosmed and another brand, iPair.
* **Reproduction Steps:**
  * Prize settings were created and a large quantity of prizes was uploaded.
  * Notifications of low or zero stock were received shortly after.
* **Expected Behavior:** Notifications should only be sent when the prize stock is genuinely low or depleted.
* **Actual Behavior:** Notifications were sent erroneously, indicating low or zero stock despite high inventory levels.

### 3. Root Cause & Solution

* **Root Cause:** The system's prize stock check job was running too frequently in relation to the asynchronous prize import process. While prize settings are created instantly, individual prize units are imported in the background. The stock check job could execute after the setting was active but before all associated prizes were fully imported and available, leading to false low/zero stock alerts.
* **Solution:** A short-term fix has been deployed to adjust the timing of the stock check job. Further adjustments may be necessary to ensure synchronization between prize import completion and stock checks.

***

## Investigation of Prize Delivery Failure in Rapid Referral Campaign

**Metadata**

* **Feature:** MAAC-Prize management
* **Created At:** 2025-09-05
* **Asana Task ID:** [1211256941142756](https://app.asana.com/1/1184020052539844/task/1211256941142756)
* **Ticket Priority:** P1 - Very High
* **Client Name:** NA Bakery
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Fix Problems

### 1. Issue Description

During a live demonstration, a client successfully invited a contact and was eligible to redeem an IceCream prize (Brand Coupon type). However, upon clicking "Redeem" on the event page, the coupon was not sent. The client inquired whether this issue was specific to the 'Brand Coupon' type or affected all prize types, as previous attempts with standard coupons were successful.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 6016
  * MAAC bot/channel ID: 5320
* **Reproduction Steps:**
  1. Set up a referral campaign with the IceCream prize as a Brand Coupon.
  2. Invite one contact to qualify for redemption.
  3. Click "Redeem" after the successful invite.
* **Expected vs Actual Behavior:**
  * **Expected:** The IceCream prize should be sent immediately after redemption.
  * **Actual:** The prize was not triggered upon redemption. It was observed that the prize could be sent via Auto Reply but not through the Rapid Referral campaign.
* **Additional Information:**
  * The issue was reproducible under the described conditions.
  * Screenshots and screen records were provided to illustrate the sequence of events.

### 3. Root Cause & Solution

* **Root Cause:** The prize message template for Rapid Referral campaigns incorrectly included an empty 'hero' section (missing image URL and aspect ratio) when no image was uploaded. This caused a validation error with the LINE Flex Message API. Unlike Auto-reply or Broadcast features, the Rapid Referral flow did not remove this invalid 'hero' section.
* **Solution:** The engineering team implemented a fix to ensure the 'hero' section is correctly removed from prize message templates in Rapid Referral campaigns when no image is present. This adjustment resolves the validation error and allows prizes to be sent as expected.
