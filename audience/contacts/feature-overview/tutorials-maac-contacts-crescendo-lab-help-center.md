# Tutorials｜MAAC Contacts – Crescendo Lab Help Center

### Feature Overview｜Contact Management & Classification

In the MAAC system, contacts are classified based on data sources and interaction channels into four main types:

| Contact Type               | Definition                                                                              | Available Interactions                                                                          | Notes                                                   |
| -------------------------- | --------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| LINE Contact               | Users who have added the brand's LINE Official Account (LINE OA)                        | Use MAAC features such as LINE push messages and auto-replies; initiate real-time chat via CAAC | Can interact and segment via the LINE OA                |
| Facebook Messenger Contact | Facebook users who have previously chatted with the brand’s fan page                    | Send Messenger messages and configure auto-replies                                              | Requires Facebook channel connection and authorization  |
| Instagram Contact          | Users who have interacted with the brand's IG Business Account (e.g. DM, story replies) | Use Instagram auto-reply features                                                               | Requires Instagram channel connection and authorization |
| Other Contact              | Users with only a phone number                                                          | Can only receive SMS campaigns                                                                  | Cannot interact via LINE, Facebook, or Instagram        |

#### Recommended Usage

* Search, view, and manage all contacts (including LINE, FB, IG, and phone contacts)
* Import/export data and batch add/remove tags
* Launch real-time chat with LINE contacts (requires login to CAAC)
* Send SMS messages for campaigns, promotions, or binding notifications

#### Additional Notes

* All contact types are displayed in **MAAC > Contact Management**, and can be searched, tagged, edited, imported, or exported.
* Starting from 2025/03/28, contacts imported via phone number will be labeled as “Unnamed Contact” by default. You may manually update their display names.
* If the channel connection is incomplete, the system cannot identify the contact’s UID and will treat them as a phone contact only.
* For brands looking to integrate cross-platform data, we recommend enabling the **Customer Data Hub** to synchronize contact tags and attributes across MAAC and CAAC.

### Common Operations

#### Search for a Specific Contact

You can search contacts by the following fields:

* Contact Name
* LINE UID
* Facebook ID
* Instagram ID
* Email
* Phone Number
* Customer ID

#### Filter Contacts

Click on “Filter Contacts” and select filters based on:

**By Platform**

* LINE: Show LINE contacts
* Messenger: Show Facebook contacts
* Instagram: Show Instagram contacts

**By Channel**

Select a specific connected LINE OA, Facebook Page, or IG Business Account.

**By Contact Conditions**

* Tags, engagement metrics, join time, last interaction time, source, gender, birthday, phone, email, Customer ID

{% hint style="info" %}
📌 Source Filter Explanation:
{% endhint %}

| Source Type          | Description                                                                                                                                 |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| Binding Message      | <p>Contact added via MAAC binding link.<br>Common scenarios:<br>- Binding SMS messages<br>- Binding messages generated via MAAC OpenAPI</p> |
| Notification Message | Contact added after receiving a notification-type message                                                                                   |

#### Bulk Tag Updates

* After applying filters, select multiple contacts and click “Bulk Tag Update” to add or remove tags for all selected contacts.

#### View & Edit Contact Details

* Click a contact’s name to expand the detail panel.
* Edit fields directly and changes will be saved in real-time.
* Switch to the “Customer Data Hub” tab to view synced data from MAAC and other platforms (e.g., CAAC).

**Related Article:** [MAAC & CAAC Customer Data Integration](https://crescendolab.zendesk.com/hc/en-us/articles/43405131619481)

#### Import & Export Contacts

**For detailed steps, see:** [MAAC Contact Import & Export Guide](https://crescendolab.zendesk.com/hc/en-us/articles/4413238667801)

### Related articles

* [Tutorials｜ MAAC x SurveyCake Form](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkr5rYDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJmIGIkDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJGL2hjL2VuLXVzL2FydGljbGVzLzQ0MTM5OTk5NTA3NDUtVHV0b3JpYWxzLU1BQUMteC1TdXJ2ZXlDYWtlLUZvcm0GOwhUOglyYW5raQY%3D--1f880d00258724a78052c515944e62345884d05f)
* [Tutorials｜New Tag System : Tag Intensity and Timespans](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBk01%2F8FBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJmIGIkDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJaL2hjL2VuLXVzL2FydGljbGVzLzQ0MjM4MTM2NDEyNDEtVHV0b3JpYWxzLU5ldy1UYWctU3lzdGVtLVRhZy1JbnRlbnNpdHktYW5kLVRpbWVzcGFucwY7CFQ6CXJhbmtpBw%3D%3D--39d28b20e765c82fd6b691508402749c5afa2387)
* [How to share LINE OA platform, LINE Developers, GA(UA) / GA4 access to Crescendo Lab?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmp1FFgBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJmIGIkDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ1L2hjL2VuLXVzL2FydGljbGVzLzgxMTAyNzExNDYzOTMtSG93LXRvLXNoYXJlLUxJTkUtT0EtcGxhdGZvcm0tTElORS1EZXZlbG9wZXJzLUdBLVVBLUdBNC1hY2Nlc3MtdG8tQ3Jlc2NlbmRvLUxhYgY7CFQ6CXJhbmtpCA%3D%3D--d991fbbb51182e9116bdebb60e77ad5ce952fc1f)
* [Tutorial | CAAC Conduct Conversation and Contact Information](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJn6ysBcBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJmIGIkDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJgL2hjL2VuLXVzL2FydGljbGVzLzgwOTQ5NTI5MTM1NjEtVHV0b3JpYWwtQ0FBQy1Db25kdWN0LUNvbnZlcnNhdGlvbi1hbmQtQ29udGFjdC1JbmZvcm1hdGlvbgY7CFQ6CXJhbmtpCQ%3D%3D--a01930e878f2067d1830d0bd81a40c9590dc2024)
* [Why Are the Pre-set Auto-reply and Rich Menu Not Working?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJletogDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJmIGIkDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJeL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMjUwNjYxMzctV2h5LUFyZS10aGUtUHJlLXNldC1BdXRvLXJlcGx5LWFuZC1SaWNoLU1lbnUtTm90LVdvcmtpbmcGOwhUOglyYW5raQo%3D--bbf7189dae5bf548a2c96fc8961dea9155795262)
