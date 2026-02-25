# game\_asana\_history\_knowledge\_base\_final

## Investigation of Consolation Message Delivery Failure in MAAC-Game Interaction

**Metadata**

* **Feature:** MAAC-Game interaction
* **Created At:** 2026-01-21
* **Asana Task ID:** [1212885006771031](https://app.asana.com/1/1184020052539844/task/1212885006771031)
* **Ticket Priority:** P3
* **Client Name:** Renishaw
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

A specific user did not receive a consolation message after playing a game and not winning. The incident occurred on January 21 at 10:05.

### 2. Context & Details

* **Environment Conditions:**
  * LINE UID: \[REDACTED\_ID]
  * MAAC ID: \[REDACTED\_ID]
  * Game: "Full Horsepower Draw Good Lot" testing (ID: 7061)
  * Consolation message template ID: 145418
  * MAAC org ID: 5677
  * MAAC bot/channel ID: 4583
  * Channel Type: LINE
  * Affected contact ID: \[REDACTED\_ID]
  * Happened time: 1/21 10:05
* **Reproduction Steps:**
  * The issue could not be reproduced. The same template settings were tested on a different account and messages were sent successfully.
* **Expected vs Actual Behavior:**
  * Expected: User receives a consolation message after not winning.
  * Actual: User did not receive the message.

### 3. Root Cause & Solution

* **Root Cause:**
  * The user closed the LINE Front-end Framework (LIFF) without clicking the "Back to LINE" button after not winning. The Redeem API, which sends messages for "no prize" scenarios, requires this click.
* **Solution:**
  * This behavior aligns with the current product design and is not a system bug. A product optimization item has been logged to evaluate implementing automatic sending of consolation messages for "no prize" scenarios. The status has been reviewed and documented, and a product optimization backlog item has been created.

***

## Investigation of Lottery Access Issues During High Traffic

**Metadata**

* **Feature:** MAAC-Game interaction
* **Created At:** 2026-01-05
* **Asana Task ID:** [1212657255744054](https://app.asana.com/1/1184020052539844/task/1212657255744054)
* **Ticket Priority:** P2
* **Client Name:** ホテラバ
* **Resolution Owner:** N/A
* **Result Breakdown:** Fix Problems

### 1. Issue Description

Between 6:30 PM and 7:15 PM (JST) on January 5, 2026, some users were unable to participate in the lottery due to high network traffic. The initial assessment indicated that this was not a system error. The client requested a review and consideration of preventive measures to avoid similar occurrences in future campaigns.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 80
  * MAAC bot ID: 79
  * Game ID: 8qO3Dq7
  * Game URL: line://app/\[REDACTED\_PHONE]-DklbOdVn?gid=l8qO3Dq7
  * Occurrence Time: 2026/01/05 18:30\~19:15 (JST)
* **Reproduction Steps:**
  * The issue was reproducible during the specified time frame.
* **Expected vs Actual Behavior:**
  * Expected: Users should be able to access and play the lottery without interruption.
  * Actual: Users experienced access issues due to high traffic.

### 3. Root Cause & Solution

* **Root Cause:**
  * The 'sforzando-http-api' game service lacked sufficient capacity to handle peak traffic, resulting in service unavailability.
* **Solution:**
  * KEDA auto-scaling was enabled for the 'sforzando-http-api' service in both Taiwan and Japan environments. This adjustment allows the service to dynamically scale its capacity to manage traffic peaks effectively for all clients and game features. The issue has been resolved.

***

## How to Extend Expiry Date of Current Game in MAAC

**Metadata**

* **Feature:** MAAC-Game interaction
* **Created At:** 2025-12-30
* **Asana Task ID:** [1212615718793669](https://app.asana.com/1/1184020052539844/task/1212615718793669)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** JY
* **Result Breakdown:** Task-Ticket

### 1. Issue Description

The client extended their contract until June 30, 2026. Adjustments were made in Django, but assistance is needed to modify the permissions of the existing game module to accommodate the extension.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC organization ID: 824
  * MAAC bot ID: 728
* **User Questions:**
  * How can the game module permissions be adjusted to reflect the extended contract?
* **Reproduction Steps:**
  * Contract extended to June 30, 2026.
  * Adjustments made in Django.
  * Permissions of the game module need modification.
* **Expected vs Actual Behavior:**
  * Expected: CSMs should be able to extend the feature/subscription validity dates directly within MAAC.
  * Actual: Manual backend database updates and cache clearing by engineering are required.

### 3. Root Cause & Solution

* **Root Cause:**
  * The MAAC system lacks a self-service or admin tool for CSMs to manage customer feature validity. The current process depends on high-privilege manual database modifications and delayed cache refresh.
* **Solution:**
  * The validity date was manually extended and verified in MAAC.
* **Suggested Actions:**
  * Develop an admin tool or enhance MAAC to allow authorized personnel to extend "Validity ended at".
  * Implement immediate cache invalidation for these changes.
  * Clarify the management of "Validity ended at" versus "Activity ended at".

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
  * Time of Occurrence: \[REDACTED]
  * Feature ID: \[REDACTED]
  * Reproducibility: \[REDACTED]
* **User Questions:**
  * None specified.
* **Reproduction Steps:**
  * Not provided.
* **Expected vs Actual Behavior:**
  * Expected: Game Module should function without interruptions.
  * Actual: Game Module is not functioning as expected.

### 3. Root Cause & Solution

* **Root Cause:**
  * System capacity reached its limit, specifically due to memory shortage, leading to system instability or degraded performance.
* **Solution:**
  * System alerts have been added to monitor resource usage.
  * An ongoing effort is in place to identify and clear temporary files to prevent future occurrences.
* **Status:**
  * Resolved.

***

## How to Extend Game Expiry Time in MAAC/Game Interaction

**Metadata**

* **Feature:** MAAC-Game interaction
* **Created At:** 2025-11-25
* **Asana Task ID:** [1212084973901131](https://app.asana.com/1/1184020052539844/task/1212084973901131)
* **Ticket Priority:** P2
* **Client Name:** ACCA KAPPA
* **Resolution Owner:** Tracy
* **Result Breakdown:** Task-Ticket

### 1. Issue Description

The current game needs to be retained, requiring an adjustment of the existing game's expiry date to March 1st. System permissions have already been extended.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org id / CAAC org id: 6224
  * MAAC bot / CAAC channel ID: 6032
* **User Questions:**
  * How can the game expiry date be extended to align with customer billing cycles?
* **Reproduction Steps:**
  * Identify the current expiry date of the game.
  * Attempt to extend the expiry date manually.
* **Expected vs Actual Behavior:**
  * Expected: Game expiry dates should automatically align with billing cycles.
  * Actual: Manual intervention is required to adjust expiry dates.

### 3. Root Cause & Solution

* **Root Cause:** The current product design does not automatically synchronize game availability periods with the actual billing purchase periods. This design gap necessitates manual adjustments, similar to a previously resolved issue for award management.
* **Solution:** Implement an automated mechanism to link game availability periods directly to their corresponding billing purchase periods. This will eliminate the need for manual adjustments and ensure consistent data alignment. This solution is foundational for future integrations.

***

## Investigation of Pointer Behavior in Spin Game Module

**Metadata**

* **Feature:** MAAC-Game interaction
* **Created At:** 2025-11-14
* **Asana Task ID:** [1211944615384056](https://app.asana.com/1/1184020052539844/task/1211944615384056)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Limit information

### 1. Issue Description

An unexpected situation was reported where, despite setting a condition for no prize, the pointer in the spin game module still lands on a LINE point after prizes are exhausted. The understanding is that this occurs because the prize is depleted, causing the pointer to land on the exhausted prize and display a message. The client expressed concern that this mechanism affects the perception of winners and inquired if the product mechanism could be adjusted.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 608
  * MAAC bot / CAAC channel ID: 600
* **User Questions:**
  * Is the understanding correct that the pointer lands on an exhausted prize due to prize depletion?
  * Can the product mechanism be adjusted to improve user perception?
* **Reproduction Steps:**
  * Set up a spin game with a condition for no prize.
  * Exhaust all available prizes.
  * Observe the pointer landing on the exhausted prize.
* **Expected vs Actual Behavior:**
  * Expected: The pointer should not land on a prize once it is exhausted.
  * Actual: The pointer lands on the exhausted prize and displays a message.

### 3. Root Cause & Solution

* **Root Cause:** The root cause was identified as insufficient campaign and prize details provided by the customer or Customer Success, making it impossible to identify and troubleshoot the specific MAAC configuration.
* **Solution:** No technical solution was applied. The ticket was closed by Customer Success as the customer stopped using the related feature. For future similar reports, complete details including campaign ID, prize name, and relevant product area are required for diagnosis.

***

## How to Extend Game Expiration Time in MAAC/Game Interaction

**Metadata**

* **Feature:** MAAC-Game interaction
* **Created At:** 2025-11-12
* **Asana Task ID:** [1211922179396606](https://app.asana.com/1/1184020052539844/task/1211922179396606)
* **Ticket Priority:** P2
* **Client Name:** 國泰健康管理
* **Resolution Owner:** N/A
* **Result Breakdown:** Task-Ticket

### 1. Issue Description

The client attempted to extend the expiration date of a game from December 1 to January 1. Although the overall game period was updated, the internal game layer still displayed the original expiration date, and the client was unable to modify it further.

### 2. Context & Details

* **Environment:** The issue occurred within the MAAC/Game interaction platform.
* **User Actions:**
  * The client initially updated the game expiration date in the billing section to January 1.
  * Despite this change, the internal game layer continued to show the expiration date as December 1.
  * Attempts to modify individual game activities did not reflect the updated expiration date.
* **Reproduction Steps:**
  1. Access the game billing section and update the expiration date.
  2. Verify the change in the overall game period.
  3. Check the internal game layer for consistency.
* **Expected vs Actual Behavior:**
  * **Expected:** The expiration date should be consistently updated across all game layers.
  * **Actual:** The internal game layer did not reflect the updated expiration date.

### 3. Root Cause & Solution

* **Root Cause:** The Customer Success Manager attempted to resolve the issue by directly modifying 'Activity' data in the database, bypassing intended permission controls. This indicates insufficient permission restrictions.
* **Solution:** The game durations were successfully extended to January 1, 2026. It is recommended to review and tighten permission controls for frontline Customer Success staff to prevent direct modification of 'Activity' data. Additionally, reinforce operational procedures to ensure proper handling of such tasks.

***

## Investigation of Missing Prize Button in Spin Wheel Feature

**Metadata**

* **Feature:** MAAC-Game interaction
* **Created At:** 2025-10-15
* **Asana Task ID:** [1211645389697787](https://app.asana.com/1/1184020052539844/task/1211645389697787)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

During testing of the spin wheel feature, the prize button did not appear after a prize was won. Consequently, the prize could not be displayed in the official account, preventing prize collection.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 3619
  * MAAC bot ID: 3029
  * Feature ID: \[REDACTED\_UUID]
  * Test link: line://app/\[REDACTED\_PHONE]-zJ8DRwae?gid=y2jOd51Y
* **User Questions:**
  * How can the issue be resolved?
  * What steps are needed to ensure the feature is ready for the client's scheduled launch?
* **Reproduction Steps:**
  * The issue can be reproduced through testing.
* **Expected vs Actual Behavior:**
  * Expected: After winning a prize, a button should appear to claim the prize, which should then be displayed in the official account.
  * Actual: The prize button did not appear, and the prize was not displayed in the official account.

### 3. Root Cause & Solution

* **Root Cause:**
  * Unknown. There are suspected logic errors in the game module's status validation or intermittent backend service issues affecting specific instances.
* **Solution:**
  * Investigate the status validation logic and service health of the MAAC game module for Org 3619.
  * Prioritize reviewing the campaign period logic and error handling for "game too popular" scenarios.
  * Status: Ongoing investigation.

***

## Investigation of Discrepancy in Roulette Points Display

**Metadata**

* **Feature:** MAAC-Game interaction
* **Created At:** 2025-10-13
* **Asana Task ID:** [1211620875047657](https://app.asana.com/1/1184020052539844/task/1211620875047657)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Limit information

### 1. Issue Description

The client reported that during a roulette game, 68 customers experienced a discrepancy where the wheel landed on 88 points, but only 10 points were displayed.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 4478
  * MAAC bot ID: 3613
  * Feature ID: \[REDACTED\_UUID]
  * The issue cannot be reproduced as the feature is currently paused.
* **User Questions:**
  1. Is this a game design bug, and can it be fixed?
  2. Is there an error in the customer settings, and if so, how should it be adjusted?
* **Reproduction Steps:**
  * The issue is not reproducible due to the feature being paused.
* **Expected vs Actual Behavior:**
  * Expected: The roulette should display the correct points as per the wheel's landing.
  * Actual: The wheel displayed 88 points, but only 10 points were shown.

### 3. Root Cause & Solution

* **Root Cause:**
  * The system displays prizes based on fixed positions defined by an internal template, not according to the custom background image's visual layout. There is no validation or warning mechanism when a custom image with a differing layout is uploaded.
* **Solution:**
  * Advise the customer to use a background image that matches the system's internal template layout for prize slots.
  * For future development, implement a mechanism to validate custom roulette wheel background images upon upload or allow dynamic prize positioning.

***

## Investigation of Non-Responsive "Use Default Image" Button in UI

**Metadata**

* **Feature:** MAAC-Game interaction
* **Created At:** 2025-10-13
* **Asana Task ID:** [1211620694707091](https://app.asana.com/1/1184020052539844/task/1211620694707091)
* **Ticket Priority:** P2
* **Client Name:** ALL
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The "Use Default Image" button in the gamification template settings does not respond when clicked. This issue prevents users from accessing design templates, which are necessary for understanding prize positions or other potential optimizations.

### 2. Context & Details

* **Environment Conditions:**
  * The issue occurs within the gamification module of the MAAC platform.
  * The problem is reproducible.
* **User Questions:**
  * Why is the "Use Default Image" button non-responsive?
  * Should the outdated "Download Instruction Manual" link be removed or updated?
* **Reproduction Steps:**
  1. Navigate to the gamification template settings.
  2. Attempt to click the "Use Default Image" button.
  3. Observe that no action occurs.
* **Expected vs Actual Behavior:**
  * **Expected:** Clicking the "Use Default Image" button should download or apply a default design template.
  * **Actual:** The button does not perform any action.

### 3. Root Cause & Solution

* **Root Cause:**
  * The system design does not currently support the direct download of example design templates. The "Use Default Image" button is present but lacks functionality.
  * The "Download Instruction Manual" link is outdated and does not reflect the current UI or direct users to the help center.
* **Solution:**
  * Remove the non-functional "Use Default Image" button from the gamification template settings.
  * Assess the need and priority for developing a design template download feature. If deemed necessary, ensure the feature is implemented with proper functionality.
  * Update the "Download Instruction Manual" link to direct users to the current and relevant documentation in the Help Center.

***

## Investigation of Prize Probability Settings in MAAC Game Wheel

**Metadata**

* **Feature:** MAAC-Game interaction
* **Created At:** 2025-10-01
* **Asana Task ID:** [1211518421563963](https://app.asana.com/1/1184020052539844/task/1211518421563963)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Jack Lee
* **Result Breakdown:** Fix Problems

### 1. Issue Description

Users experienced an issue where the game wheel continued to land on a prize with a 0% probability, despite the prize being depleted. This resulted in a "prize depleted" message, causing customer dissatisfaction as the game did not redirect to available prizes.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 4478
  * MAAC bot: 3613
  * Feature ID: \[REDACTED\_UUID]
  * Occurrence Date: 2025-10-01
* **User Questions:**
  * How can the game be configured to avoid landing on prizes with a 0% probability?
  * Why is there a discrepancy between the number of spins (6322) and the number of wins (3697)?
* **Reproduction Steps:**
  1. Set the prize probability to 0% for a specific prize.
  2. Spin the game wheel.
  3. Observe the wheel landing on the 0% probability prize and displaying a "prize depleted" message.
* **Expected vs Actual Behavior:**
  * **Expected:** The wheel should not land on prizes with a 0% probability.
  * **Actual:** The wheel lands on the 0% probability prize, displaying a "prize depleted" message.

### 3. Root Cause & Solution

* **Root Cause:**
  1. The backend drawing algorithm did not exclude prizes with a 0% probability or those already depleted.
  2. The frontend contained deprecated logic that visually redirected the wheel to a 0% probability prize slot when any drawn prize was depleted.
* **Solution:**
  1. The backend was updated to ensure only prizes with a probability greater than 0% are drawn.
  2. The deprecated frontend logic was removed, ensuring the wheel accurately reflects the drawn prize's status.

The issue has been resolved with these updates.

***

## How to Extend Game Expiry Time for Renewed Clients in MAAC

**Metadata**

* **Feature:** MAAC-Game interaction
* **Created At:** 2025-09-30
* **Asana Task ID:** [1211507309411813](https://app.asana.com/1/1184020052539844/task/1211507309411813)
* **Ticket Priority:** P2
* **Client Name:** N/A
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

Customer Success Managers (CSMs) were unable to extend the duration of existing MAAC games for a client who renewed their subscription. The games did not reflect the extended billing period.

### 2. Context & Details

* **Environment:** MAAC platform, client renewal scenario.
* **User Question:** How to extend the expiry time of existing games to match the renewed subscription period.
* **Reproduction Steps:**
  1. Client renews subscription for an additional quarter.
  2. Attempt to extend the expiry time of existing games in the MAAC interface.
* **Expected Behavior:** Existing games should automatically reflect the new billing duration.
* **Actual Behavior:** Existing games did not update to reflect the extended subscription period.

### 3. Root Cause & Solution

* **Root Cause:** The issue stems from the design of the MAAC game system. Existing games do not automatically inherit new billing durations; only newly created games do. This is a known gap in the product functionality.
* **Solution:** The specific client issue was resolved through backend adjustments or by creating new games. It is recommended to implement a feature that automatically links game duration to the billing period to prevent future occurrences.
* **Status:** Resolved. The product gap remains open for further development.

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

The system displayed incorrect messages during a lucky draw event. Specifically, after drawing a prize, the system showed the prize as "discontinued," and when drawing a "no prize" result, it incorrectly displayed "prizes exhausted" instead of the intended "better luck next time" message.

### 2. Context & Details

* **Environment Conditions:**
  * Event: Invite friends to draw LINE POINTS\_test (id: 6587).
  * Prizes involved:
    * Prize 1: 10 points, 666 available.
    * Prize 3: 10 points, 667 available.
    * Prize 5: 10 points, 666 available.
  * Non-winning outcomes: Prizes 2, 4, 6.
* **User Questions:**
  * Why does the system show a prize as discontinued when it should be available?
  * Why does the system display "prizes exhausted" instead of "better luck next time" for non-winning draws?
* **Reproduction Steps:**
  1. Conduct a lucky draw event.
  2. Draw a prize and observe the message displayed.
  3. Draw a "no prize" result and observe the message displayed.
* **Expected vs Actual Behavior:**
  * Expected: Winning a prize should show the prize details; a "no prize" result should display "better luck next time."
  * Actual: Winning a prize showed "prize discontinued"; "no prize" result showed "prizes exhausted."

### 3. Root Cause & Solution

* **Root Cause:**
  * The backend logic for the lucky draw feature misinterpreted 'no prize' configurations as 'prizes exhausted'. This was due to 'no prize' options having an implicit quantity of 0, which the system incorrectly treated as an exhausted prize. The logic failed to differentiate between a true 'prizes exhausted' scenario and a 'no prize' outcome.
* **Solution:**
  * The backend logic was adjusted to correctly identify 'no prize' outcomes by checking for the absence of a prize\_setting\_id in the detail field, rather than relying solely on a prize quantity of 0.
  * The updated logic has been deployed and verified by the client, confirming the issue is resolved.
