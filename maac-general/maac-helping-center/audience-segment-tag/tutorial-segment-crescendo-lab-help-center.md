# Tutorial｜Segment – Crescendo Lab Help Center

### Feature Overview

The **Segment** feature assists brands in creating distinct contact lists based on contact profiles, engagement behaviors, tags, or AI-driven insights. Once created, these segments can be applied to LINE, WhatsApp, or SMS broadcasts and ad audiences, enabling brands to reach specific groups with precise messaging.

#### Important Update to Segmentation Logic

For all existing MAAC segments, the system has added a default filter condition of **Reachability = Reachable**.

* **Automated Filter Change:** The system has automatically applied the `Reachability = Reachable` filter to all existing MAAC segments.
* **Impact Scope:** Segment sizes (audience counts) may decrease because the default setting now displays only reachable users. The system temporarily filters out the following two categories of users (who are considered inactive on messaging apps despite having phone numbers):
  * Users who have blocked the brand on LINE (but have a mobile number).
  * SMS-only contacts (those without a LINE/WhatsApp identity).
* **Action Required (SMS Users):** If your segment is intended for sending SMS messages to **all members** (including those who have blocked you on LINE), please navigate to the segment editing page and manually change the **Reachability** condition to **"All"**.

### Creation Methods

| Method                     | Description                                                                                     | Usage Scenario                                                      |
| -------------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **MAAC Condition Segment** | Filter based on contact fields and behavioral conditions (e.g., tags, join time).               | When data structure is clear and fields are organized.              |
| **Import LINE UID List**   | Create a segment by uploading an external list (CSV file).                                      | When you already possess specific audience UIDs.                    |
| **CDH Condition Segment**  | Use cross-platform tag data to create segments.                                                 | When integration of multi-source data (MAAC + CAAC) is needed.      |
| **AI Segment (Beta)**      | Automatically analyze tags and notes to generate a list based on natural language descriptions. | When data is unstructured or manual condition setting is difficult. |

### Screening & Exclusion Logic

When creating a segment, in addition to setting "Filter Conditions" to include specific targets, you can also use "Exclude Segment" to remove unwanted lists, creating a more precise audience group.

* You can set "Filter Conditions" only.
* You can set "Exclude Segment" only: The system will base the result on all contacts, excluding the selected list.
* You can set both (e.g., Filter active members, and exclude those who have already purchased).

{% hint style="info" %}
When setting exclusions, only segments with a status of "Ready" will be available for selection.
{% endhint %}

### How to Create a Segment

{% stepper %}
{% step %}
### Step 1. Enter the Segment Module

Click **\[Segment List]** in the MAAC side menu, then click **\[Create]** in the upper right corner to enter the creation process.
{% endstep %}

{% step %}
### Step 2. Select Creation Method

Choose the method that best suits your purpose:

* Use MAAC Conditions
* Import LINE UID List
* Use CDH Conditions
* Use AI Segment (Beta)
{% endstep %}
{% endstepper %}

#### Use MAAC Conditions

{% stepper %}
{% step %}
Select "Use MAAC Conditions".
{% endstep %}

{% step %}
Set condition combinations (supports "AND / OR" logic).
{% endstep %}

{% step %}
Confirm the estimated contact count.
{% endstep %}

{% step %}
Save and create the segment.
{% endstep %}
{% endstepper %}

Application Example:

* Condition: Has tag "VIP" AND interacted within the last 30 days.
* Usage: Sending exclusive offers or new product notifications.

#### Import LINE UID List

If the brand already holds the LINE UIDs of specific contacts, you can directly upload a list to create a static segment.

{% stepper %}
{% step %}
Select "Import LINE UID List".
{% endstep %}

{% step %}
Enter segment name and description.
{% endstep %}

{% step %}
Upload a CSV file that meets the format requirements.
{% endstep %}

{% step %}
Click **\[Create]**, and the system will automatically generate the segment.
{% endstep %}
{% endstepper %}

CSV Format Requirements:

* File Format: `.csv` (UTF-8 encoding).
* Required Column: `line_uid`.
* File Size: ≤ 25MB, max 300,000 rows.
* Can only import contacts that already exist in MAAC and are linked to LINE.

#### Use CDH Conditions

If **Customer Data Hub (CDH) integration** is enabled, you can create segments using **cross-platform tag data**.

#### Use AI Segment (Beta)

AI Segment allows users to describe conditions in natural language to automatically build a segment list.

{% stepper %}
{% step %}
### Step 1. Enter Prompt

* **Segment Name:** Custom name, e.g., "Customers complaining about logistics".
* **Prompt:** Briefly describe the audience you want to find, and the system will analyze it.

Example Prompts:

* "Contacts who asked about discounts or offers"
* "Customers mentioning shipping or logistics issues"
* "High purchase intent but haven't ordered yet"
* "Customers interested in children's products"
{% endstep %}

{% step %}
### Step 2. Generate Segment

* Click **\[Generate]**. The system will analyze tags and note contents within the brand.
* Processing time is approx. **20–60 minutes** (depending on data volume).
* The segment status will show as "Calculating" and change to "Ready" once complete.
{% endstep %}

{% step %}
### Step 3. Apply Segment

* Target for LINE / SMS broadcasts.
* Export contact list (CSV).
* Export as Ad Audience List (Facebook / LINE).
{% endstep %}
{% endstepper %}

### Notices & Limitations

To ensure system stability and logical correctness, please note the following limitations for Segment Exclusion and AI Segments.

#### Segment Exclusion Rules

| Limit Item                   | Rule Description                                                                                                                                                                                   |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Exclusion Quantity**       | A single segment can exclude a maximum of **2** other segment lists.                                                                                                                               |
| **Exclusion Depth**          | The exclusion relationship chain can be at most **2 layers** deep. _(e.g., A excludes B, and B excludes C is allowed; but extending to C excluding D is not allowed)_                              |
| **Loop/Self Exclusion**      | Segments cannot "exclude themselves" and cannot form "exclusion loops" (e.g., A excludes B, and B excludes A).                                                                                     |
| **Deletion Protection**      | **If a segment is set as an "excluded object" by another segment, it cannot be deleted.** You must remove the associated exclusion setting before deletion is possible.                            |
| **Same Channel Restriction** | All excluded segments must belong to the same channel account. (e.g., If a brand has multiple LINE OA accounts in MAAC, the segment exclusion logic only applies within the same LINE OA account). |

#### AI Segment Limitations

| Item                  | Limitation Description                                                                                                                                                                                               |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| List Update           | After creation, you can click **"Update"** at any time to recalculate and reflect the latest data. Due to the nature of generative AI, even with the exact same Prompt, generated lists may vary slightly each time. |
| Condition Combination | Currently, combining AI segments with other segment conditions is not supported.                                                                                                                                     |
| Time Range            | AI Segments do not yet support time interval filtering (e.g., "within the last 30 days").                                                                                                                            |
| List Nature           | AI Segments are static lists and do not change automatically in real-time; "Update" is required to get new results.                                                                                                  |
| Processing Time       | Approximately 20–60 minutes, depending on the brand's data volume.                                                                                                                                                   |

### Common Questions (FAQ)

<details>

<summary>Why can't I delete a segment?</summary>

If the segment is **currently set as an "excluded object" by another segment**, the system locks it to prevent deletion. You must first find the segment referencing this list, remove the exclusion setting, and then delete it.

</details>

<details>

<summary>Are there limits on the number or depth of exclusions?</summary>

Yes. A single segment can exclude a maximum of **2** other lists; and the exclusion relationship supports a maximum of **2 layers** (e.g., A excludes B, B excludes C = limit reached). If this limit is exceeded, the system will prevent saving.

</details>

<details>

<summary>Can I set mutual exclusions? (e.g., A excludes B, and B excludes A)</summary>

No. This creates a "loop exclusion" logic error, and the system does not allow this setting.

</details>

<details>

<summary>How is AI Segment different from general segments?</summary>

AI Segment uses natural language prompts, and the system automatically analyzes notes and tags; other segmentation methods require manual setting of specific conditions (e.g., gender, join date).

</details>

<details>

<summary>Can I use AI Segment and other conditions simultaneously?</summary>

Currently, no. If you need an intersection operation, it is recommended to create an AI Segment first, add a tag to those contacts, and then use that tag in a MAAC condition segment.

</details>

<details>

<summary>Can AI Segment show the estimated count beforehand?</summary>

Currently, estimating the list size is not supported. The actual number of contacts will be displayed after the system completes the calculation.

</details>

<details>

<summary>Why might the AI Segment result be different each time for the same prompt?</summary>

AI Segment performs semantic analysis based on the latest notes and tags. Due to data updates and the nature of generative models, slight variations in the re-generated list are normal.

</details>

### Related articles

* [Tutorials｜LINE Broadcast](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBmdF4kDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlzlogDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI%2BL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMzE0MzkxMjktVHV0b3JpYWxzLUxJTkUtQnJvYWRjYXN0BjsIVDoJcmFua2kG--8cca4031b8758c5a1c4783f5ee952950324af8e5)
* [Tutorials｜New Tag System : Tag Intensity and Timespans](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBk01%2F8FBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlzlogDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJaL2hjL2VuLXVzL2FydGljbGVzLzQ0MjM4MTM2NDEyNDEtVHV0b3JpYWxzLU5ldy1UYWctU3lzdGVtLVRhZy1JbnRlbnNpdHktYW5kLVRpbWVzcGFucwY7CFQ6CXJhbmtpBw%3D%3D--0e9332fd3303e976fc5b98cf011cd0723402c2bb)
* [Tutorials｜Predicted purchase probability](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBngutoDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlzlogDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJOL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQ2MDEwOTMxNDUtVHV0b3JpYWxzLVByZWRpY3RlZC1wdXJjaGFzZS1wcm9iYWJpbGl0eQY7CFQ6CXJhbmtpCA%3D%3D--a25cdd5fc53f994e21c4d9119da2fb13ea512d19)
* [Feature Description｜MAAC Contact Import and Update](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBnqhYkDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlzlogDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJYL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMzg2Njc4MDEtRmVhdHVyZS1EZXNjcmlwdGlvbi1NQUFDLUNvbnRhY3QtSW1wb3J0LWFuZC1VcGRhdGUGOwhUOglyYW5raQk%3D--d607510cccee134a1c464673632d639399f558d8)
* [How to share LINE OA platform, LINE Developers, GA(UA) / GA4 access to Crescendo Lab?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmp1FFgBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlzlogDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ1L2hjL2VuLXVzL2FydGljbGVzLzgxMTAyNzExNDYzOTMtSG93LXRvLXNoYXJlLUxJTkUtT0EtcGxhdGZvcm0tTElORS1EZXZlbG9wZXJzLUdBLVVBLUdBNC1hY2Nlc3MtdG8tQ3Jlc2NlbmRvLUxhYgY7CFQ6CXJhbmtpCg%3D%3D--9f0425eb9e473ed2a63577a35e000396daae8599)
