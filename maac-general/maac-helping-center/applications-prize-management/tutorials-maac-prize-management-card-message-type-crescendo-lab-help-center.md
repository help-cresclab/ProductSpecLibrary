# Tutorials｜MAAC Prize Management - Card message type – Crescendo Lab Help Center

#### 💁🏻‍♀️ Feature Overview

On the MAAC platform, brands can use the “Prize Management” feature to flexibly distribute incentives, enhance user engagement and event participation, effectively reduce block rates, and increase brand favorability.

Review: [Tutorials｜My Coupons](https://crescendolab.zendesk.com/hc/en-us/articles/4414607323929)

NEW! Enhanced Brand Identity\
You can now customize colors for each prize to create a unique brand style. Set display colors based on your brand identity, or use the default style.

👉 This feature is only available for users on the Brand Plan. Non-brand customers who wish to purchase additional products please contact Crescendo Lab.

***

#### 🎫 Prize Types and Features

| Prize Type     | Applicable Scenarios / Feature Description                                                                                                                                                                                                                                                                                           |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Coupon         | <p>- Applicable to most e-commerce brands<br>- Customize coupon name, button text, and button image<br>- Supports uploading serial codes (fixed or sequential)<br>- Automatically add tags to users who redeem the coupon</p>                                                                                                        |
| LINE Points    | <p>- Suitable for brands that purchase LINE Points<br>- Clicking “Click to Redeem” will redirect to the official redemption page</p>                                                                                                                                                                                                 |
| Voucher        | <p>- Ideal for physical store promotions<br>- Redeemable by store staff via the “Redeem” button<br>- Optional display of barcodes for scanning<br>- Supports API-based barcode redemption if purchased</p>                                                                                                                           |
| Game Tix       | <p>- Requires purchase of gaming module<br>- Can be targeted and distributed by audience segments<br>- Use with game module to increase engagement and participation</p>                                                                                                                                                             |
| Brand Coupon   | <p>- Clicking the “Claim” button can trigger delivery of images, messages, wallpapers, etc.<br>- Message content and delivery style can be customized using the MAAC editor</p>                                                                                                                                                      |
| Points Voucher | <p>- Suitable for brands that have purchased Webhook and integrated their membership system.<br>- Points are written directly into the brand’s member database; users can view and use them via the existing member page.<br>- Ideal for campaigns aimed at boosting member engagement and driving traffic to the member portal.</p> |

⚠️ The animated GIF claim prompt in the new version of Prize Coupons can now be flexibly toggled by the brand, with the default setting being off. This update does not affect the style of previously issued prize messages.

***

### 🎫 Features and Setup Instructions for Each Prize Type

**✨ 🆕 Exclusive to Brand Plan: Coupon Style – Card Message**

Setup Steps:

{% stepper %}
{% step %}
### Select Card Message Style

* Select “Card Message” as the coupon style.
{% endstep %}

{% step %}
### Configure Image Card Message

* Upload an image file.
* Enter the card title, card description, and button name.
* You can set claimed tags (up to 10 groups).

![](../../../.gitbook/assets/46544277253401) ![](../../../.gitbook/assets/46544277254937)
{% endstep %}
{% endstepper %}

***

#### 🎟️ Coupon

Applicable Use & Features:

* Suitable for most e-commerce brands
* Customize coupon name, button text, and button image
* Supports general code, fixed code, unique link, or unique link + code
* UTM parameters can be set to track conversion performance

Configuration Steps:

{% stepper %}
{% step %}
### Create Prize

* Go to the Prize Management page and click “Create”.
{% endstep %}

{% step %}
### Basic Settings

* Set prize name
* Award Type: Coupon
* Set validity period (time after prize is received during which it can be redeemed)
* Redemption type: general code, fixed code, unique link, or unique link + code
* Import codes: download the template and reupload after editing

![](../../../.gitbook/assets/46130262827417)
{% endstep %}

{% step %}
### Coupon Style

* Set coupon title
* Set button name

🆕 Color Customization｜Foreground Color

* Basic Plan Users: Default color applied automatically (no customization).
* Brand Plan Users: Foreground color can be customized — click on the color bar to select brand-matching colors.
* Set claimed tag (Up to 10 tags).

![](../../../.gitbook/assets/46130262829465) ![](../../../.gitbook/assets/46130262830873)
{% endstep %}

{% step %}
### Redemption Page

* Set page title
* Image settings (optional)
* Customizable rule descriptions

🆕 Redemption Page Color Settings

* Basic Plan Users: Default color scheme applied (no customization).
* Brand Plan Users: Customize foreground and background colors via the color bar.

Button Settings:

* Button Text: Customize the button label (e.g., "Redeem Now", "Get Reward").
* Button Link: Directs users to a URL (landing page, e-commerce site, campaign). If using e-commerce integration, append UTM parameters for tracking.

![](../../../.gitbook/assets/46130301204761) ![](../../../.gitbook/assets/46130301207065) ![](../../../.gitbook/assets/46130262838041)
{% endstep %}
{% endstepper %}

Review: [Tutorial | MAAC Prize Management - Prize Unique URL](https://crescendolab.zendesk.com/hc/en-us/articles/26392205202969-Tutorial-MAAC-Prize-Management-Prize-Unique-URL)

***

#### 💰 LINE Points

Applicable scenarios and features:

* Available for all brands that have purchased LINE Points
* Clicking “Redeem Now” redirects users to the official LINE Points redemption page

Setup steps:

{% stepper %}
{% step %}
### Create Prize

* Go to the Prize Management page and click Create.
{% endstep %}

{% step %}
### Basic Settings

* Enter prize name
* Set prize type to LINE Points
* Set validity period
* Import codes: download and upload your edited template

![](../../../.gitbook/assets/46130262839449)
{% endstep %}

{% step %}
### Coupon Style

* Set title
* Set button text

🆕 Prize Color Options｜Foreground Color

* Basic Plan Users: Default color applied automatically (no customization).
* Brand Plan Users: Foreground color can be customized (click color bar).
* Set claim tag (Up to 10 tags).

![](../../../.gitbook/assets/46130262843801) ![](../../../.gitbook/assets/46130301215385)
{% endstep %}

{% step %}
### Redemption Page

* Set page title
* Optional image upload
* Customize rules text

🆕 Page Color Customization

* Basic Plan Users: Default color scheme applied.
* Brand Plan Users: Customize foreground and background colors.

![](../../../.gitbook/assets/46130301216793) ![](../../../.gitbook/assets/46130262848281)
{% endstep %}
{% endstepper %}

Note:

1. Only “text format” codes purchased from LINE official or agents are supported.
2. Do not reuse the same code in multiple campaigns to avoid duplication issues.

***

#### 🏪 Voucher

Applicable scenarios and features:

* Ideal for in-store campaigns
* Staff can manually tap to redeem
* Option to display barcode
* Optional add-on: API for auto-scan redemption

Setup steps:

{% stepper %}
{% step %}
### Create Prize

* Go to the Prize Management page and click Create.
{% endstep %}

{% step %}
### Basic Settings

* Enter prize name
* Set prize type to Voucher
* Set validity period
* Select code type: General code, Unique code, Fixed code, or None
* Import codes: download and upload your edited template

![](../../../.gitbook/assets/46130262849177)
{% endstep %}

{% step %}
### Coupon Style

* Set page title
* Set button text

🆕 Prize Color Options｜Foreground Color

* Basic Plan Users: Default color applied automatically (no customization).
* Branded Plan Users: Foreground color can be customized (click color bar).
* Set claim tag (Up to 10 tags).

![](../../../.gitbook/assets/46130301223449) ![](../../../.gitbook/assets/46130301224857)
{% endstep %}

{% step %}
### Redemption Page

* Set page title
* Optional image upload
* Customize rules text

🆕 Page Color Customization

* Basic Plan Users: Default color scheme applied.
* Brand Plan Users: Customize foreground and background colors.

Barcode & Redemption Settings:

* Enable barcode if QR scan validation is needed
* Enable the manual redemption button for store staff operation
* Redemption Tag: Auto-tag contacts after successful redemption (Up to 10 tags)

![](../../../.gitbook/assets/46130262856089) ![](../../../.gitbook/assets/46130301257625)

Supported Barcode Formats: Code 39, Code 128, PZN, EAN-13, EAN-8, JAN, ISBN-13, ISBN-10, ISSN, UPC-A
{% endstep %}
{% endstepper %}

***

#### 🎮 Game Tixs (Requires Add-on Game Module)

Eligibility & Features:

* Requires the purchase of an add-on game module
* When chosen as a prize, Game tixs can be promoted via audience targeting, form completion, member binding, etc.
* Avoid using with "Daily Draw" to prevent loss of attempts due to reset timing. Failed entries cannot be retrieved via the backend.

Setup Steps:

{% stepper %}
{% step %}
### Create Prize

* Go to the Prize Management page and click Create.
{% endstep %}

{% step %}
### Basic Settings

* Set the prize name
* Prize type: Game Tix
* Set validity period
* Select the game module to link
* Set increase game times:
  * Total playable turns = game voucher turns + module turns.
  * Example: 1 voucher + 1 module turn = 2 total turns. To restrict to one turn, set game voucher to 1 and module to 0.

![](../../../.gitbook/assets/46130262860313)
{% endstep %}

{% step %}
### Coupon Style

* Set voucher title
* Set button name

🆕 Prize Color Options｜Foreground Color

* Basic Plan Users: Default color applied automatically (no customization).
* Brand Plan Users: Foreground color can be customized (click color bar).
* Set claim tag (Up to 10 tags).

![](../../../.gitbook/assets/46130301262873) ![](../../../.gitbook/assets/46130262865177)
{% endstep %}

{% step %}
### Redemption Page

* Set page title
* Optional image upload
* Customize rules text

🆕 Page Color Customization

* Basic Plan Users: Default color scheme applied.
* Brand Plan Users: Customize foreground and background colors.

![](../../../.gitbook/assets/46130262866457) ![](../../../.gitbook/assets/46130418146329)
{% endstep %}
{% endstepper %}

***

#### 🖼️ Brand Coupon

Eligibility & Features:

* After clicking "Claim" button, can send images, text, wallpaper, interactive messages, etc.
* Use rich message editor to customize content and format

Setup Steps:

{% stepper %}
{% step %}
### Create Prize

* Go to the Prize Management page and click Create.
{% endstep %}

{% step %}
### Basic Settings

* Set the prize name
* Prize type: Brand Coupon
* Set validity period

![](../../../.gitbook/assets/46130406618393)
{% endstep %}

{% step %}
### Coupon Style

* Set voucher title
* Set button name

🆕 Color Settings | Foreground Color

* Basic Plan Users: Default system color applied
* Brand Plan Users: Custom foreground color selectable
* Set claim tag (Up to 10 tags)
* Set triggered message: After clicking the button, send a message that may include:
  * Text instructions
  * Image / wallpaper
  * Prompt for user data (e.g., name, phone, address)

🚨 Note: This message will be sent immediately after claiming, and message fees apply. Please evaluate usage accordingly.

![](../../../.gitbook/assets/46130406619417) ![](../../../.gitbook/assets/46130406620441)
{% endstep %}
{% endstepper %}

***

#### 🎯 Reward Points (Add-on feature; requires Webhook purchase)

Eligibility & Features

* For brands that purchased Webhook and have a connected membership system.
* Points are added directly to the brand’s member database; members can check or use them on the original membership page.
* Supports distribution via segmented broadcast, referral links, surveys, referrals, or interactive games.
* Useful for boosting member activity and driving traffic to your member portal.

Notes

* This feature requires both Webhook and Reward Points to be enabled (not included in the basic or e-commerce plan).
* Reward Points only send points—brands need their own point system.
* To connect your point system with MAAC, you can either:
  * Have developers integrate using MAAC’s Open API (Open API technical documentation: https://cresclaben.docs.apiary.io/#)
  * Use a MAAC-integrated vendor such as Litloyal by Migo or Wishmobile

Depending on your setup:

* If your system uses LINE UID, you can send points without binding.
* If your system uses Customer ID, you’ll need to bind first before issuing points.

Some vendors support LINE binding. MAAC also supports binding via notification messages or Open API.

Configuration Steps:

{% stepper %}
{% step %}
### Create Prize

* Go to the Prize Management page and click “Create”.
{% endstep %}

{% step %}
### Basic Settings

* Set prize name
* Award Type: Reward Points
* Set validity period
* Redemption type: general code, fixed code, unique link, or unique link + code
* Import codes: download the template and reupload after editing

![](../../../.gitbook/assets/46148110155545)
{% endstep %}

{% step %}
### Coupon Style

* Set coupon title
* Set button name

🆕 Color Customization｜Foreground Color

* Basic Plan Users: Default color applied automatically (no customization).
* Brand Plan Users: Foreground color can be customized (click color bar).
* Set claimed tag (Up to 10 tags).

![](../../../.gitbook/assets/46148094625817) ![](../../../.gitbook/assets/46148110157209)
{% endstep %}

{% step %}
### Redemption Page

* Set page title
* Image settings (optional)
* Customizable rule descriptions

🆕 Redemption Page Color Settings

* Basic Plan Users: Default color scheme applied.
* Brand Plan Users: Customize foreground and background colors.

Prize Button Design:

* Button Name: Customize the button label.
* Button Type:
  * URL: directs users to a designated URL (append UTM if desired).
  * Keyword responses: customize keyword responses upon clicking the button.

![](../../../.gitbook/assets/46130301204761) ![](../../../.gitbook/assets/46148094628249) ![](../../../.gitbook/assets/46148094629145)
{% endstep %}

{% step %}
### Unbound Contact Invitation

* If the brand restricts reward points to bound contacts only, set an invitation-to-bind message.

![](../../../.gitbook/assets/46148271338009) ![](/broken/files/ee8824a94e483c6ca12d1655175df5b508c937f5)
{% endstep %}
{% endstepper %}

***

### ▶︎ View and Manage Prize Performance

* On the Prize Management page, you can view each prize’s status, code count, number of claims and redemptions. Use the search bar to locate prizes by name.
* The right side of the prize name shows the current status (e.g., "Valid", "Expired").
* Uploaded code:
  * If using a code pack, it shows the total number of codes.
  * If using a fixed code, a dash “–” will be shown.
* Claimed: Number of prizes that have been claimed by users.
* Redeemed: Number of prizes that have been redeemed by users.
* Revenue metrics:
  * Coupon: If GA is integrated, the revenue will display numbers or 0; if not integrated, a dash “–” will be shown.
  * Voucher: If the prize redemption API is purchased, revenue will display numbers or 0; otherwise, a dash “–”.
  * LINE Points, Game tixs, and Brand Coupons: Will display a dash “–”.
* Click the rightmost icon beside each prize to view reports or edit/delete the prize.

![](../../../.gitbook/assets/46130548884633)

***

### ❓ FAQs

<details>

<summary>Q1: What does “Attributed” mean and when does it appear?</summary>

A: The “Attributed” status only appears under the following circumstances:

* Rapid referral module
* Game interaction modules (5 types, e.g., gacha, wheel)

This means the follower has already won a prize, and the system has assigned the prize to them. However, the user has not yet clicked “Claim Now” to complete the process.

</details>

<details>

<summary>Q2: Can I reassign an “Attributed” prize?</summary>

A: Not recommended. Once attributed, the prize is already assigned to a specific follower. Reassigning may result in errors or duplicated delivery and should be considered as locked.

</details>

<details>

<summary>Q3: How does the “Attributed” data appear in reports?</summary>

A: In performance reports, the numbers are calculated as follows:

* Claimed = Claimed + Redeemed
* Redeemed = Redeemed

</details>

<details>

<summary>Q4: How frequently is the data on the Prize Management page updated?</summary>

A:

* Overall prize list and performance data: updated every hour
* Claim list on individual prize pages: updated in real-time

</details>

<details>

<summary>Q5: Can I limit each user to claim only once?</summary>

A: Currently, MAAC does not support this restriction. It is recommended to implement this control on your official website or e-commerce platform.

</details>

<details>

<summary>Q6: Can I control how many times a fixed code can be redeemed?</summary>

A: No. If the same fixed code (e.g., "Crescendo100") is to be reused, list it multiple times in a CSV file and upload it as a code pack.

</details>

<details>

<summary>Q7: Will the system automatically detect or block duplicate codes?</summary>

A: No. MAAC will not check for duplicate codes. Please confirm that your codes have not been uploaded before submitting.

</details>

<details>

<summary>Q8: What will users see if there are not enough prizes available?</summary>

A: If all prizes are claimed, users will see one of the following messages:

* “All prizes have been claimed”
* “Prizes are no longer available”

We recommend confirming that you have uploaded enough prizes in advance to avoid user experience issues and increased support inquiries.

</details>

***

### ▶︎ Integrate with Other MAAC Features

1. In MAAC, select functions that support the editor such as Broadcast, Auto-reply, or Customer Journey.
2. In the editor, go to the Message module and select “Prize”. You can select an existing prize or click “Create Prize” to be redirected to the Prize Management page.

![](../../../.gitbook/assets/46130576874393)

***

Related articles

* [Tutorials｜ Prize Management：Coupon、LINE Points、Vouchers、Game tixs、Brand Coupons](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBmFKXUDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJn9bZXtKToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ0L2hjL2VuLXVzL2FydGljbGVzLzQ0MTI4OTcwNjgzMTMtVHV0b3JpYWxzLVByaXplLU1hbmFnZW1lbnQtQ291cG9uLUxJTkUtUG9pbnRzLVZvdWNoZXJzLUdhbWUtdGl4cy1CcmFuZC1Db3Vwb25zBjsIVDoJcmFua2kG--89a5a8636b89753f4a24c40f336a7ddfa323eb70)
* [Tutorial | MAAC Prize Management - Prize Unique URL](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkWBOoAGDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJn9bZXtKToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJWL2hjL2VuLXVzL2FydGljbGVzLzI2MzkyMjA1MjAyOTY5LVR1dG9yaWFsLU1BQUMtUHJpemUtTWFuYWdlbWVudC1Qcml6ZS1VbmlxdWUtVVJMBjsIVDoJcmFua2kH--7f4ed38a62f25d68aa2365cfe78e8a2e721bd6c6)
* [Tutorials｜MAAC Access Management](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJlLA4mgKDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJn9bZXtKToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJHL2hjL2VuLXVzL2FydGljbGVzLzQ0NjY5OTU4NTcyOTUzLVR1dG9yaWFscy1NQUFDLUFjY2Vzcy1NYW5hZ2VtZW50BjsIVDoJcmFua2kI--aa3574b277e2396c4f0b46165261977a0b9934b9)
* [Tutorials｜ MAAC x SurveyCake Form](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkr5rYDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJn9bZXtKToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJGL2hjL2VuLXVzL2FydGljbGVzLzQ0MTM5OTk5NTA3NDUtVHV0b3JpYWxzLU1BQUMteC1TdXJ2ZXlDYWtlLUZvcm0GOwhUOglyYW5raQk%3D--ec2925741eeb17086806b4b106fa32c86308906f)
* [Tutorials｜Rapid Referral](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkzBMgDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJn9bZXtKToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI%2BL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQyODcxMzE0MTctVHV0b3JpYWxzLVJhcGlkLVJlZmVycmFsBjsIVDoJcmFua2kK--5840b821838f0adee9178c386f58273565e0f0c9)
