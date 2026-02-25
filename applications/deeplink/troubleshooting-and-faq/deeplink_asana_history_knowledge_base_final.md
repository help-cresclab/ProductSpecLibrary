# deeplink\_asana\_history\_knowledge\_base\_final

## Investigation of Deeplink Redirection Issue on Facebook App

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2026-02-02
* **Asana Task ID:** [1213079624870420](https://app.asana.com/1/1184020052539844/task/1213079624870420)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** N/A
* **Result Breakdown:** Not our issue

### 1. Issue Description

The Facebook mobile application automatically converts external links to lowercase, which causes some Deeplink URLs to redirect to incorrect accounts or become invalid.

### 2. Context & Details

* **Environment:**
  * Facebook mobile application
  * Affected Deeplink: `https://maac.io/1fKm1` becomes `https://maac.io/1fkm1`
* **User Questions:**
  * Why does the link redirect to a different account?
* **Reproduction Steps:**
  1. Place a Deeplink on a Facebook page.
  2. Click the link using the Facebook mobile app.
* **Expected vs Actual Behavior:**
  * **Expected:** The link should redirect to the correct account.
  * **Actual:** The link redirects to an incorrect account due to casing changes.

### 3. Root Cause & Solution

* **Root Cause:**
  * The Facebook mobile application modifies the casing of Deeplink URLs, which affects case-sensitive parameters and leads to incorrect redirection.
* **Solution:**
  * **Immediate Workaround:** Generate and use an all-lowercase Deeplink URL.
  * **For Product/Engineering:** Monitor the issue's frequency and consider implementing an option to generate all-lowercase Deeplinks to prevent casing modifications by external platforms.

***

## Investigation of CLID Missing During Deep Link Transitions

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2026-01-30
* **Asana Task ID:** [1213035004023053](https://app.asana.com/1/1184020052539844/task/1213035004023053)
* **Ticket Priority:** P2
* **Client Name:** A10Lab
* **Resolution Owner:** David
* **Result Breakdown:** Not our issue

### 1. Issue Description

An issue was identified where the CLID is not consistently passed to the target form when users transition through specific flows via Deep Links. This inconsistency results in an inability to identify users, negatively impacting their Marketing Automation initiatives and message delivery after the user's application.

### 2. Context & Details

* **User Flow in Scope:**
  * User clicks the Deep Link.
  * User taps the "Apply Here" button displayed within the message/template.
  * User transitions to the entry form, where the CLID is missing in some cases.
* **Suspected Cause:** The query parameter may be dropped during the transition from the message template to the final form URL.
* **Environment Details:**
  * MAAC org id: 75
  * MAAC bot id: 74
  * Channel Type: LINE
  * Affected contact id: \[REDACTED\_ID]
  * MAAC ID: \[REDACTED\_ID]
* **Reproduction:** Unclear if the issue can be consistently reproduced in the client organization.
* **Additional Information:** An Excel file with users who failed to receive the CLID is attached. Updates to the deep links have been requested.

### 3. Root Cause & Solution

* **Root Cause:** The investigation confirmed that the MAAC system consistently appended the CLID parameter during all redirections from the Deep Link to the external URL. The issue appears to originate from the external form platform (zfrmz.jp) not correctly receiving or processing the CLID parameter.
* **Solution:** The engineering team verified that MAAC's redirection mechanism is functioning as expected. It is recommended that the client investigates the parameter handling on their external form platform (zfrmz.jp). No further action is required from MAAC engineering.

***

## Investigation of Deeplink Display Failure in Customer Onboarding

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-12-30
* **Asana Task ID:** [1212585827993386](https://app.asana.com/1/1184020052539844/task/1212585827993386)
* **Ticket Priority:** P4
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The current status indicates that the deeplink is not functioning. After a new client onboarded and shared login permissions on 12/29, it was discovered that the region was set to Japan. The client was asked to reshare permissions on 12/30. The client created a new login with the region set to Taiwan and deleted the old login set to Japan. After receiving the new login permissions on 12/30, testing the deeplink during onboarding failed.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 6442
  * MAAC bot/channel ID: 6601
  * Issue occurred on: 2025/12/30
  * Reproducibility: Yes
* **User Actions:**
  * Client initially set up a login with the region as Japan.
  * Client created a new login with the region set to Taiwan and deleted the previous login.
* **Reproduction Steps:**
  1. Client shared login permissions with the region set to Japan.
  2. Client reshared permissions with the region set to Taiwan.
  3. Attempted to test the deeplink after receiving new login permissions.
* **Expected vs Actual Behavior:**
  * **Expected:** Deeplink should function correctly after setting the region to Taiwan.
  * **Actual:** Deeplink failed to work during onboarding testing.

### 3. Root Cause & Solution

* **Root Cause:**
  * MAAC failed to automatically create the necessary LIFF applications (including Deeplink LIFF) for the newly connected LINE login channel.
* **Solution:**
  * LIFFs were manually created and configured in the new login channel to match LINE Developers settings.
  * It is recommended to review MAAC's automatic LIFF generation process for new login channels to identify potential bugs.

***

## Why Do Deeplinks Not Open the LINE App When Clicked from Facebook?

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-12-25
* **Asana Task ID:** [1212588958360076](https://app.asana.com/1/1184020052539844/task/1212588958360076)
* **Ticket Priority:** P2
* **Client Name:** Sammakorn
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

When users click a deeplink from a Facebook post, it navigates to the landing page but fails to open the LINE app. Instead, it opens the LINE web interface, displaying the login page.

### 2. Context & Details

* **Environment Conditions:**
  * Affects all organizations using MAAC deeplinks.
  * Occurs when links are clicked within Meta in-app browsers (e.g., Facebook).
* **Reproduction Steps:**
  1. Create a deeplink.
  2. Place the deeplink in a Facebook post.
  3. Click the deeplink on the Facebook website.
* **Expected vs Actual Behavior:**
  * **Expected:** The link should open the OA chatroom in the LINE app.
  * **Actual:** The link opens the LINE web interface, requiring login.
* **Device Testing:**
  * Samsung Galaxy Fold 5 (Android 16/FB version 543): Stuck on LINE login page.
  * Samsung Galaxy S23 Ultra (Android 16/FB version 543): Opens LINE app correctly.
  * iPhone 17 (iOS 26.1/FB version 543): Mixed results; some devices open normally, others do not.
* **Additional Observations:**
  * Using "login with LINE app" works on some devices.
  * "Open in external browser" consistently opens the LINE app and navigates correctly.
  * The issue is reproducible on specific devices but affects all deeplinks regardless of the creator organization.

### 3. Root Cause & Solution

* **Root Cause:**
  * The issue is due to a known limitation of Meta's in-app browser environment, which prevents direct redirection to the LINE app and requires re-login through the browser. This is not a MAAC platform issue.
* **Solution:**
  * Update the Thai Deeplink Help Center article to explain the limitation of Meta's in-app browsers.
  * Advise users to open links in an external browser for proper functionality.
  * No platform fix is necessary.

***

## Investigation of Button Visibility Issue on Small-Screen iPhones

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-12-12
* **Asana Task ID:** [1212400140357443](https://app.asana.com/1/1184020052539844/task/1212400140357443)
* **Ticket Priority:** P4
* **Client Name:** N/A
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Product Optimization

### 1. Issue Description

Some users on small-screen iPhones, such as the iPhone SE, reported that the "Go to the link" and "Back to LINE" buttons were not visible on the LIFF redirect page.

### 2. Context & Details

* **Device Information:** iPhone SE with a 4.7-inch screen.
* **Reproduction:** The issue could not be consistently reproduced on an iPhone SE or other devices.
* **Expected Behavior:** Buttons should be visible on the LIFF redirect page.
* **Actual Behavior:** Buttons were not visible to users on certain small-screen iPhones.
* **Additional Information:** Normal behavior as per screenshots provided.

### 3. Root Cause & Solution

* **Root Cause:** The issue could not be consistently reproduced, and a specific root cause for this instance remains unconfirmed.
* **Solution:** The LIFF redirect page is undergoing a full optimization and redesign in January, which is expected to resolve such display issues. The customer will be notified upon release.

***

## Investigation of Message Delivery Failure in Customer Journey

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-11-21
* **Asana Task ID:** [1212011516046540](https://app.asana.com/1/1184020052539844/task/1212011516046540)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The deep link was expected to trigger a message for both new and existing contacts. However, while new contacts received the message as intended, existing contacts did not. This behavior was confirmed during testing by the Customer Success Manager (CSM).

### 2. Context & Details

* **Environment:**
  * MAAC org ID: 3763
  * MAAC bot ID: 3143
* **Reproduction Steps:**
  * Use the deep link named "2025\_MM\_Seller\_mapping\_OALink".
  * Scan the link with both new and existing contacts.
* **Expected vs Actual Behavior:**
  * **Expected:** Both new and existing contacts should receive the message upon scanning the deep link.
  * **Actual:** Only new contacts receive the message; existing contacts do not.
* **Additional Information:**
  * The issue was reproducible during internal testing.
  * No specific feature ID or time of occurrence was noted.

### 3. Root Cause & Solution

* **Root Cause:** The root cause was identified as the depletion of message credits on the customer's LINE official account. This was not due to a defect in the MAAC product.
* **Solution:** The customer is required to replenish their LINE message credits via the LINE CMS backend. This action will resolve the issue and allow messages to be sent to existing contacts as expected.

***

## How to Resolve Deeplink Issues from Facebook Requiring LINE Sign-In

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-11-17
* **Asana Task ID:** [1211963997510974](https://app.asana.com/1/1184020052539844/task/1211963997510974)
* **Ticket Priority:** P2
* **Client Name:** N/A
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

Users clicking on a Deeplink URL from a Facebook post are unexpectedly redirected to the LINE Sign-in page instead of directly opening the LINE app. This behavior has resulted in a significant drop-off as users are unwilling to proceed due to the added friction.

### 2. Context & Details

* **Environment Conditions:**
  * The issue is specific to Deeplink URLs placed in Facebook posts.
  * The Deeplink functions correctly outside of Facebook.
* **User Questions:**
  * Why are users being redirected to the LINE Sign-in page?
  * Is there a way to bypass the login prompt and redirect users smoothly into the LINE app?
* **Reproduction Steps:**
  1. Place a Deeplink URL in a Facebook post.
  2. Click the Deeplink URL from the Facebook post.
  3. Observe the redirection to the LINE Sign-in page instead of the LINE app.
* **Expected vs Actual Behavior:**
  * **Expected:** Clicking the Deeplink should open the LINE app directly, allowing users to add the account immediately.
  * **Actual:** Users are redirected to the LINE Sign-in page, and a "Go to link" button appears before redirection, adding extra friction.
* **Additional Observations:**
  * Some users are required to log in to LINE again, while others are not.
  * A reference post from the brand “Double A” does not trigger the forced LINE login.

### 3. Root Cause & Solution

* **Root Cause:**
  * Meta app in-app browsers block direct, automatic redirects to external apps, necessitating an intermediate "Go to link" page.
  * The LINE OA consent page is controlled by LINE and may appear due to LIFF permission changes or specific user contexts, not our platform.
* **Solution:**
  * A fix was deployed with the flag `enable_deeplink_in_app_browser_force_click` to reliably open Deeplinks in LINE from Facebook, addressing the previous forced LINE login page issue.
  * The "Go to link" button remains necessary due to Meta restrictions. Further UX improvements are under consideration to enhance user experience.

***

## Understanding the Definition of Total Clicks for Deeplink on Desktop and Mobile

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-11-14
* **Asana Task ID:** [1211944509814825](https://app.asana.com/1/1184020052539844/task/1211944509814825)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Jalex
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client observed discrepancies between the total clicks reported by MAAC and those reported by an advertising platform. They sought clarification on how MAAC calculates total clicks for deeplinks on desktop and mobile devices.

### 2. Context & Details

* **Environment Conditions:**
  * The client used deeplinks in advertisements on an external platform.
  * Discrepancies were noted between MAAC's reported clicks and the external platform's data.
* **User Questions:**
  * How does MAAC define total clicks for deeplinks on desktop and mobile?
  * Does clicking a deeplink on a desktop count multiple times if the same action is repeated?
  * On mobile, does clicking the link itself count as multiple clicks, or must it proceed through specific steps?
* **Reproduction Steps:**
  * The client placed a deeplink on an advertisement platform.
  * Observed the click count differences between the platform and MAAC.
* **Expected vs Actual Behavior:**
  * **Expected:** Consistent click counts between MAAC and the advertising platform.
  * **Actual:** MAAC reported fewer clicks than the platform.

### 3. Root Cause & Solution

* **Root Cause:**
  * The client misunderstood the click counting logic of MAAC's deeplink feature. MAAC counts a click each time a request is made to the deeplink URL, regardless of the device or method used. The count increases with each HTTP request to the deeplink, not necessarily when the LINE app is opened.
* **Solution:**
  * Clarified the click counting logic to the client. MAAC's total clicks are based on requests to the deeplink URL, not on subsequent actions like opening the LINE app.
  * Suggested enhancing product documentation or the user interface to clearly define the criteria for counting deeplink clicks.

***

## Investigation of Missing Coupon Delivery via Deeplink

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-11-03
* **Asana Task ID:** [1211818239155742](https://app.asana.com/1/1184020052539844/task/1211818239155742)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Limit information

### 1. Issue Description

The designed process involves users scanning a QR code to receive an auto-reply keyword, which triggers a second deeplink. Upon clicking this second deeplink, users should receive a coupon. However, two users reported not receiving the expected coupon.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org id: 548
  * MAAC bot/channel ID: 527
* **User Actions:**
  * Users scanned the "Join Friend QR code" and received the auto-reply.
  * Users clicked the second deeplink for the "Ice Cream Coupon Message."
* **Reported Issue:**
  * Users did not receive the "Ice Cream Coupon" after clicking the second deeplink.
  * No tags were applied to the users' records.
* **Reproduction Steps:**
  * Users scanned the QR code and clicked the second deeplink.
* **Expected vs Actual Behavior:**
  * Expected: Users receive a coupon message.
  * Actual: No coupon message received, and no tags applied.

### 3. Root Cause & Solution

* **Root Cause:**
  * MAAC logs confirm the deeplink was triggered, but there is no record of the message being sent in the line\_messagerecord. Tags were also missing. The issue could not be reproduced. The root cause remains unconfirmed due to the lack of access to the customer's LINE Official Account and detailed logs.
* **Solution:**
  * The task is closed. If the issue recurs, it should be reopened with reproduction steps and access to the customer's LINE Official Account.

***

## How to Update Deeplinks for A10lab

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-10-29
* **Asana Task ID:** [1211779527097305](https://app.asana.com/1/1184020052539844/task/1211779527097305)
* **Ticket Priority:** P2
* **Client Name:** A10lab
* **Resolution Owner:** N/A
* **Result Breakdown:** N/A

### 1. Issue Description

The client, A10lab, requested an update to their deeplinks. The unexpected issue identified was that deeplinks generated from templates do not automatically reflect updates made to the original template's content, such as image URLs.

### 2. Context & Details

* **Client Information:**
  * MAAC org id / CAAC org id: 75
  * MAAC bot / CAAC channel ID: 74
* **Request Details:**
  * Estimated number of updates: 1,000
  * Expected completion timeline: Mid-December
* **Reproduction Steps:**
  * Deeplinks created from templates are static and do not update with template changes.
* **Expected vs Actual Behavior:**
  * Expected: Deeplinks should dynamically update with changes to the template.
  * Actual: Deeplinks remain static and do not reflect updates.

### 3. Root Cause & Solution

* **Root Cause:** Deeplinks are created as static content copies from templates, not dynamically linked. As a result, any subsequent changes to the template do not propagate to the deeplinks.
* **Solution:** Manually updated 1,000 deeplinks and their image URLs from 2025 to 2026. It is suggested that the Product/Engineering team reviews the feasibility of implementing dynamic linking for templates and deeplinks or documents this static behavior for Customer Success Managers (CSMs).

***

## Investigation of Message Delivery Failure in Customer Journey

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-10-23
* **Asana Task ID:** [1211728764247261](https://app.asana.com/1/1184020052539844/task/1211728764247261)
* **Ticket Priority:** P2
* **Client Name:** 珍煮丹 TRUEDAN
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The customer reported that deeplinks and rich menu clicks failed to trigger prize coupons or automated journeys as expected.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 3738
  * MAAC bot ID: 3120
  * Feature ID: 2651f8ac-\[REDACTED\_PHONE]-9fee-f6067e59f4b1
  * Happened on: 10/23
* **User Actions:**
  * The customer set up a one-week limited activity with two channels.
  * Deeplink scanned: [https://maac.io/4Nj8V](https://maac.io/4Nj8V)
  * Rich menu clicked: 10/20-2025 珍煮丹10月冬茶花事（第5格）
* **Reproduction Steps:**
  * Screenshots were taken at 2:32 and 2:51 when the rich menu was clicked and the deeplink was scanned. No response was observed by 4 PM.
* **Expected vs Actual Behavior:**
  * Expected: Prize coupons should be triggered upon scanning the deeplink or clicking the rich menu.
  * Actual: No prize coupons or automated journey responses were triggered.

### 3. Root Cause & Solution

* **Root Cause:**
  * The customer's LINE CMS message quota was depleted, preventing the execution of MAAC features that require outbound LINE messages.
* **Solution:**
  * The customer replenished the LINE CMS message quota, which resolved the issue. Deeplink and journey features are now functioning correctly.
  * Suggested Action: Improve system alerts or CSM documentation regarding dependencies on LINE CMS message quotas.

***

## How to Resolve Deeplink Access Issues in Messenger

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-10-22
* **Asana Task ID:** [1211717314283351](https://app.asana.com/1/1184020052539844/task/1211717314283351)
* **Ticket Priority:** P2
* **Client Name:** Zurquiz
* **Resolution Owner:** Noel
* **Result Breakdown:** Product Optimization

### 1. Issue Description

The user is unable to access specific deeplinks via Messenger. Upon clicking the provided links, the expected content does not display, and the screen shows an error as depicted in the attached images.

### 2. Context & Details

* **Environment Conditions:**
  * Organization ID: 5058
  * Bot ID: 5967
  * User's Device: iPhone 13
  * Internet Connection: 5G
* **Reproduction Steps:**
  1. User clicks on the deeplink provided in Messenger.
  2. The screen displays an error instead of the expected content.
* **Expected vs Actual Behavior:**
  * **Expected:** The deeplink should open the intended content in the browser.
  * **Actual:** The deeplink fails to open, showing an error screen.
* **Additional Information:**
  * The issue was not reproducible on a different device, where the deeplink functioned correctly.

### 3. Root Cause & Solution

* **Root Cause:** The Messenger in-app browser blocks LINE LIFF deeplinks from opening. The current design of the deeplink does not support forcing an external browser to open, and attempts to do so result in link failure.
* **Solution:** Implement an in-app browser redirect button that allows users to manually open the link in an external browser. This solution is similar to the existing iOS Chrome workaround. The engineering team has scheduled this optimization for completion by November 4.

***

## Investigation of Deep Link Failure in Facebook Environment

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-10-16
* **Asana Task ID:** [1211658876963521](https://app.asana.com/1/1184020052539844/task/1211658876963521)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Too costly

### 1. Issue Description

The client reported that when using MAAC's deep link in Facebook messages to invite parents to join the official LINE account, multiple users encountered a failure to join. The client seeks to understand the cause of this issue.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 6148
  * MAAC bot/channel ID: 5874
  * Occurrence Date: 2025/10/16
* **User Questions:**
  * Why are users unable to join the LINE account via the deep link shared in Facebook messages?
* **Reproduction Steps:**
  1. Share the MAAC deep link in a Facebook message.
  2. Attempt to join the LINE account through the link.
* **Expected vs Actual Behavior:**
  * **Expected:** Users should be able to join the LINE account directly through the deep link.
  * **Actual:** Users encounter a failure screen and cannot join the LINE account.

### 3. Root Cause & Solution

* **Root Cause:**
  * The deep link implementation incorrectly forced the opening of an external browser, which conflicted with Meta's in-app browser policies, resulting in the link failure.
* **Solution:**
  * The deep link has been optimized for Meta environments. A redirect button is now displayed within the in-app browser, allowing users to manually click and activate the deep link. Additionally, Help Center documentation will be updated to reflect these changes. The solution was launched on 2023-11-10.

***

## How to Address SEO Tools Flagging MAAC Links as Broken

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-10-15
* **Asana Task ID:** [1211645610494507](https://app.asana.com/1/1184020052539844/task/1211645610494507)
* **Ticket Priority:** P2
* **Client Name:** Vertex Clinic
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client's SEO tool is identifying all maac.io links as broken, despite the links functioning correctly when accessed manually.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 6211
  * MAAC bot/channel ID: 6089
  * Issue occurred on: 13/10/2025 at 11:45 PM
* **User Questions:**
  * Can the SEO tool's detection of MAAC links as broken be fixed or prevented?
  * Is there any documentation available regarding this issue?
* **Reproduction Steps:**
  * The issue is not reproducible manually as the links work correctly when accessed directly.
* **Expected vs Actual Behavior:**
  * Expected: MAAC links should not be flagged as broken by SEO tools.
  * Actual: SEO tools are flagging MAAC links as broken, though they are operational.

### 3. Root Cause & Solution

* **Root Cause:**
  * The issue originates from the client's SEO tool detection mechanism, not from the functionality of the MAAC links themselves. The MAAC links are confirmed to be operational.
* **Solution:**
  * It is recommended that the client consults with their SEO tool provider to understand and adjust the detection rules. MAAC deeplinks have been verified to function correctly. The status is pending further investigation by the client with their SEO tool provider.

***

## Clarification on the Definition of "New Contacts" in Deeplink Data

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-10-14
* **Asana Task ID:** [1211634082654028](https://app.asana.com/1/1184020052539844/task/1211634082654028)
* **Ticket Priority:** P2
* **Client Name:** 雅可樂多
* **Resolution Owner:** JY
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client seeks clarification on the definition of "New Contacts" in the Deeplink data report. There is a discrepancy where the sum of new contacts from two sub-periods is one higher than the total new contacts for the combined full period.

### 2. Context & Details

* **Environment Conditions:**
  * Date of occurrence: 2025/10/14
  * The issue can be reproduced.
* **User Questions:**
  * Does unblocking a user and re-adding them via a Deeplink count them as a "New Contact"?
* **Reproduction Steps:**
  * Review the Deeplink performance report for the specified periods.
  * Compare the sum of "New Contacts" from sub-periods with the total for the full period.
* **Expected vs Actual Behavior:**
  * Expected: The sum of "New Contacts" from sub-periods should equal the total for the full period.
  * Actual: The sum from sub-periods is one higher than the total for the full period.

### 3. Root Cause & Solution

* **Root Cause:**
  * The discrepancy arises because a user who unblocks and re-adds via a Deeplink is identified as a "New Contact." At the time of LIFF authorization, if the user is in a blocked state, the process\_deep\_link() method sends a NEW\_FRIEND message. The aggregated period report counts unique "New Contacts" only once, while sub-period reports might capture a "New Contact" event for the same user if their unblock activity spans different sub-periods.
* **Solution:**
  * The behavior is by design, and no code fix is required. It is recommended to add a clarification regarding this behavior in the documentation to prevent future confusion.

***

## Investigation of Deeplink Redirect Failure in Facebook Messenger

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-09-26
* **Asana Task ID:** [1211476033978693](https://app.asana.com/1/1184020052539844/task/1211476033978693)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Too costly

### 1. Issue Description

The MAAC deeplink URLs successfully redirect to LINE when placed on Facebook post walls. However, when these links are used in Facebook Messenger, they fail to load, displaying a "Cannot display this page" error.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC organization ID: \[REDACTED]
  * CAAC organization ID: \[REDACTED]
  * Language: Traditional Chinese
  * Timezone: Asia/Taipei
  * Plan: Growth
  * Expiration Date: 2025/12/31
* **Reproduction Steps:**
  1. Place MAAC deeplink URL on a Facebook post wall.
  2. Click the link to verify successful redirection to LINE.
  3. Place the same URL in Facebook Messenger.
  4. Click the link in Messenger to observe the error.
* **Expected vs Actual Behavior:**
  * **Expected:** The deeplink should redirect to LINE in both Facebook post walls and Messenger.
  * **Actual:** The deeplink redirects successfully from post walls but fails in Messenger, showing an error message.

### 3. Root Cause & Solution

* **Root Cause:** The issue arises because the MAAC deeplink functionality does not enforce opening in an external browser. Facebook Messenger's internal browser has strict security policies that block redirects from custom or unfamiliar domains.
* **Solution:** Implement a feature to force MAAC deeplinks to open in an external browser when accessed from platforms like Facebook Messenger. This task is currently prioritized in the MAAC development backlog for optimization.

***

## Why Are Some Prize Names Not Displaying in MAAC Deeplink?

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-09-26
* **Asana Task ID:** [1211473650831117](https://app.asana.com/1/1184020052539844/task/1211473650831117)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Noel, Aaren
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The client configured seven prizes in the prize management system. However, when selecting prize names in the deeplink settings, some prize names appeared while others did not. The client seeks to understand why certain prize names are missing.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 4294
  * MAAC bot: 3476
  * Happened time: 9/26
  * UUID: \[REDACTED\_UUID]
* **User Questions:**
  * Why are some prize names not appearing in the deeplink settings?
* **Reproduction Steps:**
  1. Configure prizes in the prize management system.
  2. Set up deeplink with prize names.
  3. Observe that some prize names do not display.
* **Expected vs Actual Behavior:**
  * Expected: All configured prize names should display in the deeplink.
  * Actual: Some prize names are missing, replaced by a generic placeholder.
* **Additional Information:**
  * The client confirmed that prize management settings were correct.
  * Screenshots provided for both displayed and non-displayed prize names.

### 3. Root Cause & Solution

* **Root Cause:**
  * Likely a frontend rendering issue related to specific characteristics of the prize name. The exact root cause is not consistently reproducible for further debugging.
* **Solution:**
  * An immediate fix was deployed to resolve the display issue and ensure the correct prize name is shown. Engineering should investigate further if this issue reoccurs to identify and implement a permanent frontend solution.
* **Status:**
  * Resolved.

***

## Investigation of Message Delivery Failure in Customer Journey

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-09-19
* **Asana Task ID:** [1211405329420306](https://app.asana.com/1/1184020052539844/task/1211405329420306)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The customer reported that after scanning the deeplink, three LINE UIDs did not receive the expected messages.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 5563
  * Feature ID: Not specified
  * Reproduction: Not confirmed
* **User Questions:**
  * Why did the users not receive messages after scanning the deeplink?
* **Reproduction Steps:**
  * Users scanned the deeplink but did not receive any messages.
* **Expected vs Actual Behavior:**
  * **Expected:** Users should receive messages after scanning the deeplink.
  * **Actual:** No messages were received by the users.

### 3. Root Cause & Solution

* **Root Cause:**
  * Investigation confirmed that the reported users had previously scanned the deeplink ID 953713 in July 2025. The MAAC platform's campaign logic correctly prevented re-sending welcome or new contact messages to users who had already triggered the specific deeplink.
* **Solution:**
  * No system bug was identified; the platform functioned as designed. The CSM has been provided with the user's deeplink scan history to explain the behavior to the client. Communicate to the client that messages were not sent because the users had previously interacted with the deeplink.

***

## Investigation of Archived Deep Link Content Display for New Friends

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-09-16
* **Asana Task ID:** [1211368444546388](https://app.asana.com/1/1184020052539844/task/1211368444546388)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

Two new friends added to the client's Official Account received content from an archived deep link template. The client inquired why the archived content was still appearing and how to verify the source from which these users joined.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 5913
  * MAAC bot: 4775
  * CAAC org ID: 2676
  * Happened between: 9/12 - 9/13
* **User Questions:**
  * Why is the archived deep link content still active?
  * How can the source of user addition be verified?
* **Reproduction Steps:**
  * The issue cannot be reproduced as current deep links do not display the archived template content.
* **Expected vs Actual Behavior:**
  * Expected: Archived deep link content should not be active.
  * Actual: Archived deep link content was received by new users.
* **Additional Information:**
  * Archived deep link name: "導流連結－範本" (https://maac.io/3xSK0)
  * User IDs involved: \[REDACTED], \[REDACTED]

### 3. Root Cause & Solution

* **Root Cause:**
  * The system design allows archived deep links to remain active and clickable. Data confirmed that the two users clicked the specific deep link around their join time, indicating it was still exposed externally.
* **Solution:**
  * This behavior is consistent with system design expectations. The client has been advised to either modify the content of the archived deep link or remove its external exposure. For future improvements, consider implementing a true disable/delete function for deep links or enhancing clarity on the behavior of archived links.

***

## Investigation of Message Delivery Failure in Customer Journey

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-09-16
* **Asana Task ID:** [1211368348898205](https://app.asana.com/1/1184020052539844/task/1211368348898205)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

An existing contact did not receive the configured message after initially scanning a specific deeplink. The contact's LINE UID: \[REDACTED\_ID] \[REDACTED], and the MAAC ID: \[REDACTED\_ID] \[REDACTED]. The client reported that the user insisted this was their first scan of the deeplink, expecting to receive the message.

### 2. Context & Details

* **Client Information:**
  * MAAC org ID: 5563
  * MAAC bot/channel ID: \[REDACTED]
* **Feature Information:**
  * Incident occurred on: 2025/09/16 11:40
  * Deeplink name: "來源-2025臺法文化工作坊"
* **Reproduction Steps:**
  * The issue cannot be reproduced; it appears to be an isolated case.
* **Expected vs Actual Behavior:**
  * Expected: The contact should receive a message upon scanning the deeplink.
  * Actual: No message was received by the contact.
* **Additional Information:**
  * The user clicked the deeplink multiple times between September 5th and September 16th, 2025.
  * Tags were successfully applied during these interactions.

### 3. Root Cause & Solution

* **Root Cause:**
  * The "existing contact message" feature for the deeplink was enabled on September 16th, 2025, at 08:52. All previous interactions by the user occurred before this time. The message setting was configured as non-repeatable, preventing retrospective message delivery.
* **Solution:**
  * Ensure the "existing contact message" feature is enabled before expecting message delivery. Consider configuring the message setting to allow repeatable delivery if retrospective messaging is required.

***

## Investigation of Android Incompatibility with MAAC Referral Link

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-09-15
* **Asana Task ID:** [1211356153706723](https://app.asana.com/1/1184020052539844/task/1211356153706723)
* **Ticket Priority:** P2
* **Client Name:** 酷遊天國際旅行社股份有限公司-KKday
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

KKday reported that their MAAC referral link (https://maac.io/4ElIB) failed to open on Android devices, while it functioned correctly on iOS devices.

### 2. Context & Details

* **Environment Conditions:**
  * iOS devices: Link opens normally.
  * Android devices: Link fails to open when embedded in third-party applications.
* **User Questions:**
  * Is the issue caused by system differences between iOS and Android?
* **Reproduction Steps:**
  * Embed the MAAC referral link within a third-party application.
  * Attempt to open the link on an Android device.
* **Expected vs Actual Behavior:**
  * Expected: Link should open normally on both iOS and Android devices.
  * Actual: Link opens on iOS but fails on Android when accessed through a third-party application.

### 3. Root Cause & Solution

* **Root Cause:** The issue is an interaction problem between a third-party application and the Android operating system, not a fault of the MAAC platform or the referral link itself.
* **Solution:** No action is required from MAAC Product or Engineering. It is recommended that the customer investigates how their external application handles link opening on Android devices.
* **Status:** Closed

***

## Investigation of Deeplink Functionality in TikTok Ads

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-09-09
* **Asana Task ID:** [1211292942830085](https://app.asana.com/1/1184020052539844/task/1211292942830085)
* **Ticket Priority:** P2
* **Client Name:** Krungsri Auto
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client integrated a Deeplink into TikTok ads, but upon clicking the link, it does not directly navigate to the add friend page. Instead, users must click "back to LINE" to reach the intended page. The client inquired whether this is a limitation of the TikTok app or an issue with our system.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 5443
  * MAAC bot ID: 4329
* **Reproduction Steps:**
  * Place a Deeplink in TikTok ads.
  * Click the link within the TikTok app.
  * Observe that it does not directly open the add friend page.
* **User Questions:**
  * Is this behavior a limitation of the TikTok app?
  * Is there an issue with our Deeplink functionality?
* **Expected vs Actual Behavior:**
  * **Expected:** Clicking the Deeplink should directly open the LINE add friend page.
  * **Actual:** Users are directed to an in-app browser and must manually navigate back to LINE.

### 3. Root Cause & Solution

* **Root Cause:**
  * The behavior is attributed to TikTok's in-app browser mechanism. TikTok's in-app browser opens LINE Universal Links within itself, which prevents direct launching of the LINE app. This is a limitation of TikTok's platform and not an issue with the MAAC Deeplink functionality.
* **Solution:**
  * No engineering changes are required for the Deeplink.
  * Suggested workarounds for clients:
    1. Advise users to open the link in an external browser by tapping "..." in the TikTok in-app browser.
    2. Provide clear instructions within the ad to guide users on how to navigate back to LINE.

***

## Investigation of Message Delivery Failure in Customer Journey

**Metadata**

* **Feature:** MAAC-Deeplink
* **Created At:** 2025-08-28
* **Asana Task ID:** [1211168364860701](https://app.asana.com/1/1184020052539844/task/1211168364860701)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported that a user who clicked a MAAC deep link and was subsequently tagged did not receive the expected message from the associated campaign. The client confirmed the user had clicked the deep link.

### 2. Context & Details

* **Environment:**
  * The client is running an on-site campaign using a deep link configured in MAAC.
  * The affected user was tagged with "2508宝箱\_300pt" after clicking the deep link.
* **User Questions:**
  * Why did the tagged user not receive the message?
* **Reproduction Steps:**
  1. User clicks on the MAAC deep link.
  2. User is tagged within the campaign.
  3. Expected message is not received by the user.
* **Expected vs Actual Behavior:**
  * **Expected:** The tagged user should receive the "Existing contacts message" from the campaign.
  * **Actual:** The user did not receive the message despite being tagged.

### 3. Root Cause & Solution

* **Root Cause:**
  * The investigation revealed that the message scheduled for the affected user failed to send due to the client's MAAC account exceeding its monthly message sending limit.
* **Solution:**
  * The issue was identified as a result of the client's monthly message quota being exceeded, not a product defect. The client has been informed of the specific reason for the message delivery failure. No engineering changes or product fixes are required. Clients should monitor their message sending limits to prevent future occurrences.
