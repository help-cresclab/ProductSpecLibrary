# tag\_knowledge\_base\_final

## Why Does the Tag Order Change on the Dashboard When Adjusting Items Per Page?

**Metadata**

* **Feature:** MAAC-Tag
* **Created At:** 2026-01-21
* **Asana Task ID:** [1212896141155033](https://app.asana.com/1/1184020052539844/task/1212896141155033)
* **Ticket Priority:** P3
* **Client Name:** Gucci Thailand
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The ordering of tags on the Tag Manager Dashboard changes unexpectedly when the "items per page" filter is adjusted. Initially, tags are displayed from the highest to lowest number of tagged contacts. However, altering the items per page results in a different first tag being shown.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org id / CAAC org id: 4710
  * MAAC bot / CAAC channel ID: 3759
* **User Questions:**
  * What is the expected behavior for tag ordering when changing the items per page?
  * How can this behavior be explained to clients?
* **Reproduction Steps:**
  1. Access the Tag Manager Dashboard.
  2. Observe the initial tag order based on the number of tagged contacts.
  3. Change the "items per page" filter.
  4. Note the change in the first tag displayed.
* **Expected vs Actual Behavior:**
  * **Expected:** Tags should consistently display from highest to lowest number of tagged contacts, regardless of the items per page setting.
  * **Actual:** The order of tags changes when the items per page filter is adjusted.

### 3. Root Cause & Solution

* **Root Cause:** The backend system paginates tags based on their creation time and then sorts only the tags on the current page by member\_count. This post-pagination sorting leads to perceived order changes when the page size is altered.
* **Solution:** Adjust the sorting logic to apply the member\_count ordering globally before pagination. This ensures a consistent sort order across all pages, regardless of the page size.

***

## How to Resolve Corrupted Tag Names in the MAAC Interface

**Metadata**

* **Feature:** MAAC-Tag
* **Created At:** 2026-01-12
* **Asana Task ID:** [1212742355247023](https://app.asana.com/1/1184020052539844/task/1212742355247023)
* **Ticket Priority:** P3
* **Client Name:** Insurverse
* **Resolution Owner:** Noel
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The tag names in the MAAC interface have become corrupted and are displaying as unreadable characters. This issue affects all users, preventing them from viewing or managing the tags, which disrupts workflow and communication within the MAAC.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 4811
  * Issue affects all users within the organization.
* **Reproduction Steps:**
  * Import CSV files containing Thai characters into the MAAC system.
* **Expected vs Actual Behavior:**
  * **Expected:** Tag names should display correctly in the MAAC interface.
  * **Actual:** Tag names appear as garbled characters, such as "??”????”??\_update08122025".

### 3. Root Cause & Solution

**Root Cause:** The issue arises from importing CSV files containing Thai characters using an incompatible encoding. The MAAC system reads files using UTF-8 encoding, which cannot decode Thai characters correctly, resulting in them being replaced with '?'.

**Solution:**

* Instruct customers to save and import CSV files with UTF-8 encoding to prevent future occurrences.
* The existing garbled tags are separate entities and do not affect pre-existing correct tags or their historical data.
* Customers can delete the garbled tags and re-import them after ensuring the CSV file uses the correct UTF-8 encoding.

***

## Investigation of Contact Tag Order in MAAC Interface

**Metadata**

* **Feature:** MAAC-Tag
* **Created At:** 2025-12-19
* **Asana Task ID:** [1212526242255975](https://app.asana.com/1/1184020052539844/task/1212526242255975)
* **Ticket Priority:** P3
* **Client Name:** \[REDACTED]
* **Resolution Owner:** David
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The customer inquired whether the tags on a contact are displayed in the order they were applied.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org id / CAAC org id: 3169
  * MAAC bot / CAAC channel ID: 2720
* **User Questions:**
  * Are contact tags displayed in the order they were applied?
* **Reproduction Steps:**
  * Access the MAAC interface.
  * Observe the order of tags on a contact.
* **Expected vs Actual Behavior:**
  * **Expected:** Tags should be sorted by acquisition time, newest first.
  * **Actual:** Tags are sorted by their initial application time, newest first.

### 3. Root Cause & Solution

* **Root Cause:**
  * The MAAC interface correctly sorts tags by their initial application time, from newest to oldest. The discrepancy reported by the customer was due to an incomplete dataset in their Metabase, which lacked one tag record. This is not a system issue.
* **Solution:**
  * No bug was found in the MAAC system. The UI behavior is correct. It is necessary to clarify to the customer that the MAAC tag sorting logic is based on the initial application time, sorted from newest to oldest. The system functions as designed.

***

## How to Address Long Loading Times When Deleting Tags

**Metadata**

* **Feature:** MAAC-Tag
* **Created At:** 2025-12-11
* **Asana Task ID:** [1212388613440442](https://app.asana.com/1/1184020052539844/task/1212388613440442)
* **Ticket Priority:** P2
* **Client Name:** 全家便利商店股份有限公司-全家 FamilyMart
* **Resolution Owner:** Leo
* **Result Breakdown:** Task-Ticket

### 1. Issue Description

The client reported that the process of deleting tags takes an excessively long time. They requested assistance in deleting certain tags that are deemed unnecessary.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 998
  * MAAC bot/CAAC channel ID: 869
* **User Questions:**
  * Can assistance be provided to expedite the tag deletion process?
* **Reproduction Steps:**
  * Attempt to delete tags within the MAAC system.
  * Observe prolonged loading times during the deletion process.
* **Expected vs Actual Behavior:**
  * Expected: Tags should be deleted promptly.
  * Actual: Tags take a long time to delete, causing delays.

### 3. Root Cause & Solution

* **Root Cause:**
  * The issue was identified as a system design problem where the CDH direct write was temporarily disabled during the initial tag deletion in MAAC. This prevented the deletion from syncing to CDH, resulting in tags not being fully removed.
* **Solution:**
  * The remaining tags were manually deleted from CDH. Documentation has been provided (CDH Polyrhythmic Wiki) to enable comprehensive, end-to-end tag deletion by the requesting team for future operations. The issue has been resolved.

***

## Investigation of Tagging Failure After Clicking Broadcast Message Card

**Metadata**

* **Feature:** MAAC-Tag
* **Created At:** 2025-12-05
* **Asana Task ID:** [1212314620645881](https://app.asana.com/1/1184020052539844/task/1212314620645881)
* **Ticket Priority:** P2
* **Client Name:** 新莊典華
* **Resolution Owner:** Jalex
* **Result Breakdown:** Fix Problems

### 1. Issue Description

Some users did not receive the expected tags after clicking on broadcast message cards, which prevented them from entering the automated journey to receive messages.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 4434
  * CAAC channel ID: 3574
  * Issue occurred on: 12/5/2025
  * Reproducibility: Yes
* **User Actions:**
  * User Dash clicked the third card but did not receive a tag.
  * User Anina clicked the second card but did not receive a tag.
  * User Dash clicked the first card and received a tag.
* **Expected vs Actual Behavior:**
  * Expected: Users should receive tags upon clicking any broadcast message card.
  * Actual: Tags were not applied consistently, leading to failure in triggering the automated journey.
* **Reproduction Steps:**
  1. User clicks on a broadcast message card.
  2. System should apply the corresponding tag.
  3. User should enter the automated journey.
* **Additional Information:**
  * Journey Report: [Link](https://maac.cresclab.com/journey/report/57262)
  * Broadcast Report: [Link](https://maac.cresclab.com/broadcast/line/report/456739)

### 3. Root Cause & Solution

* **Root Cause:**
  * A synchronization delay existed between the creation/modification of "message\_editor" settings and their associated tag data in the system.
* **Solution:**
  * A fix (PR #10224) has been deployed to production. This ensures immediate synchronization of "message\_editor" keyword settings and correct tag application.
* **Status:**
  * Fixed and verified.

***

## How to Batch Delete Unused Tags in MAAC for Salesforce Data Cleanup

**Metadata**

* **Feature:** MAAC-Tag
* **Created At:** 2025-11-14
* **Asana Task ID:** [1211943713823266](https://app.asana.com/1/1184020052539844/task/1211943713823266)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Leo
* **Result Breakdown:** Task-Ticket

### 1. Issue Description

The client requires the deletion of unused tags in MAAC to facilitate data cleanup in Salesforce. The deletion must occur in MAAC before it can be executed in Salesforce. This process currently requires engineering intervention.

### 2. Context & Details

* The client is performing data cleanup in Salesforce and needs to remove unused tags.
* Tags must first be deleted in MAAC to allow subsequent deletion in Salesforce.
* The task requires engineering support as the current system does not support direct user execution.
* A list of tags to be deleted is provided in a Google Spreadsheet. Only tags marked in column D are to be deleted.
* The deadline for completion is set for November 20th, end of business day.
* Relevant identifiers:
  * MAAC Org ID: 4478
  * Bot ID: 3613
  * UUID: \[REDACTED]

### 3. Root Cause & Solution

**Root Cause:**\
The CDH system does not automatically synchronize tag deletions initiated in MAAC, necessitating manual intervention to maintain data consistency across systems.

**Solution:**

* Manually delete 1064 tags from both MAAC and CDH (including PG DB and BQ commit table).
* Implement future automation to synchronize tag deletions from MAAC to CDH to prevent manual dependencies.

***

## Investigation of Tag Discrepancy Between MAAC and Emarsys

**Metadata**

* **Feature:** MAAC-Tag
* **Created At:** 2025-11-07
* **Asana Task ID:** [1211876667612502](https://app.asana.com/1/1184020052539844/task/1211876667612502)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported a discrepancy between the number of users associated with a specific MAAC tag in the MAAC backend and the count retrieved by Emarsys from BigQuery. The client seeks to understand the cause of this mismatch.

### 2. Context & Details

* **Environment:**
  * MAAC org ID: 3775
  * MAAC bot/channel ID: 3153
* **Tag Information:**
  * MAAC Tag Name: 優惠\_免運活動
  * Tag ID: 694708
* **Reproduction Steps:**
  * Compare user count for the tag in MAAC backend with the count retrieved by Emarsys from BigQuery.
* **Expected vs Actual Behavior:**
  * Expected: User counts should match.
  * Actual: Discrepancy in user counts between MAAC backend and Emarsys's BigQuery results.

### 3. Root Cause & Solution

* **Root Cause:**
  * The discrepancy arises because Emarsys's query includes a time-based filter, whereas MAAC's tag count reflects all contacts with the tag, regardless of time (including both followed and unfollowed contacts).
* **Solution:**
  * The MAAC tag count logic is functioning as designed, providing aggregate counts without time filtering. No changes are required on the MAAC side.
  * Emarsys should be informed that MAAC tag counts are aggregate and not time-filtered. If Emarsys requires matching counts, they should adjust their query to remove the time-based filter.

***

## Investigation of Irregular Tag Synchronization from CAAC to MAAC

**Metadata**

* **Feature:** MAAC-Tag
* **Created At:** 2025-10-31
* **Asana Task ID:** [1211802724129394](https://app.asana.com/1/1184020052539844/task/1211802724129394)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

Tags applied manually in CAAC are inconsistently synchronized to MAAC, where they are attributed as originating from MAAC instead of CDH. This inconsistency affects contact segmentation data.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC enabled: Yes
  * CAAC organization ID: 2101
  * MAAC organization ID: 4433
  * Two-factor authentication enabled: Yes
* **User Questions:**
  * Why are some tags not synchronizing correctly from CAAC to MAAC?
  * Why are tags being attributed to MAAC instead of CDH?
* **Reproduction Steps:**
  1. Apply tags manually in CAAC.
  2. Observe the synchronization behavior in MAAC.
* **Expected vs Actual Behavior:**
  * **Expected:** Tags applied in CAAC should synchronize to MAAC with CDH as the source.
  * **Actual:** Tags appear in MAAC with MAAC as the source, not all tags are synchronized, and synchronization is inconsistent.
* **Affected Tags:**
  * a喜\_追蹤
  * a喜\_已約
  * a喜\_保留
  * a喜\_已訂
  * a喜\_已到流失
  * a喜\_未到流失

### 3. Root Cause & Solution

* **Root Cause:**
  * The manual replication of CAAC tag applications in the MAAC UI is due to a perceived lack of automatic synchronization from CAAC to MAAC via CDH. There may be a misunderstanding regarding the intended cross-platform tag management.
* **Solution:**
  * The Customer Success Manager (CSM) will verify the reasons and workflow for the manual tag application in MAAC.
  * Engineering will investigate the intended functionality of CDH in automatically syncing tags from CAAC to MAAC, ensuring correct source attribution if applicable.
* **Status:** Under investigation.

***

## Investigation of Tag Reappearance in MAAC System

**Metadata**

* **Feature:** MAAC-Tag
* **Created At:** 2025-10-17
* **Asana Task ID:** [1211669157227422](https://app.asana.com/1/1184020052539844/task/1211669157227422)
* **Ticket Priority:** P2
* **Client Name:** 全家便利商店股份有限公司-全家 FamilyMart
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported that after deleting the tag "康康5" on 2025-10-08, it reappeared in the tag list. The client confirmed the deletion was completed but noticed the tag again on a later date.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 998
  * MAAC bot/channel ID: 869
  * Issue occurrence: From 2025-10-08 onwards
* **User Questions:**
  * Is the tag reappearing due to manual re-creation by the client, or is the deletion process incomplete?
  * How can messages be located using the campaign ID for future troubleshooting?
* **Reproduction Steps:**
  * The issue could not be reproduced. After deleting the tag and re-entering the auto-reply, the tag did not reappear.
* **Expected vs Actual Behavior:**
  * Expected: Once a tag is deleted, it should not reappear unless manually recreated.
  * Actual: The tag "康康5" reappeared in the list despite being deleted.

### 3. Root Cause & Solution

* **Root Cause:**
  * System Design: Deleting a tag does not deactivate existing actions (e.g., from old campaigns, pushes, or rich menu links) configured to apply that specific tag ID. When a user interacts with such content, the system re-creates the deleted tag rather than ignoring the action.
* **Solution:**
  * The "康康5" tag was last deleted on 2025-10-29. To prevent future re-creation, the client must identify and update any active old campaigns, pushes, or rich menu links that are configured to apply this tag.
* **Status:** Resolved

***

## Investigation of Discrepancy in Tag List and Deep Link Data

**Metadata**

* **Feature:** MAAC-Tag
* **Created At:** 2025-10-13
* **Asana Task ID:** [1211622605919662](https://app.asana.com/1/1184020052539844/task/1211622605919662)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Limit information

### 1. Issue Description

The client reported a discrepancy between the user count for a specific tag in the tag list and the count attributed to a specific deep link. The client believed the tag was only applied through this deep link, but the numbers did not match.

### 2. Context & Details

* **Environment Conditions:**
  * Tag: Project | Philips Coffee Machine
  * Deep Link ID: 995058
* **User Questions:**
  * Why is there a discrepancy in the user count between the tag list and the deep link data?
* **Reproduction Steps:**
  * Review the tag application history using the provided dashboard links.
  * Check for any additional applications of the tag beyond the specified deep link.
* **Expected vs Actual Behavior:**
  * Expected: The tag should only be applied through deep link 995058.
  * Actual: The tag was applied through multiple sources, including other links.

### 3. Root Cause & Solution

* **Root Cause:**
  * The discrepancy was due to the tag being applied through multiple client operations or links, not solely via the specified deep link. The client independently identified additional sources applying the tag.
* **Solution:**
  * The client successfully identified the root cause of the data discrepancy, confirming it was due to their internal operations. No further action from the product or engineering team is required. The issue is resolved.

***

## Investigation of Tag Addition Delay in MAAC Contact List

**Metadata**

* **Feature:** MAAC-Tag
* **Created At:** 2025-10-07
* **Asana Task ID:** [1211575001403892](https://app.asana.com/1/1184020052539844/task/1211575001403892)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported that after adding tags to filtered contacts in MAAC before a holiday, the tags did not appear when they returned on 10/07. Although the system indicated successful tag creation, the tags were not visible immediately.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC platform used for contact management.
  * Tagging operation performed before a holiday period.
* **User Questions:**
  * How to verify if the tag addition operation was successful?
  * Can the UI be updated to reflect the delay in tag appearance?
* **Reproduction Steps:**
  1. Filter contacts in MAAC.
  2. Add tags to the filtered list.
  3. Observe the system's success message.
  4. Check for the immediate appearance of tags in the UI.
* **Expected vs Actual Behavior:**
  * **Expected:** Tags should appear immediately after the success message.
  * **Actual:** Tags do not appear immediately, leading to user perception of failure.

### 3. Root Cause & Solution

* **Root Cause:**
  * The tagging operations are correctly recorded in the backend, as confirmed by audit logs. The delay is due to an asynchronous process or data synchronization latency between the backend operation and the MAAC user interface. The current UI message does not adequately communicate this delay.
* **Solution:**
  * Engineering should investigate the specific delay mechanism and duration for tag display in MAAC after bulk operations.
  * Update the MAAC UI to provide clearer feedback on tag addition, indicating that tags are being applied and may take time to appear.

***

## Investigation of Unexpected Tag Appearance in MAAC

**Metadata**

* **Feature:** MAAC-Tag
* **Created At:** 2025-10-02
* **Asana Task ID:** [1211528743341634](https://app.asana.com/1/1184020052539844/task/1211528743341634)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported an unexpected situation where a tag named "拉03 deleted\_at 2025-03-09 07:40:51" appeared in their MAAC system. The tag ID is \[REDACTED]. The client was unable to determine the origin of this tag using the Metabase Audit Log.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 73
  * MAAC bot/channel ID: 69
  * Happened on: 10/2
* **User Questions:**
  * Why did the tag "拉03 deleted\_at 2025-03-09 07:40:51" appear in the MAAC system?
* **Reproduction Steps:**
  * The client attempted to trace the tag's origin using the Metabase Audit Log but found no clues.
* **Expected vs Actual Behavior:**
  * Expected: No unexpected tags should appear in the MAAC system.
  * Actual: The tag "拉03 deleted\_at 2025-03-09 07:40:51" appeared unexpectedly.

### 3. Root Cause & Solution

* **Root Cause:**
  * The tag was created via a Messagelink action and immediately soft-deleted on 2025-10-02. It is suspected to be due to user error or an accidental trigger through Messagelink. The origin of the `deleted_at` timestamp within the tag name is not definitively identified.
* **Solution:**
  * The tag was soft-deleted. No specific system bug was identified based on available logs. The client will monitor for future occurrences.

***

## Investigation of Extended Tag Deletion Time in MAAC-Tag

**Metadata**

* **Feature:** MAAC-Tag
* **Created At:** 2025-09-03
* **Asana Task ID:** [1211222283206634](https://app.asana.com/1/1184020052539844/task/1211222283206634)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Too costly

### 1. Issue Description

The client reported that deleting tags takes at least one minute, which they believe is a performance issue. They are concerned about whether this duration is within expected parameters, especially given the large number of tags and contacts involved.

### 2. Context & Details

* **Environment:** The issue occurs in accounts with a large number of contacts and tags, such as FamilyMart.
* **User Questions:** Is the extended duration for tag deletion expected?
* **Reproduction Steps:**
  * Attempt to delete a tag from an account with a large contact base.
  * Observe the loading time, which exceeds one minute.
* **Expected vs Actual Behavior:**
  * **Expected:** Tag deletion should complete in a reasonable time frame.
  * **Actual:** Tag deletion takes over one minute.

### 3. Root Cause & Solution

* **Root Cause:** The system performs checks on all associated contacts when a tag is deleted. For accounts with a large contact base, this process is resource-intensive, leading to extended loading times. This is considered expected behavior for large-scale operations.
* **Solution:** This behavior is an expected performance characteristic for large accounts. No immediate engineering fix is required. Customer Success should manage customer expectations regarding tag deletion duration, especially during bulk operations or tag restructuring.

***

## Investigation of Tag Disappearance After Name Change in Message Module

**Metadata**

* **Feature:** MAAC-Tag
* **Created At:** 2025-06-26
* **Asana Task ID:** [1210638961172045](https://app.asana.com/1/1184020052539844/task/1210638961172045)
* **Ticket Priority:** P2
* **Client Name:** N/A
* **Resolution Owner:** Xander
* **Result Breakdown:** Limit information

### 1. Issue Description

After changing the name of a tag, the tag disappears from the message module editor. This issue specifically affects the Deeplink's new friend message setting.

### 2. Context & Details

* **Environment Conditions:**
  * The issue occurs within the message module editor.
  * It is associated with the Deeplink's new friend message setting.
* **Reproduction Steps:**
  1. Set a tag in the message of Deeplink's new friend message.
  2. Change the name of the tag.
  3. Check the message from Deeplink again.
  4. Observe that the tag has disappeared.
* **Expected vs Actual Behavior:**
  * **Expected:** The tag name should update across all related features without disappearing.
  * **Actual:** The tag disappears from the message module editor after the name change.

### 3. Root Cause & Solution

* **Root Cause:** The root cause is currently under investigation. An initial assessment by the engineering team suggests a general understanding of the problem, but a definitive cause has not yet been identified or documented.
* **Solution:** No immediate solution has been identified or implemented. A comprehensive investigation is required to develop a robust solution for this and related tag management issues. The issue is under investigation and categorized as lower priority, with plans for a comprehensive solution addressing multiple tag-related problems.
