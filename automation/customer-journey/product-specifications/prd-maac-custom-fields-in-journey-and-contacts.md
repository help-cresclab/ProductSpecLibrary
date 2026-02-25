# PRD   MAAC   Custom fields in Journey & Contacts

## PRD - Omnichannel Customer Journey

#### MAAC

Custom fields in Journey & Contacts PRD

Empower Always-on Customer Engagements by using CRM data in MAAC journeys through Custom Fields for personalized communication.

| **PM owner** [Jean Liu](mailto:jean.liu@cresclab.com) **Eng owner** [Jack Lee](mailto:jack.lee@cresclab.com) **PD owner** [Patty Hsu](mailto:patty.hsu@cresclab.com) | **💬Slack channel** [#proj-journey](https://chatbotgang.slack.com/archives/C08JZHN576Z) **⏱️Asana\*\*\*\*📂Notion** [link](https://www.notion.so/cresclab/f1cd141a7c854af49f7d27ceaf662393?v=712b788506bb4b1ca6fbfe09a087ade4\&p=20a8ce158938808c8b7ad432781a2a98\&pm=s) **🎨Figma** [Contacts](https://www.figma.com/design/4izQy6bC4QxfvTOxuFotIl/MAAC_Contacts?node-id=2093-49567\&t=OxYFTHzoDhB9SphN-1) \| [Journey](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=9043-1915\&p=f\&t=TK5BWFhtRSzoTVMo-0) |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

### Version history

| Version | Date       | Description | Editor                                   |
| ------- | ---------- | ----------- | ---------------------------------------- |
| Ver. 1  | 2026-01-15 | PRD draft   | [Jean Liu](mailto:jean.liu@cresclab.com) |

### 🆕 AI Collaboration log

| Date  | Summary                                                           | Status     | AI Prompt (recommend)                                                                                                                                                |
| ----- | ----------------------------------------------------------------- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| @Date | User stories & test case generation                               | Unresolved | [LINK - Generate test cases](https://www.notion.so/cresclab/AI-Coding-Task-Force-1f38ce158938809ba1faea6796b8a1d3?source=copy_link#2398ce1589388013a3defc4253fd3dfd) |
| @Date | Test case updated based on MM/DD discussion (link to the section) | Unresolved | [LINK - PRD Update](https://www.notion.so/cresclab/AI-Coding-Task-Force-1f38ce158938809ba1faea6796b8a1d3?source=copy_link#2238ce158938802b835dff0ecf599e3f)          |

### Release notes

**Custom Fields empower brands to flexibly apply CRM data to trigger and branch Customer Journeys**, enabling always-on personalized communication to drive higher customer engagement and conversion.

* **Journey Trigger:** Automate journeys based on anniversaries (e.g., membership renewal) or real-time CRM data updates.
* **Journey Branch:** Split journey paths using date-based or numeric logic (e.g., points or tiers).
* **Journey Action:** Update, increment, or clear Contact Attributes (custom fields’s value) directly within the journey flow.
* **Dynamic Messaging (P1):** Inject custom field variables into all message types for personalized content.
* **Unified Data Sync:** Manage customer attributes (custom fields’s value) at scale via API, CSV import/export, or manual profile edits.

### Goal

**Business Goal**

* **Increase Journey Adoption:** Integrate CRM data into Journeys to enable always-on business communication scenario (eg. Member level upgrade, anniversary message).
* **Prevent Churn**: Close the feature gap with key competitors by providing structured data capabilities and application.
* **System of Record (SoR) Foundation:** Establish Custom Fields as the core data infrastructure across MAAC, DAAC, and CAAC, positioning CL as the primary source of truth for customer engagement data.

**User Goal**

* **Personalized Communication:** Leverage custom fields to execute highly personalized marketing scenarios (e.g., birthday rewards, loyalty milestones), driving conversions and increasing LTV.
* **Operational Efficiency:** Enable always-on automation by eliminating the manual overhead of converting CRM data into static tags, repetitive CSV imports, and constant data maintenance, thereby reducing labor time and human error.

### Background

Refer to [PRD - Custom Field Integration](https://docs.google.com/document/d/1C0Rns5GQkZ8ufGLM6KCCkF8Js9pnOkfzUJpaCQfnjzg/edit?tab=t.0#heading=h.7zhh3y7w1f1r)

### Strategy

Refer to [PRD - Custom Field Integration](https://docs.google.com/document/d/1C0Rns5GQkZ8ufGLM6KCCkF8Js9pnOkfzUJpaCQfnjzg/edit?tab=t.0#heading=h.pb6wlpk3rom7)

#### Roadmap

**MAAC Scope**

2026 Q1

* Custom fields in Contacts (import/export)
* Custom fields in Customer Journey
* Custom fields in Editors (Dynamic content) _P1 – may move to Q2 if resource constraint_

2026 Q2

* Custom fields in Segments

### TA & Problem-to-solve

| TA                                | Problem to solve                                                                                                                                                                                                                                                                                                                                                                                                                |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Marketer                          | - **Inefficient "Tag-as-Data" workarounds:** Relying on static tags to reflect CRM updates requires heavy manual CSV management, causing significant delays and high operational overhead. - **Limited Personalization & Management Clutter:** Tags lack structured data types (e.g., dates/numbers), leading to impersonal messaging and "tag explosions" that are difficult to clean and restrict advanced journey scenarios. |
| Support / Sales Agent (CAAC user) | - **Disconnected automation:** Customer insights gathered (attribute updates) during 1-on-1 interactions cannot automatically trigger follow-up journeys.                                                                                                                                                                                                                                                                       |

### Solutions

Please stay high-level at this point. Detailed solution should go to feature spec

| **Problems**                                 | **Existing Solutions**\***could be existing flow or feature**                                                                             | **Proposed Solutions**\***If there are multiple options, tell us your recommendations.**      |
| -------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Inefficient "Tag-as-Data" workarounds        | Marketers manually upload CSVs to create date-specific tags (e.g., renewal\_reminder) to trigger journeys.                                | \*\*-\*\*API Sync custom fields value - Anniversary triggers                                  |
| Limited Personalization & Management Clutter | Messy tags are created for different business scenarios, which are difficult to manage and offer no dynamic variable support in messages. | - Structured custom field type & operators - Dynamic content with custom fields variable (P1) |
| Disconnected automation from CAAC to MAAC    | Agents manually add tags to customers to trigger journeys, which need alignment on tag naming and journey setup.                          | - Attribute-driven (custom fields) Triggers                                                   |

### Selling points & Combine features

| TA                              | Selling points                                                                                                                                                                                                                                                    | Combine features |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| Marketer                        | _**Turn CRM data into high-precision, 'always-on' journeys that boost CVR and LTV**_\_ —\__Unlock the full potential of your data by automating personalized engagement across the entire customer lifecycle, ensuring every milestone drives measurable growth._ | –                |
| Sales/Support Agent (CAAC user) | _**Instantly trigger personalized automated care from real-time frontline updates —**_\_ Seamlessly bridge the gap between frontline customer updates and marketing action to ensure customers receive the right care at the perfect moment.\_                    | –                |

### User story

{% stepper %}
{% step %}
### Lifecycle & Loyalty Marketing (Always-on Journey)

#### Birthday & Anniversary Celebrations

As a Marketer in the Education or Retail industry, I want to trigger a journey based on a Child's DOB or a Wedding Anniversary, so that I can automatically send age-appropriate program offers or personalized gift vouchers every year without manual intervention.
{% endstep %}

{% step %}
### Membership Tier Upgrades

As a Beauty/Retail Marketer, I want to trigger a "Welcome to VIP" journey the moment a customer's Membership Tier transitions from "General" to "Gold", ensuring high-value customers receive immediate recognition and reward details.
{% endstep %}

{% step %}
### Contract Expiry & Renewal Reminders

As an Automotive or Financial Services Marketer, I want to split a journey branch based on the Contract Expiry Date (e.g., 30 days before expiry), so that I can send renewal reminders and proactively prevent churn.
{% endstep %}

{% step %}
### Point Balance Low-Balance Alerts

As an eCommerce Marketer, I want to use the Points Balance to filter customers in a journey, sending "Points Reminder" notifications only to those with a balance greater than 500.
{% endstep %}
{% endstepper %}

{% stepper %}
{% step %}
### Personalized Customer Experience — Dynamic Content in Promotion Messages

As a Marketer, I want to insert the customer's Preferred Branch or Last Purchase Category into a LINE message using variable tokens, so that the message feels highly relevant (e.g., "Hi {Name}, your favorite {Category} is on sale at the {Branch}!").
{% endstep %}

{% step %}
### Cross-Product Contact Data Consistency

As a Support Agent or Marketer, I want to see the External CRM ID or Contract ID clearly in the Contact Profile, so that I can provide consistent support regardless of whether the customer reached out via LINE or other channels.
{% endstep %}
{% endstepper %}

{% stepper %}
{% step %}
### Efficient Data Feeding (CSV & Import) — Bulk Membership Data Sync

As a CRM Specialist without API resources, I want to download a CSV template that already includes my custom Lead Stage and Member Score columns, allowing me to bulk-update customer statuses from my offline Excel file to trigger MAAC journeys.
{% endstep %}
{% endstepper %}

_————— Feature-level user stories —————_

**Customer Journey - Triggers & Conditions**

* **Custom fields as Journey Triggers**

As a MAAC user, I want to trigger a journey based on custom field values, including:

* Value Change: Any update to a specific field.
* Specific Value Occur: When a field changes to a specific value (e.g., Membership Tier changes to "L2").
* **Custom fields as Branch Node / Condition Filter**

As a MAAC user, I want to split customer paths in a journey using specialized operators based on field types (text, number, date, datetime)

* **System Field – Customer ID (P1)**

As a MAAC user, I want to use the contact default field "Customer ID" as a condition (e.g., "Has value" or "Is empty") within journey nodes, so that I can distinguish between bound and unbound members for different messaging strategies.

**Customer Journey - Action node & Personalization**

* **Action node: Custom Field Updates**

As a MAAC user, I want to automatically update or remove (set to Null) a customer's custom field value at any stage of a journey, allowing me to record customer progress or status dynamically.

* **Variable Personalization in Messages (P1)**

As a MAAC user, I want to insert custom field placeholders in the Message Editor and have the system automatically map them to the underlying cl\_custom\_ keys, ensuring customers receive personalized content (e.g., {Membership Tier}).

**Contact Profile Management**

* **View Custom Field Data**

As a MAAC user, I want to view all custom field attributes (Name, Value, Type) within the MAAC Contact Profile, so that I can have a comprehensive understanding of a customer's background during manual review or support sessions.

* **Manual Edit & Write-back**

As a MAAC user, I want to manually edit custom field values in the Contact Profile and sync them back to the CDH, so that the customer's data remains consistent across all product surfaces (MAAC <> CAAC).

**Contact CSV Import & Export**

* **CSV Data Import with Custom fields**

As a MAAC user, I want to update CSV columns to specific custom fields during the import process, ensuring that data is correctly routed to the corresponding cl\_custom\_ keys in CDH.

* **Contact Export with Custom fields**

As a MAAC user, I want the exported contact list to include all active custom field values, formatted according to the Organization's Timezone for DateTime fields.

### Scope

#### In-scope

* **Contacts**
  * Contact Profile UI
    * Custom Attributes Section: Unified view of all “Active” custom fields (collapsible)
    * Support manual updates custom fields value (last-write-wins)
  * Contact Import (CSV)
    * Dynamic Template Generation: fetch and include all “Active” custom fields as CSV headers.
    * CSV import updates for custom fields with formatting and numeric validation (ISO 8601)
  * Contact Export (CSV)
    * Include all active custom field values in the exported contact list.
* **Journey triggers**
  * Custom fields as trigger
    * Value updated (Any)
    * Value Transitioned to Specific Value (operator same as below)
      * All types of custom fields are triggered On data Update.
      * For Date type custom fields, also support On Specific Date and On Anniversary trigger mode.

(P1)

* System field “Customer ID” as trigger
* **Journey condition (branch node & filter)**
  * Custom fields type & operator (Text/Number/Date/DateTime)
  * Real-time Timezone Conversion from CDH (Source) to Org Timezone (MAAC) for all DateTime comparisons.

(P1)

* System field “Customer ID”
  * Operator: Has value
* **Journey Action Node**
  * Action node: Update Custom Attribute
    * Update custom field value: Automatically write a new value to a Text, Number, Date, or DateTime field.
    * Clear custom field value: Set a field to Null.
* **Message Editor – Variable Injection**

(P1)

* LINE, SMS, Email message editor
  * Variable Picker: UI for selecting custom fields by "Custom filed name" in the Message Editor.
  * Value Mapping: BE logic to replace variable placeholders (e.g., {Membership\_Tier}) with actual values from cl\_custom\_ keys.
  * Fallback Values: Ability to define a default value if the custom field is Null.

#### Out-of-scope

* Custom fields in segment
* Contact search by Custom fields & bulk update (Note: include in “Custom fields in segment” scope)

#### Dependency check

// Please tag the PIC (people in charge) here

* This project might affect the other teams/project (for those being affected, please review this PRD carefully)
  * Affected PIC 1: Affected areas
  * Affected PIC 2: Affected areas
* This project has a dependency on other teams/ project
  * Dependency 1:
  * Dependency 2:

### Success metric

### Glossary definition

💡 Hint: Glossary 是 AI 的字典。所有此專案的專有名詞、縮寫都應在此定義，避免 AI 誤解。。

| Product term | Code term | Definition |
| ------------ | --------- | ---------- |
|              |           |            |
|              |           |            |
|              |           |            |

Reminder: Update the [Product Dictionary](https://www.notion.so/cresclab/08666630ee444b44b349bdb60ec40c19?v=2281968133d64b11b25d206dd86780d4\&pvs=4)

### Feature list

* [A- Journey Triggers (Custom Attribute & Customer ID)](prd-maac-custom-fields-in-journey-and-contacts.md#_1otqltrcw39c)
* [B - Journey Conditions (Split nodes & Filters)](prd-maac-custom-fields-in-journey-and-contacts.md#_y6x02n1gikfm)
* [C - Journey Action (Change Attribute)](prd-maac-custom-fields-in-journey-and-contacts.md#_tjixaxmt6ta9)
* [D - Contacts (Profile Display & CSV Import/Export)](prd-maac-custom-fields-in-journey-and-contacts.md#_dr3proe03iiw)
* [E - Message Editor (Dynamic Content) (P1)](prd-maac-custom-fields-in-journey-and-contacts.md#_p4779av5fxgw)
* [F - Journey Node Performance](prd-maac-custom-fields-in-journey-and-contacts.md#_fm73hk61cfkc)

## Feature spec

_For Custom fields API & Admin Center Setup PRD, please refer to_ [PRD - Custom Field Integration](https://docs.google.com/document/d/1C0Rns5GQkZ8ufGLM6KCCkF8Js9pnOkfzUJpaCQfnjzg/edit?tab=t.dnzuxjsqwzbm#heading=h.vf19xkk7danu)

**A - Journey Triggers (Custom Fields & Customer ID)**

#### User Stories & AC

* **A-1 Custom Field Update Trigger**

As a Marketer, I want the journey to trigger when a custom field is updated or matches a specific criteria, so that I can automate complex lifecycle scenarios (e.g., Membership Tier, Contract Status)

**AC：**

1. The system must detect real-time updates to any **Active** custom field (prefixed with cl\_custom\_).
   * Custom filed types includes text, number, date, date time
2. The trigger must respond to updates from the [Custom Field API](https://doc.user360.cresclab.com/cdh.html#tag/Member/operation/update_member_cdh_v1_member_patch), CSV Import, and manual UI edits.
3. Advanced filter must support to filter contacts entry. (specified in B - Journey Conditions )
4. Trigger Modes & Sub-types:
   * For All Types: Support Any Value Update and Matches Specific Criteria.
     * If trigger mode is "Matches Specific Criteria", the system must dynamically display operators based on the custom field type (see Operator Matrix in Business Logic section).
   * For Date type fields only:
     * On Update: Real-time evaluation when the date value is changed.
     * On Specific Date: Daily evaluation based on date logic. Requires a Trigger Time (HH:MM).
     * On Anniversary: Daily evaluation for recurring dates. Year (YYYY) is ignored by default. Requires a Trigger Time (HH:MM).
   * For Date type field (excluding Anniversary sub-type), provide a checkbox: \[ ] Only check MM/DD (Ignore Year).
   * For DateTime type field, the system must convert the CDH source data (UTC) to the Org Timezone before evaluation and display in MAAC UI.

* **A-2 Customer ID Activation Trigger (P1)**

As a Marketer, I want the journey to trigger when a “Customer ID” is assigned to a contact, so that I can initiate welcome or binding-success workflows.

**AC：**

1. The system only triggers when the customer\_id field transitions from **Empty/Null to "Has Value"**.
2. This trigger does **not** support "Any Value Update" or specific condition matching beyond "Has Value".
3. Advanced filter must support to filter contacts entry. (specified in B - Journey Condition)

#### User Flow

**\[Customer Journey Canva > Trigger Node Configuration]**

A new trigger type “Contact Information” include **Custom Fields** and **Customer ID** selection.

{% stepper %}
{% step %}
### Flow: Trigger by "Any Value Update"

1. User navigates to the "Attribute Change" category and selects the "Contact Information" trigger node.
2. User selects an "Active" custom field (e.g., Region (text type)). → Select "Any Value Update".
3. The journey triggers whenever the Region field is updated, regardless of the value.
{% endstep %}

{% step %}
### Flow: Trigger by "Matches Specific Criteria" (On Update – Text/Number/DateTime/Date)

1. User navigates to the "Attribute Change" category and selects the "Contact Information" trigger node.
2. User selects an "Active" custom field (e.g., Point\_balance (number type)). → Select "Matches Specific Criteria".
3. UI displays number type operators → user selects operator \[ Greater than ] and inputs value \[1000 ].
4. Advanced Filter (Optional): Add conditions such as Tag = VIP using AND/OR logic.
{% endstep %}

{% step %}
### Flow: On Specific Date Path (Date Type)

1. User selects an "Active" custom field (Date type).
2. Select "Matches Specific Criteria" → Sub-trigger type "On Specific Date".
3. User selects operator (e.g., Is On, Is Before) and target date (e.g., {Today}, Relative date).
4. User sets Trigger Time (e.g., 09:00 AM).
5. System Execution: Every day at the set time, the system scans and triggers for contacts matching the criteria.
{% endstep %}

{% step %}
### Flow: Anniversary Path (Date Type)

1. User selects an "Active" custom field (e.g., Birthday).
2. Select "Matches Specific Criteria" → Sub-trigger type "On Anniversary".
3. The system ignores Year by default; user selects operator (e.g., Is On) and sets Trigger Time (e.g., 10:00 AM).
4. Every day at the set time, the system triggers the journey for contacts whose Birthday matches the current MM-DD.
{% endstep %}

{% step %}
### Flow: Customer ID Activation

1. User navigates to the "Attribute Change" category and selects the "Contact Information" trigger node.
2. User selects "Customer ID" with fixed condition "Has value".
{% endstep %}
{% endstepper %}

#### Business Logic

* Trigger Operator Matrix by Field Type

| Field Type | Operators                                                                                                                                       | Notes                                                                                                                                                                                                     |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Text       | Is, Is Not, Contains, Not Contains, Has value, Starts with, Ends with. Optional add-on: \[ ] Case-sensitive                                     | Default is case-insensitive matching.                                                                                                                                                                     |
| Number     | Equals, Not Equals, Greater than, Less than, Has value, Greater than or equal to (≥), Less than or equal to (≤), Between (Range)                |                                                                                                                                                                                                           |
| Date       | Is On, Is Before, Is After, Within the last {n} days/weeks, Within the next {n} days/weeks, Is Between (MM/DD \~ MM/DD), In Month, Has value    | 1. Anniversary Sub-type: Always ignores YYYY. 2. Other Sub-types/Filters: Include checkbox: \[ ] Only check MM/DD (Ignore Year). 3. Trigger time (required) for Specific Date/Anniversary modes: {HH:MM}. |
| DateTime   | Is On, Is Before, Is After, Within the last {n} minutes/hours/days, Within the next {n} minutes/hours/days, Between (hh:mm \~ hh:mm), Has value | - Normalized to Org Timezone. - Between: Default ignores date and only compares time (HH:MM). - Evaluated upon data update.                                                                               |

* Trigger System Rules
  1. Anniversary Logic: The comparison only matches Month and Day.
  2. Scan Timing: Anniversary triggers are processed via a daily batch scan at the user-defined Trigger Time based on the Organization's Timezone.
  3. Null Handling: If a trigger depends on a value and that value is updated to Null/Empty, it counts as a change but will not meet "Specific Criteria" logic.
  4. Definition of "Has Value": The system defines "Has Value" as a transition where a field changes from Null/Empty (empty string "" for text or null for all types) to a Non-null/Non-empty value.
  5. DateTime Evaluation Granularity: For all DateTime comparisons, the system must truncate seconds and milliseconds from both the stored value in CDH and the condition value defined in the journey. All evaluations are performed at the minute level (YYYY-MM-DD HH:MM).
     * Example: 2025-06-15T10:30:45+08:00 is treated as 10:30.
       * Logic Check: If condition is set to > 10:30, then 10:30:45 > 10:30:00 evaluates to False.
       * Logic Check: If condition is set to is at (exact time) 10:30, then 10:30:45 = 10:30:00 evaluates to True.
* Scope of Fields: Includes all “Active” custom fields and the system customer\_id field.
* Archived Custom Field impact for journey status:
  1. Draft: If a trigger uses an archived field, an error message must be displayed in the configuration panel. The journey cannot be published until the field is replaced.
  2. Published: If an active journey contains a field that becomes archived, an error alert must be displayed on the journey list and trigger node.
  3. Paused: An error message must be displayed. The journey cannot be published until the field is replaced.
  4. Ended: For journeys in the “Ended" state, the custom field name remains displayed normally for historical reference, even if the field has been archived.
* Custom Field Renaming Logic:
  1. When a Field Name is modified in the Admin Center, the updated name must be reflected across all MAAC UI surfaces (Journey Canvas, Setting Panels, and Contact Profile) in real-time.
  2. Since the backend uses the immutable Field Key for processing, renaming does not affect active journey logic.
* Latency: The journey must be triggered within 10 seconds of the data being successfully recorded in the CDH.
* Conflict Resolution: Triggering is based on the final state saved in the CDH under the Last-write-wins server timestamp.
* Unified Operator Engine: To ensure consistency, the filtering logic used in the Trigger Node must share the same backend engine and rules as the B - Journey Condition.

#### Note for discussion

* 一樣的值更新，需要被過濾「value change trigger」--> 需討論誰要做 filter (MAAC or DAAC)
* MAAC 是否需要存一份
* ✅需要釐清 空值 (or 零值) 的定義是什麼：” ” or null ?
  * 結論：針對「Has Value」判定，空值包含 null 與空字串 ""。任何從此狀態轉變為具備實際內容（非空值）的情況皆判定為「Has Value」 (已補在 business logic > trigger system rules > iv.)
* DateTime 的延遲要有「可能延遲 N 分鐘」的提醒，評估可以支援到什麼程度 (分鐘/小時?)；評估 batch 支援怎麼做；補 use case

**B - Journey Conditions (Split nodes & Filters)**

#### User Stories & AC

* **B-1 Attribute Branching (Yes/No Branch)**

As a Marketer, I want to split the journey path based on a contact's latest attribute values, so that I can deliver personalized content.

**AC：**

1. Evaluation happens the moment the contact arrives at the node.
2. Use the same operator matrix and UI as the Trigger Filter. (Date & DateTime operator flow please see [figma](https://www.figma.com/board/0yqBJ2AADUevXqzvebq0W0/Jean-s-Playground?node-id=2006-3755\&t=YCaYrC0eZ6gmpTfW-4))
3. If the contact attribute (custom field or customer ID) is Null, the contact follows the "No" path.

* **B-2 Trigger Node Filter**

As a Marketer, I want to filter contacts based on their attribute (custom field & customer ID) entering a journey (e.g., Tag Trigger), so that I only include specific segments.

**AC：**

1. Custom fields are included in the "Filter" toggle in all trigger nodes.
2. Uses the shared Advanced Filter modal as Yes/No branch node.

#### User Flow

**\[Customer Journey Canva > Yes/No branch node (Event Condition)]**

{% stepper %}
{% step %}
### Flow #1 Check Condition Node

1. User clicks the **Yes/No Branch** node.
2. Click "Select a condition" dropdown → Scroll to **Custom fields** section.
3. Select custom field(s) (e.g. Points) → Select type-specific operator (e.g. Greater than) → Input numeric value (e.g. 100).
   * For Date type: the user can check \[ ] Only check MM/DD (Ignore Year) to filter by month/day regardless of the year.
   * For DateTime type: Select Between and input a time range (e.g., 14:00 \~ 16:00) to filter contacts arriving at the node during those specific hours daily. System will ignore date.
4. (Optional) Click **"+ Add a condition"** to add another rule (e.g., Tag = VIP) using AND/OR logic.
5. Click "Save".
{% endstep %}

{% step %}
### Flow #2 Trigger Filter

1. User clicks "Tag Added" Trigger → Switches "Filter" to ON.
2. Adds condition → Select \[ Membership\_Tier ] under customer attribute → set the operator to \[ Is ] \[ Gold ].
{% endstep %}
{% endstepper %}

#### Business Logic

* Condition Operator Matrix by Field Type (same as Trigger Operator Matrix; Date & DateTime operator flows in figma)
* Filter UI is shared in Trigger node filter toggle & Event Condition (Y/N) node.

#### Note for discussion

* (Open points left for team discussion)

**C - Journey Action (Change Attribute)**

#### User Stories & AC

* **C-1 Modify Custom Field Values**

As a Marketer, I want to update or remove values of custom fields during a journey, so that I can maintain up-to-date contact profiles based on their interactions.

**AC：**

1. A new action node "Change Attribute" shall be added to the action category (alongside "Add/Remove Tag").
2. Users can select any "Active" custom field from a dropdown list (consistent with Check Condition).
3. Update Operators:
   * All Types: Support Set to (Value) and Clear value (Set to Null).
   * Number Type: Also support Increase by and Decrease by for relative adjustments.
4. Data Validation: The UI must validate that the input value matches the field's data type (Text, Number, Date, DateTime) before allowing the user to save the node.

* **C-2 Dynamic Date Assignment (P1)**

As a Marketer, I want to set a date attribute to the current system time, so that I can track the exact moment a specific milestone was reached.

**AC：**

1. Dynamic Variables:
   * When a Date field is selected, the UI should provide options to Set to {Current\_Date}.
   * When a DateTime field is selected, the UI should provide options to Set to {Current\_DateTime}.
2. These dynamic values must be based on the Org's Timezone setting.

#### User Flow

**\[Customer Journey Canva > Action Node]**

{% stepper %}
{% step %}
### Flow #1 Setting a Fixed Value (All types)

1. User adds the "Change Attribute" node.
2. Choose \[ Membership\_Tier ] (Text) → Select operator \[ Set to ] → Input value \[ VIP ].
3. When a contact reaches this node, their membership tier field will be updated to VIP.
{% endstep %}

{% step %}
### Flow #2 Math Operations (Number Only)

1. "Change Attribute" → Choose \[ Point Balance ] (Number).
2. Select operator \[ Increase by ] → Input numeric value \[ 100 ].
3. When a contact reaches this node, their existing points are incremented by 100.
{% endstep %}

{% step %}
### Flow #3 Clearing a Value (Set to Null)

1. "Change Attribute" → Choose \[ Coupon Valid ].
2. Select the "Clear value" option.
3. When a contact reaches this node, their coupon valid field will be set to null.
{% endstep %}

{% step %}
### Flow #4 Dynamic Date/DateTime Update (P1)

1. "Change Attribute" → Choose \[ Last\_Interaction\_Date ].
2. Select operator \[ Set to ] → Choose from dropdown: \[ {Current\_Date} ].
3. When a contact reaches this node, their last interaction date will be updated to the date of the action taken.
{% endstep %}
{% endstepper %}

#### Business Logic

* Update Matrix by Field Type

| Field Type | Supported Operators                                               | UI Component                                      |
| ---------- | ----------------------------------------------------------------- | ------------------------------------------------- |
| Text       | Set to {fixed value}, Clear Value                                 | Text Input / Clear option                         |
| Number     | Set to {fixed value}, Clear Value, Increase by, Decrease by       | Numeric Input / Clear option                      |
| Date       | Set to {fixed value}, Clear Value (P1) Set to {current\_date}     | Date Picker (YYYY-MM-DD) / Clear option           |
| DateTime   | Set to {fixed value}, Clear Value (P1) Set to {current\_datetime} | DateTime Picker (YYYY-MM-DD hh:mm) / Clear option |

* Last-write-wins: In the event of concurrent journey executions or API updates, the most recent write operation to the CDH will prevail.
* Conflict Resolution:
  * If a math operation (Increase/Decrease by) is attempted on a Null value, the system should treat the original value as 0 and then apply the adjustment.
  * For the Decrease by operator on Number fields, if the result is less than 0, the final stored value must be 0. No negative values are allowed for this operation.
* Traceability: Every attribute change triggered by a journey should be logged in the contact's activity history, identifying the Journey ID and Node ID as the source of the change.
* Validation: UI must block saving if a user attempts to input text into a Numeric field or an invalid date format.
* Timezone: All {Current\_DateTime} assignments are normalized to the Org’s Timezone.

#### Note for discussion

* Number increase/decrease: Coordinate with Leo; may be implemented in CDH; risk considerations noted.
* Confirm UI input validation for data formats.

**D - Contacts (Profile Display & CSV Import/Export)**

#### User Stories & AC

* **D-1 Contact Profile Custom Fields Display & Edit**

As a Marketer, I want to view and manually update a contact's custom fields in their profile so that I can manage individual records without a full CSV re-import.

**AC：**

1. A new, collapsible card titled "Custom Fields" must be added to the Contact Profile page.
2. Custom Attributes within this section follow the display order defined in the Admin Center.
3. All attributes will be displayed as editable Input Boxes.
4. The system must validate the input format (Number, Date, DateTime) upon update. If invalid, the update is blocked with an error message.

* **D-2 CSV Bulk Import with Header-based Mapping**

As a Marketer, I want to bulk update custom attributes by adding specific headers to a CSV file so that I can efficiently sync data from other systems.

**AC：**

1. The system must recognize headers starting with cl\_custom\_ followed by the exact Key name (e.g., cl\_custom\_points).
2. If the contact exists, the system overwrites values. Blank cells = No change; "null" string = Clear value.
3. Rows with incorrect data formats (e.g., text in a Number field) must fail and be summarized in the notification inbox with import result + failure report CSV (download link).

* **D-3 Contact CSV Export**

As a Marketer, I want to export contact’s custom attributes along with standard contact data so that I can analyze data offline or perform bulk edits for re-importing.

**AC：**

1. When exporting contacts, all Active custom attributes must be included as separate columns.
2. Exported headers for custom attributes must follow the cl\_custom\_{key} format.
3. Date and DateTime values must be exported in YYYY-MM-DD and YYYY-MM-DD HH:MM formats to ensure they are ready for immediate re-import.

#### User Flows

**\[Contacts > Contact Profile]**

{% stepper %}
{% step %}
### Flow #1 Manual Profile Update

1. User opens a Contact Profile → Expands "Custom Attributes".
2. User types 2024-05-20 into a date field and clicks "Update".
3. Backend validates the format. If correct, data is saved; if not, the field highlights in red.
{% endstep %}

{% step %}
### Flow #2 Contact Export & Import

1. Contact Export:
   * User exports the current contact list.
   * User opens the exported CSV and finds custom fields columns (eg. cl\_custom\_membership\_score) → update the values.
2. Contact Import:
   * User downloads the import CSV template.
   * User copies custom fields from exported CSV, and pastes them into the “Custom Field (Key Name)” column, replacing the header with the correct custom\_field\_key.
   * User uploads the CSV to MAAC to update custom fields value.
{% endstep %}
{% endstepper %}

#### Business Logic

* Data Validation & Export/Import Rules

| Field Type | Export Format    | Import Requirement      | Failure Behavior (Import)    |
| ---------- | ---------------- | ----------------------- | ---------------------------- |
| Text       | Plain text       | Max 255 chars           | Row fails if > 255 chars     |
| Number     | Numeric          | Digits only             | Row fails if text detected   |
| Date       | YYYY-MM-DD       | Strict YYYY-MM-DD       | Row fails if format mismatch |
| DateTime   | YYYY-MM-DD hh:mm | Strict YYYY-MM-DD HH:MM | Row fails if format mismatch |

* Header Case-Sensitivity: Exported headers will always be Lowercase to match the system keys and minimize re-import errors.
* Empty Values: Fields with no data (Null) will be exported as empty cells ("").
* CSV template 待補: Import | Export

#### Note for discussion

* Whether to let user select which custom\_field\_key columns to export (conclusion: design to allow selecting custom fields).
* Import template could include a step to let user choose which custom\_field\_key columns to include.

**E - Message Editor (Dynamic Content) (P1)**

#### User Stories & AC

* **E-1 Universal Placeholder Insertion**

As a Marketer, I want to insert any custom attribute into my message content using a variable picker so that I can deliver personalized messages across all supported channels (SMS, EDM, LINE, WA, etc.).

**AC：**

1. Users can access the variable list by clicking the "Dynamic content Icon" in the message editor.
2. The variable picker must include a Search Bar to find specific attributes.
3. The picker list must display the active “Custom Filed Name (cl\_cutom\_{key})”. Once selected, the editor insert the Key placeholder in the editor. (e.g., {cl\_custom\_order\_id}).
4. Omni-channel Support: This mechanism must be integrated into SMS, EDM, LINE, WA, Messenger, and IG editors.

* **E-2 Dynamic Resolution & Fallback Logic**

As a Marketer, I want to define a default value (fallback) when a contact’s attribute is empty so that the message remains coherent for all recipients.

**AC：**

1. The editor must support for custom fallback value if no value for the selected custom field.
2. Resolution Priority:
   1. If the attribute has data: Display the actual value.
   2. If the attribute is Null/Empty: Display the Fallback\_Value.
   3. If no fallback is defined (e.g., {cl\_custom\_key}): Display an empty string ("").
3. Character Warning: each editor must display a warning that dynamic variables will result in variable message lengths and potentially higher costs. (especially for SMS and WA)

#### User Flow

**\[Message Editors (All modules)]**

{% stepper %}
{% step %}
### Flow #1 Inserting a Variable with Fallback

1. In the message editor, the user clicks the "Dynamic content" Icon → a variable picker is added to the input box.
2. User clicks the variable picker → searches for "Nickname" and selects it → Editor inserts {cl\_custom\_nickname}.
3. User inputs the fallback value “Member”.
4. Message resolution:
   * Contact with nickname "Alex" receives: "Hello Alex!"
   * Contact with no nickname receives: "Hello Member!"
{% endstep %}
{% endstepper %}

#### Business Logic

* Character counter: Since custom fields vary in length, the character counter should show a "Dynamic Length" alert. (Especially for SMS & WA editor)

#### Note for discussion

* (Open points left for team discussion)

**F - Journey Node Performance**

#### User Stories & AC

**F -1 Node Performance Metrics (Trigger & Action Nodes)**

As a Marketer, I want to see performance metrics directly on each journey node, so that I can monitor the traffic and unique contacts progress status of my automation flow.

**AC：**

1. Performance data cards must be displayed on all "Trigger Nodes”, “Branch Nodes” and "Action Nodes".
2. Display Fields:
   * Traffic counts: the cumulative total number of times the node has been passed through.
   * Unique contacts: the number of unique contacts that have passed through the node.
3. Performance data is only visible on canvas (both report & edit/view page) when the journey has been published.

### Customizables

Please confirm whether a custom setting is needed

### User Stories & Test Cases (Generated by AI)

(See original for detailed test cases; the PRD includes full test matrix and status markers)

### Release plan

#### Pricing plan

#### Release region

Please check the gray out feature list ([Link)](https://www.notion.so/cresclab/Product-Availability-e9e275930be946c2b471077b02f7556e)

Please add a new backlog item, then involve PD, UX Writer, and Product Ops for in-product copy reviewing and Help Center article writing when releasing in a new market.

| - TW | - TH | - JP |
| ---- | ---- | ---- |

Release notes

| - TW | - TH | - JP | - EN |   |
| ---- | ---- | ---- | ---- | - |

#### GTM plan

**How do users adopt**

* self-serve
* set up by enable & ops \[insert steps and tools (eg Django)]

**How do users troubleshoot**

* self-serve
* raise to CS/enable & ops \[insert steps and the info provided to troubleshoot (eg metabase)

### Development Documents

#### Design docs

* Design
* Prototype

#### Technical docs

* BE design doc

#### QA docs

* Test case ([template](https://docs.google.com/spreadsheets/d/1KzYJptLPgo5k_xuNa06V8oqTjQghUI2KNFKEAK-gKhQ/edit?gid=502134957#gid=502134957))

### Open Discussion

\[Format example]

**YYYY-MM-DD | {Meeting Topic}**

* Attendees:
* Discussion:
* Decision:
* Action item:
* {Who}: {What}

***

### Internal Update - {Feature Name}

Product internal update:

Custom fields in Customer Journey & Contact Profile

One-liner feature description

| **PM Owner**            | [Jean Liu](mailto:jean.liu@cresclab.com)                                                                                                                                     |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Product**             | MAAC                                                                                                                                                                         |
| **Region**              | All                                                                                                                                                                          |
| **Target Release Date** | M1: On Update trigger & contact profile display - Tier 1: 3/11 - Tier 2: 3/18 - Tier 3: 3/25 M2: On Schedule trigger (date-type) - Tier 1: 4/7 - Tier 2: 4/14 - Tier 3: 4/21 |

### Background

**Business Goal**

* **Increase Journey Adoption:** Integrate CRM data into Journeys to enable always-on business communication scenario (eg. Member level upgrade, anniversary message).
* **Prevent Churn**: Close the feature gap with key competitors by providing structured data capabilities and application.
* **System of Record (SoR) Foundation:** Establish Custom Fields as the core data infrastructure across MAAC, DAAC, and CAAC, positioning CL as the primary source of truth for customer engagement data.

**Client Value**

* **Personalized Communication:** Leverage custom fields to execute highly personalized marketing scenarios (e.g., birthday rewards, loyalty milestones), driving conversions and increasing LTV.
* **Operational Efficiency:** Enable always-on automation by eliminating the manual overhead of converting CRM data into static tags, repetitive CSV imports, and constant data maintenance, thereby reducing labor time and human error.

### Introduction

**Custom Fields (and Customer ID) empower brands to flexibly apply CRM data to trigger and branch Customer Journeys**, enabling always-on personalized communication to drive higher customer engagement and conversion.

* **Journey Trigger:** Automate journeys based on real-time CRM data, including customer ID, updates or anniversaries (e.g., membership renewal).
* **Journey Branch:** Split journey paths using text, date, date-time or numeric custom field logic (e.g., points or tiers) or customer ID system field presence.
* **Journey Action:** Update or clear Contact custom fields' value directly within the journey flow.
* **Unified Data Sync:** Manage customer custom fields (custom fields’s value) at scale via API, CSV import/export, or manual profile edits.

#### Target Audience & Selling Points

* **Marketer**
  * Pain point:
    * **Inefficient "Tag-as-Data" workarounds:** Relying on static tags to reflect CRM updates requires heavy manual CSV management, causing significant delays and high operational overhead.
    * **Limited Personalization & Management Clutter:** Tags lack structured data types (e.g., dates/numbers), leading to impersonal messaging and "tag explosions" that are difficult to clean and restrict advanced journey scenarios.
  * Selling point:
    * _Turn CRM data into high-precision, 'always-on' journeys that boost CVR and LTV_ — Unlock the full potential of your data by automating personalized engagement across the entire customer lifecycle, ensuring every milestone drives measurable growth.
* **Sales/Support Agent (CAAC user)**
  * Pain point:
    * **Disconnected automation:** Customer insights gathered (attribute updates) during 1-on-1 interactions cannot automatically trigger follow-up journeys.
  * Selling point:
    * _Instantly trigger personalized automated care from real-time frontline updates —_ Seamlessly bridge the gap between frontline customer updates and marketing action to ensure customers receive the right care at the perfect moment.

#### Scenario Examples

* Instant VIP Recognition (Text-type custom field): Trigger when Membership\_Tier updates to "Gold"; send welcome message and coupon.
* High-Value Point Redemption Reminder (Number-type): Trigger when Point\_Balance > 1000; branch based on Point\_expiry date.
* Precise Post-Service Care (DateTime-type): Trigger real-time when Last\_Service\_Time is updated via API; send survey and update Follow\_up\_Status.
* Annual Life-Event Marketing (Date-type): Scheduled trigger for Child\_Date\_of\_Birth with "ignore year".
* Appointment Reminders (Date-type): Scheduled trigger with relative offset (e.g., 1 day before).
* New Member Onboarding (Customer ID): Trigger on Customer ID transition from Empty to Has Value.

#### Combine Feature

* Omnichannel Reach: Custom field triggers work across LINE, SMS, and EDM channels within a single journey.
* CAAC Smarketing flow: Attributes updated by agents in the CAAC Contact Profile will sync to the CDH and can immediately trigger MAAC journeys for automated follow-ups.

Figma UI: [Contact Profile](https://www.figma.com/design/4izQy6bC4QxfvTOxuFotIl/MAAC_Contacts?node-id=2083-2\&p=f\&t=ALzGD4Pm124SX4se-0) | [Customer Journey](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=9043-1915\&p=f\&t=Vrxao7c7pR9vHYZM-0)

| Feature > Section | Figma UI (mockup)                                                                                                                                                              | Description                                                                                        |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------- |
| Contact Profile   | [Figma section](https://www.figma.com/design/4izQy6bC4QxfvTOxuFotIl/MAAC_Contacts?node-id=2088-43979\&t=ALzGD4Pm124SX4se-4)![](<../../../.gitbook/assets/Unknown image (120)>) | - Users need to click \[edit] to modify the custom fields, then click \[save] to store the values. |

This prevents unintentional updates and triggers the journey.

\| | Contact export | [Figma section](https://www.figma.com/design/4izQy6bC4QxfvTOxuFotIl/MAAC_Contacts?node-id=2094-9011\&t=ALzGD4Pm124SX4se-4)![](<../../../.gitbook/assets/Unknown image (121)>) | - Users can select all or specific custom fields for customer list export CSV.

\| | Contact import | (no UIUX change to the contact import flow) | Note: Templates include only system fields.

Users must manually add custom fields to the template CSV.

* Add the custom field key as a header (e.g., cl\_custom\_points) next to the last column and modify the value for each contact.

Upload the edited template, and the system will update the custom fields accordingly.

* Enter "null" in custom fields to clear a contact's value.

\| | Journey Trigger Mode | [Figma section](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=9170-183475\&t=ALzGD4Pm124SX4se-4)![](<../../../.gitbook/assets/Unknown image (122)>) | 1.

**Action Based:** trigger journey on event or attribute\*\*\*\*update.

2.

**Scheduled:** trigger journey daily at a specific time to scan for date-matched contact and enter the journey (supports only date-type custom fields).

\| | \[Action based mode] Journey Trigger Node → Change in Contact Attribute | [Figma section](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=9178-212001\&t=ALzGD4Pm124SX4se-4)![](<../../../.gitbook/assets/Unknown image (123)>) | | | Text ([operator](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=9590-348789\&t=ALzGD4Pm124SX4se-4))![](<../../../.gitbook/assets/Unknown image (124)>) | | | Number ([operator](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=9590-350009\&t=ALzGD4Pm124SX4se-4))![](<../../../.gitbook/assets/Unknown image (125)>) | | | Date ([operator](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=9590-357957\&t=ALzGD4Pm124SX4se-4))![](<../../../.gitbook/assets/Unknown image (126)>)![](<../../../.gitbook/assets/Unknown image (127)>) | - For Date field, users can use the \[v] Ignore Year checkbox, to evaluate the filed only on the date, not the year.

(e.g.

trigger if the contact’s birthday is on 12/25) | | DateTime ([operator](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=9621-153008\&t=ALzGD4Pm124SX4se-4))![](<../../../.gitbook/assets/Unknown image (128)>)![](<../../../.gitbook/assets/Unknown image (129)>) | - For DateTime field, users can use the \[v] Ignore date checkbox, to evaluate the filed only on the time, not the year and date.

(e.g.

trigger if the contact’s historical booking time is between 9:00 \~ 12:00) | | \[Scheduled mode] Journey Trigger Node → Dynamic Date | [Figma section](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=9775-223426\&t=ALzGD4Pm124SX4se-4)![](<../../../.gitbook/assets/Unknown image (130)>) | - Only Date-type custom filed can be selected for Dynamic Date trigger node.

\| | ![](<../../../.gitbook/assets/Unknown image (131)>) | - For an annual recurring event (anniversary) journey, users must check the \[v] Ignore Year to evaluate only on the date and trigger the journey every year on the same date.

\| | Branch node & filter | [Figma section](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=9095-187983\&t=ALzGD4Pm124SX4se-4)![](<../../../.gitbook/assets/Unknown image (132)>) | | | Text ([operator](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=9156-127792\&t=ALzGD4Pm124SX4se-4))![](<../../../.gitbook/assets/Unknown image (133)>)![](<../../../.gitbook/assets/Unknown image (134)>) | - Users can use the \[v] Case sensitive checkbox, to evaluate the exact same capitalization.

\| | Number ([operator](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=9334-70530\&t=ALzGD4Pm124SX4se-4))![](<../../../.gitbook/assets/Unknown image (135)>) | | | Date ([operator](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=9278-164268\&t=ALzGD4Pm124SX4se-4))![](<../../../.gitbook/assets/Unknown image (136)>)![](<../../../.gitbook/assets/Unknown image (137)>) | - Users can use the \[v] Ignore year checkbox, to evaluate the filed only on the date, not the year.

\| | DateTime ([operator](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=9339-154644\&t=ALzGD4Pm124SX4se-4))![](<../../../.gitbook/assets/Unknown image (138)>)![](<../../../.gitbook/assets/Unknown image (139)>) | - Users can use the \[v] Ignore date checkbox, to evaluate the filed only on the time, not the year and date.

\| | Action Node → Change attribute | [Figma section](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=9147-24738\&t=ALzGD4Pm124SX4se-4)![](<../../../.gitbook/assets/Unknown image (140)>)![](<../../../.gitbook/assets/Unknown image (141)>) | - Select a custom field to - Update to a new value - Clear existing value |

{% hint style="info" %}
### Note

* **Archiving Impact**: Archiving a field removes it from all UI surfaces. If an active journey relies on an archived field, that trigger or condition node will effectively **stop functioning** and evaluate as Null.
* **Timezone Normalization**: All DateTime evaluations are automatically normalized to the **Org Timezone** setting for consistency.
* **Date vs DateTime field type selection**:
  * _Do not misuse DateTime for a Date type field, as it may cause some scenarios to become unachievable._
  * **Date Type:** Use for **calendar-based milestones** (e.g., membership anniversaries, contract dates). Only the **Date** type supports "Anniversary" and "On Specific Date" scheduled triggers.
  * **DateTime Type:** Use only for **precise event tracking** where the exact hour and minute are required (e.g., exact service completion or login time).
* Suggest workflow for **Importing contact** with custom fields’ value updates:
  * Recommend **exporting a contact list first** to capture the exact active cl\_custom\_{key} headers.
  * Simply copy these headers into your import template to eliminate manual typing errors and ensure 100% mapping success.
{% endhint %}

**🗓️Upcoming Roadmap**

* Dynamic Messaging (Q2): Injecting custom field variables into messages for hyper-personalization.
* Custom Fields in Segments (Q2): Enabling structured attribute filtering in the Segment builder

#### FAQ

<details>

<summary><strong>Q1: Why can't I see my newly created custom field in the Journey trigger list?</strong></summary>

Ensure the field status is "Active" in the Admin Center. Archived fields are hidden from all journey configuration panels.

</details>

<details>

<summary><strong>Q2: If a Unified contact's data is updated via both LINE and Email entity, will the contact enter the journey twice?</strong></summary>

No. Entry limits and cooldowns (e.g., 1-hour cooldown) apply to the **Unified Contact ("True Contact")**, not individual channel profiles, to prevent spamming the user.

</details>

### Setting (For CSM)

Instruction for CSM to set the function for customers. Ex: Django setting…

Please insert screenshots or refer links to Google Slides or Figma links

### Reference

Put related documents here. ex: related product intro

**Pricing Table**

## Feature Pricing Rollout Notice

{Pricing\_master\_sheet}

### Product Name > PM

CAAC

### Feature Name > PM

模組｜Template Add-on 擴充功能

### Feature Summary > PM

提供用戶可額外加購 template 上限，每單位加購數量為 100 templates。適用對象：Plan2（Basic / Professional）與 Plan3（Enterprise）

### HQ Pricing & Charge Mode > PM

| Market | Feature                  | Pricing(Please give the currency) | Pricing model(Plan-base / Add-on ) | Recurring / One-time fee |
| ------ | ------------------------ | --------------------------------- | ---------------------------------- | ------------------------ |
| HQ     | Template Add-on（每 100 個） | NTD 1,000/月                       |                                    |                          |

###

### Feature name translation > PM

|              | TW | EN | TH | JP |
| ------------ | -- | -- | -- | -- |
| Feature name |    |    |    |    |

###

### Local Market Pricing & Charge Mode > Local Manager

| Market | Feature | Pricing(Please give the currency) | Pricing model(Plan-base / Add-on ) | Recurring / One-time fee |
| ------ | ------- | --------------------------------- | ---------------------------------- | ------------------------ |
| TW     |         |                                   |                                    |                          |
| TH     |         |                                   |                                    |                          |
| JP     |         |                                   |                                    |                          |

###

### Exception Notes

JP 市場表示當地同類功能價格為約 JPY 4,000-5,000，HQ 接受價格區間 5,000/月 落地為例外。

### Expected Release Timeline

Release date ：2025/07/15（四）Release market：TW / TH / JP

### Attachments

* PRD ：
* Pricing Strategy Discussion Record：
* Confirmation Emails from Each Market (if any)：
* Pricing master sheet :

###

### To-Do by Stakeholders

**RevOps (Sales Pricing and Reporting Alignment)**

* Update the **Price Master Sheet**
* Define **Sales Process rules** (plan mapping, add-on eligibility)
* Adjust **KPI / Revenue Reports** accordingly

**ProductOps (Feature Access and Configuration Setup)**

* Configure **plan / add-on access control**
* Implement **feature toggle or backend configuration items**
* Conduct **QA checks** to ensure feature access is correctly restricted based on plan level

###

### Check List

| Owner      | Item                                | Status    | Note |
| ---------- | ----------------------------------- | --------- | ---- |
| PM         | Pricing confirmed with Local leader | Not start |      |
| ProductOps | Feature setting SOP                 | Not start |      |
| RevOps     | Sales process                       | Not start |      |
