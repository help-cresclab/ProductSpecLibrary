# Tutorials｜SFMC Integration - Data sync – Crescendo Lab Help Center

Creation Date: February 15, 2024\
Created By: Crescender Lab

## 💁‍♀️ Advantage

* Sending PnP/SMS+ messages via SFMC connector
* Sending LINE Push Messages via SFMC connector
* Integrating LINE contacts for smoother customization of marketing efforts

## #️⃣ What is Saleforce Marketing Cloud

Salesforce Marketing Cloud is one of the largest providers of marketing cloud services tailored for medium to large enterprises. Essentially, it allows us to understand the functionalities encompassed within a marketing cloud and how it brings value to businesses. In simple terms, the core functionality of Salesforce Marketing Cloud revolves around automating customer journeys. Successful automated journey design can deliver personalized consumer experiences, with the engine behind these automated journeys being cross-channel data integration. Let's delve into how these three components address pain points in brand marketing operations and CRM.

Ref.: https://blog.cresclab.com/zh-tw/salesforce-marketing-cloud

ℹ️ Please note that if you intend to utilize SFMC functionalities, ensure that you have requested the following permissions from the Crescendo team:

* OpenAPI Zone 1
* OpenAPI Zone 2
* Webhook Zone 1
* Webhook Zone 2
* SMS+ API

***

## Preparation Steps for Setting up MAAC x SFMC Data Import

{% stepper %}
{% step %}
### SFMC Setup (Account / Security / FTP)

* Click SFMC Setup\
  ![Login SFMC and click on Setup](<../../../.gitbook/assets/53929e59 e58b 4ed5 b3d3 093872673c7f.png>)
* Setup Home > Security > Security Settings\
  ![點擊 Setting > Security > Security Settings](<../../../.gitbook/assets/ca0d1329 f4dc 42a5 8dc2 fc4e4aeba2ff.png>)
* Click Edit\
  ![點擊 Edit](<../../../.gitbook/assets/91ba4364 755d 4cd1 902b 4bf688d2d9b8.png>)

{% hint style="warning" %}
When creating an SFTP account, you'll be required to set a password. It's recommended to set the password expiration to "never expired."

However, if you do need to set an expiration period for the password, please ensure to proactively notify the user to change their password when it expires.
{% endhint %}

* Exclude FTP From Password Expiration > uncheck\
  ![點擊 Exclude FTP From Password Expiration > 取消選取](<../../../.gitbook/assets/ee1eba47 390c 47fd 9898 bb7062a8182a.png>)
* Save the settings\
  ![點擊 Save 儲存設定](<../../../.gitbook/assets/d03508ce 4ee9 4e09 91e5 305486b6aa37.png>)
{% endstep %}

{% step %}
### Create SFTP Account (Administration > Data Management > FTP Accounts)

* Administration > Data Management > FTP Accounts\
  ![點擊 Data Management > FTP Accounts](<../../../.gitbook/assets/b18d2382 4c35 49dc 9c89 5103a31547cc.png>)
* Click Create User\
  ![點擊 Create User](<../../../.gitbook/assets/6102a738 3fd6 4ccc a7bb 98059056320e.png>)
* Setup the password > Next\
  ![設定密碼 > Next](<../../../.gitbook/assets/62ef9142 0949 4d27 aeb1 902fd047baac.png>)
* Choose Password > Next\
  ![點擊 Password > Next](<../../../.gitbook/assets/373b071d f045 4b11 95b6 60175e1ca256.png>)
* Choose Full > Next\
  ![點選 Full > Next](<../../../.gitbook/assets/ee6d95be c6f1 4748 98e4 b070339c0d2f.png>)
* Click Save\
  ![點擊 Save](<../../../.gitbook/assets/d44be296 7676 4e91 a4ca 7fa929ccf38d.png>)
{% endstep %}
{% endstepper %}

***

## Please provide the following details to Crescendo for setting up the SFTP account

* SFTP hostname
* SFTP username
* SFTP password
* SFTP remote file path

***

## Setup Data Extensions - Contact

{% stepper %}
{% step %}
### Access Contact Builder

* Click Audience Builder > Contact Builder\
  ![點擊 Audience Builder > Contact Builder](<../../../.gitbook/assets/74b80e20 41ef 46e4 9b1e ca57f6f6133f.png>)
* Contact Builder > Data Extensions\
  ![進入 Contact Builder 頁面 > 點擊 Data Extensions](<../../../.gitbook/assets/831cca08 8625 4ca7 b8c3 feab5972a63f.png>)
{% endstep %}

{% step %}
### Create Data Extension

* Click Create\
  ![點擊 Create](<../../../.gitbook/assets/e4292425 263c 47f1 9135 ccbe0015a619.png>)
* Fulfill Name & Description > Next\
  ![填入 Name 與 Description 等資訊 > Next](<../../../.gitbook/assets/64a78997 ee49 403d 92b3 8d4b4cfd6f2f.png>)
* The Data Retention Policy steps do not require any changes. Click "Next" to enter Attributes configuration.\
  ![Data Retention Policy 步驟不需變動，請直接點擊 Next 按鈕進入 Attributes 設定](<../../../.gitbook/assets/2fde4516 f017 4f41 a4c2 2bd2650e7cab.png>)
{% endstep %}

{% step %}
### Attributes & Save

* Fill in required data fields (line\_uid can be chosen as the primary key) > Complete > Save\
  ![填入所需之資料欄位 > Complete > Save](<../../../.gitbook/assets/6b757834 3ec2 4d7e 915e 9684dd23ff40.png>)
* MAAC Contact field corresponds to the following name\
  ![MAAC Contact \[聯絡人\] 欄位對應名稱](<../../../.gitbook/assets/0a23d45b 78ea 4455 bae2 c146e7f3f9b4.png>)
* MAAC Tag field corresponds to the following name\
  ![MAAC 標籤 \[Tag\] 欄位對應名稱](<../../../.gitbook/assets/d00ff5c0 18e0 4435 a028 58f8cb09c5cd.png>)
{% endstep %}
{% endstepper %}

***

## Import data - Create Automation - Contact

{% stepper %}
{% step %}
### Open Automation Studio

* Click Journey Builder > Automation Studio\
  ![點擊 Journey Builder > Automation Studio](<../../../.gitbook/assets/4d47257d 09ef 4821 99cd b5154546281c.png>)
{% endstep %}

{% step %}
### Configure File Drop

* Drag the "File Drop" source from the left sidebar to the "STARTING SOURCE" in the middle column. Click the dragged item to configure its settings.\
  ![自左邊側欄拖拉 File Drop 來源到中間欄位 STARTING SOURCE 點擊拖拉過來的項目以進行設定](<../../../.gitbook/assets/e92365e8 9eba 4d47 9815 f568e8aa93f8.png>)
* Click Configure\
  ![點擊 Configure](<../../../.gitbook/assets/6b55e3e4 cca7 4f47 9bc0 6fb1019ca8a2.png>)
* In the popup:
  * Select "Use Filename Pattern"
  * Choose "Begin with"
  * Enter "maac\_members\_" in the text field
  * Select file location as "Import"
  * Click "Done"\
    ![在跳出視窗中左側 radio buttons 選擇 Use Filename Pattern 下拉選單選擇 Begin with 文字例填入 maac\_members\_ 右側檔案位置選 Import  按下 Done 完成設定](<../../../.gitbook/assets/8fa32b8b 5b88 4e9e a990 ca79240dd8bb.png>)
{% endstep %}

{% step %}
### Import File Activity

* Drag the "Import File" component from the left sidebar to the right side. Click "Choose" to open settings.\
  ![從左側邊欄拖拉 Import File 元件到右側 點選 Choose 按鈕開啟設定視窗](<../../../.gitbook/assets/0f29c53a ecc0 4c8f acfc 3e8865fe3bd4.png>)
* If no pre-existing activities at "Choose Import File Activity", click "Create New Import Definition" (top-right) to create a new one.\
  (image reference)
{% endstep %}

{% step %}
### Import Definition Settings

* Fulfill Name, Description (optional) > Next\
  ![填入 Name, Description 等資訊 按下 Next 按鈕到下一階段](<../../../.gitbook/assets/88ae5e88 f51d 4d68 bb27 ba3da6e527e4.png>)
* In "File Naming Pattern" enter:\
  maac\_tags\_xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx.csv\
  (the xxxxxxxx... part is a UUID group; Crescendo team will provide the specific UUID string after setup)\
  ![在 File Naming Pattern 文字欄位輸入 maac\_tags\_xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx.csv 〖xxxxxx 部份為一組 uuid，在 CL 這邊完成設定之後會產生並提供給您 右側〗](<../../../.gitbook/assets/ea1ac368 6e91 476f a02d 3ae247fa82df.png>)
{% endstep %}

{% step %}
### Final Import Settings & Save

* Date Format: Select "Japanese (Japan)" (example becomes "2016/01/19 13:44") > Next\
  ![Date Format 選擇為 \`Japanese (Japan) (其下的 example 會變成 2016/01/19 13:44 的型式) 按下 Next 按鈕到下一階段](<../../../.gitbook/assets/ead643d2 07a9 47f7 95a6 4b40fb2c7f7e.png>)
* Select the previously created member data extension > Next\
  ![選擇先前建立的 member data extension 並點擊 Next 按鈕到下一步驟](<../../../.gitbook/assets/0e5a2468 279b 4c28 a706 c78b3d261d82.png>)
* Data Action: select "overwrite"
* Mapping: choose "Map by Header Row" > Next\
  ![Data Action 選 overwrite Mapping 選擇 Map by Header Row 點擊 Next 按鈕到下一步驟](<../../../.gitbook/assets/454eda11 4fd4 49cb a8d3 12f18f5356b2.png>)
* Review settings and click "Finish" to complete the setup.\
  ![重新 Review 一下是否正確設定 > Finish](<../../../.gitbook/assets/f9649c38 8531 4c8d 9cb0 6c60327b3789.png>)
{% endstep %}

{% step %}
### Save Workflow

* Click "save" to save the workflow\
  ![點擊 Save 儲存此 Workflow](<../../../.gitbook/assets/baba39dd 0081 44af b973 3703981e418c.png>)
{% endstep %}
{% endstepper %}

***

## Related articles

* Tutorials｜SFMC Integration - LINE push messages setting\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJm9KJQIGjoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJniiER3GjoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJcL2hjL2VuLXVzL2FydGljbGVzLzI4NjI0MTQ3NzU4NDg5LVR1dG9yaWFscy1TRk1DLUludGVncmF0aW9uLUxJTkUtcHVzaC1tZXNzYWdlcy1zZXR0aW5nBjsIVDoJcmFua2kG--31dee416179685502bd450672ea1a5db6183ddf1
* Feature Description｜MAAC Contact Import and Update\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBnqhYkDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJniiER3GjoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJYL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMzg2Njc4MDEtRmVhdHVyZS1EZXNjcmlwdGlvbi1NQUFDLUNvbnRhY3QtSW1wb3J0LWFuZC1VcGRhdGUGOwhUOglyYW5raQc%3D--2357fa7de694f5d43ba4c5f98a5bb4265edecf46
* Tutorials｜MAAC x Shopify member data binding integration\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBm84dG5HDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJniiER3GjoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJfL2hjL2VuLXVzL2FydGljbGVzLzMxNTg0NDE1NzU5Mzg1LVR1dG9yaWFscy1NQUFDLXgtU2hvcGlmeS1tZW1iZXItZGF0YS1iaW5kaW5nLWludGVncmF0aW9uBjsIVDoJcmFua2kI--58d2242559e9e472f8dc1bf6183ee60e9e633ba4
* How to share LINE OA platform, LINE Developers, GA(UA) / GA4 access to Crescendo Lab?\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmp1FFgBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJniiER3GjoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ1L2hjL2VuLXVzL2FydGljbGVzLzgxMTAyNzExNDYzOTMtSG93LXRvLXNoYXJlLUxJTkUtT0EtcGxhdGZvcm0tTElORS1EZXZlbG9wZXJzLUdBLVVBLUdBNC1hY2Nlc3MtdG8tQ3Jlc2NlbmRvLUxhYgY7CFQ6CXJhbmtpCQ%3D%3D--a958abcfb4e9b72a8fd2e978e250027030816c95
* Tutorials｜ Reward Points\
  https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBk8iZSxBToYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJniiER3GjoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI9L2hjL2VuLXVzL2FydGljbGVzLzYyNjAyNTkzNzIwNTctVHV0b3JpYWxzLVJld2FyZC1Qb2ludHMGOwhUOglyYW5raQo%3D--1074bfcb85f5bf2e28b5733b847dea67fdaf073a

***

View most recent version on Tango.us: https://app.tango.us/app/workflow/8b9b6fd7-8143-433d-828b-0cc03a5b588a?utm\_source=magicCopy\&utm\_medium=magicCopy\&utm\_campaign=workflow%20export%20links

(Note: All links and URLs remain unchanged.)
