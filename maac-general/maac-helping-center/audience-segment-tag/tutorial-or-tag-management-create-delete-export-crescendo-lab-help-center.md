# Tutorial | Tag Management (Create, Delete, Export) – Crescendo Lab Help Center

Any interactive sections that can be clicked by contacts, as well as links in the MAAC backend, can be recorded with tags to capture the preferences and characteristics of contacts. In the tags, you can view the number of contacts that have been tagged and manage and edit them.

### Create Tag

{% stepper %}
{% step %}
### Manage tag lists

* Click on the tab to view different types of tag lists.
* Search for specific tags.
* The tag list will display the tag name, the number of contacts tagged with that tag, and the expiration date.
* Edit tags.
* Delete tags.
* Create tags, which can be permanent or temporary.
{% endstep %}

{% step %}
### Temporary Tags

* The validity period of a tag is the pasting date plus the set number of days (for example, if the validity period is set to 1 day, a tag pasted on March 1st at 13:00 will be removed after March 2nd at 23:59).
* The validity time of a clicked tag will be refreshed based on the contact's click behavior (for example, if a temporary tag is set for 2 days, and contact A clicks it once today and once tomorrow, the 2-day validity period will start counting from tomorrow).
{% endstep %}
{% endstepper %}

![Tag management screenshot](../../../.gitbook/assets/54392768980121)

{% hint style="warning" %}
* A single tag cannot exceed 50 characters (including both full-width and half-width characters).
* A maximum of 5 tags can be applied to the same action (such as a link or a keyword).
* When editing or deleting tags, it will only affect the tags on the current contacts. If you have set specific links or interactive areas where tags are applied, you also need to make corresponding changes or deletions.
* Tagging Time Explanation:
  * In general, tags are applied based on event triggers, so the tagging time varies depending on when each event occurs.
  * For contact imports, the process is handled as a single event, so all tagged contacts will share the same timestamp.
{% endhint %}

***

### Export Tags

With the Export function, marketing teams can download all tag data from the MAAC system into a file, making it easy to perform offline data cleaning and organization using tools like Excel. This allows you to clearly understand tag usage (such as identifying duplicate or invalid tags), resolve issues related to tag clutter or confusing semantics, and ensure data flows smoothly across systems—laying a clean foundation for future precision segmentation.

**How to use the export function?**

{% stepper %}
{% step %}
### Navigate to the page

Go to the "Audience" (Contact Management) menu and click on the "Tag Manager" page.
{% endstep %}

{% step %}
### Click Export

Click the "Export" button located at the top right corner of the page.
{% endstep %}

{% step %}
### Get the file

After a few minutes of processing time, you can download the CSV format file from the Notification Center.
{% endstep %}
{% endstepper %}

![Export screenshot 1](../../../.gitbook/assets/54392771746841) ![Export screenshot 2](../../../.gitbook/assets/54392771747353)

📄 Export File Content

The downloaded CSV file will contain the following core information:

* Tag Name
* Number of tagged contacts

### Related articles

* [Tutorials｜New Tag System : Tag Intensity and Timespans](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBk01%2F8FBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJneqYgDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJaL2hjL2VuLXVzL2FydGljbGVzLzQ0MjM4MTM2NDEyNDEtVHV0b3JpYWxzLU5ldy1UYWctU3lzdGVtLVRhZy1JbnRlbnNpdHktYW5kLVRpbWVzcGFucwY7CFQ6CXJhbmtpBg%3D%3D--1c27565ef0b12425ada83d3b5f712c5a8576533d)
* [Tutorials | Deeplink](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJnloYgDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJneqYgDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI4L2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMjM3MjQ0NDEtVHV0b3JpYWxzLURlZXBsaW5rBjsIVDoJcmFua2kH--48afa5592b731654aafed511cbdfe07997fe3f60)
* [Why are my button tags all the same?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBlyDKwDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJneqYgDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJJL2hjL2VuLXVzL2FydGljbGVzLzQ0MTM4MTc5MDk3ODUtV2h5LWFyZS1teS1idXR0b24tdGFncy1hbGwtdGhlLXNhbWUGOwhUOglyYW5raQg%3D--ae89e5b7a3cf04da86d13965fce7a316cae696bb)
* [How to share LINE OA platform, LINE Developers, GA(UA) / GA4 access to Crescendo Lab?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmp1FFgBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJneqYgDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ1L2hjL2VuLXVzL2FydGljbGVzLzgxMTAyNzExNDYzOTMtSG93LXRvLXNoYXJlLUxJTkUtT0EtcGxhdGZvcm0tTElORS1EZXZlbG9wZXJzLUdBLVVBLUdBNC1hY2Nlc3MtdG8tQ3Jlc2NlbmRvLUxhYgY7CFQ6CXJhbmtpCQ%3D%3D--c78edca99e0932acc52b8d363417d627644401a5)
* [Tutorials｜Predicted purchase probability](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBngutoDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJneqYgDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJOL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQ2MDEwOTMxNDUtVHV0b3JpYWxzLVByZWRpY3RlZC1wdXJjaGFzZS1wcm9iYWJpbGl0eQY7CFQ6CXJhbmtpCg%3D%3D--c31197b1713248c7a311cf23b0013ef08b84f646)
