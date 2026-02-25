# broadcast\_asana\_history\_knowledge\_base\_final

## Why Are URLs Not Being Shortened and Tagged in Broadcast Messages?

**Metadata**

* **Feature:** MAAC-Broadcast
* **Created At:** 2025-11-20
* **Asana Task ID:** [1211999938098480](https://app.asana.com/1/1184020052539844/task/1211999938098480)
* **Ticket Priority:** P2
* **Client Name:** DK Marketing
* **Resolution Owner:** Jalex
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The client, DK Marketing, reported that URLs inserted in broadcast messages are not being converted into shortened links (https://maac.io) when sending test messages or actual broadcasts. Consequently, no tags are assigned when the URL is clicked. This issue affects both test and actual broadcast messages.

### 2. Context & Details

* **Environment Conditions:**
  * The issue is reproducible on the client account during test sending but not on the JP demo account.
  * MAAC org ID: 38
  * MAAC bot/channel ID: 37
  * Feature ID: 92186
* **Reproduction Steps:**
  1. Insert a URL in the broadcast message.
  2. Send a test message or an actual broadcast.
  3. Observe that the URL remains unshortened and no tag is assigned upon clicking.
* **Expected vs Actual Behavior:**
  * **Expected:** URLs should be converted into shortened links, and tags should be assigned upon clicking.
  * **Actual:** URLs remain unshortened, and no tags are assigned.

### 3. Root Cause & Solution

* **Root Cause:** A recently implemented MAAC logic explicitly skipped short URL conversion for URLs starting with https://miniapp.line.me. This was based on an assumption that it might cause issues similar to LIFF links. However, this assumption was found to be unnecessary after evaluation.
* **Solution:** The skip logic for https://miniapp.line.me URLs has been removed. MAAC now correctly converts these URLs into short links, resolving the issue.

***

## Investigation of Broadcast Delivery Failure to Active Contacts

**Metadata**

* **Feature:** MAAC-Broadcast
* **Created At:** 2025-10-06
* **Asana Task ID:** [1211557302787615](https://app.asana.com/1/1184020052539844/task/1211557302787615)
* **Ticket Priority:** P2
* **Client Name:** IXION - みんカラ
* **Resolution Owner:** Tracy
* **Result Breakdown:** Clarify (Meet product expectation)

### 1. Issue Description

The broadcast titled “251003\_ポイント10倍＋特集ランキング” was sent to all active contacts on October 3 via Smart Sending. However, one user reported not receiving the broadcast.

### 2. Context & Details

* **Environment Conditions:**
  * MAAC org ID: 13
  * MAAC bot: 12
  * Broadcast name: 251003\_ポイント10倍＋特集ランキング
  * UID of affected user: \[REDACTED]
* **Reproduction Steps:**
  * Broadcast sent on October 3 using Smart Sending.
  * User TAKE reported non-receipt of the broadcast.
* **Expected vs Actual Behavior:**
  * Expected: All active contacts receive the broadcast.
  * Actual: One user initially reported not receiving the broadcast.

### 3. Root Cause & Solution

* **Root Cause:**
  * The user ultimately confirmed receipt of the broadcast. The initial report of non-receipt was inaccurate or based on a misunderstanding of delivery.
* **Solution:**
  * The issue was a false alarm. No system bug was identified, and no product or engineering changes are required. The status is resolved.
