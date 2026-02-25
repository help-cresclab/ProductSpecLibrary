# Feature Description｜MAAC Contact Import and Update – Crescendo Lab Help Center

This article guides you through batch importing or updating contact data via CSV files. As MAAC upgrades to an omnichannel platform, you can now import contact lists for **Email (EDM)** and **WhatsApp** in addition to LINE.

## Import Fields & Specifications

To ensure data is imported correctly, please prepare your CSV file according to the tables below. Different channels have specific required fields.

**LINE Channel Import**

| **Field Name** | **Description**            | **Required?** | **Updatable?** | **Note**                                                                                                           |
| -------------- | -------------------------- | ------------- | -------------- | ------------------------------------------------------------------------------------------------------------------ |
| line\_uid      | LINE User UID              | No            | ❌              | Primary identifier for LINE contacts.                                                                              |
| phone          | Phone Number               | No            | △              | <p>- WhatsApp contact phone numbers cannot be edited.<br>- Other channel contact phone numbers can be updated.</p> |
| customer\_id   | Custom Brand ID            | No            | ✅              | Recommended to be unique; used for syncing external data.                                                          |
| name           | Display Name               | No            | ✅              | Will overwrite existing value if populated.                                                                        |
| email          | Email Address              | No            | △              | <p>- Email contact (EDM) addresses cannot be edited.<br>- Other channel contact emails can be updated.</p>         |
| note           | Notes                      | No            | ✅              | Will overwrite existing value.                                                                                     |
| tags           | Tags                       | No            | ✅              | Separate with commas. New tags will be merged/added.                                                               |
| Custom Fields  | Fields created in settings | No            | ✅              | Column name must match exactly.                                                                                    |

**Email (EDM) Channel Import**

Applicable for importing Email marketing lists. Please note that EDM import has strict **Status** validation mechanisms to protect sender reputation.

| **Field Name**              | **Description**     | **Required?** | **Note**                                                                               |
| --------------------------- | ------------------- | ------------- | -------------------------------------------------------------------------------------- |
| email                       | Email Address       | Yes           | The primary identifier for EDM contacts.                                               |
| <p>messaging_<br>status</p> | Subscription Status | Yes           | Value must be one of: "subscribed", "unsubscribed", "hard\_bounce", or "spam\_report". |
| display\_name               | Display Name        | No            | Max 255 characters.                                                                    |
| gender                      | Gender              | No            | Value must be: "female", "male", or "unknown".                                         |
| customer\_id                | Custom Brand ID     | No            | Recommended to be unique.                                                              |
| mobile                      | Phone Number        | No            | Must follow E.164 format. E.g., for Taiwan: "0912345678" or "+886912345678".           |
| birthday                    | Birthday            | No            | Format: YYYY-MM-DD.                                                                    |
| tag                         | Tags                | No            | Separate with commas; will be merged/added.                                            |
| consent\_source             | Consent Source      | No            | Source of consent (e.g., "Website Footer", "Checkout"). Used for auditing.             |
| consent\_at                 | Consent Time        | No            | Precise time of consent. Format: YYYY-MM-DD hh:mm:ss. Used for auditing.               |

**WhatsApp Channel Import**

Applicable for importing WhatsApp phone lists. This channel **must** include the Status field, otherwise import will fail.

| **Field Name**              | **Description**     | **Required?** | **Note**                                                                                   |
| --------------------------- | ------------------- | ------------- | ------------------------------------------------------------------------------------------ |
| WhatsApp\_mobile            | WhatsApp Number     | Yes           | **Required.** Do not change column header. Must follow E.164 format (e.g., +886912345678). |
| <p>messaging_<br>status</p> | Subscription Status | Yes           | **Required.** Value must be one of: "opted\_in", "opted\_out", or "not\_subscribed".       |
| display\_name               | Display Name        | No            | Max 255 characters.                                                                        |
| gender                      | Gender              | No            | Value must be: "female", "male", or "unknown".                                             |
| customer\_id                | Custom Brand ID     | No            | Recommended to be unique.                                                                  |
| email                       | Email               | No            | Contact email.                                                                             |
| birthday                    | Birthday            | No            | Format: YYYY-MM-DD.                                                                        |
| tag                         | Tags                | No            | Separate with commas; will be merged/added.                                                |

## Choosing a "Key Value" (Identifier)

Before importing, you must select 1 field as the Key Value. The system uses this to decide whether to "Update" or "Create" a contact:

| **Key Value** | **Description** | **Recommended Scenario**                   |
| ------------- | --------------- | ------------------------------------------ |
| line\_uid     | LINE User UID   | Contacts created via webhook/LINE.         |
| phone         | Phone Number    | WhatsApp lists, phone lists, offline data. |
| email         | Email Address   | Email (EDM) subscriber lists.              |
| customer\_id  | Brand Custom ID | CRM systems, API integration users.        |

⚠️ Note: If multiple contacts in the system share the same phone number, the system will update the contact with the **later creation time**. To avoid incorrect updates, it is recommended to use `line_uid` or `customer_id`.

## System Behavior After Import

| **Condition**                         | **Result**                                                                  |
| ------------------------------------- | --------------------------------------------------------------------------- |
| Key Value matches existing contact    | Update contact data (overwrites filled fields only).                        |
| Key Value does not match              | Create new contact (Unless Key is customer\_id, which does not create new). |
| Incorrect Column Name                 | Field skipped.                                                              |
| Multiple values in 'tags'             | Merged with existing tags; does not overwrite.                              |
| Attempt to update Channel Primary Key | System ignores update (line\_uid / email / WhatsApp\_mobile / SMS phone).   |

## Important Notes on Updates

* Blank fields in CSV do not overwrite existing data.
* Custom field names must match the backend setting exactly.
* If multiple identifier columns are present, the system follows the selected Key Value.
* LINE UID, WA mobile, Email (primary), and Phone (SMS) are non-updatable fields.
* The email address of an Email contact cannot be overwritten.

## Channel Import Restrictions

For EDM and WhatsApp channels, strictly adhere to the Status column logic and validation rules.

### A. Email (EDM) Import Restrictions

#### Status Irreversibility

To comply with **international anti-spam laws and protect domain reputation**, MAAC enforces a strict **"Status Irreversibility"** rule:

🚫 You cannot use CSV import to change a contact from "Unsubscribed" or "Hard Bounce" back to "Subscribed".

* If you attempt to change `Unsubscribed` to `Subscribed` in the CSV, the system will **ignore the status update** while updating other fields (e.g., name, phone). This prevents sending to users who have opted out, protecting your brand from being blacklisted.

#### Auto-Suspension Policy

To maintain sending quality, the system monitors domain performance. Your sending function may be **automatically suspended** if:

* Trigger Conditions (within 24 hours):
  * Hard Bounce: 20 occurrences **AND** bounce rate 5%.
  * Spam Report: 10 occurrences **AND** complaint rate 0.5%.

How to Restore?

* Clean your email list using 3rd-party tools to remove invalid addresses.
* Import the cleaned results to MAAC to update contact status.
* Contact your CSM to apply for reinstatement (requires manual review).

⚠️ Use only consensual, opted-in lists. Do not use purchased or scraped lists.

### B. WhatsApp Import Restrictions

#### Mandatory Fields: Status & Format

To meet Meta's technical specs, WhatsApp import has mandatory rules:

*   Status Field is Mandatory — Unlike other channels, the `status` field is **strictly required**.

    Allowed Values: `opted_in`, `not_subscribed`, `opted_out`.

    System Behavior: If `status` is blank, the system will **"Skip"** the row entirely.
* Phone Number Format — Must use **E.164 International Format** (e.g., `+886912345678`). Incorrect formats will result in failure.

#### Meta Quality & Suspension

* Risk: Sending to `not_subscribed` or `opted_out` users leads to blocks/reports, lowering your **Quality Rating** and sending limits.
* Risk Acceptance: If your list includes non-subscribed users, MAAC will require you to sign a **Risk Acceptance Form** before sending.

## Import Steps

{% stepper %}
{% step %}
### Download Template

Go to **Contact Management Import / Update Contacts** and download the system provided **CSV Import Template**.

Tip: Export existing contacts first to check column names and ensure Key Values match to avoid duplicates.
{% endstep %}

{% step %}
### Upload File

Upload your prepared CSV file. The system will auto-validate format and data.
{% endstep %}

{% step %}
### View Results

Once completed, you will receive a notification (bell icon). If there are failures, download the "Import Failure Report" to check for errors (e.g., invalid format, empty status) and correct them.
{% endstep %}
{% endstepper %}

## FAQ

<details>

<summary>Q: If the imported phone number exists multiple times in the system, which one is updated?</summary>

A: The system updates the contact with the **later creation time**. To avoid ambiguity, use `line_uid` or `customer_id` as the Key.

</details>

<details>

<summary>Q: Will existing tags be overwritten during import?</summary>

A: No. Imported tags are merged with existing tags.

</details>

<details>

<summary>Q: Why didn't certain fields update?</summary>

A: Possible reasons:

* The field was blank in the CSV.
* Column name does not match backend settings.
* Field is a "Channel Primary Key" and cannot be updated (line\_uid, WhatsApp\_mobile, email).
* Used `customer_id` as Key, but the ID does not exist in the system (cannot create new).

</details>

<details>

<summary>Q: Can I create and update contacts in the same file?</summary>

A: Yes. The system judges based on the Key Value. However, if using `customer_id` as the Key, it only updates existing contacts and will not create new ones.

</details>

<details>

<summary>Q: Why are contacts merged after import?</summary>

A: MAAC uses **Profile Unification** logic. If any of these fields match an existing contact, they are merged: email, phone, customer\_id, line\_uid, WhatsApp\_mobile, fb\_id, ig\_id.

</details>

<details>

<summary>Q: Why were some rows skipped during WhatsApp import?</summary>

A: WA import requires two mandatory fields: `WhatsApp_mobile` and `status`. If status is empty, the row is skipped.

</details>
