# Tutorials｜How to connect BigQuery to Google Cloud Platform and Looker Studio – Crescendo Lab Help Center

This guide is designed for customers who wish to query Crescendo Lab data using BigQuery. You can follow this tutorial even if you are unfamiliar with Google Cloud Console or Looker Studio.

## Ensure You Have Access to BigQuery

If you need access to Google BigQuery, please contact Crescendo Lab's customer support team. We will assist you with the application process.

✅ If you also require access to GCP or Looker Studio, please provide the Gmail address you intend to use. We will enable the necessary permissions for that account.

Once your application is approved, you will receive the following:

* A designated Google service account (e.g., cresclab-bot@cresclab-partnership.iam.gserviceaccount.com)
* A specific GCP project name (e.g., cresclab-prod)
* Shared dataset ID (e.g., shared\_dataset\_1)
* Permission to query the data
* Gmail access to the project folder in GCP or Looker Studio

## Access to BigQuery on the Google Cloud Platform

{% stepper %}
{% step %}
### Open Google Cloud Console

Open https://console.cloud.google.com.
{% endstep %}

{% step %}
### Sign in

Login with the Google account which has access to the project folder in GCP or Looker Studio (not the Google service account like _cresclab-bot@cresclab-partnership.iam.gserviceaccount.com_).
{% endstep %}

{% step %}
### Change the project

Change the project.\
![](../../../.gitbook/assets/45270011284121)
{% endstep %}

{% step %}
### Select the project

Select the project you like to access to.\
![](../../../.gitbook/assets/45270073381529)
{% endstep %}

{% step %}
### Open the menu

Click the icon to open the menu.\
![](../../../.gitbook/assets/45270073383321)
{% endstep %}

{% step %}
### Select BigQuery and Studio

Select "BigQuery" and "Studio".\
![](../../../.gitbook/assets/45270073385369)
{% endstep %}

{% step %}
### Access the BigQuery database

You can access the BQ database! You can access and organize your MAAC event by using SQL.\
![](../../../.gitbook/assets/45270011322777)
{% endstep %}

{% step %}
### Run SQL queries

You can enter any SQL query into the tables in the BigQuery database.

For example, enter the query in the edit box and click 'run.' The result will be displayed at the bottom.\
![](../../../.gitbook/assets/45487743510937)
{% endstep %}

{% step %}
### View table details

You can also view the table's details by selecting the table directly on the left.\
![](../../../.gitbook/assets/45487721258009)
{% endstep %}
{% endstepper %}

## Connecting Looker Studio with BigQuery

{% stepper %}
{% step %}
### Open Looker Studio

Open https://lookerstudio.google.com/.
{% endstep %}

{% step %}
### Sign in

Login with the Google account which has access to the project folder in GCP or Looker Studio (not the Google service account like _cresclab-bot@cresclab-partnership.iam.gserviceaccount.com_).
{% endstep %}

{% step %}
### Create a data source and select BigQuery

Create a data source and select BigQuery.\
![](../../../.gitbook/assets/45182256041497)
{% endstep %}

{% step %}
### Select BigQuery

Select BigQuery.\
![](../../../.gitbook/assets/45182244031129)
{% endstep %}

{% step %}
### Authorize BigQuery

Authorize BigQuery.\
![](../../../.gitbook/assets/45270011325593)
{% endstep %}

{% step %}
### Select project and dataset

Select the project and dataset Crescendo Lab provided and click "connect."

Please confirm that you have received all the information you need. Ref:

Select the 'GCP project id' as the project, the 'shared dataset id' as the dataset, and the table to which you want to build visualization on Looker.\
![](../../../.gitbook/assets/45487721261593)
{% endstep %}

{% step %}
### Customize the table

Customize the table, including data type, metrics, fields, and table refresh time. Then, create the report.\
![](../../../.gitbook/assets/45487721266713)
{% endstep %}

{% step %}
### Create visualizations

Start to create any visualizations and explore your data!\
![](../../../.gitbook/assets/45487743561497)
{% endstep %}
{% endstepper %}

## FAQ

<details>

<summary>Why can’t I find Crescendo Lab's project in GCP?</summary>

Please ensure you are signed in to GCP using the Gmail account granted access by Crescendo Lab. If you’re unsure whether your account has access, please get in touch with our Customer Success Team for assistance.

</details>

<details>

<summary>Why am I seeing an “Access Denied” error in GCP or Looker Studio?</summary>

Please get in touch with our Customer Success Team. We will help you review your permission settings and resolve the issue.

![](../../../.gitbook/assets/45533821130777)

</details>

### Related articles

* [Tutorials｜ MAAC x SurveyCake Form](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkr5rYDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnOm5cWKToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJGL2hjL2VuLXVzL2FydGljbGVzLzQ0MTM5OTk5NTA3NDUtVHV0b3JpYWxzLU1BQUMteC1TdXJ2ZXlDYWtlLUZvcm0GOwhUOglyYW5raQY%3D--0689ba1c6bc0c6aabc509db6267b08f3ab3a0b9d)
* [Tutorials｜MAAC Prize Management - Card message type](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJn9bZXtKToYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnOm5cWKToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJYL2hjL2VuLXVzL2FydGljbGVzLzQ2MTAwMzkxMDAxNDk3LVR1dG9yaWFscy1NQUFDLVByaXplLU1hbmFnZW1lbnQtQ2FyZC1tZXNzYWdlLXR5cGUGOwhUOglyYW5raQc%3D--11bc0d3ac062757526d8fa31e4ad50e7453ea5d4)
* [Tutorial｜Using WhatsApp Channel in CAAC](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBmArdtuKDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnOm5cWKToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJOL2hjL2VuLXVzL2FydGljbGVzLzQ0NDU2NTk3MDk0NDI1LVR1dG9yaWFsLVVzaW5nLVdoYXRzQXBwLUNoYW5uZWwtaW4tQ0FBQwY7CFQ6CXJhbmtpCA%3D%3D--9c9f05c70a39153ce0361b83c8a19f054fedba8a)
* [Tutorials｜ Prize Management：Coupon、LINE Points、Vouchers、Game tixs、Brand Coupons](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBmFKXUDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnOm5cWKToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ0L2hjL2VuLXVzL2FydGljbGVzLzQ0MTI4OTcwNjgzMTMtVHV0b3JpYWxzLVByaXplLU1hbmFnZW1lbnQtQ291cG9uLUxJTkUtUG9pbnRzLVZvdWNoZXJzLUdhbWUtdGl4cy1CcmFuZC1Db3Vwb25zBjsIVDoJcmFua2kJ--2a7269b2d50dfa7d7826381428fbb8b216ae403b)
* [MAAC 2025](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmfXV9UKToYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnOm5cWKToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSIwL2hjL2VuLXVzL2FydGljbGVzLzQ1NDQyMzUzOTYyOTA1LU1BQUMtMjAyNQY7CFQ6CXJhbmtpCg%3D%3D--05325145c70116cf3f230a8f0ee4164f85f5a68e)
