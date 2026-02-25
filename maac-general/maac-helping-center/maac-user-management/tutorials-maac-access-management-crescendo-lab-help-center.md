# Tutorials｜MAAC Access Management – Crescendo Lab Help Center

### MAAC Access Management Feature Overview

MAAC Access Management is designed to meet the high-security standards of enterprise customers, ensuring data protection and user permission control while improving system efficiency. Using Role-Based Access Control (RBAC) limits data access and operational privileges based on user roles. This effectively safeguards sensitive information and enhances accountability through transparent activity tracking.

### Applicable Plans

MAAC - Corporate Plan

### Feature highlights

* Role Assignment and Permission Control
  * Define roles such as Admin and Marketer.
  * Supports data masking/unmasking of contact information to prevent data leaks.
* Sensitive Data Masking and Export Restrictions
  * Restrict data visibility during exports based on user roles (e.g., masking/unmasking phone numbers, email addresses, and Customer IDs).
  * Download notifications: Users receive notifications when exporting reports containing masked/unmasked data.

### MAAC Access Management Permission Matrix

| Feature/Permission      |                  Admin |                       Marketer |
| ----------------------- | ---------------------: | -----------------------------: |
| **User Management**     |                        |                                |
| - View invite status    |                      ✅ |                              ✅ |
| - Assign Admin/Marketer |                      ✅ |                              ❌ |
| **Contact Data Access** |                        |                                |
| - Export contact data   | ✅ Export unmasked data |      ✅ Export masked data only |
| - View contact details  |   ✅ View complete data | ❌ Sensitive information masked |

＊Sensitive includes: Phone、E-mail、Customer ID

### Role Descriptions

{% stepper %}
{% step %}
### Admin (System Administrator)

* Full control over managing users and roles.
* Complete access to contact data, including unmasked information.
{% endstep %}

{% step %}
### Marketer (Marketing Personnel)

* Can execute marketing campaigns and send messages but cannot access sensitive data (e.g., contact phone numbers and email addresses).
* Can only export data with sensitive information masked, reducing data breach risks.
{% endstep %}
{% endstepper %}

***

### How to Use MAAC Access Management

{% stepper %}
{% step %}
### View and Manage Permissions

Steps:

1. Log in to MAAC > Permission management to view all user roles and permissions.

Images: ![](../../../.gitbook/assets/45183157952153)

![](../../../.gitbook/assets/45183157955481)
{% endstep %}

{% step %}
### Set Roles and Permissions (Admin Only)

{% hint style="warning" %}
User permissions currently support only "data masking settings". More options will be available in future versions.
{% endhint %}

Steps:

1. Go to MAAC Permission management > Data masking setting\
   ![](/broken/files/b3f525dcb9167a869840e02153351dd616cde7aa)
2. Click the pencil icon next to the user’s name.\
   ![](../../../.gitbook/assets/46991438231321)
3. Assign different roles with relevant permissions, such as:
   * Admin: Full permissions, including data export and user management.
   * Marketer: Can send messages but cannot access sensitive data.\
     ![](../../../.gitbook/assets/45183079128217)
4. Click **Update** to save the role assignment.

Note: Users cannot change their roles or permissions.
{% endstep %}

{% step %}
### Mask Sensitive Data When Exporting Contact Information

Steps:

1. Go to the Contact List and select the export option.
2. Based on user roles, data will be shown as masked/unmasked during export.
3. Notification Alert: Users will be notified whether the exported data includes masked or unmasked information.

Views:

* Admin View: Full contact data without masking.\
  ![](../../../.gitbook/assets/45269014093977) ![](../../../.gitbook/assets/45182296471577)
* Marketer View: Sensitive information is masked.\
  ![](../../../.gitbook/assets/45269014099097) ![](../../../.gitbook/assets/45182301467289)
{% endstep %}
{% endstepper %}

***

### FAQ & Common Questions

<details>

<summary>What is the default user permission after enabling the feature?</summary>

* The default user permission is set to **Admin**.

</details>

<details>

<summary>What happens if Access Management is disabled?</summary>

* If disabled, all users will regain full data access, including unmasked data during downloads, and notifications will no longer alert about masked/unmasked data.

</details>

<details>

<summary>Why can't I see the data?</summary>

* Please check your Access Role's permission.

</details>

***

### Related articles

* [How to add Tester and send test message](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkSiYkDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJlLA4mgKDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJNL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMzg4NzQ2NDktSG93LXRvLWFkZC1UZXN0ZXItYW5kLXNlbmQtdGVzdC1tZXNzYWdlBjsIVDoJcmFua2kG--9284f603b6a1479fa2a66e780415080f68b7b255)
* [Tutorials｜CAAC Users](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJnaVfz6BjoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJlLA4mgKDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI6L2hjL2VuLXVzL2FydGljbGVzLzc2NzUwNDUwNzU2MDktVHV0b3JpYWxzLUNBQUMtVXNlcnMGOwhUOglyYW5raQc%3D--5cd238f1cb7310c50987c0e8ccf599a57d9beec9)
* [Tutorials｜ MAAC x SurveyCake Form](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkr5rYDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJlLA4mgKDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJGL2hjL2VuLXVzL2FydGljbGVzLzQ0MTM5OTk5NTA3NDUtVHV0b3JpYWxzLU1BQUMteC1TdXJ2ZXlDYWtlLUZvcm0GOwhUOglyYW5raQg%3D--f6c1d54a636409700d06e221f24d8105b748291d)
* [Tutorial | Backend Interface, Account Settings, and Permission Management](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkuF4kDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJlLA4mgKDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJrL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMzE0MTA4NDEtVHV0b3JpYWwtQmFja2VuZC1JbnRlcmZhY2UtQWNjb3VudC1TZXR0aW5ncy1hbmQtUGVybWlzc2lvbi1NYW5hZ2VtZW50BjsIVDoJcmFua2kJ--c71cdc4e7af8151f53132e3300d4ca377d7ffb48)
* [How to share LINE OA platform, LINE Developers, GA(UA) / GA4 access to Crescendo Lab?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmp1FFgBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJlLA4mgKDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ1L2hjL2VuLXVzL2FydGljbGVzLzgxMTAyNzExNDYzOTMtSG93LXRvLXNoYXJlLUxJTkUtT0EtcGxhdGZvcm0tTElORS1EZXZlbG9wZXJzLUdBLVVBLUdBNC1hY2Nlc3MtdG8tQ3Jlc2NlbmRvLUxhYgY7CFQ6CXJhbmtpCg%3D%3D--270cb96c8b909907cd69b3036de08bd2167f8eb1)
