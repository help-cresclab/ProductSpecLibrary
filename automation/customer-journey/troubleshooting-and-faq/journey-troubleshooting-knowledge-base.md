---
description: >-
  MAAC Customer Journey troubleshooting. Covers reports, node/channel metrics,
  triggers, tags, LINE delivery, GA4/BigQuery.
---

# Journey Troubleshooting Knowledge Base

## MAAC Customer Journey Troubleshooting Knowledge Base

Use this page to troubleshoot **MAAC Customer Journey** issues. It consolidates real investigations from **Asana tickets**. It focuses on **journey reports**, **channel performance**, **node performance metrics**, **triggers**, **tags**, and **message delivery**.

This page can also serve as a troubleshooting knowledge base. Use it to debug **journey reports**, **node/channel performance**, **tag triggers**, **delays**, and **LINE message delivery** issues.

{% hint style="info" %}
**AI Answer search cheat-sheet (recommended queries)**

customer journey, journey report, node performance, channel performance, tag trigger, trigger delay, coupon delivery failure, LINE blocked, webhook, access token, message delivery failure, open count, click metrics, messages sent, traffic count
{% endhint %}

### Common questions (copy/paste into AI Answer)

* Why does the Journey report show the same numbers across different date ranges?
* Why can **open count** be higher than **messages sent**?
* A tag was applied, but the automated journey did not trigger. What are common causes?
* Why are messages not delivered when a LINE user is **blocked**?
* Why does a journey step run \~30 minutes late? Is it a queue backlog?
* After deleting a journey, why is the report not accessible by Journey ID?

Common topics:

* Journey report data discrepancy (revenue, traffic count, messages sent, open count, click metrics)
* Time range filter issues (same data across date ranges)
* Trigger and delay issues (queue backlog, race conditions, paused journeys)
* LINE delivery failures (blocked users, webhook/config issues, access token problems, message quota)
* Analytics and data pipeline fixes (GA4 definitions, BigQuery permissions, backfills, aggregation logic)

Search keywords to try (copy/paste):

* `journey report`, `channel performance`, `node performance`, `traffic`, `messages sent`, `open count`, `unique opens`, `click metrics`, `tag trigger`, `LINE webhook`, `blocked`, `coupon`, `delay`, `BigQuery`, `GA4`

Related:

* [Asana Ticket](/broken/spaces/GBP3mPdNeU7kBvG5sba7/pages/Re58O14APR7yW6mx4rFK)

***

### Troubleshooting index

Use symptoms and keywords to find relevant investigations. Every case includes Issue / Root cause / Solution.

#### Coupon delivery failure

* [Investigation of Automated Journey Coupon Distribution Failure](journey-troubleshooting-knowledge-base.md#investigation-of-automated-journey-coupon-distribution-failure) (conditions updated after traversal)
* [Investigation of Coupon Delivery Failure in Customer Journey](journey-troubleshooting-knowledge-base.md#investigation-of-coupon-delivery-failure-in-customer-journey) (journey cancelled due to LINE blocked)
* [Investigation of Automated Journey Coupon Delivery Failure](journey-troubleshooting-knowledge-base.md#investigation-of-automated-journey-coupon-delivery-failure) (LINE message quota)

#### Journey reports and metric discrepancies

* [Investigation of Report Data Discrepancy in Customer Journey](journey-troubleshooting-knowledge-base.md#investigation-of-report-data-discrepancy-in-customer-journey) (legacy API behavior)
* [Investigation of Identical Data in Journey Reports Across Different Time Ranges](journey-troubleshooting-knowledge-base.md#investigation-of-identical-data-in-journey-reports-across-different-time-ranges) (report API bug)
* [Investigation of Missing Data in Detailed Reports for Customer Journey](journey-troubleshooting-knowledge-base.md#investigation-of-missing-data-in-detailed-reports-for-customer-journey) (missing daily data / backfill)
* [Investigation of Discrepancy in Open Counts vs. Message Sends in Automated Journeys](journey-troubleshooting-knowledge-base.md#investigation-of-discrepancy-in-open-counts-vs-message-sends-in-automated-journeys) (daily unique opens definition)

#### Triggers and tags

* [Why Did the Automatic Journey Fail to Trigger?](journey-troubleshooting-knowledge-base.md#why-did-the-automatic-journey-fail-to-trigger) (journey paused)
* [Investigation of User Re-entry Failure in MAAC Journey](journey-troubleshooting-knowledge-base.md#investigation-of-user-re-entry-failure-in-maac-journey) (only MAAC-applied tags trigger journeys)
* [Investigation of Missing Tags on LINE Users in Customer Journey](journey-troubleshooting-knowledge-base.md#investigation-of-missing-tags-on-line-users-in-customer-journey) (user-initiated batch deletion)

#### LINE message delivery (blocked, token, webhook)

* [Investigation of Message Delivery Failure in Customer Journey](journey-troubleshooting-knowledge-base.md#investigation-of-message-delivery-failure-in-customer-journey) (blocked)
* [Investigation of Automated Journey Message Delivery Failure](journey-troubleshooting-knowledge-base.md#investigation-of-automated-journey-message-delivery-failure) (node missing channel link / backward compatibility)
* [Investigation of Automatic Journey Activation Failure](journey-troubleshooting-knowledge-base.md#investigation-of-automatic-journey-activation-failure) (LINE follow webhook not received)

#### Delays and queue backlog

* [How to Address Delays in Journey Trigger Execution](journey-troubleshooting-knowledge-base.md#how-to-address-delays-in-journey-trigger-execution) (queue backlog)

***

## Investigation of Automated Journey Coupon Distribution Failure

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2026-02-04
* Asana Task ID: [1213108411548197](https://app.asana.com/1/1184020052539844/task/1213108411548197)
* Ticket Priority: P2
* Client Name: POYA
* Resolution Owner: David
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

Automated journey configured to distribute coupons based on tagging conditions did not distribute coupons to customers who met conditions (Journey: https://maac.cresclab.com/journey/edit/67818).
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 1732
  * MAAC bot ID: 1411
  * Channel Types: LINE, Web, WhatsApp, EDM, FB, IG
* Affected contact ID: redacted
* Questions: Can ProductOps reproduce issue in client org?
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Journey conditional branch was updated to check for a specific tag after the member had already traversed the node. The system executes based on conditions present at traversal time.
* Solution: System functioned as configured. Advice: finalize journey conditions before activation because updates affect only subsequent traversals.
{% endstep %}
{% endstepper %}

***

## Investigation of Unexpected Click Data in Automated Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2026-01-23
* Asana Task ID: [1212903800307684](https://app.asana.com/1/1184020052539844/task/1212903800307684)
* Ticket Priority: P3
* Client Name: \[REDACTED]
* Resolution Owner: N/A
* Result Breakdown: N/A

{% stepper %}
{% step %}
### Issue Description

Unexpected click data in automated journey report: text-only journey shows click counts, including repeated keyword clicks.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 6148
  * MAAC bot/channel ID: 5874
  * Channel Type: LINE
* Journey report: https://maac.cresclab.com/journey/report/54533
* Expected: No click data for text-only journey.
* Actual: Unexpected click counts shown.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: When a journey node containing a keyword is edited and the keyword removed, the setting\_id → node\_id reference is not updated. Subsequent triggers by that keyword from other features get incorrectly attributed to this journey node.
* Solution: Update journey node editing process to properly remove or update keyword references when keywords are removed from nodes to prevent misattribution.
{% endstep %}
{% endstepper %}

***

## Investigation of Tagging Issue in Automated Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2026-01-21
* Asana Task ID: [1212890484249686](https://app.asana.com/1/1184020052539844/task/1212890484249686)
* Ticket Priority: P3
* Client Name: \[REDACTED]
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

Automated journey "台北場1-檢查人數" (ID: 65272) not applying expected tag "S1\_台北場1@教室" but user still traverses red-arrow branch.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 5395
  * MAAC bot/CAAC channel ID: 4303
* Reproduction:
  1. User enters journey without tag.
  2. Journey checks for tag "S1\_台北場1@教室".
  3. Despite absence of tag, user proceeds through branch.
* Expected: Users without tag should not proceed through red-arrow branch.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: User never entered journey 65272. The tag was applied at 2026-01-20 16:44:22, which was before journey activation at 2026-01-20 16:51. System behaved as designed by not allowing entry.
* Solution: No system bug. Clarify journey entry conditions and timing logic to Customer Success team.
{% endstep %}
{% endstepper %}

***

## Investigation of Data Anomaly in Customer Journey Reports

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2026-01-20
* Asana Task ID: [1212875406599783](https://app.asana.com/1/1184020052539844/task/1212875406599783)
* Ticket Priority: P3
* Client Name: \[REDACTED]
* Resolution Owner: Tracy
* Result Breakdown: Limit information

{% stepper %}
{% step %}
### Issue Description

Customer Success reported a journey report anomaly: record shows person entered journey but details cannot be retrieved (Journey ID: 65243).
{% endstep %}

{% step %}
### Context & Details

* Channel Type: LINE
* Affected Contact ID and MAAC ID: redacted
* Reproduction: Attempt to access journey details by Journey ID and fail.
* Expected: Journey details accessible.
* Actual: Details not retrievable.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Journey was deleted by the customer; deleted journeys are no longer accessible by ID or UI (expected behavior).
* Solution: No system bug; CSM informed journey was deleted. Consider product discussion if customers require access to deleted journey history.
{% endstep %}
{% endstepper %}

***

## Clarification of "Specified Web Channel" vs "Any Web Channel" Trigger Conditions

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2026-01-13
* Asana Task ID: [1212760721943646](https://app.asana.com/1/1184020052539844/task/1212760721943646)
* Ticket Priority: P3
* Client Name: \[REDACTED]
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

Users seek clarification on differences between "Specified Web Channel" and "Any Web Channel" trigger conditions.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 5422
  * MAAC bot ID: 4312
* Reproduction:
  * Select "Specified Web Channel" > Wedding Cake Shopping Cart > Web Channel URL
  * Select "Any Web Channel" > Web Channel URL
* Expected: Clear differentiation.
* Actual: Users confused due to lack of UI/documentation guidance.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: UI and documentation do not provide specific clarification for single web channel scenarios.
* Solution:
  * Enhance MAAC UI with contextual help.
  * Update documentation to explain web channel selection for all configurations.
* Status: Under product review for UX and documentation improvements.
{% endstep %}
{% endstepper %}

***

### Investigation of Report Data Discrepancy in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-10-16
* Asana Task ID: [1211655812496697](https://app.asana.com/1/1184020052539844/task/1211655812496697)
* Ticket Priority: P2
* Client Name: FM SHOES
* Resolution Owner: JY, Gideon, Jack Lee
* Result Breakdown: Fix Problems

{% stepper %}
{% step %}
### Issue Description

The journey report displays identical revenue data for both August and September, as well as for the entire year. This requires verification of the report's data accuracy.
{% endstep %}

{% step %}
### Context & Details

* Environment: MAAC platform, FM SHOES organization
* User Actions: Filtering journey reports for August and September
* Reproduction Steps:
  * Access the journey report for the specified months.
  * Observe the revenue data displayed.
* Expected Behavior: Different revenue data should be displayed for each month.
* Actual Behavior: Revenue data remains the same for both months and the entire year.
* Additional Information:
  * Journey Information: https://maac.cresclab.com/journey/edit/14781
  * MAAC organization ID: 411
  * MAAC bot ID: 397
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Journeys created before August 11, 2025, were incorrectly using the /journey/v2/ API instead of the /journey/v1/ API, causing missing click metrics.
* Solution: Frontend logic updated to use /journey/v1/ for journeys created before August 11, 2025. Channel performance details are hidden for these older journeys; overall performance remains accessible. Issue resolved.
{% endstep %}
{% endstepper %}

***

## Investigation of Identical Data in Journey Reports Across Different Time Ranges

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-10-16
* Asana Task ID: [1211658874580583](https://app.asana.com/1/1184020052539844/task/1211658874580583)
* Ticket Priority: P1 - Very High
* Client Name: \[REDACTED]
* Resolution Owner: Gideon, JY
* Result Breakdown: Fix Problems

{% stepper %}
{% step %}
### Issue Description

The journey report and channel performance data in MAAC displayed identical results regardless of the selected time range.
{% endstep %}

{% step %}
### Context & Details

* Journey Name: Y25MA\_W4\_GoldenRetriever5M
* Time Ranges Analyzed:
  * 03/30 - 10/16
  * 09/01 - 09/30
  * 03/30 - 08/31
* Client Info:
  * MAAC org ID: 3315
  * MAAC bot/channel ID: 2828
* Occurrence Date: 2025/10/16
* Reproduction: Issue reproducible across the specified time ranges.
* User Inquiry: Agency asked why data remained the same across different time filters.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: The /journey/v2/journey/:id/report/ API returned incorrect data (used by Journey Report Overview and Channel Performance).
* Solution: Backend /journey/v2/journey/:id/report/ API corrected. No further action required. Resolved as of 2025/10/17.
{% endstep %}
{% endstepper %}

***

## Investigation of Journey Limit Confirmation in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-10-02
* Asana Task ID: [1211529535178880](https://app.asana.com/1/1184020052539844/task/1211529535178880)
* Ticket Priority: P2
* Client Name: \[REDACTED]
* Resolution Owner: JY
* Result Breakdown: Task-Ticket

{% stepper %}
{% step %}
### Issue Description

Client reported that the current journey limit per organization is set at 350, but their organization exceeded this limit and seeks clarification.
{% endstep %}

{% step %}
### Context & Details

* Client Info:
  * MAAC org ID: 3315
  * MAAC bot/channel ID: 2828
* Reproducibility: Not specified.
* User Inquiry: Discrepancy between expected limit and current usage.
* Expected: Journey limit per org is 350.
* Actual: Client's org exceeded this limit.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: A specific customer had a hardcoded special limit (initially 600, later adjusted to 580) that overrode the standard plan limit; inconsistent when centralized Feature Setting introduced.
* Solution: Customer's specific limit (580) configured in "MAAC org plan override feature setting" in CSM Helper. Removed hardcoded logic. Future adjustments managed through Feature Setting. Issue resolved.
{% endstep %}
{% endstepper %}

***

## Investigation of Coupon Delivery Failure in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-10-27
* Asana Task ID: [1211752757731117](https://app.asana.com/1/1184020052539844/task/1211752757731117)
* Ticket Priority: P2
* Client Name: Movefree
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

A MAAC user did not receive a coupon from Journey ID 12727 despite entering the journey.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org id / CAAC org id: 1876
  * MAAC bot / CAAC channel ID: 1517
  * Happened time: 2025/10/27
* Reproduction Steps:
  * User enters Journey ID 12727.
  * User reaches the message sending node.
* Expected: User receives coupon upon reaching node.
* Actual: User did not receive coupon.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Member was "blocked" when reaching the message sending node (2025/10/18 16:27:00). Blocked status caused journey progress to be cancelled, preventing coupon sending.
* Solution: System correctly cancelled journey progress due to blocked status. A playbook will document cancellation scenarios (including blocked members). No code fix needed. Status resolved as expected.
{% endstep %}
{% endstepper %}

***

## Investigation of Missing Data in Detailed Reports for Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-10-28
* Asana Task ID: [1211766914194854](https://app.asana.com/1/1184020052539844/task/1211766914194854)
* Ticket Priority: P2
* Client Name: \[REDACTED]
* Resolution Owner: David
* Result Breakdown: Fix Problems

{% stepper %}
{% step %}
### Issue Description

Detailed reports for the customer journey initially displayed no data.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * Automatic Journey: 250327-250402\_APP Children's Day Promotion Journey (ID: 16838)
  * UTM Settings:
    * Source: Together.Line
    * Medium: tracelink
    * Campaign: 250327-250402\_APP Children's Day Promotion Short Journey
  * GA4 Data (3/17 - 11/6):
    * Sessions (Unique Clicks): 9,598
    * Total Revenue: 121,279
* Reproduction Steps:
  * Access detailed report for specified journey; observe absence of data initially.
* Expected: Reports show complete data.
* Actual: Initially no data; after fix, unique clicks sometimes exceeded total clicks.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: journey\_node\_performance\_report\_daily data missing in MAAC DB. Unique clicks sometimes > total clicks consistent with GA4 (metric definition differences).
* Solution: Engineering restored missing report data. Unique and total clicks validated against GA4; customer informed. Additional reporting fixes scheduled. Missing data issue resolved.
{% endstep %}
{% endstepper %}

***

## Why Did the Automatic Journey Fail to Trigger?

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-10-29
* Asana Task ID: [1211780413653579](https://app.asana.com/1/1184020052539844/task/1211780413653579)
* Ticket Priority: P2
* Client Name: OHHER
* Resolution Owner: David
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

Automatic journey failed to trigger. The 'shopline\_bind\_success' tag was applied but no journey initiation recorded.
{% endstep %}

{% step %}
### Context & Details

* Scenario: Consumer completed Shopline membership binding, applying 'shopline\_bind\_success' tag intended to trigger automatic journey "Bind Electronic Member 150+ Reminder Copy" (ID: 46606).
* Setting: Journey configured to trigger on 'shopline\_bind\_success'.
* User Info: MAAC ID and Line UID redacted.
* Environment: Issue occurred on 10/28 at 14:33.
* Reproduction: Apply 'shopline\_bind\_success' tag while journey is paused.
* Expected: Journey starts when tag applied.
* Actual: No journey entry recorded.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Journey (ID: 46606) was paused when tag applied. Paused status prevented activation. Logs confirmed paused state. An unrelated error observed but did not affect trigger.
* Solution: Client had manually paused the journey; informed. No system bug. Recommend client education on checking journey status.
{% endstep %}
{% endstepper %}

***

## Investigation of Message Delivery Failure in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-10-31
* Asana Task ID: [1211792484352169](https://app.asana.com/1/1184020052539844/task/1211792484352169)
* Ticket Priority: P2
* Client Name: 英飛凌
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

Automated journey (ID 51392) for a member did not pause as expected and member did not receive scheduled message.
{% endstep %}

{% step %}
### Context & Details

* Journey ID: 51392
* Member ID: redacted
* Environment: Journey did not pause; other members received messages normally.
* Reproduction: Issue occurred on 2025-10-31 at 10:19; member status checked at scheduled message time.
* Expected: Journey pauses and message is received.
* Actual: Journey did not pause; message not received.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: At scheduled delivery (2025-10-31 10:19:15) the LINE user was "blocked", preventing message send.
* Solution: No system bug; behavior due to user LINE status. Customer Success should communicate finding to client.
{% endstep %}
{% endstepper %}

***

## How to Address Delays in Journey Trigger Execution

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-10-31
* Asana Task ID: [1211802228845406](https://app.asana.com/1/1184020052539844/task/1211802228845406)
* Ticket Priority: P0 - Emergency
* Client Name: N/A
* Resolution Owner: David, Aaren
* Result Breakdown: Fix Problems

{% stepper %}
{% step %}
### Issue Description

MAAC journey members experienced approximately 30-minute delays in triggering their next actions.
{% endstep %}

{% step %}
### Context & Details

* Environment: MAAC org ID and channel ID involved; issue time unspecified.
* Reproduction: Reproducibility not confirmed.
* Expected: Immediate triggering.
* Actual: \~30-minute delay observed.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Temporary backlog in MAAC journey processing queue caused delayed execution.
* Solution: Scaled journey processing resources to clear backlog; further investigation ongoing to identify root cause and preventive measures. Status: Resolved with monitoring in place.
{% endstep %}
{% endstepper %}

***

## Investigation of Missing Tags on LINE Users in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-10-07
* Asana Task ID: [1211572630297919](https://app.asana.com/1/1184020052539844/task/1211572630297919)
* Ticket Priority: P2
* Client Name: \[REDACTED]
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

Customer reported specific LINE users had no tags despite prior records indicating tags were applied; audit logs showed no removal.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 5395
  * MAAC bot ID: 4303
* Occurrence: 10/7
* Expected: Tags remain unless manually removed.
* Actual: Tags missing without audit log records.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Tags were removed on 10/2 by the client's own account via a batch deletion action using a system API (user-initiated).
* Solution: System functioned as designed. CSM should explain tags were removed by client's batch deletion and advise review of MAAC usage practices.
{% endstep %}
{% endstepper %}

***

## Investigation of Automated Journey Message Delivery Failure

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-10-09
* Asana Task ID: [1211594862619415](https://app.asana.com/1/1184020052539844/task/1211594862619415)
* Ticket Priority: P1 - Very High
* Client Name: OHHER
* Resolution Owner: JY, Aaren
* Result Breakdown: Fix Problems

{% stepper %}
{% step %}
### Issue Description

Automated journey ID 46606 failed to send LINE messages to any recipients.
{% endstep %}

{% step %}
### Context & Details

* Automated journey ID: 46606
* Start time: 10/9 9:19
* Trigger: Tag application - shopline\_bind\_success
* Node ID (Send LINE Message): 243893
* Reward: $150 electronic membership incentive
* Reproduction Steps:
  1. Initiate journey.
  2. Apply tag to trigger.
  3. Attempt to send LINE messages.
* Expected: LINE messages sent to recipients.
* Actual: No recipients received messages.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: 'Send LINE Message' node (ID 243893) lacked a channel link due to a backward compatibility bug between 9/30 and 10/7; channel ID not saved during creation/duplication.
* Solution:
  * Manually updated affected node's channel ID.
  * Frontend and backend fixes planned for all 'Send LINE Message' nodes.
  * Tier 2 data migration scheduled before release.
  * Past 15 contacts compensated and status canceled.
  * New entries now receive messages as expected.
* Status: Resolved for new entries; long-term fix planned.
{% endstep %}
{% endstepper %}

***

## Investigation of Message Delivery Failure in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-11-17
* Asana Task ID: [1211963997996746](https://app.asana.com/1/1184020052539844/task/1211963997996746)
* Ticket Priority: P2
* Client Name: N/A
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

Week 2 message in Customer Journey not sent as expected; intended to be 14 days after tag, but system behavior resulted in 21 days.
{% endstep %}

{% step %}
### Context & Details

* Journey ID: 50886
* Behavior observed:
  * Tag is applied.
  * Step 1: Wait 7 days → send Week 1.
  * Step 2: Wait 14 days after Step 1 → intended Week 2 at day 14, system triggers at day 21.
* Expected: Week 2 sent 14 days after tag.
* Actual: Week 2 sent 21 days after tag.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: "Time Delay" is calculated sequentially from completion of previous step (so delays stack), not from journey entry point.
* Solution:
  * Workaround: Create separate journey for Week 2 (Tag Applied → Wait 14 days → Send Week 2).
  * Product Recommendation: Add Time Delay options to configure delays relative to previous step or journey entry.
  * ProductOps: Update documentation to clarify Time Delay behavior.
* Status: Pending Product/Engineering review.
{% endstep %}
{% endstepper %}

***

## Investigation of Web Unification Failure in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-11-19
* Asana Task ID: [1211989817407626](https://app.asana.com/1/1184020052539844/task/1211989817407626)
* Ticket Priority: P2
* Client Name: N/A
* Resolution Owner: N/A
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

MAAC.io UTM link identity association feature disabled, preventing website visitor identity unification.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org id / CAAC org id: 5124
  * MAAC bot / CAAC channel ID: Web Chat CL-2891F190
* User Actions:
  * Enabled SDK integration and Connect ID.
  * Generated tracelink, clicked from LINE OA to web, initiated web chat.
* Unexpected Behavior: LINE UID not unified with visitor ID.
* Expected: LINE UID unify with visitor ID upon web chat.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Feature intentionally disabled due to critical bug where previous implementation incorrectly merged distinct contact identities when links widely shared, causing data integrity issues.
* Solution: Feature removed to prevent data corruption. Product and Engineering must design a revised solution to re-enable UTM-based identity association safely. Feature remains disabled pending redesign.
{% endstep %}
{% endstepper %}

***

## Investigation of Message Delivery Discrepancy in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-11-20
* Asana Task ID: [1212000398380765](https://app.asana.com/1/1184020052539844/task/1212000398380765)
* Ticket Priority: P2
* Client Name: Chalet V
* Resolution Owner: David
* Result Breakdown: Fix Problems

{% stepper %}
{% step %}
### Issue Description

Journey message appeared to trigger only 3 times, but number of messages sent was 5 for journey "a喜\_已約(交通資訊)" (id: 46542).
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org id: 6284
  * MAAC bot id: 6290
* User Questions:
  * Is "messages sent" based on bubbles? Is "open" based on LINE messages or bubbles?
* Reproduction: Trigger journey and compare triggered events vs messages sent.
* Expected: Triggered events should match or exceed messages sent.
* Actual: Messages sent exceeded triggered events.
* Possible reasons: statistical criteria differences, multi-channel sends, data delay/deduplication, repeat-send settings, test anomalies, concurrency.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Aggregation logic for journey-level traffic\_count previously only accounted for trigger nodes and did not fully reflect message node activity, enabling sent messages to exceed recorded traffic.
* Solution: Adjusted data aggregation logic so journey traffic (entries) will always be >= message send counts. Discrepancy resolved.
{% endstep %}
{% endstepper %}

***

## Investigation of Discrepancy in Open Counts vs. Message Sends in Automated Journeys

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-11-20
* Asana Task ID: [1212003258219548](https://app.asana.com/1/1184020052539844/task/1212003258219548)
* Ticket Priority: P2
* Client Name: \[REDACTED]
* Resolution Owner: David
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

Open counts for October exceeded message sends in automated journeys; issue appeared sporadically in Aug/Sep and increased in Oct.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 3315
  * MAAC bot/channel ID: 2828
* User Question: Why are open counts > message sends?
* Reproduction: Retrieve automated journey data from October and compare opens vs sends.
* Additional Info: If message sent in September but opened in October, send counted in Sep, open in Oct.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: "Daily unique opens" calculation counts each user's first open per day; cumulative daily unique opens can exceed message sends (product design).
* Solution:
  * Calculation remains unchanged for now.
  * Customer Success to communicate logic to customers.
  * Product & Engineering plan to standardize open count calculations across MAAC features in future.
{% endstep %}
{% endstepper %}

***

## Investigation of Report and Node Performance Error in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-11-21
* Asana Task ID: [1212015323191747](https://app.asana.com/1/1184020052539844/task/1212015323191747)
* Ticket Priority: P2
* Client Name: Demo Japan
* Resolution Owner: David
* Result Breakdown: Fix Problems

{% stepper %}
{% step %}
### Issue Description

Scenario message sent to six recipients with delivery and tag assignment confirmed, Scenario Delivery List showed six triggers and completions, but report and node performance displayed zeros after >1 hour.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 84
  * MAAC bot ID: 83
  * Feature ID: 31903
* Reproducible: In multiple client accounts; tested in JP demo account.
* Journey Report: https://maac.jp.cresclab.com/journey/report/31903
* Attachments:
  * https://app.asana.com/app/asana/-/get\_asset?asset\_id=1212015323191751
  * https://app.asana.com/app/asana/-/get\_asset?asset\_id=1212015323191755
  * https://app.asana.com/app/asana/-/get\_asset?asset\_id=1212015323191753
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: rubato service account on JP server lacked BigQuery dataEditor permission for table jp-shared-resource-production:medley\_jp\_production.message\_event\_v2, preventing node performance data collection.
* Solution: Granted BigQuery permission to rubato service account and backfilled all affected historical data.
* Status: Fixed; data accurate.
{% endstep %}
{% endstepper %}

***

## Investigation of Message Delivery Failure in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-11-26
* Asana Task ID: [1212087455716410](https://app.asana.com/1/1184020052539844/task/1212087455716410)
* Ticket Priority: P2
* Client Name: 國泰健康管理顧問股份有限公司-國泰健康管理
* Resolution Owner: Jalex
* Result Breakdown: Fix Problems

{% stepper %}
{% step %}
### Issue Description

Messages scheduled within MAAC journey were delayed; messages intended on 11/10 delivered on 11/19.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 4894
  * MAAC bot/channel ID: 3904
* Reproduction: Messages scheduled for 11/10 not received until 11/19; subsequent messages received correctly two days later.
* Expected: Delivery on scheduled date.
* Actual: Significant delay observed.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Race condition under high system load; initial 2-second wait time for updates was insufficient.
* Solution: Increased internal wait time from 2 to 10 seconds and added logging to monitor. Deployed optimization; no further delays observed for three days. Engineering to continue long-term validation.
{% endstep %}
{% endstepper %}

***

## How to Adjust Broadcast Trigger Keywords for IKEA's Custom Features

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-11-26
* Asana Task ID: [1212148684444758](https://app.asana.com/1/1184020052539844/task/1212148684444758)
* Ticket Priority: P2
* Client Name: IKEA
* Resolution Owner: Tracy
* Result Breakdown: Task-Ticket

{% stepper %}
{% step %}
### Issue Description

Image menu and segmented broadcast use same keyword "My Exclusive Coupon", preventing differentiation of trigger effectiveness. Request to modify segmented broadcast keyword while keeping image menu trigger unchanged.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 58
  * MAAC bot: 56
  * Feature ID: \[REDACTED\_UUID]
* Reproduction Steps:
  1. Trigger discount coupon using "My Exclusive Coupon" via image menu and segmented broadcast.
  2. Observe both triggers use same keyword.
* Expected: Different keywords to differentiate performance.
* Actual: Same keyword used for both triggers.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Custom keyword configurations managed in Django admin panel; CSMs lack access, creating dependency on privileged users.
* Solution: Privileged CSM updated segmented broadcast keyword in Django admin from "My Exclusive Coupon" to "My Exclusive Coupon\_1127".
* Suggested Actions: Train CSMs on Django updates or integrate keyword management into MAAC UI / provide granular CSM permissions.
{% endstep %}
{% endstepper %}

***

## Investigation of Message Delivery Discrepancy in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-11-28
* Asana Task ID: [1212216398287566](https://app.asana.com/1/1184020052539844/task/1212216398287566)
* Ticket Priority: P2
* Client Name: Vitabox, \[REDACTED]
* Resolution Owner: David
* Result Breakdown: Fix Problems

{% stepper %}
{% step %}
### Issue Description

Journey reports showed "Messages Sent" significantly higher than "Traffic" (journey entries), indicating incorrect data aggregation.
{% endstep %}

{% step %}
### Context & Details

* Vitabox Journey: https://maac.cresclab.com/journey/report/46617
  * Traffic: 261
  * Messages Sent: 526
  * Org ID: 4133
  * Bot ID: 3382
* Other Journey: https://maac.cresclab.com/journey/report/46646
  * Traffic: 85
  * Messages Sent: 145
  * Org ID: 3898
  * Bot ID: 3235
* Reproduction: Access reports and compare Traffic vs Messages Sent.
* Expected: Messages Sent align with Traffic.
* Actual: Messages Sent significantly higher.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Bug in journey report data aggregation logic caused miscalculation of Messages Sent.
* Solution: Deployed fix to correct aggregation; all historical data updated. No further action required. Issue resolved.
{% endstep %}
{% endstepper %}

***

## Investigation of Message Delivery Failure in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-11-04
* Asana Task ID: [1211836275088554](https://app.asana.com/1/1184020052539844/task/1211836275088554)
* Ticket Priority: P2
* Client Name: 國泰健康管理顧問股份有限公司-國泰健康管理
* Resolution Owner: Jalex
* Result Breakdown: Fix Problems

{% stepper %}
{% step %}
### Issue Description

User did not receive expected LINE message at 10:30 AM on 11/03 despite being part of automated journey triggered by tag; journey \[46275].
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 4894
  * MAAC bot/channel ID: 3904
* Observed: Journey triggered correctly; member progress marked as 'running' but no send record.
* Expected: Message delivered as scheduled.
* Actual: No message was sent; no send record.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Race condition during transition from 'wait' to 'action' state caused temporary lock in message sending; status recorded as 'running' but message not sent.
* Solution: Engineering manually re-triggered journey for affected contact and merged a permanent fix for the race condition into codebase.
{% endstep %}
{% endstepper %}

***

## Investigation of Event Condition Probability Exceeding 100% in Automated Journeys

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-11-05
* Asana Task ID: [1211844282084109](https://app.asana.com/1/1184020052539844/task/1211844282084109)
* Ticket Priority: P2
* Client Name: \[REDACTED]
* Resolution Owner: Jalex
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

Automated journey event condition Yes/No percentages sum to over 100%; client requests clarification and how to ensure totals equal 100%.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 3898
  * MAAC bot ID: 3235
* Relevant phases: multiple named phases.
* Observed on: 2025/11/05
* Reproduction: Backend consistently shows sum > 100%.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Calculation divides downstream node traffic by upstream node traffic; when a branch connects to a shared node receiving traffic from multiple sources, percentages can sum >100%.
* Solution: An optimization to ensure split percentages sum to 100% (including shared-node scenarios) is planned for early January.
{% endstep %}
{% endstepper %}

***

## Investigation of Message Sent Tracking Discrepancy in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-11-07
* Asana Task ID: [1211876525117850](https://app.asana.com/1/1184020052539844/task/1211876525117850)
* Ticket Priority: P2
* Client Name: ZurQuiz
* Resolution Owner: David
* Result Breakdown: Fix Problems

{% stepper %}
{% step %}
### Issue Description

'Message Sent' count for a 'Send LINE Message' node exceeded its corresponding 'Traffic Count' in the journey report.
{% endstep %}

{% step %}
### Context & Details

* Occurrence: 7 Nov 2025
* Customer Journey URL: https://maac.cresclab.com/journey/edit/50886
* Reproduction: Not specified.
* Expected: Message Sent aligns with Traffic Count.
* Actual: Message Sent > Traffic Count.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Error in reporting calculation logic for 'Message Sent' metrics (reporting only); core sending functionality unaffected.
* Solution: Deployed data model fix (dbt-models/pull/674) to correct calculation logic and updated current and historical data. ProductOps will reinforce correct logic.
{% endstep %}
{% endstepper %}

***

## Investigation of Anomalous Traffic in Customer Journey Nodes

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-11-09
* Asana Task ID: [1211890618792612](https://app.asana.com/1/1184020052539844/task/1211890618792612)
* Ticket Priority: P2
* Client Name: N/A
* Resolution Owner: N/A
* Result Breakdown: N/A

{% stepper %}
{% step %}
### Issue Description

Traffic at a downstream node in a KKday journey (Org ID: 52, Journey ID: 49720) exceeds upstream node traffic.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC Org ID: 52
  * Journey ID: 49720
* Reproduction: Compare traffic for consecutive nodes and observe downstream > upstream.
* Expected: Traffic should decrease or be consistent downstream.
* Actual: Downstream node higher than upstream.
* Attachment: https://app.asana.com/app/asana/-/get\_asset?asset\_id=1211890618792618
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Unknown due to lack of details; ticket description and comments are empty.
* Solution: Await further information from CSM. Once details provided, analyze and correct root cause.
{% endstep %}
{% endstepper %}

***

## Investigation of Reward Delivery Failure in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-12-01
* Asana Task ID: [1212212943031521](https://app.asana.com/1/1184020052539844/task/1212212943031521)
* Ticket Priority: P2
* Client Name: Imager 37
* Resolution Owner: Jalex
* Result Breakdown: Too costly

{% stepper %}
{% step %}
### Issue Description

User tagged but did not enter journey; no journey entry record and therefore did not receive rewards (Journey ID: 38136).
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 5540
  * MAAC bot/channel ID: 4457
  * Journey ID: 38136
  * Event date: 2025/12/01
* Reproduction: User was tagged; expected journey entry and reward; actual: no entry and no reward.
* Investigation Links:
  * https://maac.cresclab.com/journey/report/38136
  * Additional play/query links (redacted in original)
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: System overload from 11/28 18:00-18:22 caused journey trigger tasks (including this tag event) to time out and be dropped.
* Solution: System stable now; engineering will optimize journey trigger system to prevent overloads. Affected events cannot be recovered. Issue resolved and customer informed.
{% endstep %}
{% endstepper %}

***

## Investigation of Error Message When Editing Draft Settings in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-12-19
* Asana Task ID: [1212525270720842](https://app.asana.com/1/1184020052539844/task/1212525270720842)
* Ticket Priority: P2
* Client Name: \[REDACTED]
* Resolution Owner: Gideon, Joseph, Aaren
* Result Breakdown: Product Optimization

{% stepper %}
{% step %}
### Issue Description

Error message displayed when attempting to edit any draft setting in Customer Journey.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 148
  * MAAC bot/CAAC channel ID: 191
* Reproduction Steps:
  1. Navigate to Customer Journey.
  2. Attempt to edit any draft setting.
  3. Observe error message.
* Expected: Draft settings editable.
* Actual: Error prevents edit. Issue reproducible.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Creation of a MAAC Journey requires WCCS setting. Organization's WCCS not configured during onboarding.
* Solution:
  * Manually configured WCCS to resolve immediate issue.
  * Front-end fallback: if WCCS missing, disable web channel triggers to allow Journey creation to proceed.
  * CSMs reminded to ensure WCCS configured during onboarding.
* Status: Resolved; product improvements deployed.
{% endstep %}
{% endstepper %}

***

## Investigation of Message Delivery Discrepancy in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-12-19
* Asana Task ID: [1212526067354940](https://app.asana.com/1/1184020052539844/task/1212526067354940)
* Ticket Priority: P2
* Client Name: \[REDACTED]
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

Journey traffic count 88 but message send count 99; client asks if issue resolved by Dec 10 or other causes.
{% endstep %}

{% step %}
### Context & Details

* Journey Report: https://maac.cresclab.com/journey/report/57050
* Observed Traffic: 88
* Message Send Count: 99
* Reproducible: Yes
* Related Task: previous Asana task referenced.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause:
  * Discrepancy (91 sends) due to prior manual intervention on node "12/10 10:30 13th\_動一動\_5層樓梯".
  * Open rate >100% due to "daily unique open" calculation in journeys (counts per user per day), differing from broadcast's "single unique open".
* Solution:
  * Provided detailed send logs for 91 messages to client.
  * Explained "daily unique open" logic.
  * Updated help center docs. No immediate calculation changes planned.
* Status: Addressed.
{% endstep %}
{% endstepper %}

***

## Investigation of Contact Count Discrepancy in Segment and Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-12-02
* Asana Task ID: [1212212340063599](https://app.asana.com/1/1184020052539844/task/1212212340063599)
* Ticket Priority: P2
* Client Name: Buymed
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

Discrepancy in number of contacts with purchase history: Segment shows 1.5K while Customer Journey shows >4K. Client expects alignment.
{% endstep %}

{% step %}
### Context & Details

* Environment: MAAC & CAAC org IDs involved; GA4 integration referenced.
* Reproduction: Compare contact counts in Segment vs Customer Journey for same purchase event.
* Expected: Similar counts or Segment >= Journey.
* Actual: Segment << Journey.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Design difference: Customer Journey tags both LINE contacts and un-unified web visitors; MAAC Segment filtered by tags counts only LINE contacts with that tag.
* Solution: Behavior by design. Recommend updating product docs to clarify distinction between "unique users" in Journey and "LINE contacts" in Segment. Submit Reqflow for product changes.
{% endstep %}
{% endstepper %}

***

## Investigation of Message Delivery Failure in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-12-23
* Asana Task ID: [1212562831782859](https://app.asana.com/1/1184020052539844/task/1212562831782859)
* Ticket Priority: P3
* Client Name: \[REDACTED]
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

After setting up automatic journey (ID 36037) and triggering it, no message was received.
{% endstep %}

{% step %}
### Context & Details

* Environment: JP Bot ID: 191
* Reproduction: Set up journey 36037 and trigger it.
* Expected: Message sent on trigger.
* Actual: No message received.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: LINE channel access token used by MAAC prematurely invalidated, likely due to a third-party system refreshing token more frequently than MAAC's 30-day schedule.
* Solution: Manually refreshed LINE token to resolve immediate issue. Recommend investigating third-party token refresh behavior and consider detection/handling for premature token invalidation.
{% endstep %}
{% endstepper %}

***

## Investigation of Message Delivery Failure in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-12-30
* Asana Task ID: [1212613584339580](https://app.asana.com/1/1184020052539844/task/1212613584339580)
* Ticket Priority: P4
* Client Name: N/A
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

Failure to receive messages within a MAAC journey; member progress shows "cancelled" and no messages sent.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 1026
  * MAAC bot/channel ID: 893
  * Happened on: 2025/12/30
* Reproduction:
  1. Configure journey with "Block OA" trigger.
  2. Observe member progress as "cancelled".
  3. Verify no messages sent.
* Expected: Messages delivered to participants.
* Actual: Journey cancelled; no sends.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Misconfiguration: messages set to send after users blocked the Official Account; MAAC cannot send to blocked users, so journey cancelled.
* Solution: Campaign setup issue. Advise customer to select appropriate trigger (e.g., "Add friend"). No engineering fix required; ticket downgraded and closed.
{% endstep %}
{% endstepper %}

***

## Investigation of Data Discrepancies in Journey Reports

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-12-08
* Asana Task ID: [1212300439723659](https://app.asana.com/1/1184020052539844/task/1212300439723659)
* Ticket Priority: P2
* Client Name: DK Marketing
* Resolution Owner: N/A
* Result Breakdown: N/A

{% stepper %}
{% step %}
### Issue Description

Journey report "登録2か月以降シナリオ" showed abnormally high open count rate (9450%): 246 triggers, only 10 messages pushed, open counts 253.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 38
  * MAAC bot ID: 37
* Reproduction: Access report https://maac.jp.cresclab.com/journey/report/26522 and observe metrics.
* Expected: Message push consistent with triggers.
* Actual: Discrepancy and inflated open rate.
* Additional: Screenshots and records provided.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Transition to MDS system deprecated an old table and historical send data was not fully backfilled; data conversion error caused inaccurate counts.
* Solution: Backfilled historical message send data into journey\_node\_performance aggregation, correcting report data. Issue resolved. Ensure future migrations fully backfill data.
{% endstep %}
{% endstepper %}

***

## Investigation of Auto-Tag Functionality Failure in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-08-27
* Asana Task ID: [1211159532026200](https://app.asana.com/1/1184020052539844/task/1211159532026200)
* Ticket Priority: P2
* Client Name: N/A
* Resolution Owner: Tracy
* Result Breakdown: Limit information

{% stepper %}
{% step %}
### Issue Description

Intermittent failure prevented user from being auto-tagged after clicking an imagemap in a MAAC Customer Journey (occurred 25 Aug 2025).
{% endstep %}

{% step %}
### Context & Details

* Environment: MAAC Customer Journey
* Occurrence Date: 25 Aug 2025
* MAAC Org ID: 5967
* Attachment: https://app.asana.com/app/asana/-/get\_asset?asset\_id=1211159532026218
* Expected: Users auto-tagged after imagemap interaction.
* Actual: Auto-tagging failed intermittently.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Unknown; issue transient and self-corrected during initial checks.
* Solution: Auto-tagging resumed working. Monitor for recurrence. No immediate action required.
{% endstep %}
{% endstepper %}

***

## Investigation of Automatic Journey Trigger Failure in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-08-29
* Asana Task ID: [1211179877250437](https://app.asana.com/1/1184020052539844/task/1211179877250437)
* Ticket Priority: P2
* Client Name: \[TEST] Nestlé\_1000 Days (Nestlé Maternal and Infant Nutrition)
* Resolution Owner: Tracy, David, Jalex
* Result Breakdown: Limit information

{% stepper %}
{% step %}
### Issue Description

Automatic journey (ID 38247) did not trigger for user tagged "M\&M Welcome Gift"; user did not receive associated message.
{% endstep %}

{% step %}
### Context & Details

* Environment: MAAC platform, journey ID 38247
* User tagged after journey established.
* Expected: Message upon tagging.
* Actual: No message; user entered/exited journey at expected time but no delivery records found.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Undetermined; non-reproducible. Possible failure in message dispatch/delivery at time of event.
* Solution: Monitor for recurrence and enhance logging for journey message delivery status to aid debugging. No immediate action possible.
{% endstep %}
{% endstepper %}

***

## Investigation of Automated Journey Coupon Delivery Failure

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-09-01
* Asana Task ID: [1211196757821602](https://app.asana.com/1/1184020052539844/task/1211196757821602)
* Ticket Priority: P2
* Client Name: LAUTREAMONT
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

Contact bound and tagged but automated journey did not deliver coupon (Journey ID: 23735, occurrence 2025/08/30).
{% endstep %}

{% step %}
### Context & Details

* Client:
  * MAAC org ID / CAAC org ID: 5714
  * MAAC bot / CAAC channel ID: 4616
* Reproducibility: No
* Attachments: screenshots linked in original.
* Expected: Coupon delivery triggered by tag.
* Actual: Some users did not receive coupon despite tagging.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: LINE message failed due to insufficient client LINE message quota at send time. Journey was triggered successfully.
* Solution: Not a product bug. Advise client to monitor/manage LINE message quota. Consider internal playbook for quota-related diagnosis.
{% endstep %}
{% endstepper %}

***

## Investigation of Internal Server Error on Journey Report Page

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-09-15
* Asana Task ID: [1211357485563476](https://app.asana.com/1/1184020052539844/task/1211357485563476)
* Ticket Priority: P1 - Very High
* Client Name: 財團法人羅慧夫顱顏基金會-羅慧夫顱顏基金會
* Resolution Owner: Yio, David
* Result Breakdown: Fix Problems

{% stepper %}
{% step %}
### Issue Description

Journey Report page displays 'internal server error' preventing report display; reproducible for client 羅慧夫 only.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * Organization ID: 3043
  * Bot ID: 2634
  * Occurrence Time: 2025-09-15 11:52
* Reproduction: Access Journey Report and observe internal server error.
* Note: Issue specific to journeys with 'sleep-time' setting.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Recent deployment changed data format of 'sleep-time' field; field returned in unexpected format causing processing errors on Journey Report page.
* Solution: Correct data format handling in deployment and update system to process 'sleep-time' field correctly to restore report display.
{% endstep %}
{% endstepper %}

***

## Investigation of Journey Setting Disruption in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-09-16
* Asana Task ID: [1211370049491249](https://app.asana.com/1/1184020052539844/task/1211370049491249)
* Ticket Priority: P2
* Client Name: \[REDACTED]
* Resolution Owner: Noel
* Result Breakdown: Fix Problems

{% stepper %}
{% step %}
### Issue Description

Editing a draft journey and selecting "LINE Event - Join Official Account", enabling filters and clicking tags caused UI to crash or navigate away.
{% endstep %}

{% step %}
### Context & Details

* Reproduction Steps:
  1. Edit draft journey.
  2. Select "LINE Event - Join Official Account".
  3. Enable tag filters.
  4. Click on a tag and observe crash/navigation.
* Expected: Stable interface when selecting tags.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Repeated fetching of CDP tag data led to UI re-rendering issues (similar to prior bug).
* Solution: Implemented fix (PR #6724) to prevent repeated tag fetching and UI re-rendering. Deployed to production; issue resolved.
{% endstep %}
{% endstepper %}

***

## Investigation of Automatic Journey Activation Failure

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-09-18
* Asana Task ID: [1211391637501599](https://app.asana.com/1/1184020052539844/task/1211391637501599)
* Ticket Priority: P2
* Client Name: BUTY99
* Resolution Owner: Tracy
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

Automatic journey configured but did not trigger; no users tagged as 'new friends' despite new users joining (Journey ID: 38897).
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 1672
  * MAAC bot/channel ID: 1365
  * Journey ID: 38897
  * Activation: 2025/09/16; Temporary Pause: 2025/09/18
* Reproduction: New users joined official account but journey didn't trigger/tag them.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: MAAC did not receive LINE 'follow' webhook events from client. Client's LINE webhook not directly connected to MAAC, preventing triggers.
* Solution: Confirmed MAAC functionality correct. Advised client to verify LINE webhook endpoint configuration to ensure 'follow' events arrive at MAAC. Issue resolved (external dependency).
{% endstep %}
{% endstepper %}

***

## Investigation of User Re-entry Failure in MAAC Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-09-18
* Asana Task ID: [1211394824629744](https://app.asana.com/1/1184020052539844/task/1211394824629744)
* Ticket Priority: P2
* Client Name: \[REDACTED]
* Resolution Owner: Tracy, Leo
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

User expected to re-enter journey multiple times based on tag history but journey triggered only once.
{% endstep %}

{% step %}
### Context & Details

* Environment: Journey with automatic tag application and message sending scheduled daily at 10:00; conditional tag checks apply.
* Reproduction: User expected re-entry on 9/17 10:21 but only one entry recorded on 9/16 14:04.
* Expected: Multiple re-entries.
* Actual: Only one.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: MAAC journeys are triggered only by tags applied directly within MAAC. Tags from other sources (e.g., Unify) synced into CDH do not trigger journeys. Misunderstanding came from CDH tag history which includes external sources.
* Solution: Informed customer that MAAC journey triggers require tag applications initiated in MAAC. System behaved as designed.
{% endstep %}
{% endstepper %}

***

## Investigation of Internal Server Error in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-09-19
* Asana Task ID: [1211403559851471](https://app.asana.com/1/1184020052539844/task/1211403559851471)
* Ticket Priority: P2
* Client Name: \[REDACTED]
* Resolution Owner: David
* Result Breakdown: Fix Problems

{% stepper %}
{% step %}
### Issue Description

Internal server error when viewing automated journey performance (Journey Report: https://maac.cresclab.com/journey/report/39763).
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 6148
  * MAAC bot/channel ID: 5874
* Reproduction:
  1. Access the journey report.
  2. Attempt to view performance metrics.
  3. Observe "Internal server error".
* Expected: Display metrics successfully.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Discrepancy in open count calculation: journey uses "Daily first open" (counts user multiple times across days) differing from "lifetime unique open" in other features.
* Solution: Clarified and documented "Daily first open" behavior in help center. Further discussion planned to possibly unify open count logic across products.
{% endstep %}
{% endstepper %}

***

## Investigation of Automatic Journey Trigger Failure for Coupon Delivery

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-09-02
* Asana Task ID: [1211207436710401](https://app.asana.com/1/1184020052539844/task/1211207436710401)
* Ticket Priority: P2
* Client Name: \[REDACTED]
* Resolution Owner: Tracy, David
* Result Breakdown: Clarify (Meet product expectation)

{% stepper %}
{% step %}
### Issue Description

Contacts bound and tagged but did not trigger automatic journey to deliver coupon; multiple identical automatic journeys set up with similar issues.
{% endstep %}

{% step %}
### Context & Details

* Flow: Users register, complete LINE binding. Webhook returns tag and Customer ID. Tag "1000天網站-完成申請流程" should trigger coupon via journey.
* Reproduction: Registration at https://starthealthy.nestle.com.tw/member/join → LINE binding → expected coupon send.
* Observed: Some users didn't receive coupon despite tagging; testing confirmed issue.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: System design functioning as expected. For certain MAAC IDs, message not sent if user was unfollowed at send time. Logs show successful sends/opens in other cases.
* Solution: No system defect. Future reports should verify user's LINE follow status at message send. Provide logs of send attempts and member status for customer clarification.
{% endstep %}
{% endstepper %}

***

## Investigation of Incorrect Prize Display in Customer Journey

**Metadata**

* Feature: MAAC-Customer Journey
* Created At: 2025-09-04
* Asana Task ID: [1211218241020599](https://app.asana.com/1/1184020052539844/task/1211218241020599)
* Ticket Priority: P2
* Client Name: \[REDACTED]
* Resolution Owner: Tracy, David
* Result Breakdown: Too costly

{% stepper %}
{% step %}
### Issue Description

Journey preview incorrectly displayed "August Birthday Prize" despite prize configured as "September Birthday Prize"; actual prize and tags were correct.
{% endstep %}

{% step %}
### Context & Details

* Environment:
  * MAAC org ID: 3976
  * MAAC bot/channel ID: 3282
* Reproduction:
  1. Configure September prize.
  2. Preview journey message.
  3. Observe incorrect prize month in preview.
* Expected: Preview shows correct prize.
* Actual: Preview shows old prize name.
{% endstep %}

{% step %}
### Root Cause & Solution

* Root Cause: Known issue where prize name updates not consistently reflected in journey message editor/preview after initial application (system design limitation).
* Solution: Platform-wide fix planned for Q4. Workaround: manually re-edit prize name in the sending function's message editor to ensure correct display.
{% endstep %}
{% endstepper %}
