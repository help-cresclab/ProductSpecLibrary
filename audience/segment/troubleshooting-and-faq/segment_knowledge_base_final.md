# segment\_knowledge\_base\_final

## Investigation of Data Insights Display Anomalies in Multi-Brand Segments

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2026-02-05
* **Asana Task ID:** [1213131750073052](https://app.asana.com/1/1184020052539844/task/1213131750073052)
* **Ticket Priority:** P0 - Emergency
* **Client Name:** 東森得易購股份有限公司-東森購物
* **Resolution Owner:** David
* **Result Breakdown:** Fix Problems

### 1. Issue Description

Multiple brands reported anomalies in Data Insights, specifically within the LINE overview, indicating abnormal data display.

### 2. Context & Details

* **Environment Conditions:**
  * Channel Types: LINE, Web, WhatsApp, EDM, FB, IG
  * Affected contact ID: \[REDACTED\_ID]
  * MAAC ID: \[REDACTED\_ID]
  * Issue reproducibility: Unclear if reproducible by ProductOps in client organization.
* **User Questions:**
  * Request for affected user and time information to assist ProductOps troubleshooting.
* **Reproduction Steps:**
  * Steps to reproduce the issue were not provided.
* **Expected vs Actual Behavior:**
  * Expected: Accurate data insights and segment calculations.
  * Actual: Significant drops in data insights and incorrect segment calculations.

### 3. Root Cause & Solution

* **Root Cause:**
  * Data errors occurred during the backfill of the `deleted_at` column, leading to missing members in segment calculations that rely on BigQuery.
* **Solution:**
  * The issue has been resolved, and product functionality has returned to normal. Clients are advised to resend any affected past or in-progress broadcasts. Scheduled broadcasts have been automatically updated. A list of affected clients will be compiled.

***

## Investigation of Reduced Recipient Count in Scheduled Smart Sending

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2026-02-05
* **Asana Task ID:** [1213115186501137](https://app.asana.com/1/1184020052539844/task/1213115186501137)
* **Ticket Priority:** P1 - Very High
* **Client Name:** \[REDACTED]
* **Resolution Owner:** David
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The client reported a significant reduction in the number of recipients for a scheduled smart sending campaign. They requested verification of the actual number sent and the reason for this occurrence.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org id: 3363
  * MAAC bot/channel id: 2857
  * Channel Type: LINE
  * Affected contact id: \[REDACTED\_ID]
  * MAAC ID: \[REDACTED\_ID]
* **User Questions:**
  * What was the actual number of recipients sent?
  * What caused the reduction in recipient count?
* **Reproduction Steps:**
  * The issue was observed in a scheduled smart sending campaign.
  * The client noted discrepancies in the audience segmentation data.
* **Expected vs Actual Behavior:**
  * Expected: The scheduled campaign should reach the intended number of recipients.
  * Actual: The recipient count was significantly lower than expected.

### 3. Root Cause & Solution

* **Root Cause:**
  * A data backfill process introduced incorrect data, resulting in missing members from audience segmentation calculations. This led to inaccurate or reduced recipient counts for audience broadcasts.
* **Solution:**
  * MAAC's Data Insights and Audience Segmentation have been restored. It is recommended to resend already sent broadcasts and in-progress Smart Sending campaigns to ensure accurate targeting. Scheduled broadcasts will now utilize refreshed and accurate data.

Status: Resolved

***

## Investigation of Contact Discrepancy in LINE Segment

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2026-02-05
* **Asana Task ID:** [1213084606836149](https://app.asana.com/1/1184020052539844/task/1213084606836149)
* **Ticket Priority:** P0 - Emergency
* **Client Name:** Muang Thai Life
* **Resolution Owner:** David
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The total number of contacts displayed on the LINE overview page is less than the number shown on the contact page. A broadcast was sent to the same segment on 02/03, but the number of contacts in the segment has significantly decreased.

### 2. Context & Details

* **Environment:**
  * MAAC org ID: 4661
  * MAAC bot ID: 3717
  * Channel Type: LINE
  * Affected contact ID: \[REDACTED\_ID]
  * Happened time: 02/05/2026
* **Reproduction Steps:**
  * The issue was observed when comparing the contact counts between the LINE overview page and the contact page.
  * A broadcast was sent to the same segment, resulting in a noticeable reduction in contact numbers.
* **Expected vs Actual Behavior:**
  * Expected: Consistent contact numbers across all pages and segments.
  * Actual: Discrepancy in contact numbers, with fewer contacts shown on the overview page.

### 3. Root Cause & Solution

* **Root Cause:** A data backfill process introduced incorrect data, leading to some members being excluded from audience segmentation calculations.
* **Solution:** The affected features have been restored, and audience data has been refreshed. It is recommended that customers resend past or ongoing campaigns to ensure accurate targeting.

***

## Investigation of CID Field Data Discrepancy in Segment Export

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2026-02-02
* **Asana Task ID:** [1213076444939189](https://app.asana.com/1/1184020052539844/task/1213076444939189)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** David
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported that the CID field in the segment filter showed no data, yet the exported list included users with a CID value.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org id: 5178
  * MAAC bot/channel id: 4114
* **User Questions:**
  * Why is there a discrepancy between the segment filter and the exported list?
* **Reproduction Steps:**
  * Create a segment with the condition "unbound CID" excluding those not receiving marketing notifications.
  * Export the list and check for users with CID values.
* **Expected vs Actual Behavior:**
  * Expected: The segment should exclude users with CID values.
  * Actual: The exported list included users with CID values.

### 3. Root Cause & Solution

* **Root Cause:**
  * Users updated their CID status after the segment was calculated but before the broadcast message was sent. Additionally, a frontend UI bug caused inconsistent display of CID filter options.
* **Solution:**
  * The frontend UI bug for CID filter options has been fixed and deployed. The audience discrepancy due to the timing between segment calculation and user profile updates is an expected system behavior, which has been explained to the client.

***

## How to Resolve the Inability to Select "Match Any Condition" in MAAC Segment

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2026-01-21
* **Asana Task ID:** [1212890498554108](https://app.asana.com/1/1184020052539844/task/1212890498554108)
* **Ticket Priority:** P1 - Very High
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The MAAC segmentation feature does not allow users to filter by "Match Any Condition." When attempting to click on "Match All Conditions," the screen becomes unresponsive.

### 2. Context & Details

* **Environment:** MAAC segmentation feature
* **User Actions:** Attempted to select "Match Any Condition" in the segmentation filter.
* **Reproduction Steps:**
  1. Navigate to the MAAC segmentation feature.
  2. Attempt to select "Match Any Condition."
  3. Observe the screen behavior when clicking "Match All Conditions."
* **Expected Behavior:** Users should be able to select "Match Any Condition" without the screen becoming unresponsive.
* **Actual Behavior:** The screen becomes unresponsive when attempting to select "Match All Conditions."

### 3. Root Cause & Solution

* **Root Cause:** A system bug was identified as the cause of the UI unresponsiveness when attempting to select "Match Any Condition."
* **Solution:** A fix was implemented and deployed to production, resolving the issue.

***

## Investigation of Button Selection Failure in Segment Filtering

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2026-01-21
* **Asana Task ID:** [1212803690945957](https://app.asana.com/1/1184020052539844/task/1212803690945957)
* **Ticket Priority:** P3
* **Client Name:** allyoung
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Fix Problems

### 1. Issue Description

During segment filtering, the "Match Any/Match All" button could not be selected. The button was not visible to the customer and appeared in the top left corner for customer service but was still unselectable.

### 2. Context & Details

* **Environment Conditions:**
  * Channel Types: LINE, Web, WhatsApp, EDM, Facebook, Instagram
  * Affected contact ID: \[REDACTED\_ID]
  * Reproduction: Unclear if the issue can be consistently reproduced by the product owner in the client organization.
* **User Questions:**
  * Why is the button not visible or selectable?
* **Reproduction Steps:**
  * Attempt to use the "Match Any/Match All" button during segment filtering.
* **Expected vs Actual Behavior:**
  * Expected: The button should be visible and selectable.
  * Actual: The button is either not visible or not selectable.

### 3. Root Cause & Solution

* **Root Cause:**
  * A backend processing bug caused an intermittent failure in handling specific data entities, leading to the button's malfunction.
* **Solution:**
  * A patch was applied to correct the data/process for the affected instance. The engineering team will monitor for recurrence and may investigate a more robust, long-term solution if patterns emerge. The issue is currently resolved.

***

## Investigation of Unexpected Segment Count Discrepancy

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2026-01-15
* **Asana Task ID:** [1212821275473949](https://app.asana.com/1/1184020052539844/task/1212821275473949)
* **Ticket Priority:** P3
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported that the number of contacts in the segment for "new friends" was not as expected. They anticipated that the segment tagged with "welcome message" would have more contacts than the segment for "new friends."

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 3169
  * MAAC bot/channel ID: 2720
* **User Actions:**
  * Attempted to filter new friends added after 1/6 by creation time.
  * Filtered users who triggered the welcome message by tag concentration greater than 1, including new friends and unblocked users.
* **Reproduction Steps:**
  1. Filter new friends added after 1/6.
  2. Filter users who triggered the welcome message.
* **Expected vs Actual Behavior:**
  * Expected: The segment tagged with "welcome message" should have more contacts than the "new friends" segment.
  * Actual: The "welcome message" segment had fewer contacts than expected.

### 3. Root Cause & Solution

* **Root Cause:**
  * The discrepancy was due to differences in segment update timing. The "welcome message" tag included both new contacts and unblocked users, which exceeded the client's expectation of only new friends.
* **Solution:**
  * Understand the numerical differences and clarify the client's precise definition of "new friend" to align MAAC segmentation with their business goals. Further action is pending clarification of customer requirements.

***

## Investigation of Segment Update Failure in MAAC

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2026-01-13
* **Asana Task ID:** [1212760165483455](https://app.asana.com/1/1184020052539844/task/1212760165483455)
* **Ticket Priority:** P1 - Very High
* **Client Name:** ホテラバ
* **Resolution Owner:** JY
* **Result Breakdown:** Fix Problems

### 1. Issue Description

Attempts to update the segment multiple times on both the client side and internally resulted in the last updated date and time displaying as 2026-01-12 14:48. The MAAC UI status did not change to "Calculating" and remained as "Ready". Additionally, the exported CSV of the segment did not include users added on the same day, approximately 300 users.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 80
  * MAAC bot ID: 79
  * Feature ID: 1664
  * Segment name: 【1】14日以内に友だち追加
  * Issue occurrence: 2026/01/12 14:50 to present
  * Reproducibility: Yes, on the client's MAAC UI. Testing on a Demo JP account showed expected behavior.
* **User Questions:**
  * Why does the segment not update with new users?
  * Why does the UI not reflect the "Calculating" status?
* **Reproduction Steps:**
  1. Attempt to update the segment on the client side.
  2. Observe the last updated timestamp and UI status.
  3. Export the segment CSV and verify the user list.
* **Expected vs Actual Behavior:**
  * **Expected:** The segment should update with new users, and the UI should display "Calculating".
  * **Actual:** The segment did not update with new users, and the UI remained "Ready".

### 3. Root Cause & Solution

* **Root Cause:** An interface error corrupted parameter calls for manual updates on segments containing exclusion conditions, preventing the API execution. The core segment calculation remained unaffected.
* **Solution:** A production fix has been deployed to correct the interface's parameter call mechanism for segment updates. Manual updates now function correctly.

***

## Investigation of Segment Update Failure in MAAC System

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2026-01-13
* **Asana Task ID:** [1212739151110360](https://app.asana.com/1/1184020052539844/task/1212739151110360)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** JY
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The segment labeled "Purchased This Month" has been stuck in the "calculating" state since last Friday after an update attempt, preventing completion.

### 2. Context & Details

* **Environment:**
  * Bot ID: 635
  * Org ID: 689
* **Segments Affected:**
  * "Purchased This Month" - [Segment Link](https://maac.cresclab.com/segments/edit/by-line-uid/74438)
  * "MOMO User" - [Segment Link](https://maac.cresclab.com/segments/edit/by-line-uid/75810)
* **Reproduction Steps:**
  1. Attempt to update an existing segment by re-uploading a LINE UID: \[REDACTED\_ID]
  2. Observe that the segment remains in the "calculating" state.
* **Expected vs Actual Behavior:**
  * **Expected:** Segment should update and complete processing.
  * **Actual:** Segment remains in "calculating" state indefinitely.

### 3. Root Cause & Solution

* **Root Cause:**
  * The segment editing process was missing a critical internal parameter (import\_key) during the file re-upload, which interrupted the update process.
* **Solution:**
  * Engineering has corrected the editing flow to ensure the required parameter is included during re-upload. The fix is now live, and no additional customer action is required. Segments should update normally moving forward.

***

## Investigation of Identical Contact Numbers Across Different Segments

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2026-01-09
* **Asana Task ID:** [1212714239759016](https://app.asana.com/1/1184020052539844/task/1212714239759016)
* **Ticket Priority:** P2
* **Client Name:** Tiffanyandco
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client set up five segments with different MAAC tag conditions and observed that three segments had the same number of contacts, as did two others. This was contrary to expectations.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 5208
  * MAAC bot/channel ID: 4141
* **User Observations:**
  * Segments such as "Tiffany Knot," "Tiffany Lock," and others displayed identical contact counts.
* **Reproduction Steps:**
  * Set up segments with different MAAC tag conditions.
  * Check the contact numbers in each segment.
* **Expected vs Actual Behavior:**
  * **Expected:** Different segments should have varying contact numbers based on their specific tags.
  * **Actual:** Segments displayed identical contact numbers despite differing tag conditions.

### 3. Root Cause & Solution

* **Root Cause:**
  * The segments were configured using "any filter" (OR) logic with a set of broad tags (PM, PI, RM, Jewelry) that collectively covered all 16,977 contacts. The specific "Tiffany" tags were redundant, and the system functioned as designed.
* **Solution:**
  * Customer Support should explain the "any filter" (OR) logic to the client, clarifying that broad, overlapping OR conditions result in consistent segment sizes. It is advised to select only one tag for specific filtering needs.

***

## Investigation of Smart Sending Suspension Request

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2026-01-02
* **Asana Task ID:** [1212617985199028](https://app.asana.com/1/1184020052539844/task/1212617985199028)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Gideon
* **Result Breakdown:** Task-Ticket

### 1. Issue Description

The client requested to pause or cancel the smart sending of a broadcast titled "20260102\_BRAND\_Has Your Skin Reached Its Peak Today?" due to an unverified error report.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 6394
  * MAAC bot/channel ID: 6468
* **User Questions:**
  * How to pause or cancel the ongoing smart sending?
* **Reproduction Steps:**
  * The client attempted to halt the broadcast based on an unverified error report.
* **Expected vs Actual Behavior:**
  * Expected: The broadcast continues as scheduled.
  * Actual: The broadcast was prematurely paused.

### 3. Root Cause & Solution

* **Root Cause:**
  * The broadcast was interrupted due to an unverified assumption by the client, which led to an unnecessary pause.
* **Solution:**
  * To resume the broadcast, disable the "message schedule check" and utilize MAAC's smart sending feature for missed batches.
  * Customers can identify sent contacts through MAAC's open tracking feature. Immediate contact list export is not feasible.
  * This procedure will be documented in the runbook for future reference.

The issue has been resolved following these actions.

***

## Investigation of Zero Data in High Purchase Probability LINE Contacts Segment

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-12-22
* **Asana Task ID:** [1212543508010702](https://app.asana.com/1/1184020052539844/task/1212543508010702)
* **Ticket Priority:** P2
* **Client Name:** 台灣優衣庫有限公司-UNIQLO
* **Resolution Owner:** Aaren, David
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The segment for "Contacts with purchase history" and "High purchase probability within two weeks" in MAAC for Uniqlo is displaying zero contacts. This is unexpected as LINE Broadcast campaigns have recorded revenue data since September.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 1016
  * MAAC bot/channel ID: 884
* **User Questions:**
  * Why does the segment show zero contacts despite recorded revenue?
  * Is this behavior expected, and how can the data be displayed correctly?
* **Reproduction Steps:**
  * Uniqlo has been connected to GA for over four months.
  * LINE Broadcast messages have recorded order and revenue data since early September.
* **Expected vs Actual Behavior:**
  * **Expected:** The segment should display contacts with purchase history and high purchase probability.
  * **Actual:** The segment displays zero contacts.

### 3. Root Cause & Solution

* **Root Cause:**
  * Uniqlo's website redirect process drops the `utm_term` parameter, which includes the `lm:member_id` for individual contact tracking. This prevents MAAC from mapping purchase events to specific LINE contacts in the segmentation data.
* **Solution:**
  * Uniqlo must configure their website to preserve the `utm_term` parameter through all redirects. This is essential for accurate individual contact tracking, proper segmentation, and enabling future event-triggered marketing campaigns based on user behavior.

***

## Investigation of "NaN" Display in Contact List Export

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-12-22
* **Asana Task ID:** [1212543257591550](https://app.asana.com/1/1184020052539844/task/1212543257591550)
* **Ticket Priority:** P4
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Fix Problems

### 1. Issue Description

Users observed that after creating a segment, the user interface displayed "NaN" for the number of phone contacts, despite the exported contact list containing phone numbers.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org id: 4538
  * MAAC bot/channel ID: 3645
  * Issue began on: December 19
* **User Questions:**
  * Why does the UI display "NaN" for phone contacts when the exported list contains phone numbers?
* **Reproduction Steps:**
  1. Create a segment in the MAAC system.
  2. Observe the UI displaying "NaN" for phone contacts.
  3. Export the contact list and verify the presence of phone numbers.
* **Expected vs Actual Behavior:**
  * **Expected:** The UI should display the correct number of phone contacts.
  * **Actual:** The UI displays "NaN" for phone contacts.

### 3. Root Cause & Solution

* **Root Cause:** An internal bug caused numeric values to be incorrectly displayed as "NaN" in the user interface.
* **Solution:** The bug causing the "NaN" display has been identified, fixed, and deployed to production.

***

## Investigation of Segment Data Export Format Changes

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-12-17
* **Asana Task ID:** [1212465993341273](https://app.asana.com/1/1184020052539844/task/1212465993341273)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported an unexpected change in the export of contact lists from segments. Previously, both LINE contacts and phone contacts without LINE UIDs were exported together, requiring manual exclusion in Excel. Recently, only contacts with LINE UIDs are being exported.

### 2. Context & Details

* **Environment Conditions:**
  * The issue was observed in the segment "251217\_Broadcast\_SP+Product Recommendation."
  * The segment included 396,420 LINE contacts and 411,969 phone contacts.
  * The expectation was to export phone contacts without LINE UIDs, identified as "fake-xxxxx."
* **User Questions:**
  * Has there been a recent adjustment to the MAAC contact export functionality?
  * If adjustments were made, what are the scope and date of these changes?
* **Reproduction Steps:**
  * Export the contact list from the segment.
  * Compare the number of exported LINE contacts and phone contacts.
* **Expected vs Actual Behavior:**
  * **Expected:** Export includes both LINE contacts and phone contacts without LINE UIDs.
  * **Actual:** Export includes only contacts with LINE UIDs.

### 3. Root Cause & Solution

* **Root Cause:**
  * The segment "251217\_Broadcast\_SP+Product Recommendation" was defined without criteria to include phone contacts. Therefore, no "fake-xxxxx" contacts were present in the segment for export.
* **Solution:**
  * No bug was identified. To include phone contacts in the export, the segment's criteria must be updated to encompass them. It is advised to inform the customer about the importance of segment definition.

***

## Investigation of AI Segment Displaying Zero Results

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-12-03
* **Asana Task ID:** [1212277836186691](https://app.asana.com/1/1184020052539844/task/1212277836186691)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** N/A
* **Result Breakdown:** Fix Problems

### 1. Issue Description

An AI Segment initially displayed a list of over 20,000 contacts but unexpectedly recalculated to show zero contacts the following day.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 23
  * MAAC bot/channel ID: 15
* **User Actions:**
  * The AI Segment was configured with a prompt targeting customers likely to open or click on product recommendation messages.
* **Reproduction Steps:**
  * The issue was set up on a Friday, initially showing over 20,000 contacts.
  * By the next day, the contact count recalculated to zero.
* **Expected vs Actual Behavior:**
  * Expected: The contact list should remain consistent unless manually altered.
  * Actual: The contact list unexpectedly recalculated to zero without user intervention.

### 3. Root Cause & Solution

* **Root Cause:**
  * The AI Segment dynamically selects its data sources. Currently, only the TAG\_AND\_COMMENT source is fully implemented. The system unexpectedly switched to an unimplemented source, ENGAGEMENT\_HISTORY, resulting in zero contacts.
* **Solution:**
  * The data source for the affected AI Segment was temporarily fixed to TAG\_AND\_COMMENT. Further investigation is required to understand the unexpected data source selection changes. Implementing the remaining AI Segment data sources should be prioritized.

***

## Investigation of GA Tracking Failure in MAAC EC-Features

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-12-03
* **Asana Task ID:** [1212252476377404](https://app.asana.com/1/1184020052539844/task/1212252476377404)
* **Ticket Priority:** P2
* **Client Name:** Test-Sunto Peerapol
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The MAAC EC-Features were unable to track web behavior through GA integration, resulting in failure to function as expected. This issue was observed in two cases: page views were not tracked, and add-to-cart actions did not trigger the expected customer journey.

### 2. Context & Details

* **Environment:**
  * Client: Samitivej Chonburi
  * Domain: shop.samitivejchonburi.com
  * MAAC org id: 5600
* **Reproduction Steps:**
  * **Case 1: View Page Not Tracked**
    1. Click the homepage link in LINE: `https://maac.io/4XZ9C/hMrDp`.
    2. Navigate to `https://shop.samitivejchonburi.com/promotion-period-detail.html/[REDACTED_PATH]`./\[REDACTED\_PATH]
    3. Create a segment to track contacts viewing the page.
    4. Result: Segment result is 0.
  * **Case 2: Add-to-Cart Not Tracked**
    1. Create a Customer Journey to track contacts adding products to the cart.
    2. Trigger by tag with a 3-day delay.
    3. Add tag to LINE contact to start the trigger.
    4. Click the homepage link in LINE: `https://maac.io/4XZ9C/hMrDp`.
    5. Navigate to `https://shop.samitivejchonburi.com/promotion-period-detail.html/[REDACTED_PATH]`/\[REDACTED\_PATH] and add a product to the cart.
    6. Result after 3 days: No message sent.
* **Expected vs Actual Behavior:**
  * Expected: GA should track page views and add-to-cart actions, triggering segmentation and customer journeys.
  * Actual: No tracking data was captured, and customer journeys were not triggered.

### 3. Root Cause & Solution

* **Root Cause:**
  * The MAAC system's GA4 authorization account (\[REDACTED\_EMAIL]) lacked proper permissions in the client's GA4 backend for the shop.samitivejchonburi.com domain. This prevented MAAC from retrieving necessary tracking data. Additionally, the client had internal GA4 data collection issues.
* **Solution:**
  * The client corrected their GA4 backend permissions for \[REDACTED\_EMAIL] and resolved their internal GA4 data collection issues. MAAC's Django backend now confirms valid GA4 connections for the relevant domains. All MAAC e-commerce and tracking functions are expected to work. No further action is required from Engineering or Product.

***

## Investigation of Audience Exclusion Limit Reached in MAAC-Segment

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-11-28
* **Asana Task ID:** [1212212478568915](https://app.asana.com/1/1184020052539844/task/1212212478568915)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client encountered an issue where certain audience segments could not be excluded due to a message indicating "Cannot select due to association limit reached." The client sought clarification on whether this was due to selecting too many audiences, thus reaching a limit.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 3363
  * MAAC bot: 2857
  * Feature ID: \[REDACTED\_UUID]
* **User Questions:**
  * Why does the system indicate that the association limit has been reached when excluding certain audience segments?
  * Is this due to selecting too many audiences?
* **Reproduction Steps:**
  1. Attempt to set up audience segmentation.
  2. Select segments to exclude.
  3. Encounter error message indicating the association limit has been reached.
* **Expected vs Actual Behavior:**
  * **Expected:** Ability to exclude selected audience segments without error.
  * **Actual:** Error message received, preventing exclusion of certain segments.

### 3. Root Cause & Solution

* **Root Cause:**
  * There was a misunderstanding regarding the segment exclusion depth limit. The system's depth limit applies to sequential exclusion definitions (e.g., Segment A excludes B, and Segment B then excludes C), not to the complexity of the excluded segment's own conditions.
* **Solution:**
  * The exclusion depth limit logic was clarified to the Customer Success Manager (CSM).
  * Help center documentation for segment creation was updated to explain this mechanism clearly.
  * No engineering changes were necessary as the system operated according to design.

***

## Investigation of Unexpected Segment Filtering Results

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-11-25
* **Asana Task ID:** [1212086489143431](https://app.asana.com/1/1184020052539844/task/1212086489143431)
* **Ticket Priority:** P2
* **Client Name:** 星巴克Starbucks
* **Resolution Owner:** Jack Lee, George
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The segment filtering results did not meet expectations. Specifically, the segment ID 251126 related to a customer broadcast activity was unavailable or displayed incomplete data, which prevented the execution of the customer broadcast.

### 2. Context & Details

* **Environment:**
  * MAAC organization ID: 3351
  * MAAC bot ID: 2850
* **User Actions:**
  * Attempted to filter contacts for a specific segment at 17:45, but no results were available by 18:43.
  * Results were finally available at 18:56.
* **Reproduction Steps:**
  * Filter contacts using the segment ID 251126.
  * Observe the delay in obtaining results.
* **Expected vs Actual Behavior:**
  * **Expected:** Immediate availability of filtered contact results.
  * **Actual:** Delayed availability, with results appearing over an hour later.
* **Additional Observations:**
  * Tag "是星禮程會員\_電話配對" showed an unreasonable count of 3,559,662 contacts due to slow page loading.

### 3. Root Cause & Solution

* **Root Cause:**
  * The issue was due to delayed or incomplete data synchronization for the segment. This required manual intervention to supplement the data.
* **Solution:**
  * The segment's data was manually updated by the Customer Success Manager (CSM), resolving the immediate issue.
  * It is recommended that the engineering team investigate the cause of the data synchronization delay and determine why a manual refresh was necessary for the segment's availability.

***

## Investigation of Unexpected Segment Calculation Results

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-11-25
* **Asana Task ID:** [1212084549273717](https://app.asana.com/1/1184020052539844/task/1212084549273717)
* **Ticket Priority:** P1 - Very High
* **Client Name:** FUJI 按摩椅
* **Resolution Owner:** George, Jack Lee
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The client reported that the segment filtering did not meet expectations. Specifically, the segment calculation returned zero members despite the presence of tagged contacts.

### 2. Context & Details

* **Client Operations:**
  * Imported a batch of phone numbers and added the tag "005P025112501" to these numbers.
  * Attempted to filter the segment "005P South District Storage and Transport Department" using the tag "005P025112501".
  * The segment calculation resulted in zero members.
* **Environment:**
  * MAAC org ID: 5276
  * MAAC bot/channel ID: 4193
* **Reproduction Steps:**
  * Import phone numbers.
  * Tag the numbers.
  * Filter the segment using the specified tag.
* **Expected vs Actual Behavior:**
  * Expected: Segment should include tagged contacts.
  * Actual: Segment calculation showed zero members.
* **Related Issues:** Similar issues were documented in other tasks.

### 3. Root Cause & Solution

* **Root Cause:**
  * The issue was related to the development of the WhatsApp Segment (WA Segment) feature. Adding reachability data triggered an existing system mechanism, resulting in incorrect segment calculation outcomes.
* **Solution:**
  * The engineering team reprocessed and supplemented the data. Most affected segment results have been restored. If issues persist, users are advised to manually click "Update Segment" in MAAC. If abnormalities continue after manual updates, further reporting is necessary.

***

## Investigation of Unexpected MAAC Segment Count Discrepancy

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-11-25
* **Asana Task ID:** [1212084549273694](https://app.asana.com/1/1184020052539844/task/1212084549273694)
* **Ticket Priority:** P1 - Very High
* **Client Name:** imager 37
* **Resolution Owner:** George
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The client reported that the MAAC segment displayed a count of 0 contacts, which was not expected. Previously, in November, the same filter conditions yielded a non-zero count.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 5540
  * MAAC bot/channel ID: 4457
  * Issue occurrence date: 11/25
  * Reproducibility: Yes
* **User Actions:**
  * The client attempted to filter segments using specific conditions.
  * On the contacts page, the same conditions resulted in a non-zero count.
* **Expected vs Actual Behavior:**
  * **Expected:** The segment should display a count of contacts matching the filter conditions.
  * **Actual:** The segment displayed a count of 0 contacts.

### 3. Root Cause & Solution

* **Root Cause:**
  * During the development of the WhatsApp Segment (WA Segment) functionality, the addition of reachability data inadvertently triggered an existing system mechanism. This caused some segment calculations to erroneously result in zero contacts.
* **Solution:**
  * The engineering team re-processed the data and recalculated the affected segments.
  * For segments still showing zero, users should manually click "Update Segment" in the UI.
  * If the issue persists, users are advised to report the specific segment for further investigation.
* **Status:** Fixed.

***

## Investigation of Inaccurate AI Segment Creation

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-11-20
* **Asana Task ID:** [1212000598445419](https://app.asana.com/1/1184020052539844/task/1212000598445419)
* **Ticket Priority:** P2
* **Client Name:** TelemedicineSCH
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The AI segment created with the prompt for 'customers who are interested in \[Event Location]' included contacts without the relevant tag or any tags at all. The notes for these contacts did not mention the specified interest, indicating a lack of precision in AI segment generation.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org id / CAAC org id: 4956
  * Happened on: 12th Nov
* **User Questions:**
  * Why are contacts without the specified tag included in the segment?
  * How can the AI segment generation be made more accurate?
* **Reproduction Steps:**
  1. Create an AI segment with a prompt specifying interest in a particular event location.
  2. Export the segment and review the contacts included.
* **Expected vs Actual Behavior:**
  * **Expected:** Only contacts with the specified tag should be included.
  * **Actual:** Contacts without the specified tag or any tags were included.

### 3. Root Cause & Solution

* **Root Cause:**
  * The AI model adjustment on December 8 improved overall accuracy but failed to address the specific issue of segment generation for Org 4956, requiring further intervention.
* **Solution:**
  * Engineering conducted follow-up actions, successfully generating AI segments for Org 4956 with 100% accuracy. Future model adjustments should include verification of segment generation across all relevant organizations.

***

## Investigation of AI Segmentation Failure in Broadcast

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-11-12
* **Asana Task ID:** [1211919837362932](https://app.asana.com/1/1184020052539844/task/1211919837362932)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The AI segmentation feature resulted in a segment with zero contacts when using the prompt "Message input 111", causing the broadcast to fail. The user expected the AI to identify relevant contacts.

### 2. Context & Details

* **Environment Conditions:**
  * Segment name: Audience\_Double11\_Waitlist
  * Segmentation method: AI Segmentation
  * Description: Message input 111
* **User Questions:**
  * Is the zero-contact result due to the prompt being unrelated to MAAC backend tags?
  * Is there a way to alert users if their prompt might not yield results?
* **Reproduction Steps:**
  * Create a segment using the prompt "Message input 111".
  * Attempt to broadcast to the segment.
* **Expected vs Actual Behavior:**
  * Expected: AI identifies relevant contacts based on the prompt.
  * Actual: No contacts identified, resulting in a failed broadcast.

### 3. Root Cause & Solution

* **Root Cause:**
  * The AI segmentation relies on MAAC tags and notes as data sources. The prompt "Message input 111" was too vague and did not match any existing tags or notes, resulting in zero identified contacts.
* **Solution:**
  * The core functionality is operating as designed, contingent on input clarity.
  * Suggested Actions:
    * Enhance UI/UX to guide users in crafting effective AI segmentation prompts.
    * Implement real-time feedback or warnings for ambiguous prompts.
    * Review the system's ability to initiate broadcasts with zero-contact segments.

***

## Investigation of Limited Broadcast Reach in MAAC System

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-11-03
* **Asana Task ID:** [1211818294292311](https://app.asana.com/1/1184020052539844/task/1211818294292311)
* **Ticket Priority:** P2
* **Client Name:** BEIGY
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client initiated a broadcast on November 1st targeting all contacts, with an expected reach of 28,539 recipients. However, only 200 messages were successfully sent. The client requires an investigation into the cause of this discrepancy, especially given the urgency due to the ongoing promotional period.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 5830
  * MAAC bot IDs: 4724, 4762
* **User Questions:**
  * Why was the broadcast limited to 200 recipients instead of the expected 28,539?
* **Reproduction Steps:**
  * Initiate a broadcast to all contacts using the MAAC system.
* **Expected vs Actual Behavior:**
  * Expected: Broadcast reaches 28,539 contacts.
  * Actual: Broadcast reached only 200 contacts.

### 3. Root Cause & Solution

* **Root Cause:**
  * The client's LINE official account had reached its monthly message quota. This resulted in a 429 status code ("You have reached your monthly limit.") from the LINE API.
* **Solution:**
  * There is no issue with the MAAC system. The client is advised to either upgrade their LINE official account message plan or wait for the next billing cycle. Customer Success will communicate these options to the client.

***

## Investigation of Discrepancy in MAAC Segment Import Counts

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-10-28
* **Asana Task ID:** [1209226325083447](https://app.asana.com/1/1184020052539844/task/1209226325083447)
* **Ticket Priority:** P2
* **Client Name:** MRM Japan/BOSS Japan
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The MAAC segment import process resulted in a significantly lower count of contacts (16,512) compared to the expected total (23,094) from the client's source file.

### 2. Context & Details

* **Environment Conditions:**
  * Expected LINE UIDs: 23,094 (all active, no blocks)
  * Segment result in MAAC: 16,512 (LINE following contacts)
  * Missing/unreflected UIDs: 6,582
  * Impact: Segment planned for use in a campaign scheduled for October 29.
* **Reproduction Steps:**
  1. Download CSV template from MAAC segment creation screen.
  2. Paste LINE UIDs (total verified: 23,094).
  3. Upload CSV and run calculation.
  4. Resulting segment consistently shows fewer contacts.
* **Additional Notes:**
  * Issue persists even when creating multiple segments.
  * The same procedure worked correctly in the past two months (e.g., \~26,000-record imports).
  * A smaller test import today (185 records) processed successfully.
* **Client Request:**
  * Review import processing logs.
  * Identify root cause for the \~6.6k missing records.
  * Provide initial findings and any temporary workaround by end of day (Oct 28).

### 3. Root Cause & Solution

* **Root Cause:** The client's uploaded CSV file contained duplicate LINE UIDs. MAAC's segment creation process correctly filters and counts only unique UIDs.
* **Solution:** The product functionality is correct. Advise the client to provide CSV files with unique LINE UIDs for future imports.

The issue is resolved with the client required to take action by ensuring the uniqueness of UIDs in their CSV files.

***

## How to Retrieve Historical Segmentation Conditions in MAAC

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-10-20
* **Asana Task ID:** [1211691171254904](https://app.asana.com/1/1184020052539844/task/1211691171254904)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** JY
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The MAAC broadcast report does not directly display the exact segmentation conditions used for a past broadcast, requiring manual investigation to retrieve.

### 2. Context & Details

* **Broadcast Details:**
  * Broadcast ID: 250926\_40629\_90doff
  * Report URL: [MAAC Broadcast Report](https://maac.cresclab.com/broadcast/line/report/407756)
* **Segmentation Conditions:**
  * Criteria: Users with no interaction for 90 days within the past year
  * API Reference: \[REDACTED\_PATH]
* **Client Information:**
  * MAAC org ID: 479
  * MAAC bot/channel ID: 460
* **Occurrence Date:** 2025-10-20
* **Reproduction:** Not specified

### 3. Root Cause & Solution

**Root Cause:** MAAC's user interface lacks a direct audit trail or snapshot of segmentation criteria linked to past broadcasts. The segmentation definitions can be dynamic, making historical lookups difficult.

**Solution:** ProductOps manually retrieved the specific segmentation conditions (last interaction between 2024-06-24 and 2025-06-24). It is suggested to enhance MAAC broadcast reports to include a snapshot of segmentation criteria used at the time of the broadcast. Implementing version control or audit logs for segmentation definitions is recommended.

***

## Investigation of AI Segment Results Discrepancy in Insurverse Campaign

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-10-15
* **Asana Task ID:** [1211648131247953](https://app.asana.com/1/1184020052539844/task/1211648131247953)
* **Ticket Priority:** P2
* **Client Name:** Insurverse
* **Resolution Owner:** Ray
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The AI Segment feature did not return expected results when filtering contacts based on specific campaign interactions. Specifically, contacts who interacted with both "1 free 1" campaigns and "live TikTok" were not accurately captured.

### 2. Context & Details

* **Environment:** Insurverse organization (ID: 4811)
* **Testing Scenarios:**
  * **Test 1:** Filtered contacts who clicked "1 free 1" campaigns resulted in 510 contacts.
  * **Test 2:** Filtered contacts who clicked both "1 free 1" campaigns and "live TikTok" resulted in 0 contacts.
* **Observation:** Despite several contacts having both tags, the AI failed to capture them in Test 2.
* **Tag Structure Issue:** Tags related to TikTok are scattered across different campaigns, complicating manual selection.
* **Expected Behavior:** The AI Segment should automatically identify and filter contacts with any TikTok-related tags without manual selection.
* **Actual Behavior:** The AI did not capture all relevant contacts as expected.

### 3. Root Cause & Solution

* **Root Cause:** The current system design of the CDH has a known limitation in real-time synchronization of specific behavioral tags between MAAC and CAAC. The synchronization operates on a periodic schedule rather than real-time, affecting immediate data availability for messaging actions.
* **Solution:** The issue is closed as per current product capabilities. This limitation is documented and will be considered in future CDH enhancements. For urgent messaging needs, customers should be informed about the synchronization delay for these specific tags.

***

## Inquiry on Data Update Frequency for MAAC Segments

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-09-12
* **Asana Task ID:** [1211339238787010](https://app.asana.com/1/1184020052539844/task/1211339238787010)
* **Ticket Priority:** P2
* **Client Name:** 台灣優衣庫有限公司-UNIQLO（2025）
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The customer reported that the MAAC segments for "purchased LINE contacts" and "high purchase probability LINE contacts" are showing zero members. This issue persists despite the integration of Google Analytics (GA) and UTM parameters, and the display of revenue in push notifications.

### 2. Context & Details

* **Environment Conditions:**
  * The customer began using the system and integrated GA on 8/25.
  * GA and UTM parameters are connected, and push notifications are displaying revenue data.
* **User Questions:**
  * The customer inquired about the typical time required for data to appear in segments, as they are planning their strategy.
* **Reproduction Steps:**
  * Integration of GA and UTM parameters.
  * Observation of segment data through "分眾" for LINE contacts.
* **Expected vs Actual Behavior:**
  * **Expected:** Segments should display the number of "purchased LINE contacts" and "high purchase probability LINE contacts."
  * **Actual:** Both segments show zero members.

### 3. Root Cause & Solution

* **Root Cause:**
  * The issue is attributed to insufficient data volume and processing time in Google Analytics. The calculation for segments such as "high purchase probability" requires specific GA data conditions:
    * Inclusion of "add to cart" or "checkout revenue" metrics.
    * Data for at least 14 days.
    * A minimum of 1,000 unique records.
  * Since the customer started using the system on 8/25, these conditions were not yet met. Additionally, GA4 has inherent data delays, often requiring up to 30 days for data to fully accumulate and stabilize for such calculations.
* **Solution and Suggested Actions:**
  * The customer has been advised to wait for sufficient data to accumulate and meet the necessary conditions for accurate segment calculations.

***

## Investigation of Anomalous Segment Count in MAAC-Segment

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-09-08
* **Asana Task ID:** [1211285615645748](https://app.asana.com/1/1184020052539844/task/1211285615645748)
* **Ticket Priority:** P2
* **Client Name:** 主富服裝股份有限公司- NET
* **Resolution Owner:** Leo
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The contact count for segments L4 and L5 for client NET suddenly dropped to zero. Additionally, there is a discrepancy of 232 contacts between the total active contacts (626,772) and the sum of L1-L3 and L4-L5 segments (626,540).

### 2. Context & Details

* **Client Information:**
  * Organization ID: 225
  * Channel ID: 204
* **Feature Information:**
  * Segment Feature ID: 112469 & 112470
  * Date of Occurrence: 2025/9/8
  * Reproducibility: Yes
* **Data Discrepancy:**
  * Total active contacts: 626,772
  * Sum of L1-L3 and L4-L5 segments: 626,540
* **User Questions:**
  * Why did the L4 & L5 segment counts drop to zero?
  * Why is there a discrepancy in the total contact count?
* **Expected vs Actual Behavior:**
  * Expected: Consistent segment counts and alignment with total active contacts.
  * Actual: Sudden drop in L4 & L5 counts and a discrepancy in total contact numbers.

### 3. Root Cause & Solution

* **Root Cause:**
  * The issue appears to be related to a data integrity or calculation error within the MAAC segmentation feature, affecting the L4 and L5 segment counts.
* **Solution:**
  * Conduct an engineering investigation to identify and resolve the cause of the incorrect segment counts and the overall contact discrepancy. This may involve reviewing the data processing logic and ensuring accurate calculations within the segmentation feature.

***

## Investigation of Upload Failure in MAAC-Segment

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-05-26
* **Asana Task ID:** [1210376434573383](https://app.asana.com/1/1184020052539844/task/1210376434573383)
* **Ticket Priority:** P2
* **Client Name:** 酷澎
* **Resolution Owner:** JY
* **Result Breakdown:** Limit information

### 1. Issue Description

The customer reported an unexpected error when attempting to upload LINE UIDs. A 403 Forbidden error was observed in the browser console during the upload process, particularly when handling large volumes exceeding 10,000 records.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC bot ID: 4869
  * Occurrence Date: 2025-05-26
  * Reproducibility: The issue could not be reproduced internally.
* **User Questions:**
  * The customer inquired about the cause of the 403 error and potential solutions.
* **Reproduction Steps:**
  * Attempt to upload a large volume of LINE UIDs.
  * Observe the browser console for any errors.
* **Expected vs Actual Behavior:**
  * **Expected:** Successful upload of LINE UIDs without errors.
  * **Actual:** Encountered a 403 Forbidden error in the browser console.

### 3. Root Cause & Solution

* **Root Cause:**
  * The root cause remains undetermined. Internal testing with similar large files (199k records) on the client's bot was successful, and no corresponding 403 errors were found in MAAC's system logs. This suggests the issue may be related to the client's browser, network, or local environment restrictions.
* **Solution:**
  * A workaround was provided by assisting the customer with data export/import.
  * The issue could not be reproduced internally.
  * If the issue reoccurs, the customer is advised to provide the detailed response body from the browser's network tab for the 403 error to aid in further diagnosis.
* **Status:** Closed. Workaround provided, issue not reproducible.
