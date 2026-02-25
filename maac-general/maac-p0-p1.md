# MAAC P0/P1

## Investigation of Zero Tag Coverage in Data Insights

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2026-02-09
* **Asana Task ID:** [1213185386062836](https://app.asana.com/1/1184020052539844/task/1213185386062836)
* **Ticket Priority:** P1 - Very High
* **Client Name:** all brands
* **Resolution Owner:** Gideon
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The data insights for tag coverage are displaying zero for all brands. Assistance is requested to investigate this issue.

### 2. Context & Details

* **Environment Conditions:**
  * Affected across all brands.
  * Occurred since this morning.
  * Channel Types: LINE, Web, WhatsApp, EDM, Facebook, Instagram.
* **Reproduction Steps:**
  * The issue can be reproduced consistently.
  * ProductOps can reproduce the issue in the client organization.
* **Expected vs Actual Behavior:**
  * Expected: Accurate tag coverage data should be displayed.
  * Actual: Tag coverage data is showing as zero.

### 3. Root Cause & Solution

* **Root Cause:**
  * The 'report\_membertrenddailyreport' table, updated via an Airflow job, did not populate correctly, resulting in zero tag metrics. The root cause of the intermittent failure of the Airflow job remains undetermined.
* **Solution:**
  * The Airflow job was manually re-run, restoring the current data.
  * Historical data for specific dates (e.g., January 11, December 25, December 28, September 1-9) has been backfilled.
  * An ongoing investigation into the root cause of the Airflow job failure is underway, with plans to establish a runbook for future occurrences.

***

## Investigation of Data Insights Anomaly in Multi-Brand Segment

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2026-02-05
* **Asana Task ID:** [1213131750073052](https://app.asana.com/1/1184020052539844/task/1213131750073052)
* **Ticket Priority:** P0 - Emergency
* **Client Name:** \[REDACTED]
* **Resolution Owner:** David
* **Result Breakdown:** Fix Problems

### 1. Issue Description

Multiple brands reported anomalies in the Data Insights > LINE Overview, indicating data discrepancies.

### 2. Context & Details

* **Environment Conditions:**
  * Channel Types: LINE, Web, WhatsApp, EDM, Facebook, Instagram
  * Affected Contact ID: \[REDACTED\_ID]
  * MAAC ID: \[REDACTED\_ID]
  * Issue reproducibility: Unclear if ProductOps can reproduce in client org
* **User Questions:**
  * Request for assistance in addressing data anomalies
* **Reproduction Steps:**
  * Not explicitly provided
* **Expected vs Actual Behavior:**
  * Expected: Accurate data insights and segment calculations
  * Actual: Significant drops in data insights and incorrect segment calculations

### 3. Root Cause & Solution

* **Root Cause:**
  * Data errors occurred during the backfill of the `deleted_at` column, leading to missing members in segment calculations that rely on BigQuery.
* **Solution:**
  * The issue has been resolved, and product functionality is restored. Clients are advised to resend affected past or in-progress broadcasts. Scheduled broadcasts have been automatically updated. An affected client list will be compiled.

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

The client reported a significant reduction in the number of recipients for a scheduled smart sending campaign. They requested verification of the actual number sent and an investigation into the cause of this issue.

### 2. Context & Details

* **Environment:**
  * MAAC org id: 3363
  * MAAC bot/channel id: 2857
  * Channel Type: LINE
* **User Questions:**
  * What was the actual number of recipients sent?
  * What caused the reduction in recipient count?
* **Reproduction Steps:**
  * The issue was observed in the scheduled smart sending campaign for the segment \[REDACTED\_PHONE]-KHIHO.
* **Expected vs Actual Behavior:**
  * Expected: The scheduled campaign should have reached the full intended audience.
  * Actual: The recipient count was significantly lower than expected.

### 3. Root Cause & Solution

* **Root Cause:**
  * A data backfill process introduced incorrect data, resulting in missing members from audience segmentation calculations. This led to inaccurate or reduced recipient counts for audience broadcasts.
* **Solution:**
  * MAAC's Data Insights and Audience Segmentation functionalities have been restored. It is recommended to resend already sent broadcasts and in-progress Smart Sending campaigns to ensure accurate targeting. Scheduled broadcasts will utilize refreshed data. The issue is now resolved.

***

## Investigation of Contact Discrepancy in MAAC Segment

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
  * MAAC org id: 4661
  * MAAC bot: 3717
  * Channel Type: LINE
  * Affected contact id: \[REDACTED\_ID]
* **Happened Time:** 02/05/2026
* **Reproduction Steps:**
  * Broadcast sent to a segment on 02/03.
  * Observed discrepancy in contact numbers between overview and contact pages.
* **Expected vs Actual Behavior:**
  * Expected: Consistent contact numbers across all pages.
  * Actual: Reduced contact numbers on the overview page compared to the contact page.

### 3. Root Cause & Solution

* **Root Cause:** A data backfill process introduced incorrect data, causing some members to be missing from audience segmentation calculations.
* **Solution:** Affected features have been restored, and audience data has been refreshed. Customers should resend past or ongoing campaigns to ensure correct targeting.

***

## Investigation of Login and API Access Issues in MAAC

**Metadata**

* **Feature:** MAAC-Auto Login
* **Created At:** 2026-02-03
* **Asana Task ID:** [1213074365213896](https://app.asana.com/1/1184020052539844/task/1213074365213896)
* **Ticket Priority:** P0 - Emergency
* **Client Name:** N/A
* **Resolution Owner:** N/A
* **Result Breakdown:** Fix Problems

### 1. Issue Description

MAAC users reported an inability to log in, failure to edit links, and unavailability of the MAAC Open API. The issue has been resolved.

### 2. Context & Details

* **Environment Conditions:**
  * Affected Platforms: LINE, Web, WhatsApp, EDM, Facebook, Instagram
  * Affected Contact ID: \[REDACTED\_ID]
  * MAAC ID: \[REDACTED\_ID]
* **Reproduction Steps:**
  * Users attempted to log in and edit links but encountered failures.
  * MAAC Open API was inaccessible during the incident.
* **Expected vs Actual Behavior:**
  * Expected: Users should be able to log in, edit links, and access the MAAC Open API without issues.
  * Actual: Users were unable to perform these actions during the incident window.

### 3. Root Cause & Solution

* **Root Cause:** A database index creation was executed in the foreground instead of the background, causing a temporary service lock.
* **Solution:** Corrective actions and system updates were performed to restore service. Future database index creations should be executed in the background to prevent similar service interruptions.

***

## Investigation of Broadcast Incompletion in MAAC Platform

**Metadata**

* **Feature:** MAAC-Broadcast
* **Created At:** 2026-01-26
* **Asana Task ID:** [1212973707654521](https://app.asana.com/1/1184020052539844/task/1212973707654521)
* **Ticket Priority:** P1 - Very High
* **Client Name:** N/A
* **Resolution Owner:** JY
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The broadcast scheduled for 0126 at 15:00 was not completed successfully.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 3691
  * MAAC bot ID: 3087
  * Channel Type: LINE
  * Broadcast ID: 492964
* **User Questions:**
  * Can the issue be reproduced?
  * Can ProductOps reproduce the issue in the client organization?
* **Reproduction Steps:**
  * Details on reproduction steps were not provided.
* **Expected vs Actual Behavior:**
  * Expected: The broadcast should complete successfully.
  * Actual: The broadcast was not completed.

### 3. Root Cause & Solution

* **Root Cause:**
  * An Out Of Memory (OOM) condition occurred within the MAAC platform. This was likely due to inefficient memory handling during high-volume operations.
* **Solution:**
  * A fix was implemented and released to address the OOM issue. The solution has been verified with a million-level broadcast, and no recurrence of the issue has been observed.

***

## Investigation of User Inability to Select "Match Any Condition" in Segment

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2026-01-21
* **Asana Task ID:** [1212890498554108](https://app.asana.com/1/1184020052539844/task/1212890498554108)
* **Ticket Priority:** P1 - Very High
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The user reported an issue with the MAAC segmentation feature where they were unable to filter using the "Match Any Condition" option. When attempting to click on the "Match All Conditions" option, the interface would unexpectedly close or reset.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: \[REDACTED\_UUID]
  * Occurrence Time: Not specified
  * Feature ID: Not provided
* **Reproduction Steps:**
  1. Navigate to the MAAC segmentation feature.
  2. Attempt to select "Match Any Condition."
  3. Observe the interface behavior when clicking "Match All Conditions."
* **Expected vs Actual Behavior:**
  * **Expected:** The interface should allow selection of "Match Any Condition" without interruption.
  * **Actual:** The interface resets or closes unexpectedly upon interaction.

### 3. Root Cause & Solution

* **Root Cause:** A system bug was identified by the engineering team, which caused the UI element to become unresponsive upon interaction.
* **Solution:** A fix was implemented and deployed to the production environment, resolving the issue.

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
  * MAAC org id: 5722
  * MAAC bot/channel ID: 4619
  * Occurred on: 2026-01-16
* **Reproduction Steps:**
  * The issue was reproducible for both L1 and L4 customers.
* **Expected vs Actual Behavior:**
  * **Expected:** Users should be able to edit unexpired prizes.
  * **Actual:** The edit icon was missing, preventing edits.
* **Additional Information:**
  * The issue was confirmed by customer service and could be consistently reproduced.

### 3. Root Cause & Solution

* **Root Cause:** A recent code deployment introduced a regression error, causing the edit functionality/icon for unexpired prizes to disappear.
* **Solution:** The edit functionality/icon has been restored and deployed to the production environment. The issue is now resolved.

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

Attempts to update the segment on both the client and server sides resulted in the last updated date and time displaying as 2026-01-12 14:48. The MAAC UI status did not change to "Calculating" and remained as "Ready." Additionally, the exported CSV of the segment did not include approximately 300 users added on the same day.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 80
  * MAAC bot ID: 79
  * Feature ID: 1664
  * Segment name: 【1】14日以内に友だち追加
  * Issue occurrence: 2026/01/12 14:50 onwards
  * Reproducibility: Yes, on the client's MAAC UI
  * Testing: Updating a segment on the Demo JP account worked as expected
* **User Questions:**
  * Why does the segment update not reflect the new users added today?
* **Reproduction Steps:**
  1. Attempt to update the segment on both client and server sides.
  2. Observe the last updated date and time.
  3. Check the MAAC UI status.
  4. Export the CSV and verify the user list.
* **Expected vs Actual Behavior:**
  * **Expected:** The segment should update to include new users, and the status should change to "Calculating."
  * **Actual:** The segment did not update with new users, and the status remained "Ready."

### 3. Root Cause & Solution

* **Root Cause:** An interface error corrupted parameter calls for manual updates on segments containing exclusion conditions, preventing the API execution. The core segment calculation logic was not affected.
* **Solution:** A production fix has been deployed to correct the interface's parameter call mechanism for segment updates. Manual updates now function correctly.

***

## How to Resolve Unexpected Errors When Filtering Contacts by Tag

**Metadata**

* **Feature:** MAAC-Contact
* **Created At:** 2026-01-08
* **Asana Task ID:** [1212706004501952](https://app.asana.com/1/1184020052539844/task/1212706004501952)
* **Ticket Priority:** P1 - Very High
* **Client Name:** N/A
* **Resolution Owner:** George
* **Result Breakdown:** Fix Problems

### 1. Issue Description

Users encountered an "An unexpected error occurred, please try again later" message when filtering contacts by any tag without channel selection.

### 2. Context & Details

* The issue occurs when users attempt to filter contacts by any tag without selecting a channel.
* The error message displayed is "An unexpected error occurred, please try again later."
* The problem is reproducible across different brands, including IKEA and others.
* Environment details:
  * MAAC org id: 3763
  * MAAC bot/CAAC channel ID: 3143
* The error results in a server error (500) as indicated by the HTML response.

### 3. Root Cause & Solution

**Root Cause:** A newly deployed feature related to contact search introduced a regression, causing the unexpected error when filtering contacts by tag without channel selection.

**Solution:** The issue has been resolved by reverting or patching the problematic deployment. No further action is required. The system should now function as expected without displaying the error message.

***

## Investigation of Contact Syncing Status in Customer Journey

**Metadata**

* **Feature:** MAAC-Contact
* **Created At:** 2026-01-05
* **Asana Task ID:** [1212642516473540](https://app.asana.com/1/1184020052539844/task/1212642516473540)
* **Ticket Priority:** P1 - Very High
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Gideon
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The customer reported that their contact lists displayed numerous contacts in a "syncing" status, which prevented accurate profile display in personalized messages.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 925
  * CAAC channel ID: 867
  * Issue occurred on: 2026/01/05
* **User Actions:**
  * Attempted resolution using the Django Bot to update all members, which did not resolve the issue.
* **Reproduction Steps:**
  * The issue was observed when contacts appeared in a "syncing" status after attempting to refresh.
* **Expected vs Actual Behavior:**
  * Expected: Contacts should display accurate profile information.
  * Actual: Contacts remained in a "syncing" status, affecting the display of personalized messages.

### 3. Root Cause & Solution

* **Root Cause:**
  * A recent change to the hostname, which included adding a trailing dot for DNS optimization, resulted in a DNS mismatch for the LINE API. This mismatch led to SSL certificate verification failures, blocking the synchronization of contact profiles.
* **Solution:**
  * A fix was implemented (PR 10535) to correct the hostname issue. Additionally, a script was executed to re-sync all LINE-type bots, resolving the affected contact profiles.
* **Status:**
  * The issue has been resolved.

***

## Investigation of SSL Certificate Error in Multicast to LINE

**Metadata**

* **Feature:** MAAC-MAAC Open API (except SMS+API)
* **Created At:** 2026-01-05
* **Asana Task ID:** [1212622216483021](https://app.asana.com/1/1184020052539844/task/1212622216483021)
* **Ticket Priority:** P0 - Emergency
* **Client Name:** IKEA
* **Resolution Owner:** Gideon
* **Result Breakdown:** Fix Problems

### 1. Issue Description

Since January 3, multiple multicast messages received a 200 response, but upon checking the push status, an SSLCertVerificationError was encountered. The error indicates a certificate verification failure due to a hostname mismatch.

### 2. Context & Details

* **Environment Conditions:**
  * The issue began on January 3, 2026.
  * Affected service: Multicast to LINE users.
* **Reproduction Steps:**
  * Send multicast messages to LINE.
  * Check the push status.
* **Expected vs Actual Behavior:**
  * **Expected:** Successful message delivery without errors.
  * **Actual:** Messages received a 200 response but failed with an SSL certificate verification error.
* **Error Details:**
  * Error: SSLCertVerificationError due to hostname mismatch.
  * Example timestamps:
    * 2026-01-03 17:00:01.130
    * 2026-01-04 17:00:06.300

### 3. Root Cause & Solution

* **Root Cause:**
  * The issue was due to an infrastructure update that added a trailing dot to hostnames to reduce DNS queries, resulting in a DNS hostname mismatch with LINE hosts.
* **Solution:**
  * The hostname configuration was corrected via code adjustments.
  * Customers are advised to manually resend messages sent between January 2, 17:14, and January 5, 17:00.
  * Future infrastructure changes will include comprehensive end-to-end testing with application engineering to prevent recurrence.

***

## Investigation of Audience Selection Failure in Segmented Broadcast

**Metadata**

* **Feature:** MAAC-Broadcast
* **Created At:** 2025-12-30
* **Asana Task ID:** [1212616856925841](https://app.asana.com/1/1184020052539844/task/1212616856925841)
* **Ticket Priority:** P1 - Very High
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Fix Problems

### 1. Issue Description

In the MAAC segmented broadcast feature, selecting any specific audience segment incorrectly reverted to "All Contacts".

### 2. Context & Details

* **Environment Conditions:**
  * MAAC Organization ID: 277
  * MAAC Bot ID: 504
* **Reproduction Steps:**
  * Attempt to select any audience segment within the MAAC segmented broadcast feature.
  * Observe that the selection reverts to "All Contacts".
* **Expected vs Actual Behavior:**
  * **Expected:** Selecting a specific audience segment should maintain the selection.
  * **Actual:** Selection reverts to "All Contacts" regardless of the chosen segment.
* **Additional Information:**
  * The issue was observed across all MAAC organizations.
  * Initial observations suggested potential browser-specific caching or rendering issues.

### 3. Root Cause & Solution

* **Root Cause:**
  * A front-end bug introduced by a recent update caused the audience selection mechanism to default to "All Contacts".
* **Solution:**
  * A fix for the front-end bug has been developed and deployed to the production environment.
  * Customers experiencing the issue should attempt the selection process again.
  * If the problem persists, customers are advised to clear their browser's cookies and cache, then log back into MAAC to ensure they are loading the updated code.

***

## Investigation of Missing Data in Data Insights Report for December 26 and 27

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2025-12-29
* **Asana Task ID:** [1212601716064139](https://app.asana.com/1/1184020052539844/task/1212601716064139)
* **Ticket Priority:** P1 - Very High
* **Client Name:** N/A
* **Resolution Owner:** David
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The Data Insights Report was missing data for December 26 and December 27, 2025. The report displayed data jumping directly from December 25 to December 28.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org id: 5319
  * MAAC bot id: 4232
* **Reproduction Steps:**
  * Access the Data Insights Report for the specified dates.
  * Observe the absence of data for December 26 and 27.
* **Expected vs Actual Behavior:**
  * **Expected:** Continuous data entries for each day, including December 26 and 27.
  * **Actual:** Data entries skipped from December 25 to December 28.

### 3. Root Cause & Solution

* **Root Cause:** The Airflow DAG responsible for upserting daily report data from BigQuery to PostgreSQL either failed or did not run on December 26 and 27. This resulted in the processed data not reaching the PostgreSQL reporting table.
* **Solution:** Data for December 26 and 27 has been manually backfilled for all affected customers. An alert system will be implemented to monitor for similar Airflow DAG failures to ensure prompt detection and resolution in the future.

***

## Investigation of Game Module Functionality Issues

**Metadata**

* **Feature:** MAAC-Game interaction
* **Created At:** 2025-12-24
* **Asana Task ID:** [1212555118581780](https://app.asana.com/1/1184020052539844/task/1212555118581780)
* **Ticket Priority:** P1 - Very High
* **Client Name:** N/A
* **Resolution Owner:** Gideon
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The Game Module is currently not functioning as expected.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID / CAAC org ID: \[REDACTED]
  * MAAC bot / CAAC channel ID: \[REDACTED]
* **Feature Information:**
  * Occurrence Time: \[REDACTED]
  * Feature ID: \[REDACTED]
  * Reproducibility: \[REDACTED]
* **User Questions:**
  * Can the issue be reproduced?
* **Reproduction Steps:**
  * \[Details not provided]
* **Expected vs Actual Behavior:**
  * Expected: Game Module should function without interruptions.
  * Actual: Game Module is not functioning as expected.

### 3. Root Cause & Solution

* **Root Cause:**
  * The system reached its capacity limit due to a memory shortage, leading to instability and degraded performance.
* **Solution:**
  * System alerts have been implemented to monitor resource usage.
  * An ongoing effort is in place to identify and clear temporary files to prevent future occurrences.
* **Status:**
  * Resolved

***

## Investigation of Security Alert: API Key Allows Data Retrieval Across Regional Endpoints

**Metadata**

* **Feature:** MAAC-MAAC Open API (except SMS+API)
* **Created At:** 2025-12-05
* **Asana Task ID:** [1212296350345951](https://app.asana.com/1/1184020052539844/task/1212296350345951)
* **Ticket Priority:** P1 - Very High
* **Client Name:** \[REDACTED]
* **Resolution Owner:** David
* **Result Breakdown:** Fix Problems

### 1. Issue Description

During API integration testing, it was discovered that a Japan-issued API key could retrieve member data from another brand when using the incorrect endpoint, raising concerns about data handling and security.

### 2. Context & Details

* **Environment Conditions:**
  * Correct endpoint for Japan: `https://api.jp.cresclab.com`
  * Incorrect endpoint used: `https://api.cresclab.com` (Taiwan)
* **User Questions:**
  * Is it expected that a Japan-issued API key can retrieve data from the Taiwan environment?
  * Are API keys designed to exist in both Japan and Taiwan environments?
  * Can duplicate API keys be prevented to enforce environment separation?
* **Reproduction Steps:**
  * Use a Japan-issued API key with the Taiwan endpoint.
* **Expected vs Actual Behavior:**
  * Expected: Data retrieval should be restricted to the Japan environment.
  * Actual: Data was retrieved from the Taiwan environment.

### 3. Root Cause & Solution

* **Root Cause:**
  * The Taiwan and Japan servers shared the same OpenAPI AES key, allowing cross-region token decryption and use.
* **Solution:**
  * Deploy distinct OpenAPI AES keys for new tokens in Taiwan and Japan to prevent future cross-region access.
  * Existing tokens still allow cross-region access; affected clients in Japan must regenerate their API keys.
  * The Customer Success team will communicate with clients regarding key rotation.
* **Status:**
  * New tokens are secured. Client action is required for existing tokens to perform key rotation.

***

## Investigation of Auto-Reply Failure in Multi-Brand System

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-12-04
* **Asana Task ID:** [1212301243601761](https://app.asana.com/1/1184020052539844/task/1212301243601761)
* **Ticket Priority:** P0 - Emergency
* **Client Name:** N/A
* **Resolution Owner:** David
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The auto-reply feature for multiple brands did not receive responses as expected. This issue was observed across several brands, including IKEA, Vitabox, and others.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 58
  * MAAC bot/channel ID: 56
* **Reproduction Steps:**
  * The issue was noted during testing with brands such as IKEA and Vitabox.
* **Expected vs Actual Behavior:**
  * Expected: Auto-replies should be sent and received without delay.
  * Actual: Auto-replies were not received, indicating a failure in the system.
* **Additional Information:**
  * The issue's reproducibility was not confirmed.
  * A report link was provided for IKEA auto-reply: [Report](https://maac.cresclab.com/autoreply/report/864503).

### 3. Root Cause & Solution

* **Root Cause:**
  * The failure was due to unskipped LINE webhooks from a third-party PNP service, which blocked MAAC's webhook workers. This blockage caused a backlog and processing delays, particularly in the TW and TH regions.
* **Solution:**
  * The functionality has been restored. Alert thresholds were adjusted for earlier detection of similar issues. Future research will focus on developing new Celery Worker health check methods to improve system resilience and support automatic recovery.

***

## How to Resolve Download Issues for Monthly Billing Reports

**Metadata**

* **Feature:** Admin Center
* **Created At:** 2025-12-01
* **Asana Task ID:** [1212235978076412](https://app.asana.com/1/1184020052539844/task/1212235978076412)
* **Ticket Priority:** P1 - Very High
* **Client Name:** N/A
* **Resolution Owner:** Jalex
* **Result Breakdown:** Fix Problems

### 1. Issue Description

Multiple customers reported that they were unable to download the monthly billing report from the email links received on 2025/12/01. The download attempt resulted in a brief flash but no file was downloaded.

### 2. Context & Details

* **Environment:**
  * The issue was reported by customers FUJI and Ngern Tid Lor (TH).
  * The problem was observed on 2025/12/01.
* **Reproduction Steps:**
  * Customers attempted to download the billing report by clicking the link in the email.
  * The browser flashed briefly, indicating an attempt to download, but no file appeared.
* **Expected vs Actual Behavior:**
  * **Expected:** Clicking the link should initiate the download of the billing report.
  * **Actual:** The download did not occur, and no file was available.
* **Additional Information:**
  * The issue was reproducible across different clients.
  * Browsers flagged the links as potentially risky, preventing the download.

### 3. Root Cause & Solution

* **Root Cause:**
  * The issue was caused by SendGrid's link tracking feature, which was enabled during the development of the EDM journey. This feature wrapped the report download URLs, leading browsers to flag these links as phishing risks.
* **Solution:**
  * The email tracking feature for the billing report template in SendGrid was disabled.
  * Affected emails were re-sent to clients, allowing successful downloads of the reports.
  * A permanent solution for SendGrid's click tracking is required to prevent future occurrences.

***

## Investigation of Keyword Non-Response During Specific Time Periods

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-12-01
* **Asana Task ID:** [1211891800981593](https://app.asana.com/1/1184020052539844/task/1211891800981593)
* **Ticket Priority:** P0 - Emergency
* **Client Name:** IKEA, NIKE
* **Resolution Owner:** David
* **Result Breakdown:** Fix Problems

### 1. Issue Description

During certain periods, keywords did not trigger responses as expected. The issue was reported to occur on 12/1 between 19:00 and 19:20 and had been observed on previous days as well.

### 2. Context & Details

* **Environment Conditions:**
  * Affected Regions: Taiwan and Thailand
  * Clients: IKEA (MAAC org id: 58, bot: 56), NIKE (MAAC org id: 4378, bot: 3531)
* **User Questions:**
  * Is there an issue with webhook traffic during the specified time?
* **Reproduction Steps:**
  * The issue could not be reproduced as it resolved itself after the initial report.
* **Expected vs Actual Behavior:**
  * Expected: Keywords should trigger auto-reply messages consistently.
  * Actual: Keywords failed to trigger responses during specific periods.

### 3. Root Cause & Solution

* **Root Cause:**
  * Certain LINE webhooks from a third-party PNP service were not properly skipped, causing MAAC's webhook workers to become blocked and temporarily halting the auto-reply functionality.
* **Solution:**
  * The service has fully recovered. Engineering addressed the issue by ensuring problematic webhooks are properly skipped and stabilizing worker load to prevent recurrence. The system design was adjusted to handle such webhooks more effectively.

***

## Investigation of OTP SMS Delivery Failure for IKEA

**Metadata**

* **Feature:** MAAC-SMS+ API
* **Created At:** 2025-11-29
* **Asana Task ID:** [1212223711134869](https://app.asana.com/1/1184020052539844/task/1212223711134869)
* **Ticket Priority:** P1 - Very High
* **Client Name:** IKEA
* **Resolution Owner:** Tracy
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The client reported that OTP verification SMS messages were not being received by any users. This issue is urgent and requires immediate attention.

### 2. Context & Details

* **Environment:**
  * MAAC org ID: 58
  * MAAC bot ID: 56
* **User Questions:**
  * Can the SMS be temporarily sent using an alternative service (e.g., every8d)?
* **Reproduction Steps:**
  * Attempt to send OTP SMS to provided phone numbers.
* **Expected vs Actual Behavior:**
  * Expected: Users receive OTP SMS.
  * Actual: No OTP SMS received by users.

### 3. Root Cause & Solution

* **Root Cause:**
  * The monthly allocated SMS credits from the vendor Sanchu were depleted due to usage exceeding the limit. There is no existing mechanism to alert when credits are low.
* **Solution:**
  * Service was temporarily restored by transferring credits. Future actions include increasing the monthly credit allocation, creating dedicated sub-accounts for critical clients like IKEA, and investigating the Sanchu API for implementing low-credit alerts.

***

## Investigation of Contact Redirection Issue in MAAC

**Metadata**

* **Feature:** MAAC-Contact
* **Created At:** 2025-11-26
* **Asana Task ID:** [1212148679016920](https://app.asana.com/1/1184020052539844/task/1212148679016920)
* **Ticket Priority:** P1 - Very High
* **Client Name:** \[REDACTED]
* **Resolution Owner:** N/A
* **Result Breakdown:** Fix Problems

### 1. Issue Description

When attempting to click on a contact in MAAC, the system redirects to CAAC but fails to display the corresponding conversation window.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC Organization ID: 3598
  * MAAC Bot ID: 3021
  * Issue occurrence date: 2025/11/26
* **User Actions:**
  * Users attempted to switch browsers and clear cookies, but the issue persisted.
* **Reproduction Steps:**
  * The issue could not be reproduced by the Customer Success Manager (CSM).
* **Expected vs Actual Behavior:**
  * Expected: Clicking a contact in MAAC should open the corresponding conversation in CAAC.
  * Actual: The conversation window does not appear upon redirection to CAAC.

### 3. Root Cause & Solution

* **Root Cause:**
  * A recent update related to MAAC contacts resulted in the incorrect transmission of the external Channel ID to CAAC, preventing proper contact identification and conversation linking.
* **Solution:**
  * A fix was deployed to MAAC to ensure the correct external Channel ID is passed to CAAC, resolving the issue.

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

The client reported that the segment filtering did not meet expectations. Specifically, after importing a batch of phone numbers and tagging them with "005P025112501", the segment "005P南區倉儲運輸部" was expected to filter these tagged numbers. However, the calculated segment size was zero.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 5276
  * MAAC bot/channel ID: 4193
  * Issue occurrence date: 11/25
* **User Actions:**
  * Imported a batch of phone numbers.
  * Added the tag "005P025112501" to these numbers.
  * Attempted to filter the segment "005P南區倉儲運輸部" using the tag.
* **Reproduction Steps:**
  1. Import phone numbers.
  2. Tag numbers with "005P025112501".
  3. Filter segment using the tag.
* **Expected vs Actual Behavior:**
  * **Expected:** The segment should include all tagged contacts.
  * **Actual:** The segment calculation resulted in zero members.

### 3. Root Cause & Solution

* **Root Cause:** The issue was related to the development of the WhatsApp Segment (WA Segment) feature. The addition of reachability data triggered an existing system mechanism, resulting in incorrect segment calculation results.
* **Solution:** The engineering team reprocessed and supplemented the data. Most affected segment results have been restored. If issues persist, users should manually click "Update Segment" in MAAC. If abnormalities continue after manual updates, further reporting is necessary. The issue is currently marked as resolved, with data reprocessed; however, some segments may require manual updates.

***

## Investigation of Discrepancy in Segment Filtering Results

**Metadata**

* **Feature:** MAAC-Segment
* **Created At:** 2025-11-25
* **Asana Task ID:** [1212084549273694](https://app.asana.com/1/1184020052539844/task/1212084549273694)
* **Ticket Priority:** P1 - Very High
* **Client Name:** imager 37
* **Resolution Owner:** George
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The client reported that the expected number of contacts in a segment was zero, which was not anticipated. Previously, similar conditions in November yielded results.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 5540
  * MAAC bot/CAAC channel ID: 4457
  * Issue occurred on: 11/25
  * Reproducibility: Yes
* **User Actions:**
  * Attempted to filter segments using specific conditions.
  * Observed zero contacts in the segment despite previous successful results with identical conditions.
* **Reproduction Steps:**
  * Navigate to the segment editing page.
  * Apply the same filter conditions as previously used in November.
* **Expected vs Actual Behavior:**
  * Expected: The segment should display contacts matching the filter conditions.
  * Actual: The segment displayed zero contacts.

### 3. Root Cause & Solution

* **Root Cause:**
  * During the development of the WhatsApp Segment (WA Segment) functionality, the addition of reachability data inadvertently activated a mechanism that caused some segment calculations to result in zero contacts.
* **Solution:**
  * Engineering re-processed the data and recalculated the affected segments.
  * For any segments still showing zero, users should manually click "Update Segment" in the UI.
  * If the issue persists, users are advised to report the specific segment for further investigation.

***

## Investigation of SMS Broadcast Failure with Unknown Error Message

**Metadata**

* **Feature:** MAAC-SMS Broadcast
* **Created At:** 2025-11-20
* **Asana Task ID:** [1212001011314495](https://app.asana.com/1/1184020052539844/task/1212001011314495)
* **Ticket Priority:** P1 - Very High
* **Client Name:** Nespresso
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Product Optimization

### 1. Issue Description

All SMS B broadcasts failed, displaying an "unknown error" message. It is uncertain if this is related to a recent change.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC organization ID: 5107
  * MAAC bot ID: 4048
* **Reproduction Steps:**
  * Attempt to send SMS B broadcast.
  * Observe failure with "unknown error" message.
* **Expected vs Actual Behavior:**
  * **Expected:** SMS B broadcasts are sent successfully.
  * **Actual:** All SMS B broadcasts fail with an error message.
* **Additional Information:**
  * SMS B: 1120\_Advent calendar report (ID: 5624)
  * Related task: [Link to potential related change](https://app.asana.com/1/1184020052539844/project/1201173638593204/task/1211975735028735?focus=true)

### 3. Root Cause & Solution

* **Root Cause:**
  * The MAAC UI for SMS broadcast subject field displayed a 40-character limit based on design specifications. However, the actual backend system imposed a 15-character limit for SMS subjects. Messages with subjects longer than 15 characters passed UI validation but failed during dispatch.
* **Solution:**
  * The MAAC UI was updated to correctly reflect and enforce the 15-character limit for SMS broadcast subjects. No further action is required.

***

## Investigation of Message Format Support for Line Breaks in SMS/MMS

**Metadata**

* **Feature:** MAAC-SMS Broadcast
* **Created At:** 2025-11-18
* **Asana Task ID:** [1211975735028735](https://app.asana.com/1/1184020052539844/task/1211975735028735)
* **Ticket Priority:** P1 - Very High
* **Client Name:** Nespresso
* **Resolution Owner:** Jalex
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The MMS broadcasts sent from MAAC did not display line breaks for recipients, despite being present in previews.

### 2. Context & Details

* **Environment Conditions:**
  * Broadcast ID: 5586
  * API Endpoint: `https://api.cresclab.site/rubato/sms/[REDACTED_PATH]`
* **User Questions:**
  * Does MMS/SMS support line breaks?
* **Reproduction Steps:**
  * Send a broadcast message with line breaks (`\n`) included in the text.
  * Verify the message preview displays line breaks correctly.
  * Observe the actual message received by the client lacks line breaks.
* **Expected vs Actual Behavior:**
  * **Expected:** Line breaks should appear in the message as they do in the preview.
  * **Actual:** Line breaks are not present in the received message.

### 3. Root Cause & Solution

* **Root Cause:**
  * The MAAC message dispatch system (MDS) incorrectly converted line breaks (`\n`) to a specific character (`\u0006`) for all Mitake messages. Mitake's MMS API requires `\n` directly, unlike its SMS API.
* **Solution:**
  * MDS was updated to send `\n` characters directly for MMS broadcasts to Mitake, ensuring line breaks are now rendered correctly. The issue has been fixed and verified.

***

## Investigation of MMS Broadcast Sending Failure

**Metadata**

* **Feature:** MAAC-Broadcast
* **Created At:** 2025-11-18
* **Asana Task ID:** [1211975735028717](https://app.asana.com/1/1184020052539844/task/1211975735028717)
* **Ticket Priority:** P1 - Very High
* **Client Name:** Nespresso
* **Resolution Owner:** Tracy
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The MMS broadcast failed to send. The failure reason identified in Django was "SMS vendor \[MMS\_MITAKE] does not exist", associated with broadcast ID 5583. It is suspected that the system failed to create the broadcast ID, resulting in the issue. Three broadcasts failed in total.

### 2. Context & Details

* **Environment Conditions:**
  * The issue was observed in the Django system logs.
  * Three separate broadcast attempts failed.
* **Reproduction Steps:**
  * Attempt to send an MMS broadcast using the system.
  * Observe the failure message in the Django logs.
* **Expected vs Actual Behavior:**
  * **Expected:** MMS broadcasts should be sent successfully.
  * **Actual:** MMS broadcasts failed with a vendor non-existence error.

### 3. Root Cause & Solution

* **Root Cause:** The root cause was identified as a system configuration issue where the SMS vendor configuration for MMS\_MITAKE was missing or incorrect.
* **Solution:** The configuration issue was immediately resolved. It is recommended that Product/Engineering teams investigate whether this is an isolated incident or if it indicates a broader configuration problem. Consider implementing stricter validation or better default settings to prevent recurrence.

The issue has been resolved for the client, but an internal review is pending to ensure no further occurrences.

***

## Investigation of Rich Menu Switching Failure in Customer Journey

**Metadata**

* **Feature:** MAAC-Richmenu
* **Created At:** 2025-11-14
* **Asana Task ID:** [1211943794872288](https://app.asana.com/1/1184020052539844/task/1211943794872288)
* **Ticket Priority:** P1 - Very High
* **Client Name:** 新東陽
* **Resolution Owner:** Jalex
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client's rich menu was not displaying as expected. Both default and bound menus failed to appear, even after blocking and unblocking the user.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC organization ID: 6323
  * MAAC bot ID: 6331
  * LINE API URL: `https://api.line.me/v2/bot/richmenu/list`
  * Access token obtained via CSM helper
* **User Questions:**
  * Why are the rich menus not appearing on LINE despite being configured in MAAC?
* **Reproduction Steps:**
  1. Configure rich menus in MAAC.
  2. Attempt to view menus on LINE platform.
  3. Observe that menus do not appear, even after user blocking and unblocking.
* **Expected vs Actual Behavior:**
  * **Expected:** Rich menus should display on LINE as configured in MAAC.
  * **Actual:** Rich menus do not display on LINE.

### 3. Root Cause & Solution

* **Root Cause:**
  * The rich menus were successfully registered with LINE via MAAC. However, they were unexpectedly deleted or deactivated on LINE's platform, likely due to an external issue with LINE.
* **Solution:**
  * The client paused and re-scheduled the rich menu in MAAC, which resolved the issue. This incident has occurred before and may recur. No specific action is required from our engineering team beyond monitoring.

***

## How to Address Delays in Journey Trigger Execution

**Metadata**

* **Feature:** MAAC-Customer Journey
* **Created At:** 2025-10-31
* **Asana Task ID:** [1211802228845406](https://app.asana.com/1/1184020052539844/task/1211802228845406)
* **Ticket Priority:** P0 - Emergency
* **Client Name:** N/A
* **Resolution Owner:** David, Aaren
* **Result Breakdown:** Fix Problems

### 1. Issue Description

MAAC journey members experienced a delay of approximately 30 minutes in triggering their next action.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC organization and channel IDs were involved.
  * The issue was reported to occur at a specific time but details were not provided.
* **Reproduction Steps:**
  * The ability to reproduce the issue was not confirmed.
* **Expected vs Actual Behavior:**
  * Expected: Immediate triggering of journey actions.
  * Actual: A delay of about 30 minutes was observed.

### 3. Root Cause & Solution

* **Root Cause:**
  * A temporary backlog occurred in MAAC's journey processing queue, leading to delayed execution of scheduled actions for members.
* **Solution:**
  * MAAC journey processing resources were scaled to clear the backlog. Further investigation is underway to identify the root cause of the queue buildup and implement preventive measures to ensure timely journey execution. Monitoring is in place to ensure the issue does not recur.

***

## Investigation of Broadcast Status Remaining "Scheduled" After Scheduled Time

**Metadata**

* **Feature:** MAAC-Broadcast
* **Created At:** 2025-10-24
* **Asana Task ID:** [1211737448741603](https://app.asana.com/1/1184020052539844/task/1211737448741603)
* **Ticket Priority:** P1 - Very High
* **Client Name:** Izumi
* **Resolution Owner:** David
* **Result Breakdown:** Fix Problems

### 1. Issue Description

MAAC broadcasts scheduled for 9 AM JST on 2025/10/24 experienced a significant delay (30-60 minutes) in actual delivery and status update from "Scheduled" to "Sent".

### 2. Context & Details

* **Environment Conditions:**
  * Scheduled broadcast time: 2025/10/24, 9 AM JST
  * Affected organization IDs: 110, 121, 124, 127
  * Broadcast name: 25/10/24配信
* **Reproduction Steps:**
  * Schedule a broadcast for a specific time.
  * Observe the status remaining "Scheduled" past the scheduled time.
* **Expected vs Actual Behavior:**
  * **Expected:** Broadcasts should be sent and status updated to "Sent" immediately after the scheduled time.
  * **Actual:** Broadcasts were delayed by 30-60 minutes before being sent and status updated.

### 3. Root Cause & Solution

* **Root Cause:** A temporary system incident affected broadcast delivery during the specified time.
* **Solution:** The engineering team identified and immediately resolved the temporary system incident. All affected broadcasts were successfully delivered. Under normal conditions, broadcast sending time varies by segment size (e.g., 10K-50K contacts typically <5 mins), and the status updates immediately upon completion of sending. The issue has been resolved.

***

## Investigation of Identical Data Across Different Time Ranges in Journey Reports

**Metadata**

* **Feature:** MAAC-Customer Journey
* **Created At:** 2025-10-16
* **Asana Task ID:** [1211658874580583](https://app.asana.com/1/1184020052539844/task/1211658874580583)
* **Ticket Priority:** P1 - Very High
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Gideon, JY
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The Journey Report and Channel Performance data in MAAC displayed identical results regardless of the selected time range.

### 2. Context & Details

* **Journey Name:** Y25MA\_W4\_GoldenRetriever5M
* **Data URLs:**
  * [Data for 03/30 - 10/16](https://app.asana.com/app/asana/-/get_asset?asset_id=1211658874580587)
  * [Data for 09/01 - 09/30](https://app.asana.com/app/asana/-/get_asset?asset_id=1211658874580589)
  * [Data for 03/30 - 08/31](https://app.asana.com/app/asana/-/get_asset?asset_id=1211658874580591)
* **Client Inquiry:** The agency requested clarification on why data remained the same across different time filters.
* **Environment Details:**
  * MAAC org ID: 3315
  * MAAC bot/channel ID: 2828
* **Occurrence Date:** 2025/10/16
* **Reproducibility:** Not specified

### 3. Root Cause & Solution

* **Root Cause:** The API endpoint `/journey/v2/journey/:id/report/`, responsible for providing data to both the Journey Report Overview and Channel Performance sections, was returning incorrect data.
* **Solution:** The backend API `/journey/v2/journey/:id/report/` has been corrected. No further action is required for this issue. The status was resolved on 2025/10/17.

***

## Investigation of Message Delivery Failure in Customer Journey

**Metadata**

* **Feature:** MAAC-Customer Journey
* **Created At:** 2025-10-09
* **Asana Task ID:** [1211594862619415](https://app.asana.com/1/1184020052539844/task/1211594862619415)
* **Ticket Priority:** P1 - Very High
* **Client Name:** OHHER
* **Resolution Owner:** JY, Aaren
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The automated journey with ID 46606 failed to deliver LINE messages to any recipients.

### 2. Context & Details

* **Environment Conditions:**
  * Automated journey ID: 46606
  * Start time: 10/9 9:19
  * Trigger: Tag applied -- shopline\_bind\_success
  * LINE message node ID: 243893
  * Reward: Membership application bonus $150
  * Wait period: 15 days before sending another LINE message
* **Reproduction Steps:**
  1. Initiate the automated journey.
  2. Apply the tag `shopline_bind_success`.
  3. Observe the failure in sending LINE messages.
* **Expected vs Actual Behavior:**
  * **Expected:** LINE messages should be sent to recipients as part of the journey.
  * **Actual:** No recipients received the LINE messages.

### 3. Root Cause & Solution

* **Root Cause:**
  * The 'Send LINE Message' node (ID 243893) was missing a channel link. A backward compatibility bug between 9/30 and 10/7 prevented the channel ID from being saved during node creation or duplication.
* **Solution:**
  * The affected node's channel ID was manually updated.
  * Frontend and backend fixes are planned for all 'Send LINE Message' nodes, along with Tier 2 data migration before release.
  * Past 15 contacts were compensated by the client, and their status was canceled. New entries now receive messages as expected.
* **Status:**
  * The issue is resolved for new entries. A long-term fix is planned.

***

## Investigation of Internal Server Error on Journey Report Page

**Metadata**

* **Feature:** MAAC-Customer Journey
* **Created At:** 2025-09-15
* **Asana Task ID:** [1211357485563476](https://app.asana.com/1/1184020052539844/task/1211357485563476)
* **Ticket Priority:** P1 - Very High
* **Client Name:** 財團法人羅慧夫顱顏基金會-羅慧夫顱顏基金會
* **Resolution Owner:** Yio, David
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The Journey Report page displays an 'internal server error' when accessed. This error prevents the display of report data. The issue is reproducible for the client 羅慧夫 but not for other bots.

### 2. Context & Details

* **Environment Conditions:**
  * Occurred on 2025-09-15 at 11:52.
  * Affects multiple client accounts, including 羅慧夫, 國泰, and 天下網路書店.
* **Reproduction Steps:**
  * Access the Journey Report page for journeys with a sleep-time setting.
* **Expected vs Actual Behavior:**
  * Expected: Report data should display correctly.
  * Actual: 'Internal server error' is shown, and data is not displayed.
* **Additional Information:**
  * The issue is reproducible for the client 羅慧夫.
  * The underlying journey data continues to function without disruption.

### 3. Root Cause & Solution

* **Root Cause:**
  * A recent deployment introduced a change in data format.
  * The 'sleep-time' field was returned in an unexpected format, causing errors during data processing on the Journey Report page.
* **Solution:**
  * Correct the data format handling within the deployment.
  * Update the system to correctly process the 'sleep-time' field format, ensuring accurate data display on the Journey Report page.

***

## Investigation of SMS Broadcast Failure Due to Sensitive Keywords

**Metadata**

* **Feature:** MAAC-SMS Broadcast
* **Created At:** 2025-09-15
* **Asana Task ID:** [1211355249719848](https://app.asana.com/1/1184020052539844/task/1211355249719848)
* **Ticket Priority:** P1 - Very High
* **Client Name:** One Boy
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

An SMS broadcast failed to send because the SMS provider blocked the message due to sensitive keywords.

### 2. Context & Details

* **Environment:** The issue occurred during a holiday SMS broadcast.
* **User Question:** The client was unable to determine which keywords were flagged as sensitive.
* **Reproduction Steps:**
  * An SMS was sent containing the phrase "版本更新" (Version Update).
  * The SMS was blocked by the provider.
* **Expected Behavior:** The SMS should have been sent successfully.
* **Actual Behavior:** The SMS was blocked due to sensitive keywords.

### 3. Root Cause & Solution

* **Root Cause:** The SMS content included the phrase "版本更新" (Version Update), which the third-party SMS provider (Sanzhu) flagged as sensitive, leading to message rejection. The provider's keyword library is not available to us.
* **Solution:** The customer was informed of the blocked keywords. It is advised that customers review content for potentially sensitive terms when creating SMS broadcasts.

***

## Investigation of Prize Display Errors in Lucky Draw Feature

**Metadata**

* **Feature:** MAAC-Game interaction
* **Created At:** 2025-09-10
* **Asana Task ID:** [1211312393419626](https://app.asana.com/1/1184020052539844/task/1211312393419626)
* **Ticket Priority:** P1 - Very High
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Aaren
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The system displayed incorrect messages during a lucky draw event. Specifically, after drawing a prize, the system indicated that the prize was out of stock, despite the prize still being available. Additionally, when a user drew a 'no prize' result, the system incorrectly displayed "Prizes exhausted" instead of the intended "No prize" message.

### 2. Context & Details

* **Environment Conditions:**
  * Event: Lucky Draw - Invite Friends to Draw LINE POINTS\_test (id: 6587)
  * Prize 1: 10 points, Code: PO34XHTAYU7CKDBB, Quantity: 666
  * Prize 3: 10 points, Quantity: 667
  * Prize 5: 10 points, Quantity: 666
  * Prizes 2, 4, 6: No prize
* **User Questions:**
  * Why does the system show "Prizes exhausted" when a prize is still available?
  * Why does the system show "Prizes exhausted" instead of "No prize"?
* **Reproduction Steps:**
  1. Participate in the lucky draw event.
  2. Draw a prize or a 'no prize' result.
* **Expected vs Actual Behavior:**
  * Expected: Display "No prize" when no prize is won.
  * Actual: Displayed "Prizes exhausted" when no prize was won.

### 3. Root Cause & Solution

* **Root Cause:**
  * The backend logic for the lucky draw feature mistakenly interpreted 'no prize' configurations as 'prizes exhausted'. This was due to 'no prize' options implicitly having a quantity of 0, which the previous logic incorrectly treated as an exhausted prize. The system did not properly differentiate between a true 'prizes exhausted' scenario and a 'no prize' outcome.
* **Solution:**
  * The backend logic for determining lucky draw results was adjusted. The system now differentiates 'no prize' outcomes by checking for the absence of a prize\_setting\_id in the detail field, rather than solely relying on a prize quantity of 0.
  * The adjustment has been deployed.
  * Client verification confirmed the issue is resolved.

***

## Investigation of Prize Redemption Failure in Rapid Referral Campaign

**Metadata**

* **Feature:** MAAC-Prize management
* **Created At:** 2025-09-05
* **Asana Task ID:** [1211256941142756](https://app.asana.com/1/1184020052539844/task/1211256941142756)
* **Ticket Priority:** P1 - Very High
* **Client Name:** NA Bakery
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Fix Problems

### 1. Issue Description

During a live demonstration, a client successfully invited a contact and was eligible to redeem an IceCream Brand Coupon. However, upon clicking "Redeem" on the event page, the coupon was not sent. The client inquired whether this issue was specific to the 'Brand Coupon' type or affected all prize types, as previous attempts with other coupons were successful.

### 2. Context & Details

* **Environment:**
  * MAAC org ID: 6016
  * MAAC bot/channel ID: 5320
* **Reproduction Steps:**
  1. Set up a referral campaign with the IceCream prize as a Brand Coupon.
  2. Invite one contact to redeem the prize.
  3. Click "Redeem" after a successful invite.
* **Expected vs Actual Behavior:**
  * Expected: The IceCream prize should be sent immediately after redemption.
  * Actual: The prize was not triggered after redemption. It was observed at a later time, triggered by an Auto Reply mechanism, not the Rapid Referral campaign.

### 3. Root Cause & Solution

* **Root Cause:** The prize message template for Rapid Referral campaigns incorrectly included an empty 'hero' section (missing image URL and aspect ratio) when no image was uploaded. This caused a LINE Flex Message API validation error. Unlike other features such as Auto-reply or Broadcast, the Rapid Referral flow did not remove this invalid 'hero' section.
* **Solution:** The engineering team implemented a fix to ensure the 'hero' section is correctly removed from prize message templates in Rapid Referral campaigns when no image is present.

***

## Investigation of Zero Click Counts in Broadcast Messages

**Metadata**

* **Feature:** MAAC-Broadcast
* **Created At:** 2025-08-11
* **Asana Task ID:** [1211018948239687](https://app.asana.com/1/1184020052539844/task/1211018948239687)
* **Ticket Priority:** P1 - Very High
* **Client Name:** \[REDACTED]
* **Resolution Owner:** JY
* **Result Breakdown:** Fix Problems

### 1. Issue Description

Broadcast messages sent between 2025-08-06 22:14:48 and 2025-08-11 11:43:07 (UTC+8) for specific clients displayed zero click counts in reports, despite registered links and actual user clicks.

### 2. Context & Details

* **Environment Conditions:**
  * Affected clients include Searchome, GOYOMONEY, and DK Marketing. OHCHA was likely unaffected.
  * MAAC org id: 3771
  * MAAC bot/channel ID: 3147
* **User Questions:**
  * Why are the click counts for multiple broadcast messages showing as zero?
* **Reproduction Steps:**
  * Send broadcast messages with embedded links.
  * Check the reports for click counts.
* **Expected vs Actual Behavior:**
  * **Expected:** Click counts should reflect actual user interactions with the links.
  * **Actual:** Reports show zero click counts despite user engagement.

### 3. Root Cause & Solution

* **Root Cause:**
  * A system update, activated via a feature flag, introduced a bug in the short URL tracking mechanism for Broadcast Messages. The system erroneously created new, untracked short URLs instead of utilizing the original ones, resulting in no recorded click data.
* **Solution:**
  * The problematic feature flag was disabled on 2025-08-11 11:43:07 (UTC+8), resolving the issue for all new broadcasts.
  * For historical affected broadcasts, data recovery is possible by manually identifying the actual sent short URLs from the Message Data Storage (MDS) and executing a data re-aggregation process.

***

## Investigation of Delay in Receiving LINE Webhook Forward

**Metadata**

* **Feature:** MAAC-MAAC Open API Webhook
* **Created At:** 2025-08-07
* **Asana Task ID:** [1210984742721782](https://app.asana.com/1/1184020052539844/task/1210984742721782)
* **Ticket Priority:** P1 - Very High
* **Client Name:** Krungsri Auto
* **Resolution Owner:** JY, Jalex
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The ticket management vendor reported experiencing intermittent delays in receiving the LINE webhook forward from CL. On August 4th, a delay of approximately 5 minutes was noted, impacting their SLA performance. The vendor requested an investigation into potential abnormalities with the webhook forwarding or if such delays are expected under normal circumstances.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 5443
  * MAAC bot: 4329
  * Incident occurred on August 4th at 11:45 AM (BKK time)
* **User Questions:**
  * Was there any abnormality with the webhook forwarding at the reported time?
  * Are occasional delays expected under normal circumstances?
* **Reproduction Steps:**
  * The issue appears to occur intermittently and is not consistently reproducible.
* **Expected vs Actual Behavior:**
  * Expected: Immediate receipt of LINE webhook forwards.
  * Actual: Delays of approximately 5 minutes were experienced.

### 3. Root Cause & Solution

* **Root Cause:**
  * The system's auto-scale mechanism was not sufficiently sensitive to traffic fluctuations, causing events to be queued and delivered with delays during peak periods. This was despite previous scaling of MDS resources.
* **Solution:**
  * The team is optimizing the MDS auto-scale mechanism to enhance its sensitivity and prevent future backlogs and delays. Following the initial resource adjustment after the August 4th incident, the average delay was reduced to 5 seconds, with a worst-case scenario of approximately 50 seconds. Further optimization efforts are ongoing.

***

## Investigation of Missing LINE UIDs in MAAC Contact Update

**Metadata**

* **Feature:** MAAC-Contact
* **Created At:** 2025-05-09
* **Asana Task ID:** [1210198750130352](https://app.asana.com/1/1184020052539844/task/1210198750130352)
* **Ticket Priority:** P1 - Very High
* **Client Name:** Krungsri Simple
* **Resolution Owner:** JY
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client identified that four LINE UIDs were missing from the MAAC system. During a registration campaign using the LIFF registration page integrated into the MAAC rich menu, the MAAC API failed to update these contacts. The UIDs were not found in the MAAC database, despite being active contacts retrievable via the LINE API.

### 2. Context & Details

* **Environment Conditions:**
  * The registration campaign was conducted using the LIFF registration page within the MAAC rich menu.
  * The client confirmed exclusive promotion through the MAAC rich menu.
* **User Questions:**
  * Why are the LINE UIDs missing from MAAC despite being active contacts?
* **Reproduction Steps:**
  1. Launch the registration campaign via the MAAC rich menu.
  2. Attempt to update contacts using the MAAC API.
* **Expected vs Actual Behavior:**
  * **Expected:** LINE UIDs should be updated and present in the MAAC system.
  * **Actual:** LINE UIDs are missing, leading to failed API updates.
* **Additional Information:**
  * Client's Basic Information:
    * UUID: \[REDACTED\_UUID]
    * MAAC bot / CAAC channel ID: 4421
  * Screenshots or records:
    * Successful retrieval via LINE API.
    * Error encountered when calling MAAC API.

### 3. Root Cause & Solution

* **Root Cause:**
  * The client's webhook forwarding mechanism is unreliable, resulting in event loss. MAAC's webhook response times can occasionally exceed 10 seconds. Some Import API calls initiated by the client may not reach MAAC successfully. MAAC's update API calls may return a 404 error if the contact does not exist.
* **Solution:**
  * The client should utilize the Import Contact API for missing UIDs and implement a retry mechanism or extend the timeout settings for webhook forwarding. The MAAC engineering team will investigate prolonged webhook response times and endpoint errors. The client needs to provide the task\_id and specific error logs for the missing UIDs for further investigation.
* **Status:**
  * The client has adopted the Import Contact API and extended timeout settings. Issues with MAAC response times, endpoint errors, and missing UIDs are under investigation, pending additional data from the client.
