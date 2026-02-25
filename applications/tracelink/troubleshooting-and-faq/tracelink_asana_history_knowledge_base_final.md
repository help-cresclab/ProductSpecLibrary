# tracelink\_asana\_history\_knowledge\_base\_final

## Investigation of ID Binding Failure via CLID in MAAC Tracelink

**Metadata**

* **Feature:** MAAC-Tracelink
* **Created At:** 2026-01-30
* **Asana Task ID:** [1213035004023033](https://app.asana.com/1/1184020052539844/task/1213035004023033)
* **Ticket Priority:** P3
* **Client Name:** ホテラバ
* **Resolution Owner:** N/A
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

When a user navigates to the URL via the tracking link (maac.io) set in the Rich Menu, the CLID is not appended. Consequently, the UID is not being bound to the Customer ID in their CRM system. However, when opening a URL with the CLID parameter manually appended directly in the browser, the ID binding completes successfully.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org id: 80
  * MAAC bot: 79
  * Channel Type: LINE
  * Affected contact id: \[REDACTED\_ID]
  * MAAC ID: \[REDACTED\_ID]
  * Richmenu name: \[Richmenu URL]
  * Tracelink name: \[Tracelink URL]
  * URL: \[REDACTED\_URL]
* **Reproduction Steps:**
  * Navigate to the URL via the tracking link in the Rich Menu.
  * Observe that the CLID is not appended.
  * Manually append the CLID parameter in the browser and observe successful ID binding.
* **Expected vs Actual Behavior:**
  * **Expected:** CLID should be appended automatically when navigating via the tracking link, allowing UID to bind with the Customer ID.
  * **Actual:** CLID is not appended, preventing the binding process.

### 3. Root Cause & Solution

* **Root Cause:** CLID tracking for bot 79 (MAAC ID: \[REDACTED\_ID] was disabled in system settings.
* **Solution:** CLID tracking for bot 79 was enabled in the Django admin. Customer Success Managers (CSMs) should refer to the CLID Standard Operating Procedure (SOP) and use Metabase's "Debug Liff Redirect view" for future investigations. The issue is now resolved.

***

## Investigation of Tracelink Redirection to Welcome Message

**Metadata**

* **Feature:** MAAC-Tracelink
* **Created At:** 2026-01-09
* **Asana Task ID:** [1212716056060047](https://app.asana.com/1/1184020052539844/task/1212716056060047)
* **Ticket Priority:** P4
* **Client Name:** N/A
* **Resolution Owner:** Tracy
* **Result Breakdown:** Limit information

### 1. Issue Description

The unexpected situation involves a broadcast link that, when clicked, redirects to a welcome message instead of the expected content. This issue was confirmed during customer service testing.

### 2. Context & Details

* **Environment:**
  * Broadcast URL: \[https://maac.cresclab.com/broadcast/line/\[REDACTED\_PATH]
* **Reproduction Steps:**
  * Click on the final image in the broadcast.
  * Observe the redirection to a welcome message.
* **Expected vs Actual Behavior:**
  * **Expected:** Clicking the image should lead to the intended content.
  * **Actual:** Clicking the image leads to a welcome message.
* **Additional Information:**
  * The issue was reproducible during internal testing.
  * No specific user identifiers or detailed user flow were provided.

### 3. Root Cause & Solution

* **Root Cause:**
  * The root cause cannot be determined due to insufficient information. The issue may be related to system design or a bug, but further details are required.
* **Solution:**
  * The engineering team requires detailed reproduction steps and specific user identifiers to investigate further. The ticket has been closed pending additional information from the customer.

***

## Investigation of LIFF Opening Failure Due to External Redirect

**Metadata**

* **Feature:** MAAC-Tracelink
* **Created At:** 2025-12-17
* **Asana Task ID:** [1212486166756322](https://app.asana.com/1/1184020052539844/task/1212486166756322)
* **Ticket Priority:** P3
* **Client Name:** Louis vuitton
* **Resolution Owner:** Noel
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The customer reported that despite disabling the "redirect to external browser" setting, a MAAC short URL intended to open a LIFF was still redirecting to an external browser on an iPhone 13, causing the LIFF to fail to open.

### 2. Context & Details

* **Environment:**
  * Device: iPhone 13
  * LINE Version: 15.20.4
* **Reproduction Steps:**
  * The customer accessed the MAAC short URL: `https://maac.io/52vza`.
  * The URL redirected to an external browser instead of opening the LIFF.
* **Expected vs Actual Behavior:**
  * **Expected:** The LIFF should open within the LINE app.
  * **Actual:** The URL redirected to an external browser, and the LIFF failed to open.
* **Additional Information:**
  * The issue was intermittent and could not be consistently reproduced by internal teams.
  * Customer Success (CS) was able to open the link without issues.

### 3. Root Cause & Solution

* **Root Cause:**
  * The issue could not be reproduced by internal Product Ops, Customer Success, or Engineering teams. It is suspected to be caused by a client-side specific local cache or a transient device state.
* **Solution:**
  * The customer was advised to clear the cache of their LINE application. This resolved the issue, and no further action or code changes were necessary.

***

## Investigation of Incorrect URL Generation in MAAC-Tracelink

**Metadata**

* **Feature:** MAAC-Tracelink
* **Created At:** 2025-12-15
* **Asana Task ID:** [1212440779412548](https://app.asana.com/1/1184020052539844/task/1212440779412548)
* **Ticket Priority:** P4
* **Client Name:** Buty99
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The client reported that during the period of 12/09 from 18:00 to 18:30, they created three URLs containing UTM parameters. However, instead of receiving newly generated URLs, they were provided with previously created URLs. The discrepancy was noted in the `utm_campaign` parameter. Specifically, the client attempted to create a URL with `utm_campaign=PUSH_20251209` but received a URL with `utm_campaign=PUSH20251110`, which was created in November.

### 2. Context & Details

* **Environment Conditions:**
  * Date of issue: 12/09
  * Time of issue: 18:00 to 18:30
  * URLs involved contained UTM parameters.
* **User Questions:**
  * Can the logs confirm if the `utm_campaign=PUSH_20251209` link was correctly generated and displayed?
* **Reproduction Steps:**
  * Attempt to create a URL with a specific `utm_campaign` parameter.
  * Observe if the generated URL matches the expected campaign parameter.
* **Expected vs Actual Behavior:**
  * **Expected:** A new URL with `utm_campaign=PUSH_20251209` should be generated.
  * **Actual:** A URL with `utm_campaign=PUSH20251110` was received instead.

### 3. Root Cause & Solution

* **Root Cause:**
  * The root cause is currently undetermined due to the inability to verify the client's operation records. There is uncertainty whether the issue is due to a system design flaw or a bug. The logs do not provide sufficient evidence to confirm the client's report.
* **Solution:**
  * Inform the client that no matching records were found in the MAAC system for the reported timeframe.
  * Request the client to verify the platform and details of their operations.
  * Develop a comprehensive audit log investigation playbook to assist in future verifications.

***

## Why Can't Users Open MAAC Deeplinks from Facebook Posts?

**Metadata**

* **Feature:** MAAC-Tracelink
* **Created At:** 2025-11-18
* **Asana Task ID:** [1211978338514071](https://app.asana.com/1/1184020052539844/task/1211978338514071)
* **Ticket Priority:** P2
* **Client Name:** N/A
* **Resolution Owner:** N/A
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

An Android user reported an inability to open a provided link. The user attached a screenshot showing the result after tapping the link.

### 2. Context & Details

* **Environment:** Android device
* **Reproduction Steps:**
  * User attempts to open a MAAC deeplink shared in a Facebook post.
* **Expected Behavior:** The link should open and function as intended.
* **Actual Behavior:** The link does not open or behave as expected.
* **Additional Information:**
  * URL involved: https://maac.io/4SQB
  * The same link was used in a Facebook post and broadcast.

### 3. Root Cause & Solution

* **Root Cause:** The MAAC deeplinks were functioning as designed. The issue arose from the customer's misunderstanding of the deeplink functionality and its intended behavior. No technical defect was identified.
* **Solution:** The misunderstanding has been clarified. No product or engineering action is required for this specific incident. It is suggested to review user documentation for MAAC deeplinks to enhance clarity, especially regarding their use and expected behavior on external social media platforms.

***

## Investigation of Reauthorization Process for Existing LINE Users in MAAC Tracelink

**Metadata**

* **Feature:** MAAC-Tracelink
* **Created At:** 2025-11-05
* **Asana Task ID:** [1211847487255320](https://app.asana.com/1/1184020052539844/task/1211847487255320)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Task-Ticket

### 1. Issue Description

The MAAC tracelink mechanism does not prompt existing LINE users to reauthorize the LIFF page, preventing the collection of updated data such as phone numbers. This affects approximately 1.83 million contacts that the client wishes to target through MAAC Reach.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org id: 3521
  * MAAC bot: 2964
  * UU ID: \[REDACTED\_UUID]
* **User Questions:**
  * Is there a mechanism to enable a cookie feature that allows each friend to pass through the authorization page again upon clicking the tracelink?
* **Reproduction Steps:**
  1. Existing LINE users click on the tracelink.
  2. Users are not redirected to the LIFF authorization page due to existing cookie checks.
* **Expected vs Actual Behavior:**
  * **Expected:** Users should be redirected to the LIFF authorization page to update their data.
  * **Actual:** Users are not redirected, and their data remains outdated.

### 3. Root Cause & Solution

* **Root Cause:** The internal cookie check within the MAAC tracelink mechanism prevents previously authorized users from being redirected to the LINE LIFF authorization page.
* **Solution:**
  * **Option 1 (Customization):** Implement a feature flag to temporarily bypass the cookie check, forcing LIFF re-authorization. This is recommended for short-term use.
  * **Option 2 (Alternative):** Utilize a MAAC game module, which naturally bypasses the cookie check.

The client is currently evaluating these solutions and their associated costs.

***

## Investigation of Inconsistent Page Redirection in MAAC Rich Menu

**Metadata**

* **Feature:** MAAC-Tracelink
* **Created At:** 2025-10-22
* **Asana Task ID:** [1211713182842659](https://app.asana.com/1/1184020052539844/task/1211713182842659)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The MAAC rich menu contains two cells configured with the same TraceLink URL, yet they redirect to different final pages. Specifically, the 8th cell redirects to the homepage, while the 2nd cell redirects to the product page, which is the expected behavior.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 479
  * MAAC bot: 460
* **User Questions:**
  * Why do the two cells with the same URL lead to different pages?
* **Reproduction Steps:**
  * Access the rich menu with the specified TraceLink URL in both the 8th and 2nd cells.
  * Observe the redirection behavior.
* **Expected vs Actual Behavior:**
  * Expected: Both cells should redirect to the product page.
  * Actual: The 8th cell redirects to the homepage, while the 2nd cell redirects to the product page.

### 3. Root Cause & Solution

* **Root Cause:**
  * The TraceLink URL (https://maac.io/4Kh26) correctly redirects to the client's configured URL. The discrepancy arises from the client's landing page logic, which redirects users to different content based on internal conditions such as user status or cookies.
* **Solution:**
  * There is no issue with the MAAC platform. The client should investigate their landing page's redirect logic to ensure consistent behavior for the intended TraceLink.

***

## Investigation of Safari Incompatibility with MAAC Tracking Links on iOS

**Metadata**

* **Feature:** MAAC-Tracelink
* **Created At:** 2025-09-17
* **Asana Task ID:** [1211379820597016](https://app.asana.com/1/1184020052539844/task/1211379820597016)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** Tracy
* **Result Breakdown:** Not our issue

### 1. Issue Description

The issue involves iPhone users who are unable to open web pages via MAAC tracking links embedded in LINE rich menus when using Safari. This problem has been reported consistently over the past week, with more than five instances noted. The issue appears to have emerged following recent iOS updates.

### 2. Context & Details

* **Environment Conditions:**
  * iPhone users on iOS 18.7
  * Safari browser used for accessing links
* **User Questions:**
  * Why are the tracking links not opening in Safari?
* **Reproduction Steps:**
  1. Click on the MAAC tracking link in the LINE rich menu.
  2. Attempt to open the link using Safari.
* **Expected vs Actual Behavior:**
  * **Expected:** The web page should load successfully.
  * **Actual:** Safari displays an infinite loading spinner without displaying the destination page.

### 3. Root Cause & Solution

* **Root Cause:**
  * The issue is suspected to be an incompatibility between Safari on iOS 18.7 and MAAC's redirect mechanism. It may also involve the client's specific landing page components when accessed via MAAC redirect in Safari. This is identified as a recent regression.
* **Solution:**
  * Engineering is required to investigate the behavior of MAAC's redirect in Safari on iOS 18.7. The investigation should determine if the issue is due to MAAC's redirect process, the client's landing page compatibility with Safari, or a combination of both. This issue should be prioritized for an urgent fix.
