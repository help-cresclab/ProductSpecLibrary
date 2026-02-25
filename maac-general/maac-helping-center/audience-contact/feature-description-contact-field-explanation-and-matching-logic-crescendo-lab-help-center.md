# Feature Description｜Contact Field Explanation and Matching Logic – Crescendo Lab Help Center

### Feature Overview

MAAC allows brands to create and update contacts through various methods. Based on the selected **Key** value, the system automatically determines whether to add a new contact or update an existing one. This article explains:

* Supported contact fields and formats
* Matching logic using Key values
* Field behavior during import/update
* Common errors and reasons for update failure

### Matching Logic

Each time you import contact data, you must select a **Key** for identifying existing contacts.

* If a match is found, the system updates the existing contact.
* If no match is found, a new contact is created.

| Key           | Applicable To                     | Matching Logic                    | Notes                                                  |
| ------------- | --------------------------------- | --------------------------------- | ------------------------------------------------------ |
| `line_uid`    | LINE contacts                     | Matches based on LINE UID         | Recommended when using webhook or green badge API      |
| `customer_id` | Custom contacts / API integration | Matches a brand-defined unique ID | Recommended when exporting from CRM                    |
| `phone`       | Contacts with saved phone numbers | Matches based on phone number     | If duplicates exist, the system updates the latest one |

{% hint style="info" %}
Tip: Before importing, export existing data to confirm the correct Key is used to avoid creating duplicate contacts.
{% endhint %}

### Supported Fields Overview

| Field Name           | Description              | Importable | Updatable | Notes                                                |
| -------------------- | ------------------------ | ---------- | --------- | ---------------------------------------------------- |
| `line_uid`           | LINE user UID            | ✅          | ✅         | Key field for LINE contacts                          |
| `phone`              | Phone number             | ✅          | ✅         | Avoid assigning the same number to multiple contacts |
| `customer_id`        | Brand-defined unique ID  | ✅          | ✅         | Must be unique                                       |
| `name`               | Display name             | ✅          | ✅         | Will overwrite existing value if provided            |
| `email`              | Email address            | ✅          | ✅         | Will overwrite existing value if provided            |
| `note`               | Notes                    | ✅          | ✅         | Will overwrite existing value if provided            |
| `tags`               | Contact tags             | ✅          | ✅         | Tags will be merged, not overwritten                 |
| `fb_id` / `ig_id`    | Facebook / Instagram UID | ✅          | ✅         | Must be obtained via API integration                 |
| `external_member_id` | System integration UID   | ❌          | ❌         | Export-only; not supported for import/update         |
| Custom Fields        | Brand-created fields     | ✅          | ✅         | Field name must exactly match backend configuration  |

### Field Update Behavior & Notes

| Behavior                 | System Handling                        |
| ------------------------ | -------------------------------------- |
| Field contains new value | New value will overwrite the original  |
| Field is left blank      | Original value is retained             |
| Multiple tags included   | Tags will be merged with existing ones |
| Field name is incorrect  | System will skip the field             |

### What is a "Bound Contact"?

In MAAC, a contact with a `customer_id` is considered a **bound contact**.

This means the contact is linked to your internal system (e.g., CRM or membership system) and can be used for personalized integrations and automation.

Use cases:

* Personalized Rich Menu\
  Show different menus for bound/unbound users (e.g., “Join Member” vs. “Order History”)
* Conditional Auto-reply Messages\
  Send special messages to bound users (e.g., VIP offers or birthday wishes)
* System Integration\
  Use `customer_id` in API or webhook payloads to ensure consistent identification

{% hint style="info" %}
Reminder: If your brand offers a membership program or loyalty rewards, we recommend binding contacts via `customer_id` to enable personalization and advanced automation.
{% endhint %}

### FAQ

<details>

<summary>Q1: Which field should I use as the Key?</summary>

A: Choose the Key based on your data source:

* LINE webhook → use **line\_uid**
* CRM export → use **customer\_id**
* Phone list → use **phone** (ensure no duplicates)

</details>

<details>

<summary>Q2: If I use phone as the Key, which contact will be updated?</summary>

A: The system will update the **most recently created** contact with the same phone number.

We recommend using **line\_uid** or **customer\_id** to avoid incorrect updates.

</details>

<details>

<summary>Q3: Can I use <code>external_member_id</code> for import or update?</summary>

A: No. This field is export-only and cannot be used for import or update operations.

</details>

### Learn More

* [Feature Description｜MAAC Contact Import, Update and Export](https://crescendolab.zendesk.com/hc/en-us/articles/4413238667801)

### Related articles

* [Feature Description｜MAAC Contact Import and Update](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBnqhYkDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnT4u8aLToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJYL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMzg2Njc4MDEtRmVhdHVyZS1EZXNjcmlwdGlvbi1NQUFDLUNvbnRhY3QtSW1wb3J0LWFuZC1VcGRhdGUGOwhUOglyYW5raQY%3D--f5da2a421e85d44e3c2f20dd60e6704a9ba75029)
* [Tutorials｜MAAC Contacts](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmIGIkDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnT4u8aLToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI9L2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMzE0OTk0MTctVHV0b3JpYWxzLU1BQUMtQ29udGFjdHMGOwhUOglyYW5raQc%3D--7de2c7b28afee882a1f44662e0ea3ea6a58778dc)
* [How to share LINE OA platform, LINE Developers, GA(UA) / GA4 access to Crescendo Lab?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmp1FFgBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnT4u8aLToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ1L2hjL2VuLXVzL2FydGljbGVzLzgxMTAyNzExNDYzOTMtSG93LXRvLXNoYXJlLUxJTkUtT0EtcGxhdGZvcm0tTElORS1EZXZlbG9wZXJzLUdBLVVBLUdBNC1hY2Nlc3MtdG8tQ3Jlc2NlbmRvLUxhYgY7CFQ6CXJhbmtpCA%3D%3D--088e018ef5f0e1a5e74a2d9c3e52477d81e9279f)
* [Tutorials｜CAAC AI - Chatbase Integration](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBmLClcRLToYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnT4u8aLToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJNL2hjL2VuLXVzL2FydGljbGVzLzQ5NTUyNDk4MDAyNzEzLVR1dG9yaWFscy1DQUFDLUFJLUNoYXRiYXNlLUludGVncmF0aW9uBjsIVDoJcmFua2kJ--48a01a4b7eb071acd1eb8ff29f73f9162c1ac4c9)
* [Why can't I login to MAAC? Why does the MAAC function page not display properly?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJnsaTjYBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnT4u8aLToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ0L2hjL2VuLXVzL2FydGljbGVzLzUzMjY3MDU5MTI5ODUtV2h5LWNhbi10LUktbG9naW4tdG8tTUFBQy1XaHktZG9lcy10aGUtTUFBQy1mdW5jdGlvbi1wYWdlLW5vdC1kaXNwbGF5LXByb3Blcmx5BjsIVDoJcmFua2kK--7edc6534a5d2d20cf7480f1a5bd0a629d97da17e)
