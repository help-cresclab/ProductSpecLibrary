# insight\_asana\_history\_knowledge\_base\_final

## Investigation of Zero Tag Coverage in MAAC Data Insights

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2026-02-09
* **Asana Task ID:** [1213185386062836](https://app.asana.com/1/1184020052539844/task/1213185386062836)
* **Ticket Priority:** P1 - Very High
* **Client Name:** all brands
* **Resolution Owner:** Gideon
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The MAAC data insights displayed zero tag coverage across all brands. Assistance was requested to investigate this anomaly.

### 2. Context & Details

* **Environment Conditions:**
  * Affected across multiple channels: LINE, Web, WhatsApp, EDM, Facebook, Instagram.
  * Issue has been occurring since the morning of the report date.
* **Reproduction Steps:**
  * The issue can be reproduced consistently.
* **Expected vs Actual Behavior:**
  * Expected: Tag coverage metrics should display accurate data.
  * Actual: Tag coverage metrics are showing zero for all brands.

### 3. Root Cause & Solution

* **Root Cause:**
  * The 'report\_membertrenddailyreport' table, which is updated via an Airflow job, did not populate correctly, resulting in zero tag metrics. The root cause of the intermittent failure of the Airflow job is still under investigation.
* **Solution:**
  * The Airflow job was manually re-run to restore current data. Historical data for specific dates (e.g., January 11, December 25, December 28, September 1-9) has been backfilled. An ongoing investigation into the root cause of the Airflow job failure is underway, and a runbook is planned for future occurrences.

***

## Investigation of Discrepancy in Acquired New Contacts Between Deeplink Report and Insight

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2026-01-14
* **Asana Task ID:** [1212791162159401](https://app.asana.com/1/1184020052539844/task/1212791162159401)
* **Ticket Priority:** P4
* **Client Name:** Insurverse
* **Resolution Owner:** Tracy
* **Result Breakdown:** Too costly

### 1. Issue Description

The client observed a discrepancy in the number of acquired new contacts for 2025 between two reports:

* Deeplink Report shows 3,559 new contacts.
* Insight Acquisition shows 4,020 contacts.

The client requested clarification on which report is accurate and reliable.

### 2. Context & Details

* **Client Information:**
  * MAAC org id / CAAC org id: 4811
  * MAAC bot / CAAC channel ID: \[REDACTED]
* **Feature Information:**
  * Happened time: \[REDACTED]
  * Feature ID: \[REDACTED]
  * Reproducibility: \[REDACTED]
* **Reproduction Steps:**
  * Compare the number of new contacts in the Deeplink Report and Insight Acquisition for 2025.
* **Expected vs Actual Behavior:**
  * Expected: Consistent number of new contacts across both reports.
  * Actual: Discrepancy in the number of new contacts reported.

### 3. Root Cause & Solution

* **Root Cause:**
  * The discrepancy arises from the complex logic within the Insight system, which requires significant resources to address.
* **Solution:**
  * Current workaround: Advise clients to refer to the Deeplink page for accurate performance metrics.
  * Future consideration: The product team is evaluating the possibility of hiding incorrect deeplink reports on the Insight page. Further discussions on the scope are necessary.
* **Status:**
  * This is a known issue. The workaround has been communicated to Customer Support. The product team is discussing a long-term solution.

***

## Investigation of Discrepancy in Message Count Between MAAC and LINE OA

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2026-01-13
* **Asana Task ID:** [1212736080583740](https://app.asana.com/1/1184020052539844/task/1212736080583740)
* **Ticket Priority:** P3
* **Client Name:** iHerb
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

On January 7th, there was a significant discrepancy between the number of messages recorded by MAAC and those shown in the LINE OA native dashboard. MAAC displayed 87,616 messages sent, whereas LINE OA showed 148,968 messages. The client expressed concerns due to the usual alignment of message counts on other dates.

### 2. Context & Details

* **Date of Issue:** January 7th
* **MAAC Message Count:** 87,616
* **LINE OA Message Count:** 148,968
* **Client Actions:** The client was informed about the differing definitions of "Push" between MAAC and LINE OA. However, the client remains concerned due to the unusual discrepancy on this specific date.
* **Environment Checks:**
  * No use of automatic journeys, CAAC, or Open API was detected.
  * The client was advised to confirm with LINE OA support if any additional messages were sent.
* **Reproduction Steps:** Not applicable as the issue pertains to historical data.
* **Expected vs Actual Behavior:** Typically, MAAC and LINE OA message counts are closely aligned, but a significant difference was noted on January 7th.

### 3. Root Cause & Solution

* **Root Cause:** MAAC's internal records and analytics consistently indicate that 87,300 messages were sent on January 7th. Engineering confirmed there were no system issues or data discrepancies within MAAC for that date.
* **Solution:** The Customer Success team communicated to the client that MAAC's records consistently show 87,300 messages sent. No system issues were identified within MAAC. The discrepancy appears to be due to differing definitions or reporting methods between MAAC and LINE OA. Further verification with LINE OA support was suggested to the client.
* **Status:** Resolved

***

## Investigation of Sudden Tag Coverage Drop to Zero

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2025-12-29
* **Asana Task ID:** [1212602245683188](https://app.asana.com/1/1184020052539844/task/1212602245683188)
* **Ticket Priority:** P3
* **Client Name:** \[REDACTED]
* **Resolution Owner:** David
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The tag coverage rate in the LINE overview unexpectedly dropped to zero. Despite multiple tags being present in the tag list and no deletions being made by the brand, the data suddenly shows zero coverage.

### 2. Context & Details

* **Environment Conditions:**
  * The issue is observed across multiple brands.
  * The problem can be reproduced consistently.
* **Reproduction Steps:**
  1. Navigate to the LINE overview.
  2. Observe the tag coverage rate displayed as zero.
  3. Verify the presence of multiple tags in the tag list.
* **Expected vs Actual Behavior:**
  * **Expected:** The tag coverage rate should reflect the presence of multiple tags.
  * **Actual:** The tag coverage rate is displayed as zero despite the presence of tags.

### 3. Root Cause & Solution

* **Root Cause:** Data processing and aggregation errors led to incomplete data being recorded or displayed for specific daily breakdowns in the reporting module. This is similar to a previously identified data gap in insight processing.
* **Solution:** Await the resolution of a dependent "insight" processing task (referencing task ID 1212601716064139), which is expected to address this data gap. Verify data completeness after the dependent task is resolved. The status is currently pending, dependent on the resolution of the related task.

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
  * Organization ID: 5319
  * Bot ID: 4232
* **Reproduction Steps:**
  * Access the Data Insights Report for the specified dates.
  * Observe the absence of data for December 26 and 27.
* **Expected vs Actual Behavior:**
  * Expected: Continuous daily data from December 25 through December 28.
  * Actual: Data missing for December 26 and 27, with a direct jump from December 25 to December 28.

### 3. Root Cause & Solution

* **Root Cause:**
  * The Airflow DAG responsible for upserting daily report data from BigQuery to PostgreSQL either failed or did not run on December 26 and 27. This failure prevented the processed data from being written to the PostgreSQL reporting table.
* **Solution:**
  * Data for December 26 and 27 for all affected customers has been manually backfilled.
  * An alert system will be implemented to monitor for similar Airflow DAG failures to ensure prompt detection and resolution in the future.

***

## Investigation of Data Discrepancy in Deeplink Reports

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2025-12-02
* **Asana Task ID:** [1212213023126579](https://app.asana.com/1/1184020052539844/task/1212213023126579)
* **Ticket Priority:** P2
* **Client Name:** 長汎假期
* **Resolution Owner:** Tracy
* **Result Breakdown:** Too costly

### 1. Issue Description

The MAAC "Insight" module displayed incorrect data for "Deeplink" contacts, showing discrepancies when compared to the "Deeplink Report."

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org id: 5398
  * MAAC bot/channel ID: 4295
  * Happened time: 2025/12/02
  * Reproducibility: Yes
* **User Questions:**
  * Why is there a discrepancy between the "Insight" module and the "Deeplink Report"?
* **Reproduction Steps:**
  1. Access the MAAC "Insight" module.
  2. Compare the displayed "Deeplink" contact data with the "Deeplink Report" for the period 2025/10/04 - 2025/10/31.
* **Expected vs Actual Behavior:**
  * Expected: Consistent data between "Insight" and "Deeplink Report."
  * Actual: Inconsistent data, with "Insight" showing outdated contact information.

### 3. Root Cause & Solution

* **Root Cause:**
  * There is a known systemic data inconsistency within the MAAC "Insight" module. This issue is due to a lack of resources for a permanent fix.
* **Solution:**
  * The reported "Insight" data was manually corrected to align with the "Deeplink Report."
  * It is recommended that the product manager considers temporarily hiding the affected "Insight" data until a systemic fix is implemented to prevent further manual adjustments.

Status: The data has been manually corrected; however, the systemic issue remains pending resolution.

***

## Investigation of Discrepancy in Customer ID Binding Rates

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2025-11-27
* **Asana Task ID:** [1212207562464141](https://app.asana.com/1/1184020052539844/task/1212207562464141)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client observed a discrepancy between the number of unique users tagged for "account binding" (773) and the number of new Customer IDs (CIDs) created (260) between 10/28 and 11/13. The expectation was for these numbers to align.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 5319
  * MAAC bot ID: 4232
* **User Questions:**
  * Why is there a significant difference between the tagged users and new CIDs?
* **Reproduction Steps:**
  * Set up automatic processes triggered by the addition of an "account binding" tag.
  * Compare the number of unique users tagged with the number of new CIDs.
* **Expected vs Actual Behavior:**
  * Expected: The number of tagged users and new CIDs should match.
  * Actual: 773 users were tagged, but only 260 new CIDs were created.

### 3. Root Cause & Solution

* **Root Cause:**
  * Internal system checks confirmed that the insight page and contact CID counts are accurate and consistent. The discrepancy likely arises because the "account binding" tag, used to trigger journeys, does not strictly reflect the actual completion or presence of a Customer ID in the system. There is a misalignment between the customer's tag application logic and the system's CID binding logic.
* **Solution:**
  * Confirm the customer's tag application logic aligns with the system's CID binding logic. Adjust the tagging process to ensure it accurately reflects the creation of new CIDs.

***

## Investigation of Data Discrepancy in MAAC Acquisition Dashboard

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2025-11-18
* **Asana Task ID:** [1211976775930269](https://app.asana.com/1/1184020052539844/task/1211976775930269)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Jalex
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The MAAC acquisition dashboard displayed a discrepancy on 2025-11-07, where the Deeplink member count was shown as 160, but the downloaded report indicated only 7 new members and a total of 61 clicks. This inconsistency raised questions about whether it was due to a product definition issue or a UI display error.

### 2. Context & Details

* **Environment Conditions:**
  * Date of discrepancy: 2025-11-07
  * Dashboard shows 160 members
  * Report shows 7 new members and 61 total clicks
* **User Questions:**
  * Is the discrepancy due to a product definition issue or a UI display error?
* **Reproduction Steps:**
  * Access the MAAC acquisition dashboard for 2025-11-07
  * Compare the member count with the downloaded report
* **Expected vs Actual Behavior:**
  * Expected: Consistent member count between dashboard and report
  * Actual: Dashboard shows 160 members, report shows 7 new members

### 3. Root Cause & Solution

* **Root Cause:**
  * The discrepancy is due to the MAAC acquisition dashboard's complex and legacy data pipeline, which incorrectly aggregates Deeplink member data. The precise logic error is currently untraceable.
* **Solution:**
  * The incorrect data for 2025-11-07 on the dashboard was manually corrected.
  * A fundamental fix requires redesigning the entire insight page data architecture, which is planned for future development.
  * Customers should be advised to use the Deeplink report for accurate performance metrics in the interim.

***

## Investigation of Unresponsive "View Send Record" Button in MAAC SMS+ Insight

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2025-10-29
* **Asana Task ID:** [1211780759562084](https://app.asana.com/1/1184020052539844/task/1211780759562084)
* **Ticket Priority:** P2
* **Client Name:** N/A
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The "View Send Record" button on the MAAC SMS+ Insight page was unresponsive, failing to redirect users to the message record page.

### 2. Context & Details

* The issue occurred on the MAAC SMS+ Insight page.
* Clicking the "View Send Record" button did not trigger any action.
* The problem was reproducible across all client environments.
* Attempts to resolve the issue using incognito mode were unsuccessful.
* No specific time or feature ID was provided for when the issue occurred.

### 3. Root Cause & Solution

**Root Cause:** The frontend URL for the "View Send Record" button was incorrectly configured. This was an oversight from previous SMS+ API development.

**Solution:** The incorrect frontend URL was corrected and deployed to production. The button now successfully redirects users from the SMS+ Insight page to the SMS+ Message Record Query page.

***

## Investigation of Incorrect Auto-Reply Name in Weekly Report

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2025-10-21
* **Asana Task ID:** [1211693894670618](https://app.asana.com/1/1184020052539844/task/1211693894670618)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Jack Lee, Jalex
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The client reported that the weekly report displayed an incorrect name for the auto-reply. Although the auto-reply name was updated in mid-September, the report received on 10/20 still showed the old name.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 6148
  * MAAC bot/channel ID: 5874
  * Happened on: 10/20/2025
  * Reproducibility: Yes
* **User Questions:**
  * Why does the weekly report still show the old auto-reply name despite the update?
* **Reproduction Steps:**
  1. Update the auto-reply name in the MAAC system.
  2. Generate and review the weekly report.
* **Expected vs Actual Behavior:**
  * **Expected:** The weekly report should display the updated auto-reply name.
  * **Actual:** The report displayed the old auto-reply name.

### 3. Root Cause & Solution

* **Root Cause:**
  * The issue was identified as a legacy synchronization bug. When the primary name of an auto-reply was updated, its internal "channel setting" name, which is no longer actively used, was not synchronized. The weekly report referenced this unsynced internal name, resulting in outdated information.
* **Solution:**
  * The auto-reply name was manually corrected for the client.
  * A fix was implemented to ensure synchronization of auto-reply name updates across all internal settings. The relevant pull request can be found [here](https://github.com/chatbotgang/rubato/pull/9976).
  * Further actions include auditing and correcting all other existing auto-replies with unsynced names.
* **Status:** Fixed.

***

## Investigation of Non-Unique Click Counts in Broadcast Messages

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2025-10-01
* **Asana Task ID:** [1211518421816701](https://app.asana.com/1/1184020052539844/task/1211518421816701)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported that unique click counts for multiple broadcast messages in September were identical, raising concerns about a potential display bug. Additionally, one broadcast message showed a click count of zero, prompting further investigation into possible display errors.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org: 199
  * MAAC bot: 376
  * Feature ID: \[REDACTED\_UUID]
  * Happened time: 9/30
* **User Questions:**
  * Why do multiple broadcast messages have the same unique click count?
  * Is the zero click count for one broadcast a display bug?
* **Reproduction Steps:**
  * Review broadcast messages from September.
  * Check unique click counts for specified messages.
* **Expected vs Actual Behavior:**
  * **Expected:** Each broadcast message should have a distinct unique click count.
  * **Actual:** Multiple messages showed identical unique click counts, and one message displayed a zero click count.

### 3. Root Cause & Solution

* **Root Cause:**
  * The unique clicks are tracked using GA4 and UTM parameters. The client used the same UTM combination across different broadcasts, leading GA4 to aggregate the data. This is expected behavior for UTM tracking.
* **Solution:**
  * The Customer Success Manager (CSM) confirmed the issue was due to incorrect UTM usage. Clients were advised to use unique UTM parameters for each campaign to ensure separate tracking. The issue was closed after clarification.

***

## Investigation of Zero Tag Coverage on Insight Page for All Brands

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2025-09-22
* **Asana Task ID:** [1211426159186280](https://app.asana.com/1/1184020052539844/task/1211426159186280)
* **Ticket Priority:** P2
* **Client Name:** all
* **Resolution Owner:** Leo
* **Result Breakdown:** Limit information

### 1. Issue Description

During the period from 2025-09-01 to 2025-09-09, the Tag Coverage displayed on the Insight Page was zero for all TH accounts.

### 2. Context & Details

* **Environment Conditions:**
  * Affected all TH accounts.
  * Issue observed during the specified date range.
* **Reproduction Steps:**
  * Random checks on TH accounts confirmed the zero Tag Coverage.
* **Expected vs Actual Behavior:**
  * Expected: Tag Coverage should display accurate data.
  * Actual: Tag Coverage displayed as zero.
* **Additional Information:**
  * Clients Basic Information: MAAC org id / CAAC org id, MAAC bot / CAAC channel ID.
  * Feature Information: Happened time, Feature ID.
  * Reproducibility: Not specified.
  * Screenshots or screen records were provided.

### 3. Root Cause & Solution

* **Root Cause:** An oversight occurred during a member health data pipeline rerun from 2025-09-01 to 2025-09-10, leading to incorrect historical Tag Coverage. The product logic was verified to be correct.
* **Solution:** The issue has been resolved, and the current data is accurate. There is no plan to correct the historical data for the affected period. Customers are advised to refer to recent data. The incident has been documented internally.

***

## Investigation of Discrepancy in Customer ID Binding Rate on MAAC LINE Overview

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2025-09-15
* **Asana Task ID:** [1211358426495869](https://app.asana.com/1/1184020052539844/task/1211358426495869)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The client reported a significant discrepancy in the "Customer ID binding rate" displayed on the MAAC LINE overview for September 10-11. The system showed 7058 new bound contacts, whereas the client's internal data indicated only approximately 1200 new bindings for the same period.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 1732
  * MAAC bot/channel ID: 1411
* **User Questions:**
  * Why is there a discrepancy between the MAAC data and internal records?
* **Reproduction Steps:**
  * Review the "Customer ID binding rate" on the MAAC LINE overview for the specified dates.
* **Expected vs Actual Behavior:**
  * Expected: The number of new bound contacts should match internal records.
  * Actual: MAAC displayed 7058 new bindings, while internal data showed approximately 1200.

### 3. Root Cause & Solution

* **Root Cause:**
  * A bug in the MAAC Insight page caused incorrect reporting of the "bound contacts" metric.
* **Solution:**
  * The bug was fixed on September 11. Historical data could not be re-attributed by day to the original dates, so all previously miscounted or accumulated binding data was consolidated and reflected as an increase on September 11. Data from September 12 onwards is now accurate and aligns with the client's expectations.
* **Actionable Steps:**
  * The Customer Success Manager should communicate this explanation to the client.

***

## Investigation of Membership Binding Anomalies in Data Insights

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2025-09-15
* **Asana Task ID:** [1211356786872970](https://app.asana.com/1/1184020052539844/task/1211356786872970)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Limit information

### 1. Issue Description

Between September 1 and September 10, there was an unexpected negative growth in brand binding data, decreasing from 934,746 to 934,079. On September 11, there was a sudden increase of over 3,000, resulting in a count of 933,306. This fluctuation was unexpected as no adjustments were made to the brand binding process.

### 2. Context & Details

* **Environment Conditions:**
  * The issue was observed in the Data Insights LINE Overview.
  * The client uses the "Update contact" feature for membership binding.
* **User Questions:**
  * Is there a way to investigate the cause of these fluctuations?
  * Could the fluctuations be due to delayed statistics, as experienced in the past?
* **Reproduction Steps:**
  * Review the customer\_id trends in Data Insights daily records.
  * Compare the binding and unbinding behavior over the specified period.
* **Expected vs Actual Behavior:**
  * **Expected:** Consistent daily binding numbers without significant fluctuations.
  * **Actual:** A decrease followed by a sudden increase in binding numbers, not aligning with explicit unbind requests.

### 3. Root Cause & Solution

* **Root Cause:**
  * The "bound contacts" metric in Data Insights likely counts only "valid/active contacts" with a customer\_id. User blocks (unfriending) would reduce "valid/active contacts", explaining the discrepancy from explicit unbind data. The fluctuation on September 11 suggests data update delays or batch processing.
* **Solution:**
  1. Confirm the precise definition of "bound contacts" in Data Insights and if it filters for "valid/active contacts".
  2. Investigate data update mechanisms for "valid/active contacts" and customer\_id counts for potential delays.
  3. If "valid contacts" are indeed counted, communicate that user blocks contribute to the observed discrepancies.

***

## Investigation of Open Rate Hotspot Discrepancies in MAAC Insight

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2025-09-15
* **Asana Task ID:** [1211353841908307](https://app.asana.com/1/1184020052539844/task/1211353841908307)
* **Ticket Priority:** P2
* **Client Name:** 台灣優衣庫有限公司-UNIQLO（2025）
* **Resolution Owner:** JY
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

Uniqlo's MAAC Insight page initially showed open rate hotspots only on Fridays, despite high open rates also occurring on Mondays. This was observed during their initial onboarding period.

### 2. Context & Details

* **Environment Conditions:**
  * Uniqlo sends push notifications regularly on Mondays and Fridays.
  * Observed open rate hotspots were concentrated on Tuesdays and Thursdays.
* **User Questions:**
  * Why are the open rate hotspots not aligning with the push notification schedule?
  * Could there be a delay in data reporting affecting the hotspot display?
* **Reproduction Steps:**
  * Review MAAC Insight data for open rate hotspots.
  * Compare with Uniqlo's internal tracking and Google Analytics data.
* **Expected vs Actual Behavior:**
  * **Expected:** Open rate hotspots should align with the days push notifications are sent (Mondays and Fridays).
  * **Actual:** Hotspots were observed on the following days (Tuesdays and Thursdays).

### 3. Root Cause & Solution

* **Root Cause:**
  * The anomaly was likely due to temporary data accumulation and calibration delays during the early onboarding phase of a new MAAC account.
* **Solution:**
  * The data has since normalized and now accurately reflects open rate hotspots on both Mondays and Fridays. No specific fix was required.
  * Future monitoring will be conducted to identify similar issues with new clients.

***

## Investigation of Mapping Count Recognition Failure for Customer ID

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2025-09-11
* **Asana Task ID:** [1211314354463888](https://app.asana.com/1/1184020052539844/task/1211314354463888)
* **Ticket Priority:** P2
* **Client Name:** Fits corporation
* **Resolution Owner:** Leo
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The client completed importing over 1,500 customer ID entries into contacts on 9/3. However, the MAAC dashboard has not updated the mapping counts of customer IDs since 7/9.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 27
  * MAAC bot ID: 26
* **Reproduction Steps:**
  * Import customer ID information into contacts.
  * Check the MAAC dashboard for updated mapping counts.
* **Expected vs Actual Behavior:**
  * Expected: The MAAC dashboard should reflect updated mapping counts post-import.
  * Actual: The dashboard has not updated since 7/9 despite the import on 9/3.
* **Additional Information:**
  * The issue affects multiple clients on both TW and JP servers.
  * Insight page updated on 9/10 at 0:00, while customer\_id data was logged on 9/8.

### 3. Root Cause & Solution

* **Root Cause:** A minor bug was introduced during a recent Airflow optimization, affecting the display of "Customer ID binding rate" on the MAAC insight page.
* **Solution:** The bug in Airflow was corrected, and affected data processing jobs were re-run. Verification confirmed that data for impacted organizations (MAAC org 5109, org 27) and the specific client is now accurate on the MAAC insight page. The issue is resolved.

***

## Investigation of Auto-Reply Ranking Display in Insight Reports

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2025-09-09
* **Asana Task ID:** [1211298009313561](https://app.asana.com/1/1184020052539844/task/1211298009313561)
* **Ticket Priority:** P2
* **Client Name:** 長汎假期
* **Resolution Owner:** Aaren
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The client observed that the auto-reply rankings in the Insight interaction report displayed only three entries and sought clarification on the cause.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 5398
  * MAAC bot/channel ID: 4295
  * Issue occurrence date: 2025-09-09
* **User Questions:**
  * Why are only three auto-reply rankings displayed in the report?
* **Reproduction Steps:**
  * Access the Insight interaction report.
  * Review the auto-reply rankings section.
* **Expected vs Actual Behavior:**
  * Expected: All configured auto-reply rankings should be displayed.
  * Actual: Only three auto-reply rankings are visible.

### 3. Root Cause & Solution

* **Root Cause:**
  * The backend query for auto-reply engagement data incorrectly included message editor settings. The API response lacked a unique ID, causing the frontend to group distinct message and message editor entries under the same keyword. The product definition excludes message editor data from auto-reply reports.
* **Solution:**
  * The backend logic was updated to exclude message editor data from auto-reply engagement reports. This adjustment ensures accurate auto-reply rankings, aligning with product definitions. Additionally, a separate task is planned for the removal of a related legacy API.
* **Status:**
  * The issue has been resolved and verified.

***

## Investigation of Message Discrepancy Between MAAC and LINE CMS

**Metadata**

* **Feature:** MAAC-Insight
* **Created At:** 2025-09-08
* **Asana Task ID:** [1211285609853706](https://app.asana.com/1/1184020052539844/task/1211285609853706)
* **Ticket Priority:** P2
* **Client Name:** Raipirab
* **Resolution Owner:** David, Leo
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported a significant discrepancy in the number of pushed messages between the MAAC dashboard and LINE CMS for the period of August 5 to September 5, 2025. The MAAC dashboard showed 15,752 messages, while LINE CMS reported 11,666 messages. The client requested clarification on why the MAAC message count was higher and sought guidance on checking the number of reply messages sent from MAAC.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 5338
  * MAAC bot/channel ID: 4248
  * Period: August 5 - September 5, 2025
* **User Questions:**
  * Why is there a discrepancy in message counts between MAAC and LINE CMS?
  * How can the number of reply messages sent from MAAC be verified?
* **Reproduction Steps:**
  * Compare the "Message Pushed" count on the MAAC dashboard with the "Pushed Message" count on LINE CMS for the specified period.
* **Expected vs Actual Behavior:**
  * Expected: The message counts on both platforms should align.
  * Actual: MAAC reported 15,752 messages, while LINE CMS reported 11,666 messages.

### 3. Root Cause & Solution

* **Root Cause:**
  * The discrepancy arises from a definitional difference. MAAC's "Message Pushed" metric includes both push and reply messages, whereas LINE CMS counts only push messages for billing purposes.
* **Solution:**
  * Rename the MAAC dashboard metric from "Message Pushed" to "Total Messages Sent" to accurately reflect the inclusion of both push and reply messages.
  * Consider adding separate metrics for "Push Messages" and "Reply Messages" on the MAAC dashboard for increased clarity.
  * Advise clients to use LINE CMS for billing purposes and MAAC for raw push message data verification.
