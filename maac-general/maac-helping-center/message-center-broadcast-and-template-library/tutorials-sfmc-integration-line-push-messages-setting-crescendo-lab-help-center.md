# Tutorials｜SFMC Integration - LINE push messages setting – Crescendo Lab Help Center

**Tutorials｜SFMC Integration - LINE push messages setting**

Creation Date: February 10, 2024\
Created By: Crescender Lab

View most recent version on Tango.us: https://app.tango.us/app/workflow/b05a8599-021f-4edf-8f0a-6f31354c14f1?utm\_source=magicCopy\&utm\_medium=magicCopy\&utm\_campaign=workflow%20export%20links

***

### 💁‍♀️ Advantage

1. Sending PnP/SMS+ messages via SFMC connector
2. Sending LINE Push Messages via SFMC connector
3. Integrating LINE contacts for smoother customization of marketing efforts

### #️⃣ What is Saleforce Marketing Cloud

Salesforce Marketing Cloud is one of the largest providers of marketing cloud services tailored for medium to large enterprises. Essentially, it allows us to understand the functionalities encompassed within a marketing cloud and how it brings value to businesses. In simple terms, the core functionality of Salesforce Marketing Cloud revolves around automating customer journeys. Successful automated journey design can deliver personalized consumer experiences, with the engine behind these automated journeys being cross-channel data integration. Let's delve into how these three components address pain points in brand marketing operations and CRM.

Ref.: https://blog.cresclab.com/zh-tw/salesforce-marketing-cloud

{% hint style="info" %}
Please note that if you intend to utilize SFMC functionalities, ensure that you have requested the following permissions from the Crescendo team:

* OpenAPI Zone 1
* OpenAPI Zone 3
* Webhook Zone 1
* Webhook Zone 2
* SMS+ API
{% endhint %}

***

### ▶️ How to setup MAAC x SFMC Connector

{% stepper %}
{% step %}
### Create Key (Key Management)

{% hint style="warning" %}
Please confirm that you have obtained the following information from the Crescendo team:

* External Key: Required when creating key values.
* Salt: Required when creating key values.
{% endhint %}

Login SFMC and click on Setup

![Login SFMC and click on Setup](<../../../.gitbook/assets/53929e59 e58b 4ed5 b3d3 093872673c7f (1).png>)

Navigate: Setup Home > Data Management > Key Management

![Setup Home > Data Management > Key Management](<../../../.gitbook/assets/684083c4 66eb 4b55 97cb 0a2c774e83c0.png>)

Click on Create

![Click on Create](<../../../.gitbook/assets/b6a8c552 fc22 46ed 9b00 f2a941711984.png>)

Choose Salt, input External Key & Salt, then Save

![Choose Salt > input External Key & Salt > save](<../../../.gitbook/assets/b18a5ab8 3685 4aad a23c 0b632d4a2971.png>)
{% endstep %}

{% step %}
### Message Module (Installed Packages & Components)

{% hint style="warning" %}
Please confirm that you have obtained the following information from the Crescendo team:

* MAAC Line Message Package URL
* MAAC PNP Message Package URL
* MAAC Message Open Split Package URL
* MAAC Split Package URL
{% endhint %}

Go to Setup Home > Apps > Installed Packages

![Setup Home > Click on  Apps > Installed Packages](https://images.tango.us/workflows/b05a8599-021f-4edf-8f0a-6f31354c14f1/steps/b4b7e519-ebcb-4387-81cf-6f80cd929a90/dded2f6d-f42f-4917-b331-97de77db8f1c.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.1702\&fp-y=0.5423\&fp-z=2.2211\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&blend-align=bottom\&blend-mode=normal\&blend-x=0\&blend-w=1200\&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n\&mark-x=51\&mark-y=336\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTQlMkMzMjcwRUImdz0zMDEmaD02MiZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

Click New to set up a new package/module

![Click New for setup new module](https://images.tango.us/workflows/b05a8599-021f-4edf-8f0a-6f31354c14f1/steps/e2091bcd-2063-422c-93a1-31a2f186ea76/1a8c3ff7-b2d4-42e4-a6cb-abc3de771d34.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.9657\&fp-y=0.0911\&fp-z=2.9370\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&blend-align=bottom\&blend-mode=normal\&blend-x=0\&blend-w=1200\&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n\&mark-x=1009\&mark-y=143\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTQlMkMzMjcwRUImdz0xMzkmaD04MiZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

Fulfill New Package details and Save:

* Name: customizable for future identification
* Description: optional supplementary info

![Name > You can enter it yourself for future identification purposes. Description > You may input additional supplementary information as needed for future identification. Once you have finished inputting the information > Save](https://images.tango.us/workflows/b05a8599-021f-4edf-8f0a-6f31354c14f1/steps/32ded9dd-7bf4-4440-9521-7d8e0dcafcdc/a9fe7aeb-71dc-4c1d-99d0-e649378648fc.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.5797\&fp-y=0.5145\&fp-z=1.9237\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&blend-align=bottom\&blend-mode=normal\&blend-x=0\&blend-w=1200\&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTQlMkMzMjcwRUImdz04NDAmaD0zNjImZml0PWNyb3AmY29ybmVyLXJhZGl1cz0xMA%3D%3D)

On the module page, click "Add Component" to add components. You need to create four components total for the LINE Push Message module—repeat the following steps for each component.

![On the module page > click on "Add Component" > Add Component](https://images.tango.us/workflows/b05a8599-021f-4edf-8f0a-6f31354c14f1/steps/391b5a9e-ffd3-44fd-9fc9-40ce945e47f5/e62b9807-c776-4baf-93fb-80a4f5977bcb.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.6125\&fp-y=0.6336\&fp-z=1.6368\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&blend-align=bottom\&blend-mode=normal\&blend-x=0\&blend-w=1200\&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n\&mark-x=444\&mark-y=539\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTQlMkMzMjcwRUImdz0xNTUmaD00NiZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

Choose Journey Builder Activity > Next

![Choose Journey Builder Activity > Next 進入下一步](https://images.tango.us/workflows/b05a8599-021f-4edf-8f0a-6f31354c14f1/steps/e84921cb-6901-4a96-ac40-eaa85b43dab6/dba2351a-cf96-46fc-84d2-ada2118ae30c.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.5730\&fp-y=0.5381\&fp-z=2.0000\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&blend-align=bottom\&blend-mode=normal\&blend-x=0\&blend-w=1200\&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n\&mark-x=161\&mark-y=359\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTQlMkMzMjcwRUImdz04NzMmaD00OSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

Input the component information:

* Name: customizable
* Description: customizable
* Category: select based on module
* Endpoint URL: enter the corresponding Message Package URL

![Input the information Name: Customizable for ease of identification during operation Description: Customizable description text for easier differentiation Category: Select based on the current module configuration Endpoint URL: Enter the corresponding Message Package URL](https://images.tango.us/workflows/b05a8599-021f-4edf-8f0a-6f31354c14f1/steps/143c8c84-5c59-492e-99d8-28b9dfcf5d4f/f0df4b24-4744-4184-ab24-b1ea2f279e44.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.5906\&fp-y=0.5089\&fp-z=2.0000\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&blend-align=bottom\&blend-mode=normal\&blend-x=0\&blend-w=1200\&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n\&mark-x=116\&mark-y=9\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTQlMkMzMjcwRUImdz04ODAmaD03MjEmZml0PWNyb3AmY29ybmVyLXJhZGl1cz0xMA%3D%3D)

Required Category types for each module:

* MAAC Line Message Package -> Category: Message
* MAAC PNP Message Package -> Category: Message
* MAAC Message Open Split Package -> Category: Flow control
* MAAC Split Package -> Category: Flow control
{% endstep %}

{% step %}
### How to setup LINE Push Messages in SFMC Journey

Click on Journey Builder

![Click on Journey Builder](https://images.tango.us/workflows/b05a8599-021f-4edf-8f0a-6f31354c14f1/steps/1e7c3dee-46e7-444c-a790-c587e2bb4da0/34ef1982-747f-4fba-b5ce-c56367aab36e.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.5935\&fp-y=0.2893\&fp-z=2.0672\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&blend-align=bottom\&blend-mode=normal\&blend-x=0\&blend-w=1200\&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n\&mark-x=372\&mark-y=382\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkMzMjcwRUImdz00NTYmaD02NyZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

In Journey Builder, create a New Journey

![In Journey Builder > Create New Journey](https://images.tango.us/workflows/b05a8599-4da9-486b-b8d7-43b629ac9441/steps/34842fa5-4da9-486b-b8d7-43b629ac9441/5868bbc8-22e9-43e0-a91d-ab621f9f4dec.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.7445\&fp-y=0.2742\&fp-z=1.8412\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&blend-align=bottom\&blend-mode=normal\&blend-x=0\&blend-w=1200\&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n\&mark-x=825\&mark-y=184\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkMzMjcwRUImdz0zMzkmaD0xMDEmZml0PWNyb3AmY29ybmVyLXJhZGl1cz0xMA%3D%3D)

Click on Multi-Step Journey > Create

![Click on Multi-Step Journey > Create](https://images.tango.us/workflows/b05a8599-021f-4edf-8f0a-6f31354c14f1/steps/90a9aacc-204b-4d37-b22c-64742e5009dd/ea80c3c6-fc3d-48a0-9cf1-1466374f586a.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.5000\&fp-y=0.5000\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&blend-align=bottom\&blend-mode=normal\&blend-x=0\&blend-w=1200\&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n\&mark-x=21\&mark-y=252\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTQlMkMzMjcwRUImdz01MTImaD0xMTYmZml0PWNyb3AmY29ybmVyLXJhZGl1cz0xMA%3D%3D)

For Journey Builder message activities, refer to: https://help.salesforce.com/s/articleView?id=sf.mc\_jb\_message\_activities.htm\&type=5
{% endstep %}

{% step %}
### Journey Builder — Add & Configure MAAC Message Node

Pull the MAAC Message icon into a node

![Pull MAAC Massage icon into node](https://images.tango.us/workflows/b05a8599-021f-4edf-8f0a-6f31354c14f1/steps/93a29f37-862b-4ab3-83fa-3dcfe5a59a3e/f0ed4356-63c6-4b8c-8eba-a6629d506000.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.5000\&fp-y=0.5000\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&blend-align=bottom\&blend-mode=normal\&blend-x=0\&blend-w=1200\&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n\&mark-x=763\&mark-y=237\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTMlMkMzMjcwRUImdz03MCZoPTcwJmZpdD1jcm9wJmNvcm5lci1yYWRpdXM9MTA%3D)

You may change the node name for future identification purposes

![You may change the name of node for future identification purposes](https://images.tango.us/workflows/b05a8599-021f-4edf-8f0a-6f31354c14f1/steps/726ee366-1fc5-48ce-9d1e-e021359da785/1539c8be-14a4-47aa-9c8d-60a8414ef859.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.6606\&fp-y=0.3333\&fp-z=2.5718\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&blend-align=bottom\&blend-mode=normal\&blend-x=0\&blend-w=1200\&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n\&mark-x=448\&mark-y=438\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTQlMkMzMjcwRUImdz0zMDUmaD0xMTMmZml0PWNyb3AmY29ybmVyLXJhZGl1cz0xMA%3D%3D)

SFMC journey builder — Set message node name:

* In each message node of SFMC Journey Builder, you can fill in a message event. If multiple nodes select the same event, you can attribute these nodes together to see the total effect of this event.
* Message template is a message template that has been created on MAAC. (Tutorials｜Template library: https://crescendolab.zendesk.com/hc/en-us/search/click?data=BAh7DjoHaWRsKwgZA%2FOHAwQ6D2FjY291bnRfaWRpA4S4sDoJdHlwZUkiDGFydGljbGUGOgZFVDoIdXJsSSJgaHR0cHM6Ly9jcmVzY2VuZG9sYWIuemVuZGVzay5jb20vaGMvZW4tdXMvYXJ0aWNsZXMvNDQxMzIxMjI2MzE5My1UdXRvcmlhbHMtVGVtcGxhdGUtbGlicmFyeQY7CFQ6DnNlYXJjaF9pZEkiKTAxMTM4ZTJkLTRiNDItNDUyZi1iNzk5LWQyYjgzMGFjMTA0YQY7CEY6CXJhbmtpCDoLbG9jYWxlSSIKZW4tdXMGOwhUOgpxdWVyeUkiDXRlbXBsYXRlBjsIVDoScmVzdWx0c19jb3VudGkf--aaf0d2677f29447fbdb29234b357212ce31a22e0)

![SFMC journy builder - 設定訊息節點名稱](<../../../.gitbook/assets/5973457c 2a3c 4363 b0ae 99f3fee755a3.jpeg>)
{% endstep %}

{% step %}
### Insight & Reporting

{% hint style="info" %}
The SFMC backend does not provide visibility into LINE message performance. Review message effectiveness within the MAAC API Broadcast. The API push report is updated daily.
{% endhint %}

Through the MAAC backend's API push feature, you can track the effectiveness of LINE messages.

![Through the MAAC backend's API push feature, you can track the effectiveness of LINE messages.](https://images.tango.us/workflows/b05a8599-021f-4edf-8f0a-6f31354c14f1/steps/a1ed3c2b-8d22-41aa-9ec7-49df79c5480c/653d3766-b6fb-44c8-9af4-9715fe819a26.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.5000\&fp-y=0.5000\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&blend-align=bottom\&blend-mode=normal\&blend-x=0\&blend-w=1200\&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n\&mark-x=3\&mark-y=383\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTQlMkMzMjcwRUImdz0yMDEmaD0zNyZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

Through the API Broadcast, you can confirm the number of clicks on sent messages:

* The name of each row in the API list page corresponds to the event name of each node in the SFMC Journey Builder.
* The Trigger column corresponds to the "send message" in the message template.
* Limitation: If it's "Open website URL" or a URL provided by the API, it won't be accessible.

![Through the API Broadcast, you can confirm the number of clicks on sent messages.](https://images.tango.us/workflows/b05a8599-021f-4edf-8f0a-6f31354c14f1/steps/f78f3872-468d-46ba-bbc2-81a5f3771b50/f20fc179-c4b8-46d3-b807-fc3d7210dee3.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.4872\&fp-y=0.4847\&fp-z=1.0321\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&blend-align=bottom\&blend-mode=normal\&blend-x=0\&blend-w=1200\&blend64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL21hZGUtd2l0aC10YW5nby13YXRlcm1hcmstdjIucG5n\&mark-x=229\&mark-y=131\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXmvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkMzMjcwRUImdz0yMzgmaD05MCZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

{% hint style="info" %}
For detailed message effectiveness beyond the click-through rate in OpenAPI Broadcast reports, consider purchasing the "BigQuery Integrator" from the Crescendo team.

Ref.: https://crescendolab.zendesk.com/hc/en-us/articles/24670497894937-Tutorials-BigQuery-Connector
{% endhint %}
{% endstep %}
{% endstepper %}

***

### Related articles

* Tutorials｜LINE Broadcast — https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBmdF4kDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJm9KJQIGjoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI%2BL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMzE0MzkxMjktVHV0b3JpYWxzLUxJTkUtQnJvYWRjYXN0BjsIVDoJcmFua2kG--00d0c7983dc339744307667f1846dc74d42996fd
* Tutorials｜MAAC Message Module & Template Library — https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkb49oDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJm9KJQIGjoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJUL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQ2MDM3Mjk2ODktVHV0b3JpYWxzLU1BQUMtTWVzc2FnZS1Nb2R1bGUtVGVtcGxhdGUtTGlicmFyeQY7CFQ6CXJhbmtpBw%3D%3D--e74bbe24b289cb0ecd4c7c76d2017420216bb769
* Tutorial｜Personalized Rich Menu — https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBm5rw6DGDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJm9KJQIGjoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJGL2hjL2VuLXVzL2FydGljbGVzLzI2OTUxMTY2MTc5NjA5LVR1dG9yaWFsLVBlcnNvbmFsaXplZC1SaWNoLU1lbnUGOwhUOglyYW5raQg%3D--a3efa73efb2741f2bcfb2a66b07b560a6a0b96a3
* Tutorials｜Template library — https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkD84cDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJm9KJQIGjoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJAL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMTIyNjMxOTMtVHV0b3JpYWxzLVRlbXBsYXRlLWxpYnJhcnkGOwhUOglyYW5raQk%3D--a74595f52d2e3f424581cecfbb6e2d978c7b8e60
* SMS Broadcast — https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJnlSWCkGDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJm9KJQIGjoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI0L2hjL2VuLXVzL2FydGljbGVzLzI3MDk0MjY5MTU4ODA5LVNNUy1Ccm9hZGNhc3QGOwhUOglyYW5raQo%3D--c04fcd57c03e6f2664808b82ab47ff623ed9a5ba
