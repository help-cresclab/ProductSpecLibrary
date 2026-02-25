# auto reply\_asana\_history\_knowledge\_base\_final

## Investigation of Auto-Reply Trigger Failure on Facebook Messenger

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2026-02-06
* **Asana Task ID:** [1213145171671763](https://app.asana.com/1/1184020052539844/task/1213145171671763)
* **Ticket Priority:** P2
* **Client Name:** N/A
* **Resolution Owner:** Kade
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client configured an auto-reply by keyword on Facebook Messenger, but it was not triggered as expected. The specific keyword used was 'สนใจ'.

### 2. Context & Details

* **Environment:**
  * MAAC org ID: 5967
  * MAAC bot/CAAC channel ID: 5058
* **Reproduction Steps:**
  * A new contact sends a message containing the keyword 'สนใจ' on Facebook Messenger.
  * The auto-reply is expected to trigger upon the first interaction.
* **Expected vs Actual Behavior:**
  * **Expected:** The auto-reply should trigger immediately upon receiving the keyword from a new contact.
  * **Actual:** The auto-reply does not trigger on the first interaction but only from the second interaction onward.

### 3. Root Cause & Solution

* **Root Cause:** The MAAC system design, in compliance with Meta's policy, blocks keyword auto-replies for new contacts. The recipient type "New Friend" is disabled by default.
* **Solution:** To ensure auto-replies for initial contacts, enable the "Welcome Message for New Friends" feature. This will allow keyword auto-replies to function correctly in subsequent interactions.

The product team has logged this requirement and is currently evaluating the logic. Optimizations are planned for later this year.

***

## Investigation of Message Delivery Failure in Instagram Auto-Reply

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2026-02-05
* **Asana Task ID:** [1213115186501125](https://app.asana.com/1/1184020052539844/task/1213115186501125)
* **Ticket Priority:** P3
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Kade
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The Instagram auto-reply feature fails to trigger on the first keyword input. The auto-reply names affected include:

* "2/4廣告＿我想了解 外輪廓固定 活動價格"
* "2/4廣告＿我想了解 線雕美鼻優惠價格"

### 2. Context & Details

* **Environment:**
  * Channel Type: Instagram
  * MAAC org id: 6542
  * Affected contact id: \[REDACTED\_ID]
* **User Questions:**
  * Why does the auto-reply require two keyword inputs to trigger?
* **Reproduction Steps:**
  1. User inputs a keyword via Instagram Story.
  2. Auto-reply fails to trigger on the first input.
* **Expected vs Actual Behavior:**
  * **Expected:** Auto-reply should trigger on the first keyword input.
  * **Actual:** Auto-reply requires a second input to trigger.

### 3. Root Cause & Solution

* **Root Cause:**
  * MAAC's system logic prevents keyword auto-replies from being sent to new contacts on Meta channels. The "new friend" recipient type is disabled by default for keyword auto-replies, resulting in "Message Replied = false". This is a known product limitation.
* **Solution:**
  * **For Customers:** Utilize the "New Friend Welcome Message" for initial interactions, then guide users to trigger keyword auto-replies for subsequent engagements.
  * **For Product:** Evaluate and optimize the interaction and priority logic between keyword auto-replies and new contact handling.

***

## Investigation of Keyword Case Sensitivity Issue in MAAC Auto-Reply

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2026-02-04
* **Asana Task ID:** [1213109852110296](https://app.asana.com/1/1184020052539844/task/1213109852110296)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Task-Ticket

### 1. Issue Description

The MAAC auto-reply system does not retain user-defined case for keywords during storage, display, or matching. This is a known issue.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 668
  * MAAC bot ID: 642
  * Channel Type: LINE
* **User Questions:**
  * Why are keyword settings not retaining the specified case?
* **Reproduction Steps:**
  * Set a keyword in uppercase.
  * Observe that it is automatically converted to lowercase.
* **Expected vs Actual Behavior:**
  * **Expected:** Keywords should retain the case as set by the user.
  * **Actual:** Keywords are converted to lowercase, affecting storage, display, and matching.

### 3. Root Cause & Solution

* **Root Cause:** The current keyword mechanism in MAAC lacks support for case sensitivity, leading to automatic conversion to lowercase.
* **Solution:**
  * Inform customers that keyword matching is currently case-insensitive.
  * Engineering team to implement case sensitivity for MAAC auto-reply keywords as part of planned optimizations.
  * Status: The issue is confirmed, the customer has been notified, and optimization is planned.

***

## How to Configure Uppercase Keywords in MAAC Auto-Reply

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2026-01-15
* **Asana Task ID:** [1212821276171610](https://app.asana.com/1/1184020052539844/task/1212821276171610)
* **Ticket Priority:** P3
* **Client Name:** N/A
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The unexpected situation reported was that the MAAC auto-reply feature does not allow setting keywords in uppercase.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 5722
  * MAAC bot/channel ID: 4619
* **User Questions:**
  * Is there a restriction on setting uppercase keywords?
  * What are the design considerations if such a restriction exists?
* **Reproduction Steps:**
  * Attempt to set an auto-reply keyword in uppercase.
  * Observe that the keyword is converted to lowercase in the UI.
* **Expected vs Actual Behavior:**
  * **Expected:** Keywords should retain their original casing as entered by the user.
  * **Actual:** Keywords are displayed in lowercase, although functionality remains unaffected.

### 3. Root Cause & Solution

* **Root Cause:**
  * The MAAC backend stores keywords in lowercase, and the UI reflects this stored value. The keyword matching logic is case-insensitive, ensuring that the functionality is not impacted by the casing.
* **Solution:**
  * The MAAC UI will be updated to display the original casing entered by the user. Customers should be informed that the case conversion in the UI does not affect the auto-reply trigger functionality. The UI adjustment is planned, and communication with customers has been completed.

***

## Investigation of Auto-Reply Delays and Failures in Specific Time Intervals

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2026-01-15
* **Asana Task ID:** [1212806889218671](https://app.asana.com/1/1184020052539844/task/1212806889218671)
* **Ticket Priority:** P2
* **Client Name:** Deanston \[REDACTED]
* **Resolution Owner:** JY
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The MAAC auto-reply feature experienced failures and delays in message delivery during specific time intervals. On January 15th, there was no response at 16:56, and a delayed response at 17:06, which was only sent at 17:09.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC Organization ID: 5236
  * MAAC Bot ID: 4165
  * Incident Date: January 15th
  * Recent update to auto-reply feature on the same day
* **User Questions:**
  * Can the issue be reproduced?
* **Reproduction Steps:**
  * Attempt to trigger auto-reply messages during the specified time intervals.
* **Expected vs Actual Behavior:**
  * Expected: Auto-reply messages should be sent immediately upon triggering.
  * Actual: No response at 16:56 and a delayed response at 17:06, sent at 17:09.

### 3. Root Cause & Solution

* **Root Cause:**
  * The LINE channel access token for the client's MAAC organization expired prematurely. This was due to either another system or frequent manual refreshes by the client, which invalidated MAAC's token and resulted in an "Authentication failed" error.
* **Solution:**
  * The issue was resolved by manually refreshing the token. It is recommended to monitor the client's token refresh behavior and advise them on proper LINE token management, especially if multiple systems are involved, to prevent recurrence.

***

## Investigation of Keyword Auto-Reply Trigger Issue on Instagram

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2026-01-13
* **Asana Task ID:** [1212740607334933](https://app.asana.com/1/1184020052539844/task/1212740607334933)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported that the Instagram keyword auto-reply feature does not trigger a message when a keyword is entered once. It requires a second entry of the keyword to successfully trigger the message.

### 2. Context & Details

* **Environment:**
  * MAAC org ID: 5319
  * MAAC bot/channel ID: 4232
* **Reproduction Steps:**
  1. Enter the keyword "我想要模擬考題包" once in the Instagram chat.
  2. Observe that the auto-reply is not triggered.
  3. Enter the keyword a second time.
  4. Observe that the auto-reply is successfully triggered.
* **Expected vs Actual Behavior:**
  * **Expected:** The auto-reply should trigger upon the first entry of the keyword.
  * **Actual:** The auto-reply only triggers after the keyword is entered a second time.
* **Additional Information:**
  * The issue can be reproduced consistently.
  * Relevant screenshots or screen recordings are available [here](https://app.asana.com/app/asana/-/get_asset?asset_id=1212740607334948).

### 3. Root Cause & Solution

* **Root Cause:** The MAAC's Meta channel keyword auto-reply feature does not support sending messages to new contacts. The system classifies the first interaction as a "new friend," and if no welcome message is set, the keyword auto-reply is disabled.
* **Solution:**
  * Update the help documentation to clearly explain this behavior.
  * Advise clients to enable a "new friend welcome message" for the first contact, followed by keyword auto-replies for subsequent interactions.
  * The product team plans to optimize the interaction logic between keyword auto-replies and welcome messages within the year.

The issue has been confirmed, documentation has been updated, and product enhancements are planned.

***

## Investigation of Image Carousel Addition Failure in Auto-Reply

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-12-19
* **Asana Task ID:** [1212516260073008](https://app.asana.com/1/1184020052539844/task/1212516260073008)
* **Ticket Priority:** P2
* **Client Name:** Panpuri
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client is unable to add more images to the image carousel in the Auto-Reply message for bounded contacts. The UI does not display the "+" button needed to add images, despite attempts to slide and locate it. This issue does not occur when tested by others.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 5403
  * MAAC bot/CAAC channel ID: 4300
  * Auto-Reply URL: \[REDACTED]
* **User Actions:**
  * Attempted to slide and find the "+" button to add images.
  * Issue persists after refreshing the page.
* **Reproduction Steps:**
  * Log into the MAAC system.
  * Navigate to the Auto-Reply message configuration.
  * Attempt to add images to the carousel.
* **Expected vs Actual Behavior:**
  * Expected: "+" button should be visible to add images.
  * Actual: "+" button is not visible, preventing image addition.

### 3. Root Cause & Solution

* **Root Cause:**
  * The root cause is undetermined as the issue is not reproducible by the Engineering team.
* **Solution:**
  * A temporary workaround was provided by the Customer Success Manager, who manually configured the image carousel.
  * Engineering requires a screen recording from the client to investigate further.
  * Suggested workaround: The client may create a new auto-reply as a potential solution.
* **Status:** Pending client's screen recording for further investigation.

***

## Investigation of Auto-Reply Failure on Instagram

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-12-03
* **Asana Task ID:** [1212278988595118](https://app.asana.com/1/1184020052539844/task/1212278988595118)
* **Ticket Priority:** P2
* **Client Name:** creammm.t
* **Resolution Owner:** Jalex
* **Result Breakdown:** Too costly

### 1. Issue Description

The auto-reply feature on Instagram failed to trigger when a new contact, whose profile does not exist in MAAC, replied to an IG story with a specific keyword.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC organization ID: 5881
  * MAAC IG ID: 5348
  * Occurrence Date: 12/3
* **Reproduction Steps:**
  * A new contact replies to an IG story using the keyword "新年".
* **Expected vs Actual Behavior:**
  * **Expected:** The auto-reply should be sent to the new contact.
  * **Actual:** No auto-reply message was sent.
* **Additional Information:**
  * The issue can be reproduced as demonstrated in the first comment video.
  * It is noted that if a message is received during testing, it may have been manually sent by the user.

### 3. Root Cause & Solution

* **Root Cause:** The MAAC system's logic for Meta channels does not support sending keyword-triggered auto-replies to "new contacts." The system defaults to disabling message sending to new contacts, resulting in "Message Replied = false."
* **Solution:** No immediate product optimization is planned. The help center will be updated to clarify the current behavior of Meta channels regarding new contacts and keyword auto-replies. The product team will evaluate and optimize the logic for Meta auto-replies concerning new contacts and the interaction between keyword auto-replies and welcome messages, with expected improvements in the first quarter alongside the WA auto-reply project.

***

## Investigation of Anomalous Data in Auto Reply Feature

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-11-28
* **Asana Task ID:** [1212207746495315](https://app.asana.com/1/1184020052539844/task/1212207746495315)
* **Ticket Priority:** P2
* **Client Name:** Vitabox維他盒子
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The auto-reply journey exhibits an inconsistency where the keyword trigger count is only 10, yet the subsequent click count exceeds a thousand, which appears unreasonable.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org id / CAAC org id: 4133
  * MAAC bot / CAAC channel ID: 3382
* **User Questions:**
  * Can the issue be reproduced?
* **Reproduction Steps:**
  * Access the auto-reply report at: \[REDACTED\_URL]
* **Expected vs Actual Behavior:**
  * Expected: The keyword trigger count should align with the click count.
  * Actual: The keyword trigger count is significantly lower than the click count.

### 3. Root Cause & Solution

* **Root Cause:**
  * The MAAC system aggregates performance metrics for the "send message" component based on message text content rather than the specific feature instance. This results in aggregated metrics across different features using identical message texts, preventing feature-specific analysis.
* **Solution:**
  * Implement distinct metric tracking for identical message texts based on their feature context. Consider adding context identifiers or unique message IDs to each instance to differentiate metrics accurately.
* **Status:**
  * Awaiting Product/Engineering Design Review.

***

## Investigation of Auto-Reply Editing Failure in MAAC System

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-11-25
* **Asana Task ID:** [1212084549446863](https://app.asana.com/1/1184020052539844/task/1212084549446863)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Jalex
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The client reported that specific auto-replies, namely "I want product information" and "A1 My investment performance is not as expected, how should I handle it?" could not be edited. Attempts to proceed with editing did not result in any navigation changes, and no errors were logged in the console.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 824
  * MAAC bot/channel ID: 728
  * Issue reproducible: Yes
  * Occurrence date: 11/25
* **User Actions:**
  * Attempted to edit specific auto-replies via the provided URL.
  * Navigation failed to proceed to the next step without any console errors.
* **Reproduction Steps:**
  1. Access the auto-reply edit page.
  2. Attempt to proceed to the next step.
  3. Observe the lack of navigation or error messages.
* **Expected vs Actual Behavior:**
  * **Expected:** Successful navigation to the next step upon editing auto-replies.
  * **Actual:** No navigation occurs, and no error messages are displayed.

### 3. Root Cause & Solution

* **Root Cause:**
  * The legacy auto-reply data contained parameters with empty URL strings. The current frontend validation requires valid URLs, which led to silent validation failures and blocked UI interactions.
* **Solution:**
  * Manually removed invalid URL parameters from the affected auto-replies.
  * Executed a system-wide script to clean 3212 similar invalid URL parameters from all old webhook trigger messages.
  * The issue has been resolved.

***

## Investigation of Error Code and Content Loss During Editing

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-11-19
* **Asana Task ID:** [1211990876371633](https://app.asana.com/1/1184020052539844/task/1211990876371633)
* **Ticket Priority:** P2
* **Client Name:** 法國在台協會
* **Resolution Owner:** Tracy
* **Result Breakdown:** Too costly

### 1. Issue Description

Users encountered an error code (2d0dfa3cb7ab4a0fa993a2160a810955) while editing auto-replies in MAAC, resulting in the loss of all editing content. The client did not provide screenshots, only the copied error code.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC organization ID: 5190
  * MAAC bot ID: 4127
  * Error occurred on 11/19
* **User Questions:**
  * Can the issue be reproduced?
* **Reproduction Steps:**
  * Users were editing auto-replies when the error occurred.
* **Expected vs Actual Behavior:**
  * Expected: Successful editing of auto-replies without errors.
  * Actual: Error code appeared, and all editing content was lost.

### 3. Root Cause & Solution

* **Root Cause:**
  * The exact root cause was not definitively identified. It appears to be an intermittent client-side or API error, as refreshing the page resolved the issue. MAAC audit logs did not show corresponding backend failures for the action.
* **Solution:**
  * The immediate workaround was for users to refresh the page. The issue is considered low priority due to its intermittent nature and the customer being unblocked. Further investigation is not planned at this time. The status is resolved, with monitoring for recurrence.

***

## Investigation of Display Name Issue for New OA Contacts

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-11-18
* **Asana Task ID:** [1211975651294654](https://app.asana.com/1/1184020052539844/task/1211975651294654)
* **Ticket Priority:** P2
* **Client Name:** Vertex Clinic
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported that when a user messages the OA, the display name appears as "Khun + New Friend" instead of "Khun + Display Name." This issue occurs for users who have just added the OA and are not existing friends.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 5909
  * MAAC bot/CAAC channel ID: 4773
  * Occurrence time: 01:44 AM
* **User Questions:**
  * Have similar cases been observed previously?
* **Reproduction Steps:**
  * A new user adds the OA and sends a message.
* **Expected vs Actual Behavior:**
  * Expected: Display name should appear as "Khun + Display Name."
  * Actual: Display name appears as "Khun + New Friend."

### 3. Root Cause & Solution

* **Root Cause:**
  * The issue arises when users do not grant third-party service permission via a LIFF page. The LINE API restricts access to the user's profile name, resulting in the display of "New Friend."
* **Solution:**
  * This behavior is an expected limitation due to LINE LIFF API permissions. The team will explore strategies for handling profiles without names and communicate this limitation to Customer Success Managers (CSMs). The status is acknowledged as "By Design."

***

## Why Are MAAC Keyword-Triggered Auto-Replies Failing to Send Messages?

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-10-30
* **Asana Task ID:** [1211790517659590](https://app.asana.com/1/1184020052539844/task/1211790517659590)
* **Ticket Priority:** P2
* **Client Name:** N/A
* **Resolution Owner:** Jalex
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The unexpected situation involves MAAC keyword-triggered auto-replies that are created using templates. These auto-replies successfully trigger but fail to send messages. In contrast, manually created auto-replies function correctly.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 6214
  * MAAC bot/channel ID: 6022
  * Occurrence time: 10/30 at 14:00
  * Reproducibility: Yes
* **User Questions:**
  * Why do template-based auto-replies fail to send messages after triggering?
* **Reproduction Steps:**
  1. Create a keyword-triggered auto-reply using a template.
  2. Trigger the auto-reply using the specified keyword.
  3. Observe that the message does not send.
* **Expected vs Actual Behavior:**
  * **Expected:** Auto-replies should send messages upon keyword trigger.
  * **Actual:** Auto-replies trigger but do not send messages.

### 3. Root Cause & Solution

* **Root Cause:** A configuration error specific to template-generated auto-replies prevents message dispatch after the keyword trigger is detected.
* **Solution:** Investigate the message dispatch logic for template-based auto-replies. As a workaround, advise customers to create keyword auto-replies manually.

***

## How to Migrate MAAC Settings Across Different LINE Providers

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-10-24
* **Asana Task ID:** [1211737450106162](https://app.asana.com/1/1184020052539844/task/1211737450106162)
* **Ticket Priority:** P2
* **Client Name:** DMM
* **Resolution Owner:** Tracy
* **Result Breakdown:** Task-Ticket

### 1. Issue Description

The client requested the replication of existing MAAC settings, including over 80 auto-replies, 3 rich menus, and around 10 scenario journeys, to a newly created MAAC account. The request was made to avoid manual reconfiguration due to a setup miscommunication that rendered the current MAAC unusable for production.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org id: 155
  * MAAC bot/CAAC channel ID: 198
* **User Questions:**
  * Can the engineering team support bulk migration of MAAC settings?
* **Reproduction Steps:**
  * Attempt to migrate settings from MAAC org 155 to a new MAAC account.
* **Expected vs Actual Behavior:**
  * Expected: Seamless migration of settings.
  * Actual: Technical limitations prevented automated migration.

### 3. Root Cause & Solution

* **Root Cause:**
  * MAAC settings are intricately linked to specific LINE Bot/Channel IDs and their provider configurations. The system is not designed to support direct migration between different LINE providers, making such operations technically complex and risky.
* **Solution:**
  * The Customer Success team manually re-created all auto-replies, rich menus, and journeys from MAAC org 155 into MAAC org 158.
  * It is recommended that Product/Engineering evaluate the demand for cross-provider migration features and enhance internal guidance for Customer Success Managers (CSMs) on handling such scenarios.

Status: Closed.

***

## Investigation of Unexpected Automated Reply in MAAC System

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-10-23
* **Asana Task ID:** [1211730242249302](https://app.asana.com/1/1184020052539844/task/1211730242249302)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

A customer reported receiving an automated reply that was not configured in the MAAC's general responses or in the native backend auto-reply settings.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 3216
  * MAAC bot/channel ID: 2755
  * Occurrence Date: 2025/10/23
  * Reproducibility: Yes
* **User Questions:**
  * Why is an unconfigured automated reply being sent?
* **Reproduction Steps:**
  1. Verify the automated reply settings in MAAC.
  2. Check the native backend auto-reply settings.
  3. Observe the unexpected automated reply.
* **Expected vs Actual Behavior:**
  * **Expected:** Only configured automated replies should be sent.
  * **Actual:** An unconfigured automated reply was sent.

### 3. Root Cause & Solution

* **Root Cause:** The automated reply was configured in an external Content Management System (CMS), which was not initially checked.
* **Solution:** The issue was resolved by the customer upon identifying the external CMS configuration. No further action from the product or engineering team is required. For future occurrences, it is recommended that Customer Success Managers (CSMs) guide customers to verify all integrated messaging system settings.

***

## Investigation of Image Display Issue in MAAC Auto-Reply on Specific Device

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-10-16
* **Asana Task ID:** [1211658874580570](https://app.asana.com/1/1184020052539844/task/1211658874580570)
* **Ticket Priority:** P2
* **Client Name:** BABI
* **Resolution Owner:** Tracy
* **Result Breakdown:** Not our issue

### 1. Issue Description

The images in the MAAC auto-reply are not visible on a specific Windows 10 device using the LINE Desktop application version 9.12.1.3713. This issue does not occur on mobile devices, and the Customer Support Manager (CSM) could not reproduce the issue on a Mac OS.

### 2. Context & Details

* **Environment Conditions:**
  * Device: Windows 10
  * LINE Desktop Version: 9.12.1.3713
* **Reproduction Steps:**
  * The issue occurs when viewing auto-reply images on the specified Windows 10 device.
  * The issue does not occur on mobile devices or when tested on Mac OS.
* **User Actions:**
  * The client attempted to change the network connection, but the issue persisted.
* **Expected vs Actual Behavior:**
  * Expected: Images should display correctly in the auto-reply on all devices.
  * Actual: Images do not display on the specified Windows 10 device.

### 3. Root Cause & Solution

* **Root Cause:**
  * The issue is likely client-side, possibly due to an outdated version of the LINE Desktop application. There are unofficial reports of image display issues in LINE Desktop versions 9.12-9.13 on Windows.
* **Solution:**
  * Advise the client to update their LINE Desktop application to the latest version available.
* **Status:**
  * Pending client action to update the application.

***

## Investigation of Google Maps Link Display Issue in MAAC Auto-Reply

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-10-02
* **Asana Task ID:** [1211529952491962](https://app.asana.com/1/1184020052539844/task/1211529952491962)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported that the Google Maps link embedded in the MAAC auto-reply, which previously directed to the correct address, now results in an "invalid coord" error when accessed. The auto-reply in question is named "Toilet\_Suao Area" with an ID of 876428.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC Organization ID: 5553
  * MAAC Bot/CAAC Channel ID: 4476
  * Issue occurrence date: 2025/10/02
  * Reproducibility: Yes
* **User Questions:**
  * Why does the Google Maps link no longer direct to the correct address?
* **Reproduction Steps:**
  1. Access the MAAC auto-reply named "Toilet\_Suao Area."
  2. Click on the embedded Google Maps link.
  3. Observe the "invalid coord" error on Google Maps.
* **Expected vs Actual Behavior:**
  * **Expected:** Clicking the link should direct the user to the correct Google Maps address.
  * **Actual:** The link results in an "invalid coord" error, failing to direct to the intended location.

### 3. Root Cause & Solution

* **Root Cause:**
  * The issue stems from complex Google Maps URLs with coordinates being corrupted due to encoding issues when processed by MAAC's internal link handling mechanism, such as through https://maac.io/. Directly clicking the original link outside MAAC does not exhibit this problem.
* **Solution:**
  * The auto-reply was updated with a Google Maps shortened URL (e.g., maps.app.goo.gl link), which resolved the issue. Users are advised to use shortened Google Maps URLs within MAAC to prevent this problem. The issue is now resolved.

***

## Investigation of Keyword Auto-Reply Failure in MAAC System

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-10-01
* **Asana Task ID:** [1211518547270482](https://app.asana.com/1/1184020052539844/task/1211518547270482)
* **Ticket Priority:** P2
* **Client Name:** Hotel Lovers
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported that the auto-reply with the keyword "UG6S9" is not triggering.

### 2. Context & Details

* **Client Information:**
  * MAAC org ID: 80
  * MAAC bot ID: 79
* **Feature Information:**
  * Occurrence Time: 2025/10/01 14:28
  * Auto-reply names and keywords:
    * ホテラバチャンスくじ／250903: keywords "ug6s9", "ｕｇ６ｓ９"
    * 宝箱【300ptプレゼント】／250925\_アプリ用: keywords "rt7w", "ｒｔ７ｗ"
    * 宝箱【お好きなカラコン1箱プレゼント】／250925\_アプリ用: keywords "hs5b", "ｈｓ５ｂ"
* **Reproduction:** The issue can be reproduced.
* **Attachments:** [Screenshot](https://app.asana.com/app/asana/-/get_asset?asset_id=1211518547270494)

### 3. Root Cause & Solution

* **Root Cause:** The client's LINE Developers Webhook URL was changed or removed, and it was not pointing to Crescendo Lab. As a result, MAAC did not receive any LINE Webhook events, which prevented the auto-reply from triggering.
* **Solution:** The client re-configured the LINE Developers Webhook URL to point back to Crescendo Lab's system, which resolved the auto-reply issue. It is suggested to investigate the missing MAAC/Django configuration for the client's paid Webhook forwarding feature. The auto-reply issue is resolved, but the Webhook forwarding investigation is ongoing.

***

## Investigation of Auto-Reply Discrepancy in MAAC Settings

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-09-19
* **Asana Task ID:** [1211405329420293](https://app.asana.com/1/1184020052539844/task/1211405329420293)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported that when entering the keyword "SEA!誰在海底," the response "查無相關商品" was received, which does not match the auto-reply settings configured in MAAC.

### 2. Context & Details

* **Environment:**
  * MAAC org ID: 5563
  * MAAC bot/channel ID: 4484
* **Reproduction Steps:**
  * Enter the keyword "SEA!誰在海底" in the system.
  * Observe the auto-reply "查無相關商品."
* **Expected Behavior:** The auto-reply should match the configured settings in MAAC.
* **Actual Behavior:** The auto-reply "查無相關商品" was received, which is not configured in MAAC.
* **Additional Information:**
  * The issue can be reproduced as confirmed by customer support testing.
  * Relevant report link: [MAAC Auto-reply Report](https://maac.cresclab.com/autoreply/report/881041)
  * Screenshot evidence available in Asana task asset.

### 3. Root Cause & Solution

* **Root Cause:**
  * The client's LINE webhook forwards messages to their middleware (e.g., Cyberbiz). The auto-reply originated from the client's system, not MAAC.
* **Solution:**
  * MAAC confirmed that no message was sent from our platform. It is advised that the client investigates their middleware or Cyberbiz system to identify the source of the auto-reply. The issue is resolved from the MAAC side.

***

## Investigation of Missing Tag Application for New Contacts in Auto-Reply System

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-09-17
* **Asana Task ID:** [1211383189088844](https://app.asana.com/1/1184020052539844/task/1211383189088844)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** JY
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The unexpected situation reported was that new LINE contacts were not automatically tagged with the "New Friend" label, and the welcome message was not sent as configured in the auto-reply settings.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC organization ID: 5395
  * MAAC bot ID: 4303
  * Client: \[REDACTED]
* **User Questions:**
  * Does the tag apply automatically upon adding a friend, or is a message required for the tag to apply?
* **Reproduction Steps:**
  * A new contact was added to the LINE account.
  * The auto-reply system was expected to apply the "New Friend" tag and send a welcome message.
* **Expected vs Actual Behavior:**
  * **Expected:** New contacts should receive the "New Friend" tag and a welcome message.
  * **Actual:** Neither the tag was applied nor the message was sent.

### 3. Root Cause & Solution

* **Root Cause:**
  * The MAAC system did not receive the LINE follow events for these users. The user profiles were created through subsequent message interactions. The system functions as expected, suggesting that these users might have been pre-existing LINE friends or that the follow events were not transmitted by LINE.
* **Solution:**
  * There is no system bug. The MAAC mechanism is functioning correctly. It is recommended to inform customer support that the issue is not due to a system error. The case is closed as it meets the product expectations.

***

## Investigation of Image Display Issues in Facebook Messenger Card Messages

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-09-08
* **Asana Task ID:** [1211289255692411](https://app.asana.com/1/1184020052539844/task/1211289255692411)
* **Ticket Priority:** P2
* **Client Name:** N/A
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Not our issue

### 1. Issue Description

Some Facebook Messenger users occasionally reported that images in card messages sent via MAAC auto-reply were not displayed.

### 2. Context & Details

* **Issue Occurrence Date:** 8 Sep 2025
* **Reproduction:** The issue is not reproducible; images display normally during testing.
* **Environment Information:**
  * CAAC bot ID: 3992
  * MAAC org ID: 5026
* **User Actions:** Users reported the issue intermittently.
* **Expected Behavior:** Images should display correctly in card messages.
* **Actual Behavior:** Images occasionally do not display for some users.

### 3. Root Cause & Solution

* **Root Cause:** The issue is currently not reproducible by ProductOps or Engineering. Initial investigation showed the image displaying correctly. It is suspected that the issue might be related to an outdated Messenger application version on the user's device.
* **Solution:** Since the issue cannot be reproduced, no immediate fix is implemented. If the issue reoccurs, gather specific user device information (device type, Messenger app version). This ticket will be closed for now.

***

## Investigation of Deeplink Redirection Failure in Meta Auto-reply

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-07-24
* **Asana Task ID:** [1210875549357676](https://app.asana.com/1/1184020052539844/task/1210875549357676)
* **Ticket Priority:** P2
* **Client Name:** Org 1 Test Account
* **Resolution Owner:** Tracy
* **Result Breakdown:** Too costly

### 1. Issue Description

When a MAAC LINE Deeplink is placed in a Meta Auto-reply and clicked within the iOS Messenger in-app browser, it results in a 404 error, failing to redirect users to LINE OA.

### 2. Context & Details

* **Environment Conditions:**
  * Occurs within the iOS Messenger in-app browser.
  * MAAC org ID: 1
  * Reproducible: Yes
* **User Questions:**
  * Why does the deeplink fail to redirect in the iOS Messenger in-app browser?
* **Reproduction Steps:**
  1. Place a MAAC LINE Deeplink in a Meta Auto-reply template.
  2. Click the deeplink within the iOS Messenger in-app browser.
* **Expected vs Actual Behavior:**
  * **Expected:** The deeplink should redirect to LINE OA.
  * **Actual:** A 404 error occurs, preventing the redirect.

### 3. Root Cause & Solution

* **Root Cause:** The issue arises from the behavior of MAAC's short URL (LIFF) when opened in the iOS Messenger in-app browser. The restrictions of the in-app browser lead to a 404 error during the LIFF opening process. This is not an issue with the Meta Auto-reply feature itself.
* **Solution:** Implement a mechanism to detect when a MAAC Deeplink is clicked within the iOS Messenger in-app browser and force it to open through an external browser. This approach has been successfully implemented in CAAC and SRT and should be considered for the full-channel Deeplink POC.

***

## Investigation of Auto Reply Functionality Failure

**Metadata**

* **Feature:** MAAC-Auto reply
* **Created At:** 2025-07-12
* **Asana Task ID:** [1210776362195812](https://app.asana.com/1/1184020052539844/task/1210776362195812)
* **Ticket Priority:** P2
* **Client Name:** Demo\_Thailand
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

Recently created auto-replies are not functioning as expected. Keywords such as "fb," "fb2," "fb3," and "linealone" fail to trigger the auto-replies.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 1820
  * MAAC bot ID: \[REDACTED]
* **Reproduction Steps:**
  * Create new auto-replies using specified keywords.
  * Attempt to trigger auto-replies with these keywords.
* **Expected vs Actual Behavior:**
  * **Expected:** Auto-replies should be triggered by the specified keywords.
  * **Actual:** Auto-replies are not triggered by any of the keywords.
* **Additional Information:**
  * The issue is reproducible.
  * Relevant screenshots and screen records are available:
    * [Screenshot 1](https://app.asana.com/app/asana/-/get_asset?asset_id=1210776362195819)
    * [Screenshot 2](https://app.asana.com/app/asana/-/get_asset?asset_id=1210776362195821)

### 3. Root Cause & Solution

* **Root Cause:**
  * The auto-reply issue has been resolved, but the specific cause was not specified.
  * The Facebook Quick Reply auto-tagging issue is still under investigation.
* **Solution:**
  * The functionality for LINE and Facebook auto-replies has been restored.
  * Engineering will continue to investigate the Facebook Quick Reply tag issue.
