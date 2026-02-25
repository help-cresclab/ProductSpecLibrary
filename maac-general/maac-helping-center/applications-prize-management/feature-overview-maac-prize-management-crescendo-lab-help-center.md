# Feature Overview｜MAAC Prize Management – Crescendo Lab Help Center

## Purpose

On the unified MAAC platform, you can use prizes to enhance engagement, motivate user interaction, and reduce block rates.

Prizes can be customized with images, availability dates, labels, and redirect buttons. Combined with the MAAC message editor, they can be deployed through broadcasts, auto-replies, and customer journeys across various touchpoints.

***

## Prize Types

There are two main prize types:

* **Prize Coupons** (five subtypes):
  * Discount coupon
  * Voucher
  * LINE Points coupon
  * Brand coupon
  * Game coupon
*   **Card Message**:

    Brands can design custom visual layouts to present prizes as static visual messages.

***

## Prize campaign duration

![](../../../.gitbook/assets/48005839354009) ![](../../../.gitbook/assets/48033830243865)

For all prize types, the " **Prize Expiration Time**" is a required field. Brands can also optionally add a " **Valid Period After Claiming**" setting. The system will determine the actual validity period of prizes based on the following logic:

### Feature availability period

Some prizes belong to add-on modules. If the **add-on module's activation period** expires earlier than either the "Prize Expiration Time" or "Valid After Redemption," the prize will expire early and display as "Expired."

### Prize expiration time (Required)

* Brands must set a clear prize end time (e.g., 2025/07/01 23:59).
* This is the **unified deadline for all contacts to use the prize**, regardless of when users claim it. **Once this time is exceeded, redemption is no longer possible**.
* Redemption screen display (LIFF page): Expires at YYYY-MM-DD HH:MM

### Valid after redemption (Optional)

* You can set the redemption validity period calculated from the moment of claiming, with flexible time combinations (days, hours, minutes):
  * Maximum of **999 days**
  * Maximum of **23 hours**
  * Maximum of **59 minutes**
* For example, you can set prizes to be redeemed "within 3 days of claiming" or "within 2 hours 30 minutes of claiming".
* This feature helps create urgency for limited-time redemption, effectively improving conversion rates.
* Redemption screen display (LIFF page): Valid for: X days X hours X minutes remaining

### Expiration Logic

If **both** a fixed expiration time and a validity after redemption are configured, the system will automatically use **whichever expires first** as the final expiration time.

Example:

* Fixed Expiration Time: July 10
* Validity After Redemption: 3 days
* A user claims the prize on July 9 → Final expiration time = **July 10** (not July 12)

### Recommended Use Case

For **long-running campaigns**, we recommend the following setup:

* Configure a later **Fixed Expiration Time** to cover the full campaign period.
* Pair it with a **Validity After Redemption** to limit each user’s redemption window.

This approach allows:

* One-time prize setup (no need to update daily).
* Stronger urgency and better conversion from users upon receiving the prize.

***

## Redemption Methods

MAAC supports four redemption configurations:

* **General code**:
  * Requires a list of codes to be uploaded. All users will receive a code and a redemption URL. Codes may be unique or duplicated. Redemption quantity is based on the number of uploaded codes.
* **Fixed code**:
  * All users receive the same code. No need to upload a code list.
* **Unique URL**:
  * Requires code upload. Each user receives a dedicated redemption URL. Redemption quantity is based on the number of uploaded URLs.
* **Unique URL + Code**:
  * Requires code upload. Each user receives both a unique redemption URL and a code. Codes may be unique or duplicated.

***

## Prize Ownership ("Owned" Status)

The **Owned** status appears only when a prize is distributed through **Rapid Growth** or **Gamified Modules**.

This status indicates:

* The prize has been assigned to a user (i.e., the user has won).
* The user has not yet clicked the "Claim" button to receive the prize.

Prizes marked as **Owned** are already attributed to specific users and should not be reused or reassigned.

***

## Inventory Alert

MAAC supports **Inventory Alert** notifications:

* The system regularly checks remaining quantity.
* If the available quantity drops below the configured threshold or reaches zero, a notification email is sent automatically.
* If the threshold value is changed and the quantity is still below the new threshold, another alert email will be sent.
* Only one alert email is triggered per threshold breach.

***

## Prize Status and Analytics Overview

In the **Prize Management** list, you can track distribution progress and real-time status through the following fields.

![](../../../.gitbook/assets/54794404536345)

### Prize Lifecycle Flow

The status of a prize progresses from left to right based on contact interaction:

Unowned (Stock) → Owned (Won) → Claimed (Opened) → Redeemed (Used)

### Field Definitions

| Field Name   | Description                                                                                                                |
| ------------ | -------------------------------------------------------------------------------------------------------------------------- |
| **Uploaded** | The total number of prizes imported (only displayed for "Upload Serial Number" or "Unique Link" types).                    |
| **Unowned**  | In Stock: Remaining prizes that have not yet been won by or sent to a contact.                                             |
| **Owned**    | Won/Sent: The contact has received the prize but has **not yet clicked** the claim link.                                   |
| **Claimed**  | Confirmed: The contact has clicked the prize message and completed the claiming process.                                   |
| **Redeemed** | Completed: The contact has presented the prize and completed verification (only applicable to "Redeemable Voucher" types). |

* Status Display: In addition to the quantities above, the system displays **Active** or **Expired** under the prize name based on the "Availability Period."
* Revenue: If the prize involves a monetary value, the system automatically accumulates and displays it in the **Revenue** field.

***

## Revenue Display

* **Discount Coupons**:
  * Brands with GA integration: shows a numeric value (or 0).
  * Without GA: displays "-".
* **Vouchers**:
  * With prize redemption API: shows a numeric value (or 0).
  * Without API: displays "-".
* **LINE Points / Brand Coupons / Game Coupons**: always displays "-".

***

## Reports & Management

![](../../../.gitbook/assets/54794404540697)

* Export Prize Details: Click the **Export** button on the right side of the report to view the detailed performance of each prize.
* Add / Delete Serial Numbers: For prizes using the "Upload Serial Number" type, you can add or edit serial numbers as needed.

### Data Update Frequency

* List Page and Performance Overview: Updated **hourly**.

***

## Configuration Steps

To configure and launch prizes, please refer to the following Help Center articles based on the prize type or use case:

* https://crescendolab.zendesk.com/hc/en-us/articles/4412897068313
* https://crescendolab.zendesk.com/hc/en-us/articles/46100391001497
* https://crescendolab.zendesk.com/hc/en-us/articles/26392205202969

***

## FAQs

<details>

<summary>Are there any precautions when uploading codes?</summary>

* **Fixed codes** do not support quantity limits. Suitable only when the same code is issued to all users.
* To limit redemption quantity, use **uploaded code lists**:
  * For example, to offer 500 codes with the value "Crescendo 100", you must upload a CSV file with that same value listed in 500 rows.
* The system does not block duplicate codes. Please verify the code list before uploading.

</details>

<details>

<summary>What happens when both Prize Expiration Time and Valid After Redemption are set?</summary>

When both "Prize Expiration Time" and "Valid After Redemption" are configured, contacts will see **two types of deadline reminders** on the redemption screen (LIFF):

| Display Item                     | Description                                                                                     | Example Screen Display                        |
| -------------------------------- | ----------------------------------------------------------------------------------------------- | --------------------------------------------- |
| Valid Period (Dynamic Countdown) | Calculated from when the contact clicks to claim, based on **“Valid After Redemption”** setting | Valid for: 1 day 6 hours 31 minutes remaining |
| Fixed Expiration Time            | Latest redemption deadline for the prize, based on **“Prize Expiration Time”** setting          | Expires at 2022-12-31 23:59                   |

</details>

<details>

<summary>What are the rules for expiration settings when creating prizes?</summary>

* **Prize Expiration Time**: Required field - you must specify a clear end time when creating.
* **Valid After Redemption**: Optional field - you can set a validity period based on when users claim (e.g., valid within 7 days).

</details>

<details>

<summary>Can I modify the Prize Expiration Time after creation?</summary>

* Yes, modifications are supported before the prize expires.
* After modification, all users (including those who have already claimed) will see the deadline updated to the "new expiration time".

</details>

<details>

<summary>Can the Valid After Redemption be modified after prizes have been claimed?</summary>

* If "Dynamic Expiration" was checked during creation: Time can be modified, but **users who have already claimed will still see the "original Valid After Redemption"**.
* If "Dynamic Expiration" was not checked during creation: This setting cannot be added later, so the option will appear disabled.

</details>

<details>

<summary>Can I limit users to only claim once?</summary>

MAAC currently does not support limiting claims to one per user. This restriction must be implemented through the brand's own website or e-commerce platform.

</details>

<details>

<summary>What happens when inventory runs out?</summary>

* The system will display “All prizes claimed.”
* Users will be unable to claim any more prizes.
* This may result in user complaints. We recommend estimating inventory needs in advance and uploading sufficient quantities before launching a campaign.

</details>

<details>

<summary>When are inventory alert emails triggered?</summary>

* When remaining inventory falls below the threshold, an email is sent within 1 minute.
* Only one email is triggered per threshold breach.
* If the threshold is modified and inventory is still below the new value, another alert email will be sent.

</details>

***

### Related articles

* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBmFKXUDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkA6ewrKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ0L2hjL2VuLXVzL2FydGljbGVzLzQ0MTI4OTcwNjgzMTMtVHV0b3JpYWxzLVByaXplLU1hbmFnZW1lbnQtQ291cG9uLUxJTkUtUG9pbnRzLVZvdWNoZXJzLUdhbWUtdGl4cy1CcmFuZC1Db3Vwb25zBjsIVDoJcmFua2kG--f3b2310e7ab3679034adb825374d898d68becddd
* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJn9bZXtKToYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkA6ewrKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJYL2hjL2VuLXVzL2FydGljbGVzLzQ2MTAwMzkxMDAxNDk3LVR1dG9yaWFscy1NQUFDLVByaXplLU1hbmFnZW1lbnQtQ2FyZC1tZXNzYWdlLXR5cGUt dGFn
* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkNOwV6KzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkA6ewrKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJkL2hjL2VuLXVzL2FydGljbGVzLzQ3ODAzMDczNzYwNTM3LUZlYXR1cmUtT3ZlcnZpZXctU21hcnQtUmVkaXJlY3QtVG9vbC1Qcm9maWxlLVVuaWZpY2F0aW9uLUxpbmsGOwhUOglyYW5raQg%3D--9a5cf1fd493581497c3ba9e902c1e8d18adf97d0
* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkb49oDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkA6ewrKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJUL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQ2MDM3Mjk2ODktVHV0b3JpYWxzLU1BQUMtTWVzc2FnZS1Nb2R1bGUtVGVtcGxhdGUtTGlicmFyeQY7CFQ6CXJhbmtpCQ%3D%3D--65fd1c099348f4bcd5bb9cccb4485db564fc4048
* https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJlhmbH9JToYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBkA6ewrKzoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJDL2hjL2VuLXVzL2FydGljbGVzLzQxNzcxNTM2NTcyODI1LUZlYXR1cmUtT3ZlcnZpZXctUmV0YXJnZXRpbmcGOwhUOglyYW5raQo%3D--82ae0a7ee1d6f3433af964893d564ca9498fc08d

(Keep all links and query parameters unchanged.)
