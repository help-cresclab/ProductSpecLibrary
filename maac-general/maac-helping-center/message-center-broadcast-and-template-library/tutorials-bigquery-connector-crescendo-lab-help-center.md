# Tutorials｜BigQuery Connector – Crescendo Lab Help Center

### Tutorials｜BigQuery Connector

Creation Date: October 31, 2023\
Created By: Crescender Lab

***

### 💁‍♀️ Advantage

* Effective analysis of cross-channel marketing performance
* Achieving personalized cross-channel communication
* Creating multi-dimensional, precise audience groups
* Integrating a 360º consistent customer profile

***

#### 1. What is BigQuery Data Exporter？

Let's start with a simple understanding of what BigQuery is. BigQuery is a cloud-based data analysis service introduced by Google Cloud. It can handle data analysis operations at a scale of petabytes (PB). Some of the services you use in your daily life, like Google Search and Google Ads, rely on BigQuery as a core technology for data processing and analysis. BigQuery also comes with built-in machine learning capabilities, allowing users to perform more in-depth data analysis according to their needs.

4 main advantage of BigQuery

1. Fast: BigQuery is incredibly speedy. It can retrieve or analyze data at the scale of terabytes or petabytes in just seconds.
2. Versatile: It supports a variety of Business Intelligence (BI) tools and allows integration with third-party applications to enhance data analysis.

In addition to the above two major advantages, BigQuery uses SQL-like syntax to make it easier for users to query data. Data access is also encrypted to strengthen the security mechanism. As for the DR (Disaster Recovery) capability that everyone is most concerned about, BigQuery provides a wide range of data copy functions to avoid the risk of data loss.

Source： https://mile.cloud/zh/resources/blog/the-case-of-bigquery-require-leads-without-data-migration-by-this-step\_166

***

### ▶️ Setting steps (taking Emarsys as an example)

If any data-related platform receives BQ data, it can be connected to the Crescendo Labs BQ Connector. Here are six common platform connection instructions for reference:

BI system: Power BI (https://learn.microsoft.com/en-us/power-query/connectors/google-bigquery#authenticating-through-a-google-service-account), Tableau (https://help.tableau.com/current/pro/desktop/zh-tw/examples\_googlebigquery.htm), Metabase (https://www.metabase.com/data\_sources/bigquery)

CDP: Emarsys (https://help.emarsys.com/hc/en-us/articles/4411175189521-Client-hosted-Relational-Data-Relational-Data-Connect-your-Google-BigQuery-databases), Treasure data (https://docs.treasuredata.com/display/public/INT/Google+BigQuery+Import+Integration), Insider (https://academy.useinsider.com/docs/sending-google-bigquery-data-to-insider)

{% hint style="info" %}
Please confirm that you have already obtained the following data from Crescendo Lab Team before proceeding with the setup on your existing platform:

* GCP project id
* Dataset id
* Client email address
* Secret.json file
{% endhint %}

### Log-in Emarsys Marketing Platform

https://login.emarsys.net/bootstrap.php?r=customer/Login

{% stepper %}
{% step %}
### Select "Relational Data" from the Add-ons menu

![Select "Relational Data" from the Add-ons menu](<../../../.gitbook/assets/03270b59 4e5e 427a ae16 71f47dcf945d.png>)
{% endstep %}

{% step %}
### In "Relational Data," choose "Connections"

![In "Relational Data," choose "Connections"](<../../../.gitbook/assets/8878d8f7 e14a 424c 88ec 2ee6010be1dd.png>)
{% endstep %}

{% step %}
### Click Create Connection

![Click Create Connection](<../../../.gitbook/assets/d44d588e 8a89 4d71 8aad 34a703fa8917.png>)
{% endstep %}

{% step %}
### Choose BigQuery

![Choose BigQuery](<../../../.gitbook/assets/09cfe94f 70ba 4781 aee2 b20d9a9d1833.png>)
{% endstep %}

{% step %}
### Enter the four data values provided by Crescendo Lab

![Enter the four data values provided by Crescendo Lab](<../../../.gitbook/assets/899d289d 0898 4ee2 aff1 b5e448e08533.png>)
{% endstep %}

{% step %}
### After entering the data, click on "Save"

![After entering the data, click on "Save"](<../../../.gitbook/assets/613686b5 005a 4984 880d 94bd19ac0279.png>)
{% endstep %}
{% endstepper %}

***

{% hint style="info" %}
How to create Segment Templates in Emarsys to retrieve data, please refer to：\
https://help.emarsys.com/hc/en-us/articles/360002169933-Relational-and-AI-segments-Creating-relational-segments
{% endhint %}

***

### Considerations

* Requires proficiency in SQL programming language
* Data synchronization direction is one-way from MAAC → BQ
* Transaction tracking data is limited to Web GA data from domains already integrated with the MAAC platform
* Daily usage limit per client: 500 GB

{% hint style="info" %}
BigQuery Connector Daily Usage Limit: 500 GB

Definition of the 500GB limit:

* When running a query, if BQ estimates that the required data volume exceeds 500GB, the system will block the query and prompt you to adjust the query conditions (e.g., narrowing the range or reducing the data size).
* If the estimated data volume is below 500GB, the query will run successfully. Even if the actual fetched data exceeds 500GB, the query will still return results successfully.

Reset time: The daily usage limit resets at midnight Pacific Time (UTC-7). Please pay attention to time zone differences when planning queries to avoid exceeding the daily limit.
{% endhint %}

***

### ▶️ Explanations of the relevant data types provided by BigQuery

Currently, using BigQuery, you can access contact attributes, labels, open rates, click data, and consumption behavior data collected from Crescendo Lab's MAAC product database.

Update frequency:

* Attribute profile data: Updated daily at 00:00 AM
* Event-type data: Real-time updates (with a potential 1-2 minute delay in case of system overload)

Data record starting point:

* Profile attribute data: accumulated since the brand’s MAAC backend activation
* Event data: available starting from the activation of BigQuery Connector / CDH webhook for the brand

***

#### Attribute profile data - Contacts

* Clients can filter out contacts by the date of contact added to MAAC, the date will align with the contacts created time on MAAC UI

![Attribute profile data - Contacts](<../../../.gitbook/assets/8e6e811c 6df0 48b3 9752 a915e27f20ff.png>)

***

#### Attribute profile data - Tags

![Attribute profile data - Tags](<../../../.gitbook/assets/0661e212 d872 4d94 b7de 660723fb1fdf.png>)

***

#### Event-type data - Transactions

![Event-type data - Transactions](<../../../.gitbook/assets/8505dfdb a26a 4371 a454 8bc7e4c7a3e4.png>)

{% hint style="warning" %}
Consumption behavior (Transaction) tracking data is only available through domain Web GA data that has been connected to the MAAC platform.
{% endhint %}

***

#### Event-type data - Message send

![Event-type data - Message send](<../../../.gitbook/assets/51d730eb 629f 4f2c b1fc f8c22a6c7ee5.png>)

***

#### Event-type data - Message open

![Event-type data - Message open](<../../../.gitbook/assets/e2e65236 09ff 416a 8a9b 45b928038400.png>)

***

#### Event-type data - Message click

![Event-type data - Message click](<../../../.gitbook/assets/6e88d8e5 da07 49c5 94d8 b82be83c9e5f.png>)

* Each message open and message click are independent BQ events.
* If you need to retrieve data on message opens and click interactions when pushing messages using the Open API, please make sure to create an event ID.
* In MAAC, different functionalities generate click interaction data. If you use the same UTM, it will result in two separate data entries (with different campaign names).

***

#### Event-type data - Prize send

![Event-type data - Prize send](<../../../.gitbook/assets/8b0723e8 ad90 4cd1 9ed5 2d6a622646f8.png>)

***

#### Event-type data - Prize send (alternate view)

![Event-type data - Prize send](<../../../.gitbook/assets/4e9a40a8 5352 4b68 9ba0 d03e0baa1dd8.png>)

***

#### Event-type data - Prize redeem

![Event-type data - Prize redeem](<../../../.gitbook/assets/0e5c80fe 7522 4b39 9449 5d0697d6fa8a.png>)

***

#### Event-type data - Contact Profile Customer ID update

![Event-type data - Contact Profile Customer ID update](<../../../.gitbook/assets/63e0b676 4f2e 4661 82b6 a3e0ed03ee57.png>)

***

#### Event-type data - Contact tag add

![Event-type data - Contact tag add](<../../../.gitbook/assets/168f4518 8040 4a36 bc91 df93215270db.png>)

***

#### Event-type data - Contact tag remove

![Event-type data - Contact tag remove](<../../../.gitbook/assets/077ec403 f562 433b 9bac 8a5cb150c440.png>)

{% hint style="info" %}
The engagement history data is collected after the connector is established.
{% endhint %}

***

Created with https://tango.us/?utm\_source=magicCopy\&utm\_medium=magicCopy\&utm\_campaign=workflow%20export%20links

***

Related articles (external links)

* How to share LINE OA platform, LINE Developers, GA(UA) / GA4 access to Crescendo Lab?\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmp1FFgBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlyQwxwFjoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ1L2hjL2VuLXVzL2FydGljbGVzLzgxMTAyNzExNDYzOTMtSG93LXRvLXNoYXJlLUxJTkUtT0EtcGxhdGZvcm0tTElORS1EZXZlbG9wZXJzLUdBLVVBLUdBNC1hY2Nlc3MtdG8tQ3Jlc2NlbmRvLUxhYgY7CFQ6CXJhbmtpBg%3D%3D--1aebdfb17e4ef172c89b59dc383159bb25470f13
* Tutorials｜ MAAC x SurveyCake Form\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkr5rYDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlyQwxwFjoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJGL2hjL2VuLXVzL2FydGljbGVzLzQ0MTM5OTk5NTA3NDUtVHV0b3JpYWxzLU1BQUMteC1TdXJ2ZXlDYWtlLUZvcm0GOwhUOglyYW5raQc%3D--f1db8cc7787f0608926975380eeef6b8a1f0d85f
* Tutorials | Integration of MAAC and CAAC Customer(Contact) Data - Customer data hub\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJk12ZpvEjoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlyQwxwFjoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ1L2hjL2VuLXVzL2FydGljbGVzLzIwMjcwNTQ4NTk2MTIxLVR1dG9yaWFscy1JbnRlZ3JhdGlvbi1vZi1NQUFDLWFuZC1DQUFDLUN1c3RvbWVyLUNvbnRhY3QtRGF0YS1DdXN0b21lci1kYXRhLWh1YgY7CFQ6CXJhbmtpCA%3D%3D--a2186ddee9bdadadabc05019129b68dc62102110
* What is the CTR in Broadcast? Why there is no data?\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkCt4gDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlyQwxwFjoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJXL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMjUxMDc5OTMtV2hhdC1pcy10aGUtQ1RSLWluLUJyb2FkY2FzdC1XaHktdGhlcmUtaXMtbm8tZGF0YQY7CFQ6CXJhbmtpCQ%3D%3D--bd9118a9996dae5c7a28cfc4efe88f7f9b71a182
* Tutorial | CAAC Conduct Conversation and Contact Information\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJn6ysBcBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlyQwxwFjoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJgL2hjL2VuLXVzL2FydGljbGVzLzgwOTQ5NTI5MTM1NjEtVHV0b3JpYWwtQ0FBQy1Db25kdWN0LUNvbnZlcnNhdGlvbi1hbmQtQ29udGFjdC1JbmZvcm1hdGlvbgY7CFQ6CXJhbmtpCg%3D%3D--442583bf389d351b21eec0f4506088bf433f59df
