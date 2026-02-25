---
description: >-
  Troubleshooting knowledge base for MAAC Contacts. Covers LINE OA, CDH sync,
  webhooks, API import, display names, tags, and contact metrics.
---

# MAAC Contacts Troubleshooting Knowledge Base

This is an internal troubleshooting knowledge base for **MAAC Contacts** (Audience → Contacts).

It consolidates real investigations from **Asana tickets**. It focuses on **LINE OA** contact sync, **CDH** profile updates, **webhook** payload issues, **Contact Import API** failures, and common UI/metrics misunderstandings.

{% hint style="info" %}
**Search keywords (copy/paste)**

MAAC Contacts, contact sync, CDH synchronization, LINE OA, webhook, API import, contact name synchronizing, display name, original name, UID binding, CID unification, customer\_id, tag filter 400, contact import country code, last interaction, acquisition metrics zero
{% endhint %}

Common symptoms:

* Contact name stuck at **synchronizing**
* Contact display name inconsistent or unexpected
* Contact import/update via API fails
* Tag filter errors (e.g., **400 Bad Request**)
* Metrics show 0 or don’t match expectations
* LINE friend status shows **Auth** instead of **Following**

Related docs:

* [Feature Description｜MAAC Contact Import and Update – Crescendo Lab Help Center](../feature-overview/feature-description-maac-contact-import-and-update-crescendo-lab-help-center.md)
* [Feature Description｜Contact Field Explanation and Matching Logic – Crescendo Lab Help Center](../feature-overview/feature-description-contact-field-explanation-and-matching-logic-crescendo-lab-help-center.md)
* [PRD — Contact Profile Unification (MAAC)](../product-specifications/prd-contact-profile-unification-maac.md)

***

## MAAC Contacts - API import failure and contact name synchronizing (LINE OA token)

**Metadata**

* Feature: MAAC-Contact
* Created At: 2026-02-10
* Asana Task ID: [1213213099354367](https://app.asana.com/1/1184020052539844/task/1213213099354367)
* Ticket Priority: P4
* Client Name: \[REDACTED]
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

An official brand certified Official Account (OA) could not import contacts via the API. Contact names were not displayed and appeared as "synchronizing."

### Context & Details

* Environment:
  * Channel Type: LINE
  * Affected contact ID: \[REDACTED\_ID]
  * MAAC ID: \[REDACTED\_ID]
  * Happened time: 2026/02/10
* The issue can be reproduced consistently. ProductOps can reproduce it in the client organization.
* Developer confirmed integration was correctly set up.
* Screenshots and screen records were provided.

### Expected vs Actual

* Expected: Contacts import via API; names display correctly.
* Actual: API import failed; names shown as "synchronizing."

### Root Cause & Solution

* Root Cause: The LINE API token used for integration had expired or become invalid, causing import failure.
* Solution:
  * Manually refreshed the LINE API token in the Django admin panel — this immediately resolved the import failure.
  * Suggested next steps: investigate LINE API token management to enable automatic refresh before expiration; implement monitoring/alerts for token validity to avoid manual intervention.

***

## MAAC Contacts - Display name logic (display\_name vs original\_name, LINE channel entity)

**Metadata**

* Feature: MAAC-Contact
* Created At: 2026-02-04
* Asana Task ID: [1213072354903129](https://app.asana.com/1/1184020052539844/task/1213072354903129)
* Ticket Priority: P4
* Client Name: 新東陽
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

Client expected the "channel entity name" in the contact list to remain static (original channel name). Instead the display name appeared dynamic or different.

### Context & Details

* Environment:
  * MAAC org ID: 6323
  * MAAC bot ID: 6331
  * Channel Type: LINE
* User expectation: Both the `display_name` and the original LINE user name should be visible simultaneously in MAAC/CAAC.
* When importing and overwriting `display_name` via the MAAC UI, both relevant data fields are overwritten.

### Expected vs Actual

* Expected: Static display of the original channel name.
* Actual: Display name is dynamic and can differ from the original channel name.

### Root Cause & Solution

* Root Cause: System design prioritizes `display_name` from the contact profile for both MAAC member and channel entity names. `original_name` from the channel is shown only if `display_name` is empty/not provided. This aligns with intended design.
* Solution: Clarified display logic to CSM team and client. No code changes required. Consider documentation/UI improvements to clarify prioritization.

Status: Resolved by clarification.

***

## MAAC Contacts - Last interaction not updated (Rapid Fan Growth)

**Metadata**

* Feature: MAAC-Contact
* Created At: 2026-01-08
* Asana Task ID: [1212704522210445](https://app.asana.com/1/1184020052539844/task/1212704522210445)
* Ticket Priority: P4
* Client Name: BOARDRIDERS
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

"Last Interaction" time recorded as 2025-05-18, but a customer participating in Rapid Fan Growth and redeeming a prize on 2025-12-11 did not update the "Last Interaction" field.

### Context & Details

* Environment:
  * MAAC org ID: 4650
  * MAAC bot ID: 3741
* Question: Why was the interaction not recorded in "Last Interaction"?

### Reproduction Steps

{% stepper %}
{% step %}
### Step

Customer participates in the Rapid Fan Growth game.
{% endstep %}

{% step %}
### Step

Customer redeems a prize.
{% endstep %}
{% endstepper %}

### Expected vs Actual

* Expected: "Last Interaction" should update to prize redemption date.
* Actual: "Last Interaction" remained unchanged.

### Root Cause & Solution

* Root Cause: "Last Interaction" logs only direct interactions with MAAC platform features (e.g., sending messages or triggering auto-replies). Rapid Fan Growth actions are outside this definition.
* Solution: System functions as designed; no code changes required. Clarified the metric scope to stakeholders.

***

## MAAC Contacts - UID binding issues and contact merge (CID as unification key)

**Metadata**

* Feature: MAAC-Contact
* Created At: 2026-01-08
* Asana Task ID: [1212704108191283](https://app.asana.com/1/1184020052539844/task/1212704108191283)
* Ticket Priority: P4
* Client Name: \[REDACTED]
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

Different UIDs were linked to a single contact account; modifying one UID affected the other. Need to separate accounts.

### Context & Details

* Environment:
  * MAAC org ID: 6018
  * MAAC bot ID: 5323

### Reproduction Steps

{% stepper %}
{% step %}
### Step

Two different UIDs are linked to a single contact account.
{% endstep %}

{% step %}
### Step

Modify one UID and observe that changes affect the other UID.
{% endstep %}
{% endstepper %}

### Expected vs Actual

* Expected: Each UID operates independently.
* Actual: Changes to one UID modify the other due to shared linkage.

### Root Cause & Solution

* Root Cause: "CID as unification key" was enabled in CDH settings, causing merging of contacts sharing the same CID.
* Solution:
  * Assign a unique CID to one contact to separate them.
  * Disable "CID as unification key" in CDH to prevent unintended merges.

***

## MAAC Contacts - Welcome message shows New Friend (LINE profile sync delay)

**Metadata**

* Feature: MAAC-Contact
* Created At: 2026-01-08
* Asana Task ID: [1212703625992711](https://app.asana.com/1/1184020052539844/task/1212703625992711)
* Ticket Priority: P2
* Client Name: N/A
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

Welcome messages for new LINE contacts display "New Friend" instead of actual contact names.

### Context & Details

* Environment:
  * MAAC org ID: 3786
  * Issue occurs with new LINE contacts.
* Reproduction Steps:
  * Add a new contact in LINE.
  * Observe the MAAC welcome message.

### Expected vs Actual

* Expected: Welcome message includes actual contact name.
* Actual: Displays "New Friend."

### Root Cause & Solution

* Root Cause: 0.5–1 second delay in CDH synchronization for LINE contact names. Welcome messages are sent before profile name data is available in MAAC.
* Solution:
  * CSMs should advise customers to temporarily remove the contact name field from new-friend welcome messages.
  * Engineering to optimize CDH synchronization so profile data is available prior to message sending (ongoing technical project).

***

## MAAC Contacts - Tag filter error 400 Bad Request

**Metadata**

* Feature: MAAC-Contact
* Created At: 2025-12-26
* Asana Task ID: [1212593890270662](https://app.asana.com/1/1184020052539844/task/1212593890270662)
* Ticket Priority: P4
* Client Name: Infineon 英飛凌
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

Client encountered an unexpected error when attempting to filter tags on the MAAC contact page.

### Context & Details

* Environment:
  * MAAC org ID: 5266
  * MAAC bot ID: 4183
  * Client: Infineon TW (英飛凌台灣)
* Reproduction Steps: Issue could not be reproduced internally by Product Owners and CSMs.
* Observed: "400 Bad Request" error in browser console.

### Expected vs Actual

* Expected: Successful filtering of contacts using tags.
* Actual: "400 Bad Request" error observed intermittently.

### Root Cause & Solution

* Root Cause: Likely intermittent client-side issue (temporary network/caching) or timing problem where newly created tags not immediately available. "400" suggests malformed request or invalid input/state at that moment. Could not reproduce internally; systemic bug less likely.
* Solution:
  * Advise client to refresh the page, clear browser cookies, and retry.
  * If persistent, engineering should review MAAC and CDH audit logs around incident time for tag sync/filtering errors.

***

## MAAC Contacts - Acquisition metrics show zero (real-time data)

**Metadata**

* Feature: MAAC-Contact
* Created At: 2025-12-25
* Asana Task ID: [1212585549859625](https://app.asana.com/1/1184020052539844/task/1212585549859625)
* Ticket Priority: P2
* Client Name: Zurquiz
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

Acquisition metrics for 2025-12-24 displayed as zero across multiple accounts despite expectations of non-zero values.

### Context & Details

* Environment:
  * MAAC org ID: 5967
  * MAAC bot/channel ID: 5058
* Observations: Values expected to be real-time showed zero across accounts.

### Reproduction Steps

* Access acquisition metrics for 2025-12-24 and observe displayed value.

### Expected vs Actual

* Expected: Real-time acquisition numbers.
* Actual: Zero displayed.

### Root Cause & Solution

* Root Cause: Undetermined. Issue appeared transient and self-resolved.
* Solution: No action taken. Recommend monitoring metrics for recurrence.

***

## MAAC Contacts - Slow contact search with filters (background processing)

**Metadata**

* Feature: MAAC-Contact
* Created At: 2025-12-25
* Asana Task ID: [1212584013956004](https://app.asana.com/1/1184020052539844/task/1212584013956004)
* Ticket Priority: P4
* Client Name: Insurverse
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

Slow loading and errors when searching contacts using filters, reproducible across accounts.

### Context & Details

* Environment:
  * MAAC org ID: 4811
* Users experience delays and errors when applying filters.

### Reproduction Steps

* Apply filters to search contacts in MAAC and observe load time and errors.

### Expected vs Actual

* Expected: Prompt loading without errors.
* Actual: Noticeable delay and occasional errors.

### Root Cause & Solution

* Root Cause: Deeplink processing for updating contacts occurs in background and takes \~2–3 minutes; this is expected after system optimizations. No bugs identified.
* Solution: Monitor Contact List for significant delays. If persistent, open engineering evaluation. Currently closed with no action required.

***

## MAAC Contacts - Blocked contacts count discrepancy (MAAC vs LINE CMS)

**Metadata**

* Feature: MAAC-Contact
* Created At: 2025-12-25
* Asana Task ID: [1212571876611200](https://app.asana.com/1/1184020052539844/task/1212571876611200)
* Ticket Priority: P2
* Client Name: Krungsri Simple
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

Discrepancy in blocked contacts trend between MAAC and LINE CMS over a month: MAAC increased; LINE CMS decreased.

### Context & Details

* Environment:
  * MAAC org ID: 5505
  * MAAC bot/channel ID: 4421

### Reproduction Steps

* Monitor blocked contacts count in MAAC and LINE CMS at month-end.

### Expected vs Actual

* Expected: Consistent trends between MAAC and LINE CMS.
* Actual: Different trends observed.

### Root Cause & Solution

* Root Cause: Different definitions of "blocked" contacts. MAAC includes users who passed authorization but did not add the Official Account along with truly blocked users; LINE CMS counts only truly blocked users.
* Solution: Clarify definitional differences to customer. Consider documentation or UI updates if confusion recurs.

***

## MAAC Contacts - Contact count discrepancy in LINE Overview (report pipeline timing)

**Metadata**

* Feature: MAAC-Contact
* Created At: 2025-12-24
* Asana Task ID: [1212571876611185](https://app.asana.com/1/1184020052539844/task/1212571876611185)
* Ticket Priority: P2
* Client Name: Krungsri Simple
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

Mismatch between Total Contacts on LINE Overview (5,300,500) and sum of Contacts Engagement Level breakdown (5,302,274), discrepancy of 1,774.

### Context & Details

* Environment:
  * MAAC org id / CAAC org id: 5505
  * MAAC bot / CAAC channel ID: 4421
* Attachments:
  * Screenshot 1: https://app.asana.com/app/asana/-/get\_asset?asset\_id=1212571876611196
  * Screenshot 2: https://app.asana.com/app/asana/-/get\_asset?asset\_id=1212571876611198

### Reproduction Steps

* Compare Total Contacts on Overview with sum of engagement-level contacts.

### Expected vs Actual

* Expected: Totals match.
* Actual: 1,774 discrepancy.

### Root Cause & Solution

* Root Cause: Metrics derived from separate daily reports and distinct calculation pipelines executed at different times; different tracked data points. This is expected from current system design.
* Solution: No fix required. Consider future improvements to align metrics or improve user clarity. Status closed.

***

## MAAC Contacts - Error when opening a contact (error ID investigation)

**Metadata**

* Feature: MAAC-Contact
* Created At: 2025-11-24
* Asana Task ID: [1212059548060044](https://app.asana.com/1/1184020052539844/task/1212059548060044)
* Ticket Priority: P2
* Client Name: \[REDACTED]
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

Customer encountered an error (Error ID: 21a2ea75120243f19261dafc33e7e74e) when clicking a contact. Customer Support could not reproduce the error.

### Context & Details

* Browser updated; incognito tried; network devices changed.
* Potential causes include MAAC API connection failures, auth token issues, or malformed API responses.
* Internal adapter failing at harmony/internal/adapter/server/maac\_server.go to retrieve contact data.

### Reproduction Steps

* The error could not be reproduced by Customer Support.

### Expected vs Actual

* Expected: Access contact information.
* Actual: Error prevented access.

### Root Cause & Solution

* Root Cause: Possible MAAC API connection/auth/token/data format issues.
* Solution:
  * Engineering to investigate logs using the error ID.
  * Verify MAAC API service status and auth token validity.
  * Follow MAAC\_CONTACT\_LIST\_ERROR\_TROUBLESHOOTING.md guide.
  * CSM to reconfirm with customer if issue persists.

***

## MAAC Contacts - International phone number import blocked (country code validation)

**Metadata**

* Feature: MAAC-Contact
* Created At: 2025-11-24
* Asana Task ID: [1212056497282134](https://app.asana.com/1/1184020052539844/task/1212056497282134)
* Ticket Priority: P2
* Client Name: N/A
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

Failure importing international phone numbers: MAAC did not accept phone numbers with country codes different from the one selected during import.

### Context & Details

* Users attempted to import mixed country-code phone numbers (e.g., Taiwan and Hong Kong) while selecting a single country code.

### Reproduction Steps

{% stepper %}
{% step %}
### Step

Attempt to import a list containing phone numbers with mixed country codes.
{% endstep %}

{% step %}
### Step

Select one country code during the import process.
{% endstep %}

{% step %}
### Step

Observe that numbers not matching the selected country code are blocked.
{% endstep %}
{% endstepper %}

### Expected vs Actual

* Expected: System imports all provided phone numbers.
* Actual: System accepted only numbers matching the selected country code.

### Root Cause & Solution

* Root Cause: Import function is designed to accept only phone numbers corresponding to the single selected country code (intended behavior for security/data integrity).
* Solution: Instruct customer to split contact lists by country code and run separate imports per list with correct country selection. No product changes necessary.

***

## MAAC Contacts - Bulk tag add failure after tag removal (stale filter criteria)

**Metadata**

* Feature: MAAC-Contact
* Created At: 2025-11-12
* Asana Task ID: [1211918779487776](https://app.asana.com/1/1184020052539844/task/1211918779487776)
* Ticket Priority: P2
* Client Name: \[REDACTED]
* Resolution Owner: Jess
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

Operation to add a tag did not succeed (2025/11/07 \~18:37).

### Context & Details

* Environment:
  * MAAC org ID: 5395
  * MAAC bot ID: 4303
* User actions:
  * Filter contacts by tag "Unknown Distributor".
  * Click update tag to remove it.
  * Click update tag to add it again.
* Result: Tag not added as of 11/11.

### Reproduction Steps

* Filter contacts by "Unknown Distributor".
* Remove the tag from filtered contacts.
* Attempt to re-add the same tag to the same contacts.

### Expected vs Actual

* Expected: Tag successfully added.
* Actual: Tag not added.

### Root Cause & Solution

* Root Cause: User removed the tag then immediately attempted to re-add it. The system used outdated filter criteria (contacts having the tag) for the add operation, so no contacts matched after removal.
* Solution:
  * Engineering: Implement dynamic re-evaluation of bulk tag filters at execution time to reflect current contact state.
  * Product: Improve UI/UX to prevent or warn against self-conflicting tag operations.
  * CSM: Advise alternative workflows (use import, refresh filters before reapplying tags).

***

## MAAC Contacts - Contact list shows same name repeatedly (pagination rendering)

**Metadata**

* Feature: MAAC-Contact
* Created At: 2025-11-10
* Asana Task ID: [1211896250042306](https://app.asana.com/1/1184020052539844/task/1211896250042306)
* Ticket Priority: P2
* Client Name: MCJeans
* Resolution Owner: Jack Lee
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

When navigating MAAC audience > Contacts using search/filter, contact names displayed were consistently the same.

### Context & Details

* Browser: Chrome
* MAAC org ID: 6364
* MAAC bot/CAAC channel ID: 6411
* Occurrence: 10 Nov 2025, 15:00

### Reproduction Steps

1. Go to MAAC audience > Contacts.
2. Use search or filter to navigate contact list.
3. Observe that displayed contact names remain unchanged.

### Expected vs Actual

* Expected: Each contact name corresponds to a distinct entry.
* Actual: Same contact name repeated.

### Root Cause & Solution

* Root Cause: Front-end rendering problem due to transition from previous table display to new Pagination Table style.
* Solution: Deploy new Pagination Table style — issue resolved. CSM confirmed fix.

***

## MAAC Contacts - LINE user ID not found in MAAC (webhook payload destination vs userId)

**Metadata**

* Feature: MAAC-Contact
* Created At: 2025-10-01
* Asana Task ID: [1211518421563981](https://app.asana.com/1/1184020052539844/task/1211518421563981)
* Ticket Priority: P2
* Client Name: \[REDACTED]
* Resolution Owner: Kade
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

LINE user ID U4af0276046c369865595c048d478828a not found in MAAC, preventing rich menu usage despite webhook sent to Cresclab returning 200.

### Context & Details

* Environment:
  * MAAC org ID: 4478
  * MAAC bot: 3613
  * Happened on: 2025-09-30

### Reproduction Steps

* Search for LINE user ID U4af0276046c369865595c048d478828a in MAAC.

### Expected vs Actual

* Expected: LINE user ID searchable and rich menu usable.
* Actual: Not found in MAAC; rich menu access blocked.

### Root Cause & Solution

* Root Cause: Client's webhook payload placed LINE user ID in 'destination' instead of 'userId' within the event object. Event Hub therefore failed to process/create the contact in MAAC.
* Solution:
  * Advise client to correct webhook payload per LINE Messaging API docs.
  * Or configure LINE Developer to send webhooks directly to Cresclab.
  * Manual correction in MAAC may be required for immediate resolution.

***

## MAAC Contacts - LINE friend status shows Auth not Following (follow webhook missing)

**Metadata**

* Feature: MAAC-Contact
* Created At: 2025-09-10
* Asana Task ID: [1211314992828207](https://app.asana.com/1/1184020052539844/task/1211314992828207)
* Ticket Priority: P2
* Client Name: A RAMEN
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

A contact added as a friend in LINE OA is shown as 'Auth' in MAAC instead of 'Following', affecting coupon delivery in a campaign.

### Context & Details

* Environment:
  * MAAC bot / CAAC channel ID: 4268

### Reproduction Steps

* Add a contact as a friend in LINE OA and check MAAC status.

### Expected vs Actual

* Expected: Status updates to 'Following'.
* Actual: Remains 'Auth' until contact sends a message.

### Root Cause & Solution

* Root Cause: MAAC did not receive the initial LINE 'follow' webhook event. Status updated to 'Following' only upon receiving a subsequent 'message' event.
* Solution: Client should verify forwarding of LINE 'follow' events to our endpoint. If forwarded but not received, investigate webhook receiving logs. If not forwarded, client should fix forwarding.

***

## MAAC Contacts - Unbinding issue: customer\_id reappears after removal

**Metadata**

* Feature: MAAC-Contact
* Created At: 2025-09-02
* Asana Task ID: [1211206950744508](https://app.asana.com/1/1184020052539844/task/1211206950744508)
* Ticket Priority: P2
* Client Name: 遠東商銀HAPPY+
* Resolution Owner: N/A
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

After unbinding a LINE contact, the `customer_id` unexpectedly reappeared in MAAC shortly afterward.

### Context & Details

* Occurrences:
  * 2025/5/13: Unbind at 14:15; `customer_id` reappeared at 14:16.
  * 2025/5/21: Unbind at 08:45; `customer_id` reappeared at 08:55.
* Affected user LINE UID and MAAC ID: \[REDACTED\_ID]

### Reproduction Steps

{% stepper %}
{% step %}
### Step

Perform unbinding via the web interface.
{% endstep %}

{% step %}
### Step

Observe `customer_id` reappearing in MAAC shortly after.
{% endstep %}
{% endstepper %}

### Expected vs Actual

* Expected: `customer_id` permanently removed.
* Actual: `customer_id` reappears shortly after unbinding.

### Root Cause & Solution

* Root Cause: Undetermined — unclear if system design or bug. Further investigation required.
* Solution: Engineering to investigate logs in MAAC and CDH for contact profile updates and unbinding events for this user.

***

## MAAC Contacts - Unexpected customer\_id update (bindlink callback TooManyRedirects)

**Metadata**

* Feature: MAAC-Contact
* Created At: 2025-08-28
* Asana Task ID: [1211168081754537](https://app.asana.com/1/1184020052539844/task/1211168081754537)
* Ticket Priority: P2
* Client Name: 遠東商銀HAPPY+
* Resolution Owner: David
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

`customer_id` for a MAAC LINE contact was unexpectedly updated on 2025/08/13 14:30 despite client recording the user as unbound.

### Context & Details

* Affected contact:
  * LINE Contact `line_uid`: U91c2b7e8520623a9c3137bec5a6f7110
  * `customer_id`: N2I4OWRlNDM5NzdlNDFlZGEwZDE5YmQ0N2JmZjg0MDg=
* Timeline:
  1. 2025/8/13 14:22: API generated a bindlink.
  2. 2025/8/13 14:22: API updated data.
  3. 2025/8/13 14:27: API cleared `customer_id`.
  4. 2025/8/13 14:30: `customer_id` was stored (method uncertain).

### Expected vs Actual

* Expected: `customer_id` remains cleared.
* Actual: `customer_id` was updated.

### Root Cause & Solution

* Root Cause: Update was triggered by a bindlink callback within MAAC, but callback from MAAC to client failed with "TooManyRedirects" — likely misconfiguration in client's endpoint.
* Solution: Route client callbacks through Messaging Delivery System (MDS) for improved stability and observability. Solution tested and confirmed effective.

Status: Resolved

***

## MAAC Contacts - Missing LINE UIDs in contact updates (webhook forwarding and API 404)

**Metadata**

* Feature: MAAC-Contact
* Created At: 2025-05-09
* Asana Task ID: [1210198750130352](https://app.asana.com/1/1184020052539844/task/1210198750130352)
* Ticket Priority: P1 - Very High
* Client Name: Krungsri Simple
* Resolution Owner: JY
* Result Breakdown: Clarify (Meet product expectation)

### Issue Description

Four LINE UIDs missing from MAAC during a registration campaign using LIFF rich menu. MAAC API failed to update contacts for these UIDs though LINE API returns info for them.

### Context & Details

* Environment:
  * MAAC bot / CAAC channel ID: 4421

### Reproduction Steps

{% stepper %}
{% step %}
### Step

Launch registration campaign using LIFF registration page in MAAC rich menu.
{% endstep %}

{% step %}
### Step

Attempt to update contacts via MAAC API for specified UIDs.
{% endstep %}
{% endstepper %}

### Expected vs Actual

* Expected: UIDs updated in MAAC.
* Actual: UIDs not found in MAAC; updates failed.

### Root Cause & Solution

* Root Cause: Client's webhook forwarding unreliable, causing event loss. MAAC webhook response time occasionally >10s. Client import/update API calls may not reach MAAC successfully; MAAC update API returns 404 if contact absent.
* Solution:
  * Client: Use Import Contact API for missing UIDs; implement webhook retry/extend forwarding timeout.
  * MAAC engineering: Investigate long response times and endpoint errors. Client to provide task\_id and specific error logs for disappeared UIDs for deeper investigation.

Status: Client adopted Import Contact API and extended timeouts; investigation ongoing pending client data.

***
