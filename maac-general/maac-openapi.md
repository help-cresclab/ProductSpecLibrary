---
description: >-
  MAAC OpenAPI REST API docs for MAAC + LINE OA integrations. Covers auth, rate
  limits, webhook events, contacts, tags, segments, broadcast messaging, and
  SMS+.
---

# MAAC OpenAPI

## MAAC OpenAPI（MAAC Open API）REST API 文件

MAAC OpenAPI 是 Crescendo Lab MAAC 的官方 **REST API**（JSON / UTF-8）。 你可以用它串接 **LINE 官方帳號（LINE Official Account）** 與你的 **CRM/CDP/EC** 系統。 常見用途包含 **聯絡人（Contacts）管理**、**標籤（Tags）**、**受眾分眾（Audience segments）**、**訊息推播（Broadcast / Push / Multicast）**、**簡訊+（SMS+ / PNP）** 與 **Webhook 事件訂閱**。

{% hint style="info" %}
這是技術文件。若你是行銷或客服同仁，請改看 [教學手冊](https://reurl.cc/v5xggo)。
{% endhint %}

如有任何 OpenAPI / MAAC API 串接問題，請聯繫 [customer-supoort@cresclab.com](mailto:customer-supoort@cresclab.com)。 信件主旨請附上「MAAC OpenAPI」。

English version: [MAAC OpenAPI (English)](https://cresclaben.docs.apiary.io/)

### 快速導覽

* [目的與常見整合情境](maac-openapi.md#目的)
* [注意事項（HTTPS、Base URL、Server-to-server）](maac-openapi.md#注意事項)
* [API 說明（REST、JSON、Authorization header）](maac-openapi.md#api-說明)
* [流量限制（MAAC / LINE rate limit）](maac-openapi.md#流量限制)
* [Webhook（事件訂閱、簽章驗證、重試機制）](maac-openapi.md#webhook)
* [常見問題（啟用、Access token、收費）](maac-openapi.md#常見問題)

### 目的

***

提供使用 MAAC 的官方帳號接入 MAAC OpenAPI，可透過 API 存取與操作以下能力：

* 聯絡人（Contacts）資料查詢、更新、匯入
* 標籤（Tags）建立、查詢、貼標 / 移除
* 受眾分眾（Audience / Segment）建立、查詢、名單匯出
* 訊息推播（Broadcast / Push / Multicast / Enhanced Multicast）
* Webhook 事件訂閱與資料同步（含簽章驗證與重試策略）

目標是讓你能自主開發，串接第三方平台，完成自動化行銷與 CRM 資料同步。

### 注意事項

* API 串接時，請勿使用 `http`，請使用 `https`，以免造成資料傳輸不安全。
* 正式環境下，請使用 `https://api.cresclab.com`，並且串接須為 Server-to-server 的資料串接。
* 若您使用的是位在日本區域的 MAAC，請使用 `https://api.jp.cresclab.com` 作為 API URL

### API 說明

***

#### 格式

MAAC OpenAPI 使用 REST API 形式、JSON 格式、UTF-8 編碼。

#### 請求表頭

呼叫 MAAC OpenAPI 時，需於 HTTP 表頭中帶入 Authorization 參數，使可執行請求動作。

| Request header | Description             |
| -------------- | ----------------------- |
| Authorization  | Bearer `{Access token}` |

#### 流量限制

**MAAC流量限制**

MAAC Server 會依據官方帳號對個別 API 進行呼叫次數限流，詳細 API 上限，列於下表。

| API                              | 速度限制  |
| -------------------------------- | ----- |
| 匯入聯絡人                            | 15/m  |
| 訊息推播 - 單則(Push)                  | 170/s |
| 訊息推播 - 群發(Multicast)             | 10/s  |
| 訊息推播 - 增強型群發(Enhanced multicast) | 170/s |
| 簡訊+ 推播 - 單則(Push)                | 170/s |
| 簡訊+ 推播 - 群發(Multicast)           | 10/s  |

**Line流量限制**

Line Server 會根據各官方帳號，對特定 API 設定呼叫次數的限流。該流量會計入所有用途的總使用量，包含 MAAC 產品（例如分眾推播）及其他非 MAAC 的使用情境。詳細的 API 上限列於下表

| API                  | 速度限制   |
| -------------------- | ------ |
| 訊息推播 - 單則(Push)      | 2000/s |
| 訊息推播 - 群發(Multicast) | 200/s  |

#### 狀態代碼

| 代碼  | 說明                                                                                                             |
| --- | -------------------------------------------------------------------------------------------------------------- |
| 200 | `OK` - 成功 (部分創建資源API請求成功時回應狀態代碼為201)                                                                           |
| 201 | `Created` - 成功，且資源已被創建                                                                                         |
| 204 | `No Content` - 成功，沒有資源可被回應                                                                                     |
| 400 | `Bad Request` - 失敗，缺少必須的參數或請求無法被 Server 解析                                                                     |
| 401 | `Unauthorized` - 失敗，對於操作的資源缺乏權限或授權失敗                                                                           |
| 403 | `Forbidden` - 失敗，禁止操作                                                                                          |
| 404 | `Not Found` - 失敗，資源不存在                                                                                         |
| 405 | `Method Not Allowed` - 失敗，請求動作不被許可                                                                             |
| 429 | `Too Many Requests` - 請求數量過多。可能因為超過每個 bot 的[流量限制](maac-openapi.md#流量限制)，或系統正處於高峰流量時段。建議幾秒後重試，並且拉長每個請求之間的發送間隔時間 |

### Webhook

***

#### Webhook 介紹

當您訂閱的相關事件發生時，MAAC 將會透過 Webhook 主動通知您的系統，達到資訊的即時同步。

#### Webhook Headers

* `CrescLab-Idempotency-Key` 辨識每個獨立的 Webhook 事件。
* `CrescLab-Signature` 驗證來自於 MAAC 的 Webhook 事件。

#### 注意事項

* 我們建議以非同步的方式處理事件，以便即時回應 HTTP POST 請求，不會導致後續事件接受上的延遲。
* 您的服務可能會收到不是從 MAAC 平台發送的惡意 HTTP POST 請求。在驗證它們的簽名之前，不要處理任何未經驗證的 Webhook 事件。
* 需確保自身連線的穩定度與流量控管，我方提供重試服務但不協助保存所有 Log 紀錄。

#### Response

您的服務收到 MAAC 平台發送的 HTTP POST 請求後，須回覆 [HTTP 狀態碼 200](https://developer.mozilla.org/zh-TW/docs/Web/HTTP/Status/200)。

#### 重試機制

如果對您的服務的 Webhook POST 收到以下 Responses 時，將會重試該暫時性錯誤的回覆:

* HTTP 408, 429, 及 5xx response codes。
* Socket timeouts 及 TCP 斷線。

我們通過指數輪詢來實作重試，將重試之間的等待時間以指數的形式增加。\
MAAC 將按以下步驟重試:

{% stepper %}
{% step %}
### 第一步

發送 request 至 Webhook endpoint。
{% endstep %}

{% step %}
### 第二步

若該次請求失敗, 等待 1 秒後重試。
{% endstep %}

{% step %}
### 第三步

若該次請求失敗, 等待 2 秒後重試。
{% endstep %}

{% step %}
### 第四步

若該次請求失敗, 等待 4 秒後重試。
{% endstep %}
{% endstepper %}

您可以通過將 `CrescLab-Idempotency-Key` Headers 與之前的事件進行比較來偵測重複的 Webhook 事件。

#### 驗證 Webhook 數位簽章

MAAC 使用 HMAC-SHA256 及 hex digest 編碼對 Webhook 事件進行簽章，方法是在每個事件的 `CrescLab-Signature` 標頭中包含一個簽章。\
這允許您驗證事件是由 MAAC 發送的，而不是由第三方發送的。\
我們提供以下 Python 片段作為參考實現。

在驗證簽章之前，您需要從 [Webhooks 設定後台](https://maac.cresclab.com/webhooks) 中檢索 Webhook endpoint 的 ShareSecret。\
MAAC 為每個 endpoint 生成一個唯一的 ShareSecret。 選擇要為其獲取 ShareSecret 的 endpoint，然後單擊眼睛圖標按鈕以顯示 ShareSecret。

下面舉例說明如何在 Python® 中實現簽章驗證。

```python
import hashlib
import hmac

# Please use row string `r"..."` to present body.
# if you don't use raw string, you need to escape the backslash to present unicode. E.g: do not use `\u65b0`, instead, use escape `\\u65b0`
# In json string, please keep the space after comma and colon. E.g: do not remove spaces {"a":1,"b":2}, instead, keep spaces {"a": 1,"b": 2}

share_secret = "..." # share secret string
header_signature = "..." # CrescLab-Signature in request header
body = r"..." # Request body string (python's raw string).
signature = hmac.new(
 share_secret.encode("utf-8"), body.encode("utf-8"), hashlib.sha256
).hexdigest()
assert hmac.compare_digest(signature, header_signature)
```

### 常見問題

***

怎麼啟用 OpenAPI ?

若您已開通 MAAC 但尚未啟用 OpenAPI ，請洽詢 [Customer support](mailto:customer-supoort@cresclab.com) ，由專人為您服務。

如何取得 Access token ？

若您已開通 MAAC 且已啟用了 OpenAPI，可於 [MAAC](https://maac.cresclab.com/) 後台介面，透過 UI 生成 Access token： API > API token > 點擊「取得token」按鈕。

![後台示意圖](<../.gitbook/assets/OpenAPI issue token.png>)

如果 Access token 遺失?

點擊「產生Token」後自行保存，即可開始使用Open API。如果遺失，請再產生一次。如果為了安全性需要刪除Token，請聯繫漸強實驗室夥伴。

Access token 有使用期限嗎?

使用期限為漸強實驗室與夥伴簽訂的合約期限。

收費標準?

API 收費分類請看說明文件，共有四大類別，每項分類的皆可對應於此文件的逐項API。詳細計價規則根據您的官方帳號購買方案而定，詳情請洽詢 [Customer support](mailto:customer-supoort@cresclab.com)。

### 更新紀錄

***

#### v1.1.0 / 2020.12.17

* 初版

#### v1.1.1 / 2021.04.21

* 修正 API 描述及錯字
* 移除追蹤連結、導流連結無效參數 `event_id`

#### v1.1.2 / 2021.04.27

* 修正 流量限制， `匯入聯絡人` 時間單位 : `1/s` -> `1/m`

#### v1.1.3 / 2021.04.27

* 新增 自訂名單分眾 API

#### v1.1.4 / 2021.06.21

* 新增 `birthday` 欄位至 聯絡人 API

#### v1.1.5 / 2021.09.29

* 修正 List APIs 分頁筆數描述

#### v1.1.6 / 2021.09.30

* 修正 導流連結 API response body

#### v1.1.7 / 2021.11.15

* 新增 範例檔案至自訂名單分眾 API
* 調整 刪除分眾 API example

#### v1.1.8 / 2021.12.07

* 調整 增強型群發聯絡人參數顯示為空值
* 新增 Webhook 及 Events payload

#### v1.1.9 / 2022.01.10

* 移除 Proxy Server 及 Production Server 測試功能
* 新增 OpenAPI 串接注意事項

#### v1.1.10 / 2022.02.11

* 新增 `pnp.status_updated` 訂閱事件至 Webhook 功能

#### v1.1.11 / 2022.04.08

* 修正 `Tag` 相關 API 裡 `available_days` 欄位的描述
* 新增 匯入聯絡人 API 的 rate limit 與 concurrency limit

#### v1.1.12 / 2022.04.28

* 新增 Webhook 訂閱事件 `prize.points_added`

#### v1.1.13 / 2022.05.09

* 新增 Webhook 訂閱事件 `pnp.profile_updated`

#### v1.1.14 / 2022.06.02

* 調整通知型訊息的 API 描述

#### v1.1.15 / 2022.06.15

* 新增 `receipt validated` webhook 裡 `datetime` 欄位的描述

#### v1.1.16 / 2022.06.22

* 更新 `查詢匯入聯絡人狀態` API 描述
* 調整 `匯入聯絡人` API Rate limit

#### v1.1.17 / 2022.07.20

* 更新 `查詢發送狀態` API 描述

#### v1.1.18 / 2022.08.25

* 棄用 `取得訊息主題列表` 與 `取得訊息主題` API 當中的 `archived` 欄位

#### v1.1.19 / 2022.09.01

* 新增 Webhook 訂閱事件 `message.first_open`

#### v1.1.20 / 2022.09.14

* 新增 `取得追蹤成效報表` API 當中的 `opens` 欄位

#### v1.1.21 / 2022.09.16

* 新增 `unique_clicks` 欄位至 追蹤連結 API

#### v1.1.22 / 2022.09.18

* 修正教學手冊連結

#### v1.1.23 / 2022.10.05

* 新增 `unique_clicks` 欄位至訊息追蹤 API

#### v1.1.24 / 2022.10.26

* 新增通知型訊息的 `發送紀錄查詢` API

#### v1.1.25 / 2022.10.31

* 新增 `訊息推播` 中的 **注意事項**
* 新增 `answer_hash` 欄位至 `Webhook` 中的 `SurveyCake Submitted`

#### v1.1.26 / 2022.11.10

* 新增 `sms_blocked` 狀態至通知型訊息 API 以及 webhook
* 新增 `sms_temporary_error` 狀態至通知型訊息 API 以及 webhook
* 新增通知型訊息的 `發送紀錄查詢` API 回傳資料排序資訊

#### v1.1.27 / 2022.11.30

* Add `sms_error_category` 欄位至通知型訊息 API 以及 webhook
* Add `sms_callback_timeout` 狀態至通知型訊息 API 以及 webhook
* 在 `Send message` 部份，新增圖片參數的限制

#### v1.1.28 / 2023.01.03

* 新增 兌換獎項 API - 兌換券(Voucher)的唯一序號類型使用

#### v1.1.29 / 2023.05.05

* 新增 `API說明` 下 `狀態代碼` 429 Too Many Requests 的說明與建議處理方式

#### v1.1.30 / 2023.05.29

* 新增 `訊息` 下的 `查詢發送狀態` 中關於 `fail_info` 的注意事項

#### v1.1.31 / 2023.06.27

* 通知型訊息 API 支援 Line 訊息發送
* 更新通知型訊息 API 以及 webhook 說明文件
* 更名 "通知型訊息" 為 "簡訊+"

#### v1.1.32 / 2023.07.03

* 以 "聯絡人" 來代表 LINE OA 當中的會員

#### v1.1.33 / 2023.07.28

* 更正匯入聯絡人 API 之請求次數限流為 15/m

#### v1.1.34 / 2023.08.22

* 新增更新聯絡人的 `tags` 欄位

#### v1.1.35 / 2023.08.25

* 忽略更新聯絡人的 `tags` 欄位

#### v1.1.36 / 2023.09.12

* 新增 `自訂名單分眾` API 的 CSV 檔案限制

#### v1.1.37 / 2023.10.25

* 新增以電話號碼 `取得聯絡人列表` 時的特殊字元處理說明

#### v1.1.38 / 2023.10.26

* 新增簡訊錯誤類別 "sensitive\_words"

#### v1.1.39 / 2023.12.18

* 在訊息推播 API 範例中加入更多對 `event_id` 的說明
* 增加在聯絡人追蹤 API 回傳值中的 `ingestion_timestamp` 欄位
* 在 "取得聯絡人列表" 新增 `tags_detail` 欄位

#### v1.1.40 / 2024.04.29

* 在 "取得聯絡人列表" 新增 `member_id` 查詢參數

#### v1.1.41 / 2024.05.28

* 新增 `display_name` 欄位於聯絡人

#### v1.1.42 / 2024.06.12

* 新增簡訊+ API 的錯誤狀態

#### v1.1.43 / 2024.07.04

* 補充 webhook 簽章驗證流程
* 調整 webhook 重試之間的等待時間為 1, 2, 4 秒

#### v1.1.44 / 2025.01.02

* 補充 enhanced\_multicast 說明

#### v1.1.45 / 2025.01.09

* 大量會員數據導入說明

#### v1.1.46 / 2025.08.26

* 修正 API 文件型別錯誤：line\_uid 從 number 改為 string，tag\_id 從 string 改為 number

#### v1.1.47 / 2025.10.07

* 簡訊+ API 新增功能：whatsapp.template\_data.header.parameters 新增支援多媒體訊息參數

#### v1.1.48 / 2025.11.28

* 簡訊+ API (PNP push) 現在同時支援 E.164 與 SHA256 雜湊電話號碼格式
* SHA256 雜湊電話號碼僅在簡訊+ 範本停用簡訊功能時才可使用
* LINE 訊息僅支援精確比對（E.164 與 SHA256 格式不相容）
* Webhook (pnp.status\_updated, pnp.profile\_updated) 現在支援 SHA256 雜湊電話號碼

## Group 聯絡人

| 欄位                  | 型別     | 說明                                |
| ------------------- | ------ | --------------------------------- |
| line\_uid           | String | 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元      |
| line\_display\_name | String | 聯絡人於LINE官方帳號中自行定義之名稱，長度最長為 255 字元 |
| display\_name       | String | 聯絡人於 MAAC 後台顯示之名稱，長度最長為 255 字元    |
| email               | String | 聯絡人電子郵件信箱位址                       |
| mobile              | String | 聯絡人手機號碼                           |
| customer\_id        | String | 第三方系統之用戶識別碼                       |
| gender              | String | 聯絡人性別（預設係由 MAAC AI 進行預測）          |

`male` :男性

`female`：女性

`unknown`：未知 |birthday| String | 聯絡人生日 (ISO Format) |tags| Array\[String] | 聯絡人於 MAAC 中被貼的所有有效標籤 |status| String | 聯絡人狀態

`follow` : 官方帳號之有效聯絡人

`auth` : 聯絡人已授權官方帳號取得其資訊

### `unfollow` : 聯絡人已封鎖該官方帳號 |updated\_at| String | 聯絡人資料更新時間 |created\_at| String | 聯絡人創建時間 |blocked\_at| String | 聯絡人封鎖時間

### 聯絡人 \[/openapi/v1/member/]

#### 取得聯絡人列表 \[GET /openapi/v1/member/{?line\_uid,email,mobile,customer\_id,status,updated\_at\_min,updated\_at\_max,all\_tag,start}]

取得在 MAAC 中屬於該官方帳號的聯絡人基本資料列表，列表以每300筆聯絡人資料進行分頁。

* 可帶 Query Parameter 來篩選符合條件的聯絡人
* 包含特殊字元或符號的查詢參數應進行編碼
* 將前一頁 response `next` 參數中的 token 帶入 request的 `start` 參數中，以獲取下一分頁之聯絡人資料
* Request (application/json)
  *   Headers

      Authorization: Bearer {Access token}
* Parameters
  * line\_uid : `Uoooxxxoooxxxoooxxxoooxxxoooxx` (optional, string)
  * member\_id : `20240429` (optional, int)
  * email : `demo@cresclab.com` (optional, string)
  * mobile : `%2b886912345678` (optional, string) - 符號 **"+"** 應編碼為 **"%2b"**
  * customer\_id : `1235734897` (optional, string)
  * status : `follow` (optional, string)
  * updated\_at\_min : `2017-05-17` (optional, string) ... 篩選此日期之後有更新資料之聯絡人 **(YYYY-MM-DD)**
  * updated\_at\_max : `2020-05-17` (optional, string) ... 篩選此日期之前有更新資料之聯絡人 **(YYYY-MM-DD)**
  *   all\_tag = 0 (optional, number) ... **0**: 根據上二項參數對聯絡人標籤被貼標籤之時間進行篩選

      **1**: 取得聯絡人全部標籤
  * start : `OwNdFUXTfIyunwhn55vJh4fE0wu13wSPRTCUiaqhN1Nu0vLXHpzatVFtb9ZYKBxwGKoy3jOfvxSzEfOOZnFz5Y%2BKcvexmL39l5xQqQSwtiA%3D`(optional, string)- 下一分頁之識別碼，會回覆於前一分頁之`next`參數
*   Response 200 (application/json)

    * Attributes (object)
      * `results` (array) - 聯絡人資料陣列
      * (object)
        * `line_uid` (string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
        * `line_display_name` (string) - 聯絡人於LINE官方帳號中自行定義之名稱，長度最長為 255 字元
        * `display_name` (string) - 聯絡人於 MAAC 後台顯示之名稱，長度最長為 255 字元
        * `email` (string) - 聯絡人電子郵件信箱位址
        * `mobile` (string) - 聯絡人手機號碼
        * `customer_id` (string) - 第三方系統之用戶識別碼
        * `gender` (string) - 聯絡人性別
        * `birthday` (string) - 聯絡人生日 (ISO Format)
        * `tags` (array) - 聯絡人於 MAAC 中被貼的所有有效標籤陣列
          * (string) - 標籤名稱
        * `tags_detail` (array) - 聯絡人於 MAAC 中被貼的所有有效標籤陣列詳情
          * (object)
            * `name` (string) - 標籤名稱
            * `tagged_at` (string) - 標籤第一次標記到該聯絡人時的時間戳
        * `status` (string) - 聯絡人狀態
        * `updated_at` (string) - 聯絡人資料更新時間
        * `created_at` (string) - 聯絡人創建時間
        * `blocked_at` (string) - 聯絡人封鎖時間
        * `next` (string) - 下一分頁的page token
    * Body

    { "results": \[ { "line\_uid": "U353dc4b8ea88acaa8663c6cd9a4f4000", "line\_display\_name": "Alan Mathison Turing", "display\_name": "Alan Mathison Turing", "email": "alan@example.com", "mobile": "+886987654321", "customer\_id": "1235734897", "gender": "male", "birthday": "2017-05-17", "tags": \[ "tag1" ], "tags\_detail": \[ { "name": "tag1", "tagged\_at": "2020-01-13T18:58:21.604283+08:00" } ], "status": "follow", "updated\_at": "2020-01-13T18:58:21.604283+08:00", "created\_at": "2020-01-13T18:48:23.604283+08:00", "blocked\_at": "2020-01-13T18:48:23.604283+08:00" } ], "next": "OwNdFUXTfIyunwhn55vJh4fE0wu13wSPRTCUiaqhN1Nu0vLXHpzatVFtb9ZYKBxwGKoy3jOfvxSzEfOOZnFz5Y%2BKcvexmL39l5xQqQSwtiA%3D" }

#### 更新聯絡人 \[PATCH /openapi/v1/member/{line\_uid}/]

更新您在 MAAC 中的聯絡人基本資料

* 可透過此 API 更新 `customer_id` 來完成聯絡人資料綁定，並更新 MAAC 中的聯絡人資料
* 若需解綁可藉由存入 `null` 至 `customer_id` 來實現
* Parameters
  * line\_uid (required, string, `U21d78de43c3ce40fbcbc5c4ce6dfe0b0`)
*   Request (application/json)

    * Attributes (object)
      * `display_name` (optional, string) - 聯絡人於 MAAC 後台顯示之名稱
      * `customer_id` (optional, string) - 第三方系統之用戶識別碼
      * `email` (optional, string) - 聯絡人電子郵件信箱位址
      * `mobile` (optional, string) - 聯絡人手機號碼，，請使用 E.164 格式，如為 09XX，則會依據渠道地區設定自動轉換為 E.164 格式，如為 09XX，則會依據渠道地區設定自動轉換為 E.164 格式
      * `gender` (optional, string) - 聯絡人性別 選項: **male**, **female**, **unknown**
      * `birthday` (optional, string) - 聯絡人生日 (ISO Format)
    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "display\_name": "Alan Mathison Turing", "customer\_id": "fake-cid", "email": "example@example.com", "mobile": "+886910123456", "gender": "male", "birthday": "2017-05-17" }
*   Response 200 (application/json)

    * Attributes (object)
      * `line_uid` (string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
      * `line_display_name` (string) - 聯絡人於LINE官方帳號中自行定義之名稱，長度最長為 255 字元
      * `display_name` (string) - 聯絡人於 MAAC 後台顯示之名稱，長度最長為 255 字元
      * `email` (string) - 聯絡人電子郵件信箱位址
      * `mobile` (string) - 聯絡人手機號碼
      * `customer_id` (string) - 第三方系統之用戶識別碼
      * `gender` (string) - 聯絡人性別
      * `birthday` (string) - 聯絡人生日 (ISO Format)
      * `tags` (array) - 聯絡人於 MAAC 中被貼的所有有效標籤陣列
        * (string) - 標籤名稱
      * `status` (string) - 聯絡人狀態
      * `updated_at` (string) - 聯絡人資料更新時間
      * `created_at` (string) - 聯絡人創建時間
      * `blocked_at` (string) - 聯絡人封鎖時間
    * Body

    { "line\_uid": "U353dc4b8ea88acaa8663c6cd9a4f4000", "line\_display\_name": "Alan Mathison Turing", "display\_name": "Alan Mathison Turing", "email": "example@example.com", "mobile": "+886910123456", "customer\_id": "fake-cid", "gender": "male", "birthday": "2017-05-17", "tags": \[ "tag1" ], "tags\_detail": \[ { "name": "tag1", "tagged\_at": "2020-01-13T18:58:21.604283+08:00" } ], "status": "follow", "updated\_at": "2020-01-13T18:48:23.604283+08:00", "created\_at": "2020-01-13T18:48:23.604283+08:00", "blocked\_at": "2020-01-13T18:48:23.604283+08:00" }

#### 匯入聯絡人 \[POST /openapi/v1/member/import/]

如果您有既有聯絡人資料庫，也能透過 MAAC OpenAPI 匯入以整合跨平台的資料。

* 單次請求最多匯入 10000 筆聯絡人資料
* 最大同時請求數量: 1
* 請求次數限流: 15/m
* 單次請求 Body size 最大 10MB
* 針對比對成功的聯絡人，會使用匯入聯絡人資料中提供的非空白 `customer_id`、`line_display_name`、`email`、`mobile`、`gender`、`birthday`覆寫 MAAC 聯絡人資料
* 上述規則不包含 `tags` ，系統僅會為聯絡人貼上新標籤，不會覆寫或移除聯絡人過去已被貼上之標籤
* 由於匯入聯絡人資料需要時間，可藉由`task_id`查詢匯入狀態
* 如果要進行大量的匯入行為，建議可以下面的流程來設計：

{% stepper %}
{% step %}
### 呼叫匯入 API

呼叫 API `匯入聯絡人`，進行第一筆匯入，從 API 回傳值中得到 task ID
{% endstep %}

{% step %}
### 查詢匯入狀態

呼叫 API `查詢匯入聯絡人狀態`，確認任務是否已完成
{% endstep %}

{% step %}
### 已完成時

已完成 → 回到「呼叫匯入 API」繼續下一筆匯入
{% endstep %}

{% step %}
### 尚未完成時

尚未完成 → 等待 1 秒，重複「查詢匯入狀態」與操作
{% endstep %}
{% endstepper %}

*   Request (application/json)

    * Attributes (object)
      * `import_key` (required, string) - 指定用以與 MAAC 資料庫中的聯絡人資料比對的欄位 選項: **line\_uid**, **customer\_id**, **email**, **mobile**
      * data (required, array)
        * (object)
          * `line_uid` (optional, string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
          * `line_display_name` (optional, string) - 聯絡人於LINE官方帳號中自行定義之名稱，長度最長為 255 字元
          * `email` (optional, string) - 聯絡人電子郵件信箱位址
          * `mobile` (optional, string) - 聯絡人手機號碼，請使用 E.164 格式，如為 09XX，則會依據渠道地區設定自動轉換為 E.164 格式
          * `customer_id` (optional, string) - 第三方系統之用戶識別碼
          * `gender` (optional, string) - 聯絡人性別 選項: **male**, **female**
          * `tags` (optional, array) - 對個別聯絡人欲貼上的標籤之標籤名稱陣列
            * (string) - 標籤名稱
          * `birthday` (optional, string) - 聯絡人生日(ISO 8601: YYYY-MM-DD)
      * tags (optional, array) - 對全部匯入聯絡人，統一欲貼上的標籤之標籤名稱陣列
        * (string) - 標籤名稱
    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "import\_key": "line\_uid", "data": \[ { "line\_uid": "U21d78de43c3ce40fbcbc5c4ce6dfe0b0", "line\_display\_name": "test\_member1", "email": "alan@example.com", "mobile": "+886987654321", "customer\_id": "1235734897", "gender": "male", # personal tags "tags": \[ "tag1", "tag2" ] }, { "line\_uid": "U21d78de43c3ce40fbcbc5c4ce6dfe0b1", "line\_display\_name": "test\_member1", "email": "alan@example.com", "mobile": "+886987654321", "customer\_id": "1235734897", "gender": "male", # personal tags "tags": \[ "tag1", "tag3" ] } ], "tags":\["20200101import"] # global tags }
*   Response 200 (application/json)

    * Attributes (object)
      * `id` (number) - 匯入聯絡人之異步 task 識別 id，可以用以查詢匯入進度
      * `result` (string) - 狀態文字說明
    * Body

    { "id": 999, "result": "start importing" }

#### 查詢匯入聯絡人狀態 \[GET /openapi/v1/member/import/{task\_id}/]

藉由 `task_id` 查詢匯入聯絡人運行的狀態，`response code`代表此次查詢成功與否，與 task 是否成功無關。此外，隨著 task 狀態不同可能會有不同的 `response body`。

* Request 匯入聯絡人等待處理中 (application/json)
  *   Headers

      Authorization: Bearer {Access token}
* Parameters
  * task\_id : 1 (required, number)
*   Response 200 (application/json)

    * Attributes (object)
      * `category` (string) - `import_member`
      * `status` (string) - 聯絡人匯入狀態 pending, processing, done
      * `created_at` (string) - 創建時間
      * `updated_at` (string) - 更新時間
    * Body

    { "category": "import\_member", "status": "pending", "created\_at": "2021-04-23T22:34:07.360839+08:00", "updated\_at": "2021-04-23T22:34:07.427273+08:00" }
* Request 匯入聯絡人處理中 (application/json)
  *   Headers

      Authorization: Bearer {Access token}
* Parameters
  * task\_id : 1 (required, number)
*   Response 200 (application/json)

    * Attributes (object)
      * `category` (string) - `import_member`
      * `status` (string) - 聯絡人匯入狀態 pending, processing, done
      * `created_at` (string) - 創建時間
      * `updated_at` (string) - 更新時間
    * Body

    { "category": "import\_member", "status": "processing", "created\_at": "2021-04-23T22:34:07.360839+08:00", "updated\_at": "2021-04-23T22:34:07.427273+08:00" }
* Request 匯入聯絡人已完成 (application/json)
  *   Headers

      Authorization: Bearer {Access token}
*   Response 200 (application/json)

    * Attributes (object)
      * `category` (string) - `import_member`
      * `result` (object) - 匯入成功後的詳細報告
      * `tags` (array)
        * (string) - 標籤名稱
      * `success` (boolean) - 匯入成功與否
      * `total_num` (number) - 匯入用戶數量
      * `created_num` (number) - 創建用戶數量
      * `updated_num` (number) - 更新用戶數量
      * `mismatch_num` (number) - 不存在(已封鎖)之用戶數量
      * `mismatch_export_link` (string) - 不存在(已封鎖)用戶之名單(使用 line\_uid 為比對欄位匯入才會有值)
      * `start_time` (string) - 匯入開始時間
      * `end_time` (string) - 匯入完成時間
      * `status` (string) - 聯絡人匯入狀態 pending, processing, done
      * `created_at` (string) - 創建時間
      * `updated_at` (string) - 更新時間
    * Body

    { "category": "import\_member", "result": { "tags": \[ "testtag" ], "success": true, "end\_time": "2021-04-23T22:33:06.643646+08:00", "total\_num": 2, "start\_time": "2021-04-23T22:33:06.031562+08:00", "created\_num": 0, "updated\_num": 0, "mismatch\_num": 2, "mismatch\_export\_link": "https://storage.googleapis.com/cresclab-maac-production/public/org\_368/export\_member/XXXXXX.csv" }, "status": "done", "created\_at": "2021-04-23T22:33:05.936006+08:00", "updated\_at": "2021-04-23T22:33:06.673536+08:00" }
* Request 匯入聯絡人失敗 (application/json)
  *   Headers

      Authorization: Bearer {Access token}
*   Response 200 (application/json)

    * Attributes (object)
      * `category` (string) - `import_member`
      * `result` (object) - 匯入失敗後的詳細報告
      * `success` (boolean) - 匯入成功與否
      * `blank_error` (number) - 匯入用戶之比對欄位值(i.e., import key)缺值數量
      * `miss_fields` (array) - 缺少的用戶資料欄位
        * (string) - 欄位名稱
      * `gender_error` (number) - 匯入用戶之 gender 欄位值錯誤數量
      * `mobile_error` (number) - 匯入用戶之 mobile 欄位值錯誤數量
      * `birthday_error` (number) - 匯入用戶之 birthday 欄位值錯誤數量
      * `useless_fields` (array) - 多餘的用戶資料欄位
        * (string) - 欄位名稱
      * `duplicate_error` (number) - 匯入用戶之比對欄位值(i.e., import key)重複數量
      * `status` (string) - 聯絡人匯入狀態 pending, processing, done
      * `created_at` (string) - 創建時間
      * `updated_at` (string) - 更新時間
    * Body

    { "category": "import\_member", "result": { "success": false, "blank\_error": 1, "miss\_fields": \[], "gender\_error": 0, "mobile\_error": 0, "birthday\_error": 0, "useless\_fields": \[], "duplicate\_error": 1 }, "status": "done", "created\_at": "2022-06-15T11:23:43.465063+08:00", "updated\_at": "2022-06-15T11:23:43.465086+08:00" }

### 聯絡人追蹤 \[/openapi/v1/behavior/download/]

取得聯絡人透過點擊 MAAC 推播訊息、導流連結、圖文選單中，追蹤連結跳轉至官網後的Google Analytics數據資訊，包含以下行為數據。

#### 網頁瀏覽 \[GET /openapi/v1/behavior/download/{date}/pageview/]

* Parameters
  * date (required, string, `2017-05-17`) ... 日期 (ISO Format)
* Request (application/json)
  *   Headers

      Authorization: Bearer {Access token}
* Response 200 (text/csv)
  *   Headers

      Content-Disposition: attachment; filename={date}\_pageview.csv
  * Attributes (object)
    * csv 欄位說明(object)
      * `line_uid` (string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
      * `utm_campaign` (string) - 於 MAAC 設定欲追蹤的 `utm_campaign`
      * `utm_source` (string) - 於 MAAC 設定欲追蹤的 `utm_source`
      * `utm_medium` (string) - 於 MAAC 設定欲追蹤的 `utm_medium`
      * `utm_content` (string) - 於 MAAC 設定欲追蹤的 `utm_content`
      * `time` (string) - 紀錄時間(ISO Format)
      * `page_path` (string) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:pagePath)
      * `page_title` (string) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:pageTitle)
      * `page_views` (number) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:pageviews)
      * `views_per_session` (number) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:pageviewsPerSession)
      * `entrances` (number) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:entrances)
      * `avg_time_on_page` (number) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:avgTimeOnPage)
      * `exits` (number) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:exits)
      * `ingestion_timestamp` (string)- 資料實際寫入到表中的時間

#### 商品操作 \[GET /openapi/v1/behavior/download/{date}/product/]

* Parameters
  * date (required, string, `2017-05-17`) ... 日期 (ISO Format)
* Request (application/json)
  *   Headers

      Authorization: Bearer {Access token}
* Response 200 (text/csv)
  *   Headers

      Content-Disposition: attachment; filename={date}\_product.csv
  * Attributes (object)
    * csv 欄位說明(object)
      * `line_uid` (string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
      * `utm_campaign` (string) - 於 MAAC 設定欲追蹤的 `utm_campaign`
      * `utm_source` (string) - 於 MAAC 設定欲追蹤的 `utm_source`
      * `utm_medium` (string) - 於 MAAC 設定欲追蹤的 `utm_medium`
      * `utm_content` (string) - 於 MAAC 設定欲追蹤的 `utm_content`
      * `time` (string) - 紀錄時間(ISO Format)
      * `product_name` (string) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:productName)
      * `product_sku` (string) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:productSku)
      * `adds_to_cart` (number) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:productAddsToCart)
      * `removes_from_cart` (number) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:productRemovesFromCart)
      * `item_revenue` (number) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:itemRevenue)
      * `item_quantity` (number) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:itemQuantity)
      * `checkouts` (number) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:productCheckouts)
      * `list_clicks` (number) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:productListClicks)
      * `list_views` (number) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:productListViews)
      * `ingestion_timestamp` (string)- 資料實際寫入到表中的時間

#### 交易行為 \[GET /openapi/v1/behavior/download/{date}/transaction/]

* Parameters
  * date (required, string, `2017-05-17`) ... 日期 (ISO Format)
* Request (application/json)
  *   Headers

      Authorization: Bearer {Access token}
* Response 200 (text/csv)
  *   Headers

      Content-Disposition: attachment; filename={date}\_transaction.csv
  * Attributes (object)
    * csv 欄位說明(object)
      * `line_uid` (string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
      * `utm_campaign` (string) - 於 MAAC 設定欲追蹤的 `utm_campaign`
      * `utm_source` (string) - 於 MAAC 設定欲追蹤的 `utm_source`
      * `utm_medium` (string) - 於 MAAC 設定欲追蹤的 `utm_medium`
      * `utm_content` (string) - 於 MAAC 設定欲追蹤的 `utm_content`
      * `time` (string) - 紀錄時間(ISO Format)
      * `transactions` (number) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:transactions)
      * `revenue` (number) - [說明](https://ga-dev-tools.appspot.com/dimensions-metrics-explorer/#ga:transactionRevenue)
      * `ingestion_timestamp` (string)- 資料實際寫入到表中的時間

## Group 標籤

| 欄位              | 型別     | 說明               |
| --------------- | ------ | ---------------- |
| id              | Number | 標籤於 MAAC 中的識別 id |
| name            | String | 標籤名稱             |
| available\_days | Number | 標籤貼至聯絡人身上後的有效天數  |

### `null` 值表示 tag 永久有效

### 標籤 \[/openapi/v1/tag/]

#### 取得標籤列表 \[GET /openapi/v1/tag/{?name,start}]

取得在 MAAC 中屬於該官方帳號的標籤列表，列表以每300筆標籤進行分頁。

* 可帶 Query Parameter 來篩選符合條件的標籤
* 將前一頁 response `next` 參數中的 token 帶入 request的 `start` 參數中，以獲取下一分頁之標籤
* Request (application/json)
  *   Headers

      Authorization: Bearer {Access token}
* Parameters
  * name : `fake-tag-name` (optional, string)
  * start : `OwNdFUXTfIyunwhn55vJh4fE0wu13wSPRTCUiaqhN1Nu0vLXHpzatVFtb9ZYKBxwGKoy3jOfvxSzEfOOZnFz5Y%2BKcvexmL39l5xQqQSwtiA%3D`(optional, string)- 下一分頁之識別碼，會回覆於前一分頁之`next`參數
*   Response 200 (application/json)

    * Attributes (object)
      * `results` (array) - 標籤陣列
        * (object)
          * `id` (number) - 標籤於 MAAC 中的ID
          * `name` (string) - 標籤名稱
          * `available_days` (number) - 標籤貼至聯絡人身上的有效天數. `null` 值表示 tag 永久有效
      * `next` (string) - 下一分頁的page token
    * Body

    { "results": \[ { "id": 1, "name": "tag 1", "available\_days": null }, {...} ], "next": "OwNdFUXTfIyunwhn55vJh4fE0wu13wSPRTCUiaqhN1Nu0vLXHpzatVFtb9ZYKBxwGKoy3jOfvxSzEfOOZnFz5Y%2BKcvexmL39l5xQqQSwtiA%3D" }

#### 取得標籤 \[GET /openapi/v1/tag/{tag\_id}/]

* Parameters
  * tag\_id: `1` (required, number)
* Request (application/json)
  *   Headers

      Authorization: Bearer {Access token}
*   Response 200 (application/json)

    * Attributes (object)
      * `id` (number) - 標籤於 MAAC 中的ID
      * `name` (string) - 標籤名稱
      * `available_days` (number) - 標籤貼至聯絡人身上的有效天數. `null` 值表示 tag 永久有效
    * Body

    { "id": 1, "name": "fake-tag-name", "available\_days": 100 }

#### 建立標籤 \[POST]

*   Request (application/json)

    * Attributes (object)
      * `name` (required, string) - 標籤名稱
      * `available_days` (optional, number) - 標籤貼至聯絡人身上後的有效天數. 用 `null` 值表示永久有效的標籤
    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "name": "fake-tag-name", "available\_days": 100 }
*   Response 201 (application/json)

    * Attributes (object)
      * `id` (number) - 標籤於 MAAC 中的ID
      * `name` (string) - 標籤名稱
      * `available_days` (number) - 標籤貼至聯絡人身上的有效天數. `null` 值表示 tag 永久有效
    * Body

    { "id": 1, "name": "fake-tag-name", "available\_days": 100 }

### 聯絡人vs標籤 \[/openapi/v1/taglinemember/]

為聯絡人貼上新的標籤或移除已被貼的標籤。

#### 聯絡人貼標籤 \[POST]

*   Request (application/json)

    * Attributes (object)
      * `tag_id` (required, number) - 標籤於 MAAC 中的ID
      * `line_uid` (optional, string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "tag\_id": 1, "line\_uid": "U353dc4b8ea88acaa8663c6cd9a4f4000" }
*   Response 201 (application/json)

    * Attributes (object)
      * `tag_id` (number) - 標籤於 MAAC 中的識別 id
      * `line_uid` (string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
      * `created_at` (string) - 標籤被貼至聯絡人身上的時間(ISO Format)
      * `expired_at` (string) - 標籤在該聯絡人身上的有效截止時間(ISO Format)
    * Body

    { "tag\_id": 1, "line\_uid": "U353dc4b8ea88acaa8663c6cd9a4f4000", "created\_at": "2020-12-17T23:00:00+08", "expired\_at": "9999-12-31T23:59:59+08" }

#### 聯絡人移除標籤 \[DELETE]

*   Request (application/json)

    * Attributes (object)
      * `tag_id` (required, number) - 標籤於 MAAC 中的ID
      * `line_uid` (optional, string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "tag\_id": 1, "line\_uid": "U353dc4b8ea88acaa8663c6cd9a4f4000" }
* Response 204

## Group 分眾

| 欄位            | 型別     | 說明   |
| ------------- | ------ | ---- |
| name          | Number | 分眾名稱 |
| description   | String | 分眾簡介 |
| segment\_type | Number | 分眾類別 |

`1`:一般分眾

`2`:自訂名單分眾 |status| Number | 分眾狀態

`1`: 準備中

### `2`: 準備完成 |member\_count| Number | 分眾聯絡人數量 (若 `status` 尚未準備完成，member\_count 將回覆 `-1`) |last\_updated\_time| String | 分眾最近更新時間(ISO Format)

### 分眾 \[/openapi/v1/segment/]

#### 取得分眾列表 \[GET /openapi/v1/segment/{?name,start}]

取得官方帳號在 MAAC 中的分眾列表，列表以每300筆分眾資料進行分頁。

* 一個官方帳號預設上限為30組，如需購買更多組數請聯繫[customer-supoort@cresclab.com](mailto:customer-supoort@cresclab.com)
* 將前一頁 response `next` 參數中的 token 帶入 request的 `start` 參數中，以獲取下一分頁之標籤
* Request (application/json)
  *   Headers

      Authorization: Bearer {Access token}
* Parameters
  * name : `fake-tag-name` (optional, string)
  * start : `OwNdFUXTfIyunwhn55vJh4fE0wu13wSPRTCUiaqhN1Nu0vLXHpzatVFtb9ZYKBxwGKoy3jOfvxSzEfOOZnFz5Y%2BKcvexmL39l5xQqQSwtiA%3D`(optional, string) - 下一分頁之識別碼，會回覆於前一分頁之`next`參數
*   Response 200 (application/json)

    * Attributes (object)
      * `results` (array) - 分眾陣列
        * (object)
          * `id` (number) - 分眾於 MAAC 中的識別 id
          * `name` (string) - 分眾名稱
          * `description` (string) - 分眾簡介
          * `segment_type` (number) - 分眾種類 選項: **一般分眾=1**, **自訂名單分眾=2**
          * `member_count` (number) - 分眾包含聯絡人人數
          * `status` (number) - 分眾狀態 選項: **pending=1**, **ready=2**
          * `last_updated_time` (string) - 分眾最近更新時間(ISO Format)
      * `next` (string) - 下一分頁的page token
    * Body

    { "results": \[ { "id": 1, "name": "tag\_1分眾", "description": "包含有被貼tag\_1標籤的聯絡人", "segment\_type": 1, "member\_count": 100, "status": 2, "last\_updated\_time": "2020-12-17T23:00:00+08" }, {} ], "next": "OwNdFUXTfIyunwhn55vJh4fE0wu13wSPRTCUiaqhN1Nu0vLXHpzatVFtb9ZYKBxwGKoy3jOfvxSzEfOOZnFz5Y%2BKcvexmL39l5xQqQSwtiA%3D" }

#### 取得分眾 \[GET /openapi/v1/segment/{segment\_id}/]

* Parameters
  * segment\_id: `1` (required, number)
* Request (application/json)
  *   Headers

      Authorization: Bearer {Access token}
*   Response 200 (application/json)

    * Attributes (object)
      * `id` (number) - 分眾於 MAAC 中的識別 id
      * `name` (string) - 分眾名稱
      * `description` (string) - 分眾簡介
      * `segment_type` (number) - 分眾種類 選項: **一般分眾=1**, **自訂名單分眾=2**
      * `member_count` (number) - 分眾包含聯絡人人數
      * `status` (number) - 分眾狀態 選項: **pending=1**, **ready=2**
      * `last_updated_time` (string) - 分眾最近更新時間(ISO Format)
    * Body

    { "id": 1, "name": "tag\_1分眾", "description": "包含有被貼tag\_1和tag\_2標籤的聯絡人", "segment\_type": 1, "member\_count": 100, "status": 2, "last\_updated\_time": "2020-12-17T23:00:00+08" }

#### 建立分眾 \[POST]

*   Request (application/json)

    * Attributes (object)
      * `name` (required, string) - 分眾名稱
      * `operator` (optional, string) - 分眾filter間的運算邏輯單元 預設: **AND**
      * `description` (optional, string) - 分眾簡介
      * `tags` (required, array) - 標籤篩選條件陣列
        * (object)
          * `status` (required, string) - 包含或不包含標籤 選項: **with**, **without**
          * `tag_id` (required, number) - 標籤於 MAAC 中的識別 id
    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "name": "tag\_1 & tag\_2", "operator": "AND", "description": "包含有被貼tag\_1和tag\_2標籤的聯絡人", "segment\_type": 1, "tags": \[ { "status": "with", "tag\_id": 1 }, { "status": "with", "tag\_id": 2 } ] }
*   Response 201 (application/json)

    * Attributes (object)
      * `id` (number) - 分眾於 MAAC 中的識別 id
      * `name` (string) - 分眾名稱
      * `description` (string) - 分眾簡介
      * `segment_type` (number) - 分眾種類 選項: **一般分眾=1**, **自訂名單分眾=2**
      * `member_count` (number) - 分眾包含聯絡人人數
      * `status` (number) - 分眾狀態 選項: **pending=1**, **ready=2**
      * `last_updated_time` (string) - 分眾最近更新時間(ISO Format)
    * Body

    { "id": 2, "name": "tag\_1 & tag\_2", "description": "包含有被貼tag\_1和tag\_2標籤的聯絡人", "segment\_type": 1, "member\_count": -1, "status": 1, "last\_updated\_time": none }

#### 建立自訂名單分眾 \[POST /openapi/v1/custom\_segment/]

* 上傳自訂 LINE UID 名單建立分眾，[範例檔案](https://drive.google.com/uc?export=download\&id=12RswSx_9HyBNqs-OEm-O5bZaq1l6aEcb)。
* CSV 支援最大分眾個數: 300,000; CSV 檔案大小上限: 25MB
*   Request (multipart/form-data)

    * Attributes (object)
      * `name` (required, string) - 分眾名稱
      * `description` (optional, string) - 分眾簡介
      * `file` (required, _csv_) - line uid 檔案
    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "name": "crm 行銷分眾名單(2021-05-06)", "description": "crm 行銷分眾名單", "file": **file** }
*   Response 201 (application/json)

    * Attributes (object)
      * `id` (number) - 分眾於 MAAC 中的識別 id
      * `name` (string) - 分眾名稱
      * `description` (string) - 分眾簡介
      * `segment_type` (number) - 分眾種類 選項: **一般分眾=1**, **自訂名單分眾=2**
      * `member_count` (number) - 分眾包含聯絡人人數
      * `status` (number) - 分眾狀態 選項: **pending=1**, **ready=2**
      * `last_updated_time` (string) - 分眾最近更新時間(ISO Format)
    * Body

    { "id": 3, "name": "crm 行銷分眾名單(2021-05-06)", "description": "crm 行銷分眾名單", "segment\_type": 2, "member\_count": -1, "status": 1, "last\_updated\_time": none }

#### 移除分眾 \[DELETE /openapi/v1/segment/{segment\_id}/]

* Parameters
  * segment\_id (required, number, `1`)
* Request (application/json)
  * Attributes (object)
    * `segment_id` (number) - 分眾於 MAAC 中的識別 id
  *   Headers

      Authorization: Bearer {Access token}
* Response 204 (application/json)

#### 更新自訂名單分眾 \[PATCH /openapi/v1/custom\_segment/{segment\_id}/]

* 上傳自訂 LINE UID 名單建立分眾，[範例檔案](https://drive.google.com/uc?export=download\&id=12RswSx_9HyBNqs-OEm-O5bZaq1l6aEcb)。
* CSV 支援最大分眾個數: 300,000; CSV 檔案大小上限: 25MB
* `name`、`description`、`file`三者需至少擇一帶入 Request body。
* Parameters
  * segment\_id (required, number, 3)
*   Request (application/json)

    * Attributes (object)
      * `name` (optional, string) - 分眾名稱
      * `description` (optional, string) - 分眾簡介
      * `file` (optional, _csv_) - line uid 檔案
    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "name": "crm 行銷分眾名單(2021-05-07)", "description": "crm 行銷分眾名單", "file": **file** }
*   Response 200 (application/json)

    * Attributes (object)
      * `id` (number) - 分眾於 MAAC 中的識別 id
      * `name` (string) - 分眾名稱
      * `description` (string) - 分眾簡介
      * `segment_type` (number) - 分眾種類 選項: **一般分眾=1**, **自訂名單分眾=2**
      * `member_count` (number) - 分眾包含聯絡人人數
      * `status` (number) - 分眾狀態 選項: **pending=1**, **ready=2**
      * `last_updated_time` (string) - 分眾最近更新時間(ISO Format)
    * Body

    { "id": 3, "name": "crm 行銷分眾名單(2021-05-07)", "description": "crm 行銷分眾名單", "segment\_type": 2, "member\_count": -1, "status": 1, "last\_updated\_time": none }

#### 取得分眾聯絡人名單 \[GET /openapi/v1/segment/{segment\_id}/members/]

* Parameters
  * segment\_id: 3 (required, number)
* Request (application/json)
  *   Headers

      Authorization: Bearer {Access token}
* Response 200 (text/csv)
  *   Headers

      Content-Disposition: attachment; filename={date}_segment_{segment\_id}\_members.csv
  * Attributes (object)
    * csv 欄位說明(object)
      * `line_uid` (string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元

## Group 訊息

### 訊息範本 \[/openapi/v1/template/{?start}]

發送訊息推播時，需填入欲發送的訊息範本ID，範本需透過MAAC平台的「訊息中心」>「訊息範本庫」中建立。

#### 取得訊息範本列表 \[GET]

* 列表以每300筆訊息範本資料進行分頁
* 將前一頁 response `next` 參數中的 token 帶入 request的 `start` 參數中，以獲取下一分頁之標籤
* Request (application/json)
  *   Headers

      Authorization: Bearer {Access token}
* Parameters
  * start : `OwNdFUXTfIyunwhn55vJh4fE0wu13wSPRTCUiaqhN1Nu0vLXHpzatVFtb9ZYKBxwGKoy3jOfvxSzEfOOZnFz5Y%2BKcvexmL39l5xQqQSwtiA%3D`(optional, string) - 下一分頁之識別碼，會回覆於前一分頁之`next`參數
*   Response 200 (application/json)

    * Attributes (object)
      * `results` (array) - 訊息範本陣列
        * (object)
          * `id` (number) - 訊息範本於 MAAC 中的識別 ID
          * `name` (string) - 訊息範本名稱
          * `parameters` (array) - 訊息範本包含的變數陣列
            * (string) - 變數名稱
      * `next` (string) - 下一分頁的page token
    * Body

    { "results": \[ { "id": 1, "name": "best\_sellers\_recommendation" "parameters": \[ "store\_name", "product\_name", "product\_price" ] }, {} ], "next": "OwNdFUXTfIyunwhn55vJh4fE0wu13wSPRTCUiaqhN1Nu0vLXHpzatVFtb9ZYKBxwGKoy3jOfvxSzEfOOZnFz5Y%2BKcvexmL39l5xQqQSwtiA%3D" }

### 訊息主題 \[/openapi/v1/event/]

發送訊息推播時，若需追蹤訊息成效，需填入發送的訊息所屬的主題ID。

**注意事項**

MAAC 系統會以訊息主題為追蹤成效的對象，使用同一訊息主題推播的訊息，其成效數據會整合在一起

#### 取得訊息主題列表 \[GET /openapi/v1/event/{?name,start}]

* 列表以每300筆訊息範本資料進行分頁
* 將前一頁 response `next` 參數中的 token 帶入 request的 `start` 參數中，以獲取下一分頁之標籤
* Request (application/json)
  *   Headers

      Authorization: Bearer {Access token}
* Parameters
  * name : `到貨通知` (optional, string)
  * start : `OwNdFUXTfIyunwhn55vJh4fE0wu13wSPRTCUiaqhN1Nu0vLXHpzatVFtb9ZYKBxwGKoy3jOfvxSzEfOOZnFz5Y%2BKcvexmL39l5xQqQSwtiA%3D`(optional, string) - 下一分頁之識別碼，會回覆於前一分頁之`next`參數
*   Response 200 (application/json)

    * Attributes (object)
      * `results` (array) - 訊息主題陣列
        * (object)
          * `id` (number) - 訊息主題於 MAAC 中的識別 ID
          * `archived` (boolean) - 此欄位已經被棄用，請勿使用此欄位
          * `name` (string) - 訊息主題名稱
          * `created_at` (string) - 訊息主題創建的時間(ISO Format)
      * `next` (string) - 下一分頁的page token
    * Body

    { "results": \[ { "id": 12, "archived": false, "name": "到貨通知", "created\_at": "2020-05-27T17:48:56.042752+08:00" }, { "id": 2, "archived": false, "name": "行銷訊息", "created\_at": "2020-05-27T08:00:00+08:00" }, { "id": 1, "archived": false, "name": "一般通知", "created\_at": "2020-05-27T08:00:00+08:00" } ], "next": "OwNdFUXTfIyunwhn55vJh4fE0wu13wSPRTCUiaqhN1Nu0vLXHpzatVFtb9ZYKBxwGKoy3jOfvxSzEfOOZnFz5Y%2BKcvexmL39l5xQqQSwtiA%3D" }

#### 取得訊息主題 \[GET /openapi/v1/event/{event\_id}/]

* Request (application/json)
  *   Headers

      Authorization: Bearer {Access token}
* Parameters
  * event\_id : 1 (required, number)
*   Response 200 (application/json)

    * Attributes (object)
      * `id` (number) - 訊息活動於 MAAC 中的識別 ID
      * `archived` (boolean) - 此欄位已經被棄用，請勿使用此欄位
      * `name` (string) - 訊息活動名稱
      * `created_at` (string) - 訊息活動創建的時間(ISO Format)
    * Body

    { "id": 1, "archived": false, "name": "123", "created\_at": "2020-05-27T08:00:00+08:00" }

#### 建立訊息主題 \[POST]

**🚨 請注意：**\
`event_id` 有數量上的限制，系統上限為 **1,000 個 event\_id**。\
若您遇到錯誤訊息：`The number of events has reached the limit`，請聯繫您的 **Crescendo Lab 服務專員**。

*   Request (application/json)

    * Attributes (object)
      * `name` (required, string) - 訊息活動名稱
    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "name": "12月行銷活動訊息" }
*   Response 201 (application/json)

    * Attributes (object)
      * `id` (number) - 訊息活動於 MAAC 中的識別 id
      * `name` (string) - 訊息活動名稱
    * Body

    { "id": 1, "name": "12月行銷活動訊息" }

### 訊息推播 \[/openapi/v1/direct\_message/]

推播訊息前需要的三個資訊

* template\_id: 透過MAAC前台製作客製化訊息範本，並取得訊息範本id
* event\_id: 透過API 創建訊息主題，並取得主題id

**🚨請注意：如需追蹤成效，請務必建立 event\_id，以確保品牌可完整追蹤相關數據！**

* line\_uid: 欲發送的用戶line\_uid

**注意事項**

* 回覆 status code `200` 時，代表 MAAC 已嘗試將訊息送出並產生發送紀錄，但 LINE 不一定將訊息成功送出，詳細資訊請見 `response` payload 中的 `detail`。
* 提供訊息範本變數值時，若值為圖檔網址，該網址需為圖檔副檔名結尾，例如: `.jpg`, `.png`, `.jpeg` 等，否則此圖片將無法於使用者的某些電腦版本 LINE 上正常顯示，手機版 LINE 不受此限制。
*   若訊息範本變數值為圖檔網址時，該圖片必須遵守以下限制:

    **圖片格式**: JPEG or PNG

    **圖片長寬比**: 1:1

    **圖片大小**: 小於 4096x4096

    **檔案大小**: 小於 1MB
* Enhanced Multicast API 發送之訊息不支援個人化追蹤，發送之訊息不會有開封以及點擊的追蹤數據。

#### 單則 (Push) \[POST /openapi/v1/direct\_message/push/]

適用於對單一用戶推播訊息。

* **注意事項**
  * MAAC 系統會以訊息主題為追蹤成效的對象，若希望追蹤訊息推播成效，請求時請填入`event_id`
  * 系統會即時推播訊息，並將狀態即時回覆
  * 訊息推播 API 回覆中的`result`有兩種可能型態(`string`, `object`)，不同型態詳見右側範例
  * 此 API 請求會被納入 LINE Push API 的流量限制，請參考[Line流量限制](maac-openapi.md#Line流量限制)
*   Request (application/json)

    * Attributes (object)
      * `template_id` (required, number) - 訊息範本ID
      * `data` (required, object) - 推播訊息設定
      * `line_uid` (required, string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
      * `PARAM_1` (optional, string) - 訊息範本中的變數：名稱vs數值
      * `PARAM_2` (optional, string) - 訊息範本中的變數：名稱vs數值
      * `event_id` (optional, number) - 訊息主題ID，若希望追蹤訊息推播成效，則此欄位必填
    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "template\_id": 45629, "event\_id": 346, "data": { "line\_uid":"U1348y18439jefidsgjf924r2", "parameter1": "hello", "parameter2": "world" } }
*   Response 200 (application/json)

    * Attributes (object)
      * `id` (number) - 訊息推播ID
      * `event_id` (number) - 訊息主題ID
      * `result` (string) - 訊息推播狀態 選項: **success**, **timeout**, **error**
    * Body

    { "id": 1342, "event": "cart retarget", "result": "success" }
*   Response 200 (application/json) (錯誤範例)

    * Attributes (object)
      * `id` (number) - 訊息推播ID
      * `event_id` (number) - 訊息主題ID
      * `result` (object) - 訊息推播狀態
        * `message` (string) - LINE 回覆的錯誤原因
        * `details` (array) - 錯誤原因
          * (object)
            * `message` (string) - 錯誤細節
            * `property` (string) - 錯誤屬性
    * Body

    { "id": 1342, "event": "cart retarget", "result": { "message": "The request body has 1 error(s)", "details": \[ { "message": "Must be one of the following values: \[text, image, video, audio, location, sticker, template, imagemap, flex]", "property": "messages\[0].type" } ] } }

#### 群發 (Multicast) \[POST /openapi/v1/direct\_message/multicast/]

適用於單次推播不同訊息給少量用戶，單次請求最多推播 150 位聯絡人。(每一位用戶的訊息變數設定獨立)

* **注意事項**
  * MAAC 系統會以訊息主題為追蹤成效的對象，若希望追蹤訊息推播成效，請求時請填入`event_id`
  * 系統會採用異步推播訊息，故 API 回覆當下狀態為 `pending`，若需查詢推播狀態可使用[查詢發送狀態](maac-openapi.md#查詢發送狀態)查詢
  * 單次請求最多推播 150 位聯絡人
  * 此 API 請求會被納入 LINE Multicast API 的流量限制，請參考[Line流量限制](maac-openapi.md#Line流量限制)
*   Request (application/json)

    * Attributes (object)
      * `template_id` (required, number) - 訊息範本ID
      * `data` (required, array) - 推播訊息設定陣列
        * (object)
          * `line_uid` (required, string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
          * `PARAM_1` (optional, string) - 訊息範本中的變數：名稱vs數值
          * `PARAM_2` (optional, string) - 訊息範本中的變數：名稱vs數值
          * `event_id` (optional, number) - 訊息主題ID，若希望追蹤訊息推播成效，則此欄位必填
    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "template\_id": 45629, "event\_id": 346, "data": \[ { "line\_uid":"U1348y18439jefidsgjf924r2", "parameter1": "hello", "parameter2": "world" }, { "line\_uid":"Uofkowekgowrpgwrkpglpwlpe", "parameter1": "cresclab", "parameter2": "api" } ] }
*   Response 200 (application/json)

    * Attributes (object)
      * `id` (number) - 訊息推播ID
      * `result` (string) - 訊息推播狀態
    * Body

    { "id": 1342, "result": "pending" }

#### 增強型群發 (Enhance multicast) \[POST /openapi/v1/direct\_message/enhanced\_multicast/]

適用於單次推播相同訊息大量用戶，單次請求最多推播 500 位聯絡人。

* **注意事項**
  * 與一般群發不同，每一位用戶必須使用同一組訊息變數設定
  * MAAC 系統會以訊息主題為追蹤成效的對象，若希望追蹤訊息推播成效，請求時請填入`event_id`
  * 系統會採用異步推播訊息，故 API 回覆當下狀態為 `pending`，若需查詢推播狀態可使用[查詢發送狀態](maac-openapi.md#查詢發送狀態)查詢
  * 單次請求最多推播 500 位聯絡人
  * 請注意：訊息範本中使用的聯絡人參數不適用增強型群發，將一律顯示為空值
  * 請注意：個人化訊息如獎項無法在此 API 使用，請用單則訊息或群發訊息發送。
  * 此 API 請求會被納入 LINE Multicast API 的流量限制，請參考[Line流量限制](maac-openapi.md#Line流量限制)
  * 此 API 發送之訊息不支援個人化追蹤，發送之訊息不會有開封以及點擊的追蹤數據。
*   Request (application/json)

    * Attributes (object)
      * `template_id` (required, number) - 訊息範本ID
      * `line_uids` (required, array) - 聯絡人於LINE官方帳號中的唯一用戶ID陣列
        * (required, string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
      * `data` (required, object) - 推播訊息設定
      * `PARAM_1` (optional, string) - 訊息範本中的變數：名稱vs數值
      * `PARAM_2` (optional, string) - 訊息範本中的變數：名稱vs數值
      * `event_id` (optional, number) - 訊息主題ID，若希望追蹤訊息推播成效，則此欄位必填
    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "template\_id": 45629, "line\_uids": \[ "U1348y18439jefidsgjf924r2....", "Uofkowekgowrpgwrkpglpwlpe...." ], "data": { "parameter1": "hello", "parameter2": "world" }, "event\_id": 346 }
*   Response 200 (application/json)

    * Attributes (object)
      * `id` (number) - 訊息推播ID
      * `result` (string) - 訊息推播狀態
    * Body

    { "id": 1342, "result": "pending" }

### 訊息狀態 \[/openapi/v1/direct\_message/{direct\_message\_id}/]

#### 查詢發送狀態 \[GET]

用於查詢過去推播的訊息發送狀態，包含: 單則、群發、增強型群發。\
`status` 的欄位值包含以下：`pending`, `sending`, `sent`. 而 `result` 欄位只有當狀態為 `sent` 時才會回傳。

* **注意事項**
  * 回覆 `200` 代表在 MAAC 可查詢到該發送紀錄
  * 若是 `fail_info` 不為空值表示該發送有收到來自 LINE 的錯誤訊息，有較高機率 LINE 端未發送成功。需自行評估是否重新發送。
* Parameters
  * direct\_message\_id: `1` (required, number)
* Request (application/json)
  *   Headers

      Authorization: Bearer {Access token}
*   Response 200 (application/json)

    * Attributes (object)
      * `id` (number) - 推播訊息於 MAAC 中的識別 id
      * `category` (string) - 推播訊息種類
      * `status` (string) - 推播訊息狀態
      * `result` (object) - 發送結果 (此範例為 **multicast** )
      * `sent_time` (string) - 發送時間
      * `to` (object) - 發送對象
        * `line_ids` (array)
          * `line_id` (string)
      * `total_count` (number) - 發送總數
      * `fail_count` (number) - 發送失敗數
      * `fail_info` (array) - 每則失敗訊息的詳細資訊
        * (object)
          * `line_uid` (string) - 發送失敗的 LINE 用戶 ID
          * `mark` (number) - 在原始 push/multicast LINE IDs 陣列中的索引位置 (從 0 開始)
          * `response` (string) - LINE 回傳的錯誤訊息或內部錯誤
    * Body

    { "id": 1, "category": "multicast", "status": "sent", "event\_id": null, "result": { "sent\_time": "2024-01-15T10:30:00+08:00", "to": { "line\_ids": \[ "U11111111111111111111111111111111", "U22222222222222222222222222222222", "U33333333333333333333333333333333" ] }, "total\_count": 5, "fail\_count": 3, "fail\_info": \[ { "line\_uid": "U11111111111111111111111111111111", "mark": 0, "response": "timeout" }, { "line\_uid": "U22222222222222222222222222222222", "mark": 2, "response": "{"message": "Invalid user"}" }, { "line\_uid": "U33333333333333333333333333333333", "mark": 3, "response": "429 Too Many Requests" } ] } }

### 訊息追蹤 \[/openapi/v1/event/{event\_id}/report/{?start\_date,end\_date}]

#### 取得追蹤成效報表 \[GET /openapi/v1/event/{event\_id}/report/{?start\_date,end\_date}】

用於查詢過去推播訊息中的成效報表。

* **注意事項**
  * MAAC 系統會以訊息主題為追蹤成效的對象，若希望取得追蹤訊息推播成效，推播時請填入`event_id`
  * 請求時可設定成效報表計算的起始、截止日期
  * 新欄位 `unique_clicks` 於 2022-10-05 啟用。無資料來源時為空值。
  * Enhanced Multicast API 發送之訊息不支援個人化追蹤，故不會有開封及點擊的數據。
* Request (application/json)
  *   Headers

      Authorization: Bearer {Access token}
* Parameters
  * event\_id : 1 (required, number)
  * start\_date : `2017-05-17` (optional, string) ... 成效的起始日期 **(YYYY-MM-DD)**
  * end\_date : `2020-05-17` (optional, string) ... 成效的截止日期 **(YYYY-MM-DD)**
*   Response 200 (application/json)

    * Attributes (object)
      * `id` (number) - 訊息活動於 MAAC 中的識別 ID
      * `report` (object)
        * `total` (object)
          * `clicks` (number) - 點擊數
          * `unique_clicks` (number, nullable) - 不重複點擊數，無資料來源時為空值
          * `adds_to_cart` (number) - 加入購物車次數
          * `transactions` (number) - 成交次數
          * `transaction_revenue` (number) - 成交金額
          * `opens` (number) - 開封數
        * `urls` (array) - URL 追蹤資料
          * (object)
            * `id` (number) - URL 追蹤 ID
            * `link` (number) - 連結 ID
            * `url` (string) - 追蹤的網址
            * `utm_campaign` (string, nullable) - UTM campaign 參數
            * `utm_source` (string, nullable) - UTM source 參數
            * `utm_medium` (string, nullable) - UTM medium 參數
            * `utm_content` (string, nullable) - UTM content 參數
            * `clicks` (number) - 點擊數
            * `unique_clicks` (number, nullable) - 不重複點擊數
            * `adds_to_cart` (number) - 加入購物車次數
            * `transactions` (number) - 成交次數
            * `transaction_revenue` (number) - 成交金額
            * `tags` (array) - 相關標籤
        * `messages` (array) - 觸發關鍵字追蹤資料
          * (object)
            * `id` (number) - 訊息追蹤 ID
            * `message` (string) - 訊息範本中的觸發關鍵字
            * `clicks` (number) - 點擊數
            * `tags` (array) - 相關標籤
    * Body

    { "id": 1, "report": { "total": { "opens": 1234, "clicks": 567, "unique\_clicks": 432, "adds\_to\_cart": 89, "transactions": 23, "transaction\_revenue": 12500.00 }, "urls": \[ { "id": 1, "link": 101, "url": "https://example.com/product", "utm\_campaign": "summer\_sale", "utm\_source": "line", "utm\_medium": "message", "utm\_content": "banner", "clicks": 150, "unique\_clicks": 120, "adds\_to\_cart": 30, "transactions": 8, "transaction\_revenue": 4500.00, "tags": \["promo", "summer"] } ], "messages": \[ { "id": 1, "message": "Buy now", "clicks": 75, "tags": \["cta", "purchase"] } ] } }

## Group 導流連結

### 導流連結 \[/openapi/v1/deeplink/]

#### 取得導流連結成效報表 \[GET /openapi/v1/deeplink/{?start\_date,end\_date}]

用於查詢過去推播訊息中的成效報表。

* **注意事項**
  * 請求時可設定成效報表計算的起始、截止日期
* Request (application/json)
  *   Headers

      Authorization: Bearer {Access token}
* Parameters
  * start\_date : `2017-05-17` (optional, string) ... 成效的起始日期 **(YYYY-MM-DD)**
  * end\_date : `2020-05-17` (optional, string) ... 成效的截止日期 **(YYYY-MM-DD)**
*   Response 200 (application/json)

    * Attributes (object)
      * `id` (number) - 導流連結於 MAAC 中的識別 ID
      * `name` (string) - 導流連結名稱
      * `description` (string) - 導流連結描述
      * `shorten_url` (string) - 導流連結短連結
      * `created_at` (string) - 導流連結創建的時間(ISO Format)
      * `tags` (array) - 導流連結設定之標籤陣列
        * (string)
      * `report` (object) - 成效報表
        * `click_count` (number) - 點擊數
        * `auth_count` (number) - 授權聯絡人數
        * `new_friend_count` (number) - 新聯絡人數
        * `existing_friend_count` (number) - 舊聯絡人數
        * `unique_auth_count` (number) - 不重複授權聯絡人數
        * `unique_new_friend_count` (number) - 不重複新聯絡人數
        * `unique_existing_friend_count` (number) - 不重複舊聯絡人數
    * Body

    { "id": 1, "name": "deeplink\_1", "description": "1st deeplink", "shorten\_url": "https://maac.io/xxxxx", "created\_at": "2020-07-27T14:52:41.874151+08:00", "tags": \["tag\_1", "tag\_2"], "report": { "click\_count": 0, "auth\_count": 0, "new\_friend\_count": 0, "existing\_friend\_count": 0, "unique\_auth\_count": 0, "unique\_new\_friend\_count": 0, "unique\_existing\_friend\_count": 0 } }

## Group 追蹤連結

### 追蹤連結 \[/openapi/v1/tracelink/]

#### 取得追蹤連結成效報表 \[GET /openapi/v1/tracelink/{?start\_date,end\_date}]

用於查詢過去推播訊息中的成效報表。

* **注意事項**
  * 請求時可設定成效報表計算的起始、截止日期
  * 新欄位 `unique_clicks` 於 2022-09-16 啟用。無資料來源時為空值。
* Request (application/json)
  *   Headers

      Authorization: Bearer {Access token}
* Parameters
  * start\_date : `2017-05-17` (optional, string) ... 成效的起始日期 **(YYYY-MM-DD)**
  * end\_date : `2020-05-17` (optional, string) ... 成效的截止日期 **(YYYY-MM-DD)**
*   Response 200 (application/json)

    * Attributes (object)
      * `id` (number) - 追蹤連結於 MAAC 中的識別 ID
      * `name` (string) - 追蹤連結的名稱
      * `description` (string, nullable) - 追蹤連結的描述，可能為空值
      * `shorten_url` (string) - 追蹤連結的短網址
      * `created_at` (string) - 追蹤連結創建的時間 (ISO 8601 Format)
      * `tag` (array\[string]) - 追蹤連結關聯的標籤列表 (可能為空陣列)
      * `report` (object) - 此訊息活動的成效報告彙總數據
        * `clicks` (number) - 總點擊次數
        * `unique_clicks` (number, nullable) - 不重複點擊次數。無資料來源時為空值 (舊有說明：於 2022-09-16 啟用)
        * `adds_to_cart` (number) - 加入購物車次數
        * `transactions` (number) - 總交易筆數
        * `transaction_revenue` (number) - 總交易金額
      * `utm` (object, nullable) - 此訊息活動關聯的 UTM 參數。若無設定可能不存在或為空物件。
        * `utm_campaign` (string)
        * `utm_source` (string)
        * `utm_medium` (string)
        * `utm_content` (string)
    * Body

    { "id": 388101, "name": "This is for TraceLink", "description": null, "shorten\_url": "https://maac.io/3iuM7", "created\_at": "2025-01-23T17:41:37.142001+08:00", "tag": \[], "report": { "clicks": 5, "unique\_clicks": null, "adds\_to\_cart": 0, "transactions": 0, "transaction\_revenue": 0 }, "utm": { "utm\_campaign": "20241111", "utm\_source": "LINE", "utm\_medium": "offline", "utm\_content": "taipei\_branch" } }

## Group 綁定連結

### 綁定連結 \[/openapi/v1/binding/bindlink/]

#### 生成綁定連結 \[POST]

從 MAAC 後台的左側欄＞訊息中心＞訊息範本庫＞綁定訊息範本中，建立綁定訊息後，即可取得到所建立之範本 ID。

* **注意事項**
  * 聯絡人完成綁定後，若您想更新聯絡人資料，請使用[更新聯絡人](maac-openapi.md#reference/0/0/3)API。
*   Request (application/json)

    * Attributes (object)
      * `bind_link_id` (required, number) - 綁定訊息範本ID
      * `customer_id` (required, string) - 第三方聯絡人系統之用戶識別碼
      * `email` (optional, string) - 聯絡人電子郵件信箱位址
      * `mobile` (optional, string) - 聯絡人手機號碼
      * `bind_once` (optional, boolean) - 若為 true，產生的綁定連結僅能綁定一次。若為 false 或省略，綁定連結可多次綁定（預設行為）
    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "customer\_id": "1235734897", "bind\_link\_id": 1, "bind\_once": false }
*   Response 201 (application/json)

    * Attributes (object)
      * `link` (string) - 綁定連結
      * `is_login` (boolean) - 此 `customer_id` 是否已被綁訂於該官方帳號中的聯絡人身上
      * `line_display_name` (optional, string) - 上述若為 `True`，則回覆綁定該 `customer_id` 的用戶名稱
    * Body

    { "link": "https://maac.io/XXXX", "is\_login": false }

### Callback \[/partner/maac/binding/callback/]

#### Callback \[POST]

當用戶點擊綁定連結並加入官方帳號完成綁定後，MAAC 會透過登錄的 callback endpoint 給予 event 通知。(欲登陸 callback endpoint 請聯繫 [Customer support](mailto:customer-supoort@cresclab.com))

(MAAC OpenAPI 並沒有 `/partner/maac/binding/callback/` 這個 endpoint，請不要用這個做測試，這只是個設計範例，僅供參考)

> **Request**

`POST https://your-api-domain.com/your/callback/endpoint`

> **Headers**

| 欄位     | 數值   |
| ------ | ---- |
| \`\`\` | \`\` |

> **Body**

| 欄位           | 型別     | 說明                           |
| ------------ | ------ | ---------------------------- |
| line\_uid    | String | 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元 |
| customer\_id | String | 第三方系統之用戶識別碼                  |
| email        | String | 聯絡人電子郵件信箱位址                  |
| mobile       | String | 聯絡人手機號碼                      |
| status       | String | 聯絡人狀態                        |

`follow` : 官方帳號之有效聯絡人

`auth` : 聯絡人已授權官方帳號取得其資訊

`unfollow` : 聯絡人已封鎖該官方帳號

*   Request (application/json)

    * Attributes (object)
      * `line_uid` (string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
      * `customer_id` (string) - 第三方系統之用戶識別碼
      * `email` (string) - 聯絡人電子郵件信箱位址
      * `mobile` (string) - 聯絡人手機號碼
      * `status` (string) - 聯絡人狀態
    *   Headers

        x-api-key: api\_key\_here
    * Body

    { "line\_uid": "U12345678901234567890123456789012", "customer\_id": "C123456789", "email": "sample@cresclab.com", "mobile": "0912345678", "status": "follow", }
*   Response 200 (application/json)

    * Body

    {}

## Group 獎項

### 獎項 \[/openapi/v1/prize/]

#### 兌換獎項 \[POST /openapi/v1/prize/{code}/redeem/]

使用唯一序號兌換獎項.

**Notes**

* 目前僅提供兌換券(Voucher)的唯一序號使用。
* 請盡可能**不要同時**按\[兌換按鈕]跟透過POS機掃碼來兌換獎券。

**Parameters**

| 欄位   | 型別         | 特性       | 說明       |
| ---- | ---------- | -------- | -------- |
| code | String(32) | required | 兌換券之唯一序號 |

**Body**

| 欄位           | 型別                  | 特性                 | 說明                                               |
| ------------ | ------------------- | ------------------ | ------------------------------------------------ |
| tags         | Array\[String(255)] | optional           | 聯絡人於 MAAC 中將被貼的標籤名稱列表. 最多標籤數量: 5. 標籤名稱最大長度: 255. |
| customer\_id | String(1024)        | required, nullable | 第三方系統之用戶識別碼                                      |
| mobile       | String(16)          | required, nullable | 聯絡人手機號碼                                          |
| gender       | String              | required, nullable | 聯絡人性別                                            |

`male` :男性

`female`：女性

`unknown`：未知 |store| String(16) | required, nullable | 店家名稱 |revenue| Float | required, nullable | 該次兌換營收

**Response**

```json
{
 "detail":
}
```

| 狀態碼 | detail                      | 說明                          |
| --- | --------------------------- | --------------------------- |
| 201 | Success                     | 成功兌換                        |
| 403 | Token Invalid               | API token缺少或是無效             |
| 404 | Prize Code Does Not Exist   | 找不到獎項                       |
| 404 | Prize Status Expired        | 獎項過期                        |
| 404 | Member Not Found            | 找不到聯絡人資料                    |
| 408 | Prize Redemption Need Retry | 交易失敗 (例如：獎項設定正在修改中), 須重試一次. |
| 409 | Prize Has Been Redeemed     | 獎項已被兌換                      |
| 409 | Prize Is Not Received       | 獎項尚未領取                      |
| 500 | Other errors                | 未知錯誤                        |

* Parameters
  * code: `xxx12345` (optional, string) - 獎項序號最大長度: 32
*   Request (application/json)

    * Attributes (object)
      * `tags` (optional, array\[string]) - 聯絡人於 MAAC 中將被貼的標籤名稱列表. 預設: `[]` (若未給值). 最多標籤數量: 5. 標籤名稱最大長度: 255.
      * `customer_id` (required, string, nullable) - 第三方系統之用戶識別碼 (可為`null`) 最大長度: 1024.
      * `mobile` (required, string, nullable) - 聯絡人手機號碼 (可為`null`) 最大長度: 16.
      * `gender` (required, string, nullable) - 聯絡人性別 (可為`null`) 選項: **male**, **female**, **unknown**
      * `store` (required, string, nullable) - 店家名稱 (可為`null`) 最大長度: 1024.
      * `revenue` (required, number, nullable) - 該次兌換營收 (可為`null`) 預設: `0.0` if `null`.
    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "tags": \["1111 Activity", "1111 Acitivity 2"] "customer\_id": "1235734897", "mobile": "0912345678", "gender": "unknown", "store": "CrescLab", "revenue": 1.0, }
*   Response 201 (application/json)

    * Attributes (object)
      * `detail` (string) - success/error message
    * Body

    { "detail": "Success" }
*   Response 403 (application/json)

    * Body

    { "detail": "Token Invalid" }

## Group 自動回覆

### 自動回覆報表 \[/openapi/v1/auto\_reply/]

#### 搜尋自動回覆報表 \[POST /openapi/v1/auto\_reply/search/]

搜尋並統計自動回覆報表資料，支援時間區間、渠道類型等篩選條件。

**注意事項**

* 單次查詢的日期範圍建議不超過 3 個月，以獲得最佳效能
* 專有名詞說明：
  * `new_friend`: 新聯絡人
  * `original_friend`: 未綁定聯絡人
  * `bound_friend`: 綁定聯絡人

**Request Body**

| 欄位            | 型別      | 特性       | 預設值            | 說明               |
| ------------- | ------- | -------- | -------------- | ---------------- |
| start\_date   | String  | optional | `"2016-01-01"` | 開始日期（YYYY-MM-DD） |
| end\_date     | String  | optional | 今天             | 結束日期（YYYY-MM-DD） |
| channel\_type | String  | optional | `null`         | 渠道類型篩選           |
| offset        | Integer | optional | `0`            | 分頁偏移量            |
| limit         | Integer | optional | `20`           | 每頁筆數（1-20）       |

**欄位詳細說明**

* **start\_date / end\_date**
  * 格式：`YYYY-MM-DD`（例如：`2025-01-15`）
  * 驗證：`start_date` 必須 ≤ `end_date`
  * 用途：用於統計報表的時間範圍
* **channel\_type**
  * 可選值：
    * `line` - LINE 官方帳號
    * `whatsapp` - WhatsApp Business
    * `wccs` - web chat
    * `fb` - Facebook Messenger
    * `ig` - Instagram 訊息
  * 用途：只返回指定渠道類型的自動回覆資料
* **offset / limit**
  * offset：跳過的記錄數（≥ 0）
  * limit：返回的記錄數（1-20）
  * 用途：實現分頁查詢

**Response (200 OK)**

**根層級欄位**

| 欄位      | 型別      | 說明                 |
| ------- | ------- | ------------------ |
| count   | Integer | 符合條件的自動回覆總數(供分頁使用) |
| reports | Array   | 報表統計資料             |

**Report 物件**

| 欄位                        | 型別      | 說明                 |
| ------------------------- | ------- | ------------------ |
| id                        | Integer | 自動回覆 ID            |
| name                      | String  | 自動回覆名稱             |
| created\_at               | String  | 自動回覆建立時間（ISO 8601） |
| start\_date               | String  | 報表開始日期（YYYY-MM-DD） |
| end\_date                 | String  | 報表結束日期（YYYY-MM-DD） |
| total                     | Object  | 總體統計資料             |
| channel\_setting\_reports | Array   | 各渠道的詳細統計           |

**TotalReport 物件（total）**

| 欄位             | 型別      | 說明                     |
| -------------- | ------- | ---------------------- |
| triggers       | Integer | 觸發次數                   |
| replies        | Integer | 回覆次數                   |
| opens          | Integer | 開啟次數                   |
| unique\_opens  | Integer | 不重複開啟次數                |
| clicks         | Integer | 點擊次數                   |
| unique\_clicks | Integer | 不重複點擊次數                |
| click\_rate    | Float   | 點擊率（clicks / triggers） |
| adds\_to\_cart | Integer | 加入購物車次數                |
| orders         | Integer | 訂單數                    |
| revenue        | Float   | 營收金額                   |

**ChannelSettingReport 物件**

| 欄位               | 型別      | 說明                        |
| ---------------- | ------- | ------------------------- |
| id               | Integer | 渠道設定 ID                   |
| channel\_id      | Integer | 渠道（Bot）ID                 |
| channel\_type    | String  | 渠道類型                      |
| channel\_name    | String  | 渠道名稱                      |
| total            | Object  | 該渠道的總體統計（結構同 TotalReport） |
| new\_friend      | Object  | 新聯絡人的統計資料                 |
| original\_friend | Object  | 未綁定聯絡人的統計資料               |
| bound\_friend    | Object  | 綁定聯絡人的統計資料                |

**MessageReport 物件（new\_friend / original\_friend / bound\_friend）**

| 欄位       | 型別     | 說明                           |
| -------- | ------ | ---------------------------- |
| total    | Object | 該類型聯絡人的統計資料（結構同 TotalReport） |
| urls     | Array  | URL 點擊與轉換統計                  |
| messages | Array  | 互動式訊息點擊統計                    |

**UrlMetric 物件（urls 陣列元素）**

| 欄位                   | 型別             | 說明                              |
| -------------------- | -------------- | ------------------------------- |
| id                   | Integer        | 連結 ID                           |
| utm\_campaign        | String         | UTM 追蹤參數 - 活動名稱                 |
| utm\_source          | String         | UTM 追蹤參數 - 來源（如 LINE, WhatsApp） |
| utm\_medium          | String         | UTM 追蹤參數 - 媒介（如 message）        |
| utm\_content         | String         | UTM 追蹤參數 - 內容描述                 |
| clicks               | Integer        | 點擊次數                            |
| adds\_to\_cart       | Integer        | 加入購物車次數                         |
| transactions         | Integer        | 交易次數（訂單數）                       |
| transaction\_revenue | Float          | 交易金額（營收）                        |
| link                 | Integer        | 連結 ID（與 id 相同）                  |
| tags                 | Array\[String] | 標籤列表（用於分類）                      |

**MessageMetric 物件（messages 陣列元素）**

| 欄位      | 型別             | 說明        |
| ------- | -------------- | --------- |
| id      | Integer        | 訊息/按鈕 ID  |
| message | String         | 訊息/按鈕文字內容 |
| tags    | Array\[String] | 相關標籤列表    |
| clicks  | Integer        | 點擊次數      |

**注意事項**

* **`urls` 用途**：追蹤訊息中的外部連結（如產品頁、官網等）成效，包含完整 UTM 參數與轉換數據
* **`messages` 用途**：追蹤互動式訊息元素（如 LINE Quick Reply、Postback Action）的點擊情況
* **轉換追蹤**：`urls` 中的 `adds_to_cart`、`transactions`、`transaction_revenue` 需要整合GA才能取得數據
*   Request (application/json)

    * Attributes (object)
      * `start_date` (optional, string) - 開始日期（YYYY-MM-DD） 預設: `"2016-01-01"`.
      * `end_date` (optional, string) - 結束日期（YYYY-MM-DD） 預設: 今天.
      * `channel_type` (optional, string) - 渠道類型篩選 可選值: `line`, `whatsapp`, `wccs`, `fb`, `ig`.
      * `offset` (optional, number) - 分頁偏移量 預設: `0`. 必須 >= 0.
      * `limit` (optional, number) - 每頁筆數 預設: `20`. 範圍: 1-20.
    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "start\_date": "2025-01-01", "end\_date": "2025-01-07", "channel\_type": "line", "offset": 0, "limit": 10 }
*   Response 200 (application/json)

    * Attributes (object)
      * `count` (number) - 符合條件的自動回覆總數
      * `reports` (array) - 報表統計資料
        * (object)
          * `id` (number) - 自動回覆 ID
          * `name` (string) - 自動回覆名稱
          * `created_at` (string) - 自動回覆建立時間（ISO 8601）
          * `start_date` (string) - 報表開始日期（YYYY-MM-DD）
          * `end_date` (string) - 報表結束日期（YYYY-MM-DD）
          * `total` (object) - 總體統計資料
            * `triggers` (number) - 觸發次數
            * `replies` (number) - 回覆次數
            * `opens` (number) - 開啟次數
            * `unique_opens` (number) - 不重複開啟次數
            * `clicks` (number) - 點擊次數
            * `unique_clicks` (number) - 不重複點擊次數
            * `click_rate` (number) - 點擊率
            * `adds_to_cart` (number) - 加入購物車次數
            * `orders` (number) - 訂單數
            * `revenue` (number) - 營收金額
          * `channel_setting_reports` (array) - 各渠道的詳細統計
            * (object)
              * `id` (number) - 渠道設定 ID
              * `channel_id` (number) - 渠道（Bot）ID
              * `channel_type` (string) - 渠道類型
              * `channel_name` (string) - 渠道名稱
              * `total` (object) - 該渠道的總體統計
                * `triggers` (number) - 觸發次數
                * `replies` (number) - 回覆次數
                * `opens` (number) - 開啟次數
                * `unique_opens` (number) - 不重複開啟次數
                * `clicks` (number) - 點擊次數
                * `unique_clicks` (number) - 不重複點擊次數
                * `click_rate` (number) - 點擊率
                * `adds_to_cart` (number) - 加入購物車次數
                * `orders` (number) - 訂單數
                * `revenue` (number) - 營收金額
              * `new_friend` (object) - 新聯絡人的統計資料
                * `total` (object) - 統計資料（結構同上）
                * `urls` (array) - URL 點擊與轉換統計（結構同 new\_friend.urls）
                * `messages` (array) - 互動式訊息點擊統計（結構同 new\_friend.messages）
              * `original_friend` (object) - 未綁定聯絡人的統計資料
                * `total` (object) - 統計資料（結構同 new\_friend.total）
                * `urls` (array) - URL 點擊與轉換統計（結構同 new\_friend.urls）
                * `messages` (array) - 互動式訊息點擊統計（結構同 new\_friend.messages）
              * `bound_friend` (object) - 綁定聯絡人的統計資料
                * `total` (object) - 統計資料（結構同 new\_friend.total）
                * `urls` (array) - URL 點擊與轉換統計（結構同 new\_friend.urls）
                * `messages` (array) - 互動式訊息點擊統計（結構同 new\_friend.messages）
    * Body

    { "count": 2, "reports": \[ { "id": 1, "name": "Welcome Message", "created\_at": "2025-01-01T10:00:00+08:00", "start\_date": "2025-01-01", "end\_date": "2025-01-07", "total": { "triggers": 1250, "replies": 1200, "opens": 800, "unique\_opens": 750, "clicks": 320, "unique\_clicks": 300, "click\_rate": 0.256, "adds\_to\_cart": 45, "orders": 28, "revenue": 15600.50 }, "channel\_setting\_reports": \[ { "id": 101, "channel\_id": 501, "channel\_type": "line", "channel\_name": "Official LINE Bot", "total": { "triggers": 1000, "replies": 980, "opens": 650, "unique\_opens": 620, "clicks": 260, "unique\_clicks": 245, "click\_rate": 0.26, "adds\_to\_cart": 38, "orders": 24, "revenue": 13200.00 }, "new\_friend": { "total": { "triggers": 300, "replies": 295, "opens": 200, "unique\_opens": 190, "clicks": 80, "unique\_clicks": 75, "click\_rate": 0.267, "adds\_to\_cart": 12, "orders": 8, "revenue": 4200.00 }, "urls": \[ { "id": 631197, "utm\_campaign": "202501-Welcome-Product-Page", "utm\_source": "LINE", "utm\_medium": "message", "utm\_content": "welcome-new-user", "clicks": 50, "adds\_to\_cart": 8, "transactions": 5, "transaction\_revenue": 2800.00, "link": 631197, "tags": \["welcome", "new\_user"] } ], "messages": \[ { "id": 124817, "message": "了解更多", "tags": \["info"], "clicks": 180 } ] }, "original\_friend": { "total": { "triggers": 500, "replies": 490, "opens": 330, "unique\_opens": 315, "clicks": 130, "unique\_clicks": 122, "click\_rate": 0.26, "adds\_to\_cart": 18, "orders": 11, "revenue": 6100.00 }, "urls": \[], "messages": \[] }, "bound\_friend": { "total": { "triggers": 200, "replies": 195, "opens": 120, "unique\_opens": 115, "clicks": 50, "unique\_clicks": 48, "click\_rate": 0.25, "adds\_to\_cart": 8, "orders": 5, "revenue": 2900.00 }, "urls": \[], "messages": \[] } } ] }, { "id": 2, "name": "Follow Auto Reply", "created\_at": "2025-01-02T11:00:00+08:00", "start\_date": "2025-01-01", "end\_date": "2025-01-07", "total": { "triggers": 350, "replies": 340, "opens": 280, "unique\_opens": 270, "clicks": 120, "unique\_clicks": 115, "click\_rate": 0.343, "adds\_to\_cart": 15, "orders": 10, "revenue": 5500.00 }, "channel\_setting\_reports": \[ { "id": 102, "channel\_id": 501, "channel\_type": "line", "channel\_name": "Official LINE Bot", "total": { "triggers": 350, "replies": 340, "opens": 280, "unique\_opens": 270, "clicks": 120, "unique\_clicks": 115, "click\_rate": 0.343, "adds\_to\_cart": 15, "orders": 10, "revenue": 5500.00 }, "new\_friend": { "total": { "triggers": 350, "replies": 340, "opens": 280, "unique\_opens": 270, "clicks": 120, "unique\_clicks": 115, "click\_rate": 0.343, "adds\_to\_cart": 15, "orders": 10, "revenue": 5500.00 }, "urls": \[], "messages": \[] }, "original\_friend": { "total": { "triggers": 0, "replies": 0, "opens": 0, "unique\_opens": 0, "clicks": 0, "unique\_clicks": 0, "click\_rate": 0.0, "adds\_to\_cart": 0, "orders": 0, "revenue": 0.0 }, "urls": \[], "messages": \[] }, "bound\_friend": { "total": { "triggers": 0, "replies": 0, "opens": 0, "unique\_opens": 0, "clicks": 0, "unique\_clicks": 0, "click\_rate": 0.0, "adds\_to\_cart": 0, "orders": 0, "revenue": 0.0 }, "urls": \[], "messages": \[] } } ] } ] }
*   Response 400 (application/json)

    * Attributes (object)
      * `message` (string) - 錯誤訊息
      * `errors` (array) - 錯誤詳細資訊
        * (object)
          * `loc` (array\[string]) - 錯誤欄位位置
          * `msg` (string) - 錯誤訊息
          * `type` (string) - 錯誤類型
    * Body

    { "message": "", "errors": \[ { "loc": \["**root**"], "msg": "Invalid start\_date format. Use YYYY-MM-DD.", "type": "value\_error" } ] }
*   Response 403 (application/json)

    * Body

    { "detail": "You do not have permission to perform this action." }
*   Response 404 (application/json)

    * Body

    { "message": "Bot does not exist" }

## Group 簡訊+

本段落描述該如何正確使用簡訊+ API。

## 簡訊+ 範本 \[/openapi/v1/pnp/setting/]

發送訊息推播時，需填入欲發送的簡訊+ 範本 ID。\
如果該範本有啟用通知型訊息，其資格與情境需先經過 LINE 官方的審核，會由漸強協助完成申請。

請洽詢 [Customer support](mailto:customer-supoort@cresclab.com)，由專人為您服務。

#### 取得簡訊+ 範本列表 \[GET /openapi/v1/pnp/setting/{?start}]

取得簡訊+ 範本列表，列表以每300筆範本進行分頁。

* Request (application/json)
  * Headers Authorization: Bearer {Access token}
* Parameters
  * start : `OwNdFUXTfIyunwhn55vJh4fE0wu13wSPRTCUiaqhN1Nu0vLXHpzatVFtb9ZYKBxwGKoy3jOfvxSzEfOOZnFz5Y%2BKcvexmL39l5xQqQSwtiA%3D`(optional, string) - 下一分頁之識別碼，會回覆於前一分頁之`next`參數
*   Response 200 (application/json)

    * Attributes (object)
      * `results` (array) - 範本陣列
        * (object)
          * `id` (number) - 簡訊+ 範本 ID
          * `name` (string) - 簡訊+ 範本名稱
          * `status` (string) - 簡訊+ 範本狀態
          * `line_push_enabled` (boolean) - 是否開啟 LINE 訊息
          * `pnp_enabled` (boolean) - 是否開啟 LINE 通知型訊息
          * `fallback_enabled` (boolean) - 否開啟簡訊訊息
          * `fallback_period` (number) - 轉發簡訊等候時間 (分鐘)
          * `parameters` (array) - LINE 通知型訊息包含的變數陣列
            * (string) - 變數名稱
          * `sms_parameters` (array) - 簡訊訊息包含的變數陣列
            * (string) - 變數名稱
      * `next` (string) - 下一分頁的page token
    * Body

    { "results": \[ "id": 1111, "name": "到貨通知", "status": "enable", "line\_push\_enabled": true, "pnp\_enabled": true, "fallback\_enabled": true, "fallback\_period": 1440, "parameters": \[ "days", "location\_name", "order\_number", "arrival\_date", "order\_url" ], "sms\_parameters": \[ "order\_number", "arrival\_date", "location\_name", "days" ] ], "next": null }

#### 取得簡訊+ 範本 \[GET /openapi/v1/pnp/setting/{pnp\_setting\_id}/]

取得指定的簡訊+ 範本以及統計數據

* Request (application/json)
  * Headers Authorization: Bearer {Access token}
* Parameters
  * pnp\_setting\_id : 1111 (required, number) - 簡訊+ 範本 ID
*   Response 200 (application/json)

    * Attributes (object)
      * `id` (number) - 簡訊+ 範本 ID
      * `name` (string) - 簡訊+ 範本名稱
      * `status` (string) - 簡訊+ 範本狀態
      * `line_push_enabled` (boolean) - 是否開啟 LINE 訊息
      * `pnp_enabled` (boolean) - 是否開啟 LINE 通知型訊息
      * `fallback_enabled` (boolean) - 否開啟簡訊訊息
      * `fallback_period` (number) - 轉發簡訊等候時間 (分鐘)
      * `parameters` (array) - LINE 通知型訊息包含的變數陣列
        * (string) - 變數名稱
      * `sms_parameters` (array) - 簡訊訊息包含的變數陣列
        * (string) - 變數名稱
      * `metric` (object) - 簡訊+ 訊息統計數據
        * `all` (number) - 簡訊+ 訊息觸發總數
        * `fail` (number) - 簡訊+ 訊息失敗總數
        * `pnp` (number) - LINE 通知型訊息總數
        * `sms` (number) - 轉發簡訊總數
    * Body

    { "id": 1111, "name": "到貨通知", "status": "enable", "line\_push\_enabled": true, "pnp\_enabled": true, "fallback\_enabled": true, "fallback\_period": 1440, "parameters": \[ "days", "location\_name", "order\_number", "arrival\_date", "order\_url" ], "sms\_parameters": \[ "order\_number", "arrival\_date", "location\_name", "days" ], "metric": { "all": 0, "fail": 0, "pnp": 0, "sms": 0 } }

### 簡訊+ 訊息推播 \[/openapi/v1/pnp/message/]

簡訊+ 訊息推播前需要的資訊

* `pnp_setting_id`: 簡訊+ 範本 ID。
* `phone_number`: 欲發送用戶之電話號碼

電話號碼格式支援以下兩種：

* **E.164** 格式：國際電信組織制定的通訊編碼格式（例如：`+886912345678`）。
* **SHA256 雜湊** 格式：經 SHA256 雜湊處理的 E.164 電話號碼（64 個小寫十六進位字元，例如：`e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855`）。**注意：SHA256 雜湊格式僅在簡訊+ 範本 (PNP setting) 停用簡訊功能時才可使用。此外，LINE 訊息僅支援精確比對，因此 E.164 與 SHA256 格式不相容。**

LINE 通知型訊息內容需 LINE 審核通過才可使用

#### 單則 (Push) \[POST /openapi/v1/pnp/message/push/]

適用於對單一用戶推播簡訊+ 訊息。

* **注意事項**
  * 若您收到 `200` 狀態碼，表示系統已保存您的簡訊+ 訊息推播請求，此時您無須再做重傳。
  * 若在 `fallback_period` 時間內無法傳送成功的話，系統會將訊息自動使用簡訊傳送。
  * MAAC 系統會以訊息主題為追蹤成效的對象，若希望追蹤訊息推播成效，請求時請填入`event_id`
*   Request (application/json)

    * Attributes (object)
      * `pnp_setting_id` (required, number) - 簡訊+ 範本 ID
      * `event_id` (optional, number) - 訊息主題ID
      * `data` (required, object) - 推播訊息設定
        * `phone_number` (required, string) - 聯絡人的電話號碼。支援 E.164 格式（如 `+886912345678`）或 SHA256 雜湊的 E.164 格式（64 個十六進位字元）。SHA256 格式僅在簡訊+ 範本停用簡訊時可使用。LINE 訊息僅支援精確比對（E.164 與 SHA256 不相容）。
        * `line_push_template_id` (optional, number) - LINE 訊息範本 ID。. 如果有啟用 LINE 訊息則必填。
        * `line_push` (optional, object) - LINE 訊息設定。 如果有啟用 LINE 訊息則必填。
          * `PARAM_1` (optional, string) - LINE 訊息中的變數：名稱vs數值
          * `PARAM_2` (optional, string) - LINE 訊息中的變數：名稱vs數值
        * `pnp` (required, object) - LINE 通知型訊息設定
          * `PARAM_1` (optional, string) - LINE 通知型訊息中的變數：名稱vs數值
          * `PARAM_2` (optional, string) - LINE 通知型訊息中的變數：名稱vs數值
        * `sms` (required, object) - 簡訊設定
          * `PARAM_1` (optional, string) - 簡訊訊息中的變數：名稱vs數值
          * `PARAM_2` (optional, string) - 簡訊訊息中的變數：名稱vs數值
        * `whatsapp` (optional, object) - WhatsApp範本訊息設定
          * `template_name` (required, string) - WhatsApp範本名稱
          * `language` (required, string) - WhatsApp範本語言
          * `template_data` (required, object) - WhatsApp範本變數
            * `header` (optional, object) - whatsapp範本標題
              * `parameters` (array) - whatsapp範本標題變數
                * (string) - 變數內容
                * (object) - 變數內容
                  * `type` (enum) - 變數類型
                    * text - 文字類型
                    * image - 圖片類型
                    * video - 影片類型
                    * document - 文件類型
                    * location - 地點類型
                  * `text` (optional, string) - 文字內容。 如果 type 為 text 則必填。
                  * `media_id` (optional, string) - WhatsApp Media Object ID。 如果 type 為 image、video 或 document 且未使用 media\_url 時，此欄位為必填。
                  * `media_url` (optional, string) - Media URL。 如果 type 為 image、video 或 document 且未使用 media\_id 時，此欄位為必填。
                  * `filename` (optional, string) - 檔案名稱。如果 type 為 document 則必填。
                  * `latitude` (optional, string) - 緯度數值。如果 type 為 location 則必填。
                  * `longitude` (optional, string) - 經度數值。如果 type 為 location 則必填。
                  * `name` (optional, string) - 名稱。如果 type 為 location 則必填。
                  * `address` (optional, string) - 地址。如果 type 為 location 則必填。
            * `body` (optional, object) - WhatsApp範本內文
              * `parameters` (array\[string]) - whatsapp範本內文變數
        * `customized_id` (optional, string) - 使用者自訂的識別碼，可用於在自身系統中關聯或追蹤訊息。
    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "pnp\_setting\_id": 1111, "event\_id": 123, "data": { "phone\_number": "+886912345678", "line\_push\_template\_id": 123, "line\_push": { "days": "7", "location\_name": "A store", "order\_number": "AJ1234567", "arrival\_date": "2020/7/30", "order\_url": "http://your.domain.com/order/" }, "pnp": { "days": "7", "location\_name": "全家金林門市", "order\_number": "AJ1234567", "arrival\_date": "2020/7/30", "order\_url": "http://your.domain.com/order/" }, "sms": { "order\_number": "AJ1234567", "arrival\_date": "2020/7/30", "location\_name": "全家金林門市", "days": "7" }, "whatsapp": { "template\_name": "deliver\_confirmation\_test", "template\_data": { "header": { "parameters": \[ { "type": "text", "text": "全家金林門市" } ] }, "body": { "parameters": \["AJ1234567"] } }, "language": "en\_US" }, "customized\_id": "AJ1234567890" } }
*   Request 使用 WhatsApp image header 範本訊息 (application/json)

    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "pnp\_setting\_id": 1111, "event\_id": 123, "data": { "phone\_number": "+886912345678", "pnp": {}, "sms": { "order\_number": "AJ1234567", "arrival\_date": "2020/7/30", "location\_name": "全家金林門市", "days": "7" }, "whatsapp": { "template\_name": "deliver\_confirmation\_test", "template\_data": { "header": { "parameters": \[ { "type": "image", "media\_url": "http://maac.io/xxxxx.jpg" } ] }, "body": { "parameters": \["AJ1234567"] } }, "language": "en\_US" }, "customized\_id": "AJ1234567890" } }
*   Response 200 (application/json)

    * Attributes (object)
      * `id` (number) - 簡訊+ 訊息 ID。對應至 Webhook results 以及 發送紀錄查詢 中的 `pnp_message_id`
      * `result` (string) 簡訊+ 訊息推播狀態
        * `success` - 已遞交給 LINE 發送此訊息
        * `we're under maintenance` - LINE 的系統維護中。在轉發簡訊等待時間 (`fallback_period`) 後，系統將會自動使用簡訊傳送此訊息。
        * `failed to send messages` - LINE 無法完成電話號碼配對。在轉發簡訊等待時間 (`fallback_period`) 後，系統將會自動使用簡訊傳送此訊息。
        * `access token expired` - 無效的 LINE token。在轉發簡訊等待時間 (`fallback_period`) 後，系統將會自動使用簡訊傳送此訊息。
        * `timeout` - LINE API 並未返回結果。在轉發簡訊等待時間 (`fallback_period`) 後，系統將會自動使用簡訊傳送此訊息。
        * 其他未詳列於此的異常狀態，系統皆會在轉發簡訊等待時間 (`fallback_period`) 後，自動使用簡訊傳送此訊息。
    * Body

    { "id": 1342, "result": "success" }
*   Response 400 (text/plain)

    * `pnp setting not found` - 簡訊+ 範本 ID 錯誤
    * `xxx field is required` - 在簡訊+ 訊息推播中有遺漏的欄位設定
    * `this value does not match the required pattern` - 電話號碼格式錯誤
    * `your SMS points are insufficient, please recharge before sending` - 您的剩餘 MAAC 點數不足，請聯絡客服
    * Body

    pnp setting not found
*   Response 403 (text/plain)

    * `You do not have permission to perform this action` - 提供的 authorization header 錯誤
    * Body

    You do not have permission to perform this action
*   Response 503 (text/plain)

    * `failed to emit messages` - 該請求遇到暫時性的系統異常，請稍後重試。
    * Body

    failed to emit messages

#### 群發 (Multicast) \[POST /openapi/v1/pnp/message/multicast/]

適用於單次推播不同簡訊+ 訊息給少量用戶，單次請求最多推播 150 位聯絡人。每一位用戶的訊息變數設定獨立。

**此 API 不支援發送 LINE 訊息。如果有需求，請使用單則 (Push)。**

* **注意事項**
  * 若您收到 `200` 狀態碼，表示系統已保存您的簡訊+ 訊息請求，此時您無須再做重傳。
  * 系統會採用異步推播訊息，故 API 回覆當下狀態為 `pending`
  * 若在 `fallback_period` 時間內無法傳送成功的話，系統會將訊息自動使用簡訊傳送。
  * MAAC 系統會以訊息主題為追蹤成效的對象，若希望追蹤訊息推播成效，請求時請填入`event_id`
*   Request (application/json)

    * Attributes (object)
      * `pnp_setting_id` (required, number) - 簡訊+ 範本 ID
      * `event_id` (optional, number) - 訊息主題ID
      * `data` (required, array) - 簡訊+ 訊息設定陣列
        * (object)
          * `phone_number` (required, string) - 聯絡人的電話號碼。支援 E.164 格式（如 `+886912345678`）或 SHA256 雜湊的 E.164 格式（64 個十六進位字元）。SHA256 格式僅在簡訊+ 範本停用簡訊時可使用。
          * `pnp` (required, object) - 通知型訊息設定
            * `PARAM_1` (optional, string) - 訊息範本中的變數：名稱vs數值
            * `PARAM_2` (optional, string) - 訊息範本中的變數：名稱vs數值
          * `sms` (required, object) - 簡訊設定
            * `PARAM_1` (optional, string) - 訊息範本中的變數：名稱vs數值
            * `PARAM_2` (optional, string) - 訊息範本中的變數：名稱vs數值
          * `customized_id` (optional, string) - 使用者自訂的識別碼，可用於在自身系統中關聯或追蹤訊息。
    *   Headers

        Authorization: Bearer {Access token}
    * Body

    { "pnp\_setting\_id": 1111, "event\_id": 123, "data": \[ { "phone\_number": "+886912345678", "pnp": { "days": "7", "location\_name": "全家金林門市", "order\_number": "AJ1234567", "arrival\_date": "2020/7/30", "order\_url": "http://maac.io/xxxxx" }, "sms": { "order\_number": "AJ1234567", "arrival\_date": "2020/7/30", "location\_name": "全家金林門市", "days": "7" }, "customized\_id": "AJ1234567890" }, { "phone\_number": "+886912345679", "pnp": { "days": "7", "location\_name": "7-11龍潭門市", "order\_number": "BK7654321", "arrival\_date": "2020/7/30", "order\_url": "http://maac.io/xxxxx" }, "sms": { "order\_number": "BK7654321", "arrival\_date": "2020/7/30", "location\_name": "7-11龍潭門市", "days": "7" }, "customized\_id": "BK7654321890" } ] }
*   Response 200 (application/json)

    * Attributes (array)
      * (object)
        * `id` (number) - 通知型訊息推播 ID
        * `result` (string) LINE Notification Message status
          * `pending` - 系統正在處理訊息
    * Body

    \[ { "id": 1111, "result": "pending" }, { "id": 1112, "result": "pending" } ]
*   Response 400 (text/plain)

    * `pnp setting not found` - 簡訊+ 範本 ID 錯誤
    * `field is required` - 在簡訊+ 訊息中有遺漏的欄位設定
    * `this value does not match the required pattern` - 電話號碼格式錯誤
    * `your SMS points are insufficient, please recharge before sending` - 您的剩餘 MAAC 點數不足，請聯絡客服
    * Body

    pnp setting not found
*   Response 403 (text/plain)

    * `You do not have permission to perform this action` - 提供的 authorization header 錯誤
    * Body

    You do not have permission to perform this action

#### 發送紀錄查詢 \[GET /openapi/v1/pnp/message/{?pnp\_setting\_id,updated\_at\_min,updated\_at\_max,start}]

單則與群發發送後，可查詢其發送紀錄。此 API 可用來追蹤發送紀錄的狀態更動，發送紀錄以每三百筆進行分頁，並以更新時間由新到舊排序。

> 使用發送紀錄欄位 `updated_at` 的起訖 `updated_at_min` 與 `updated_at_min` 來取得該時間區間內有狀態更動的發送紀錄

* **注意事項**
  * `updated_at_min` 與 `updated_at_max` 僅接受 ISO 8601 之時間格式
  * ISO 8601 中時區的 `+` 號須經過 url 編碼 (編碼後結果為 `%2B`)，否則將收到 `400` 格式錯誤。
  * 若無攜帶時區資訊，將統一以 `Asia/Taipei` 時間為主。
* Request (application/json)
  * Headers Authorization: Bearer {Access token}
* Parameters
  * pnp\_setting\_id (required, number) - 訊息範本 ID
  * updated\_at\_min : `2022-10-13T16:03:15.248652%2B08:00` (required, string) - `updated_at` 範圍起始時間(ISO 8601)
  * updated\_at\_max : `2022-10-18T16:03:15.248652%2B08:00` (required, string) - `updated_at` 範圍結束時間(ISO 8601)
  * customized\_id (optional, string) - 使用者自訂的識別碼
  * start : `OwNdFUXTfIyunwhn55vJh4fE0wu13wSPRTCUiaqhN1Nu0vLXHpzatVFtb9ZYKBxwGKoy3jOfvxSzEfOOZnFz5Y%2BKcvexmL39l5xQqQSwtiA%3D`(optional, string) - 下一分頁之識別碼，會回覆於前一分頁之`next`參數
* Response 200 (application/json)
  * Attributes (object)
    * `results` (array) - 訊息主題陣列
      * (object)
        * `pnp_message_id` (number) - 簡訊+ 訊息發送紀錄 ID，對應至使用單則發送 API 時回傳的 `id` 欄位
        * `phone_number` (string) - 訊息接收者之電話號碼
        * `status` (enum) - 訊息發送狀態
          * line\_push\_preparing - 該訊息已進入 Line 訊息發送流程
          * line\_push\_delivered - Line 訊息已送達用戶手中
          * line\_push\_failed - Line 訊息發送失敗
          * line\_push\_undeliverable - Line 訊息無法送達 (可能原因：LINE 訊息額度用完, 聯絡人已封鎖 LINE OA, LINE API 超時).
          * pnp\_preparing - 該訊息已進入 PNP 發送流程
          * pnp\_accepted - LINE 已接收 PNP 發送請求
          * pnp\_delivered - PNP 已送達用戶手中
          * pnp\_failed - PNP 發送失敗
          * pnp\_undeliverable - PNP 無法送達 (ex:封鎖OA)
          * sms\_preparing - 該訊息已進入 SMS 發送流程
          * sms\_accepted - 簡訊商已接收 SMS 發送請求
          * sms\_delivered - SMS 已送達用戶手中
          * sms\_failed - SMS 發送失敗
          * sms\_undeliverable - SMS 無法送達(ex: 訊號不佳、關機)
          * sms\_blocked - SMS 停止發送因該電話在禁止發送清單中
          * sms\_temporary\_error - 因簡訊商暫時錯誤而無法發送時的狀態，MAAC 系統會嘗試重新發送直到重試時間區間結束為止。若重試時間區間已結束但結果仍失敗時，系統會將此狀態轉為 `sms_failed`
          * sms\_callback\_timeout - MAAC 在時限內未收到簡訊的狀態回應
        * `line_push_template_id` (number, nullable) - LINE 訊息範本 ID
        * `line_push_status` (string, nullable) - LINE 訊息發送狀態
        * `line_push_delivered_at` (string, nullable) - 訊息經由 LINE 訊息發送之送達時間 (ISO 8601)
        * `line_push_error_category` (enum, nullable) - LINE 訊息錯誤類別
          * member\_not\_found - LINE 訊息因為無法找到 LINE OA 聯絡人而發送失敗（可能原因：電話號碼找到多名聯絡人或聯絡人已封鎖）
          * reach\_monthly\_limit - LINE 訊息發送額度用罄
          * others - 其他錯誤
        * `pnp_status` (string, nullable) - LINE 通知型訊息發送狀態
        * `pnp_delivered_at` (string, nullable) - 訊息經由 LINE 通知型訊息發送之送達時間 (ISO 8601)
        * `sms_status` (string, nullable) - 簡訊發送狀態
        * `sms_delivered_at` (string, nullable) - 訊息經由簡訊商發送之送達時間 (ISO 8601)
        * `sms_error_category` (enum, nullable) - 簡訊錯誤類別
          * target\_reception\_issue - 因電信商或接收端原因無法送達簡訊 (e.g., 關機、基地台異常)
          * invalid\_phone\_number - 手機號碼格式不符、空號或停用中
          * sensitive\_words - 簡訊內容包含敏感詞彙
          * others - 其他錯誤
        * `updated_at` (string) - 該發送紀錄之更新時間 (ISO 8601)
        * `event_id` (number) - 訊息主題ID
        * `customized_id` (string, nullable) - 使用者自訂的識別碼
    * `next` (string) - 下一分頁的 page token
  * Body { "next": "OwNdFUXTfIyunwhn55vJh4fE0wu13wSPRTCUiaqhN1Nu0vLXHpzatVFtb9ZYKBxwGKoy3jOfvxSzEfOOZnFz5Y%2BKcvexmL39l5xQqQSwtiA%3D", "results": \[ { "phone\_number": "+886912345678", "pnp\_message\_id": 5, "status": "line\_push\_delivered", "line\_push\_template\_id": 1, "line\_push\_status": "line\_push\_delivered", "line\_push\_delivered\_at": "2022-10-14T10:33:41.343356+08:00", "line\_push\_error\_category": null, "pnp\_status": null, "pnp\_delivered\_at": null, "sms\_status": null, "sms\_delivered\_at": null, "sms\_error\_category": null, "updated\_at": "2022-10-14T10:33:41.343356+08:00", "event\_id": 123, "customized\_id": "AJ1234567890" }, { "phone\_number": "+886912345678", "pnp\_message\_id": 4, "status": "pnp\_preparing", "line\_push\_template\_id": null, "line\_push\_status": null, "line\_push\_delivered\_at": null, "line\_push\_error\_category": null, "pnp\_status": "pnp\_preparing", "pnp\_delivered\_at": null, "sms\_status": null, "sms\_delivered\_at": null, "sms\_error\_category": null, "updated\_at": "2022-10-14T10:33:41.343356+08:00", "event\_id": 123, "customized\_id": "AJ1234567890" }, { "phone\_number": "+886912345678", "pnp\_message\_id": 3, "status": "pnp\_delivered", "line\_push\_template\_id": null, "line\_push\_status": null, "line\_push\_delivered\_at": null, "line\_push\_error\_category": null, "pnp\_status": "pnp\_delivered", "pnp\_delivered\_at": "2022-10-13T16:39:15.248652+08:00", "sms\_status": null, "sms\_delivered\_at": null, "sms\_error\_category": null, "updated\_at": "2022-10-13T16:39:15.248652+08:00", "event\_id": 123, "customized\_id": "AJ1234567890" }, { "phone\_number": "+886912345678", "pnp\_message\_id": 2, "status": "sms\_delivered", "line\_push\_template\_id": null, "line\_push\_status": null, "line\_push\_delivered\_at": null, "line\_push\_error\_category": null, "pnp\_status": "pnp\_undeliverable", "pnp\_delivered\_at": null, "sms\_status": "sms\_delivered", "sms\_delivered\_at": "2022-10-13T16:39:15.248652+08:00", "sms\_error\_category": null, "updated\_at": "2022-10-13T16:36:48.440109+08:00", "event\_id": 123, "customized\_id": "AJ1234567890" }, { "phone\_number": "+886912345678", "pnp\_message\_id": 1, "status": "sms\_undeliverable", "line\_push\_template\_id": null, "line\_push\_status": null, "line\_push\_delivered\_at": null, "line\_push\_error\_category": null, "pnp\_status": "pnp\_undeliverable", "pnp\_delivered\_at": null, "sms\_status": "sms\_undeliverable", "sms\_delivered\_at": null, "sms\_error\_category": "target\_reception\_issue" "updated\_at": "2022-10-13T16:35:10.200642+08:00", "event\_id": 123, "customized\_id": "AJ1234567890" } ] }
* Response 400 (application/json)
  * Body { "updated\_at\_min": \[ "Datetime has wrong format. Use one of these formats instead: YYYY-MM-DDThh:mm\[:ss\[.uuuuuu]]\[+HH:MM|-HH:MM|Z]." ], "pnp\_setting\_id": \[ "This field is required." ] }
* Response 404 (application/json)
  * Body { "detail": "pnp\_setting\_id not found" }
* Response 403 (application/json)
  * Body { "detail": "You do not have permission to perform this action." }

## Group Webhook

您可以使用 Webhook 來訂閱有關用戶中特定事件的通知。訂閱 Webhook 事件後，您的服務可以在發生特定事件後立即執行程式碼，而不必定期進行 API 輪詢以檢查其狀態與更新。

(欲使用 Webhook 請聯繫 [Customer support](mailto:customer-supoort@cresclab.com))

**注意事項**

* MAAC OpenAPI 並沒有 `/partner/maac/webhook/` 這個 endpoint，請不要用這個做測試，這只是個設計範例，僅供參考

| Topics                                    | Event                      |
| ----------------------------------------- | -------------------------- |
| receipt                                   | receipt.receipt\_validated |
| form                                      | form.surveycake\_submitted |
| LINE notification message status updated  | pnp.status\_updated        |
| LINE notification message profile updated | pnp.profile\_updated       |
| Prize Points Added                        | prize.points\_added        |

> **Request**

`POST https://your-api-domain.com/your/webhook/endpoint`

> **Headers**

| 欄位                       | 數值                                             |
| ------------------------ | ---------------------------------------------- |
| Content-Type             | `application/json; charset=utf-8`              |
| CrescLab-Idempotency-Key | 由 MAAC 生成的唯一值。使用此標識來識別同一請求的後續重試，避免重試導致系統重複或衝突。 |
| CrescLab-Signature       | 用以確認請求是從 MAAC 平台發送的。                           |

> **Body**

| 欄位        | 型別     | 說明   |
| --------- | ------ | ---- |
| timestamp | String | 觸發時間 |
| topic     | String | 事件類別 |
| data      | Object | 事件資料 |

### Webhook \[/partner/maac/webhook/]

#### Receipt Validated \[POST]

*   Request (application/json; charset=utf-8) 200

    * Attributes (object)
      * `timestamp` (string) - 觸發時間
      * `topic` (string) - 事件類別
      * `data` (object) - 事件資料
        * `line_uid` (string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
        * `customer_id` (string, nullable) - 第三方系統之用戶識別碼
        * `campaign_name` (string, nullable) - 活動名稱
        * `number` (string) - 發票字軌號碼
        * `datetime` (string) - 交易時間
        * `upload_datetime` (string) - 發票上傳時間
        * `random_number` (string) - 發票隨機碼
        * `channel` (string) - 購買渠道
        * `items` (array) - 購買明細
          * (object)
            * `description` (string) - 商品描述
            * `unit_price` (number) - 商品單價
            * `quantity` (number) - 購買數量
            * `amount` (number) - 合計
    *   Headers

        CrescLab-Idempotency-Key: 191fecc0b2644d3f875ce84b1340b645\
        CrescLab-Signature: 0ff864b8f3bf8353e9a8e0b62f17da3be16cb66adf653561da482be93c836df5
    * Body

    { "timestamp": "2021-11-29T15:43:26.582968+08:00", "topic": "receipt.receipt\_validated", "data": { "line\_uid": "U58c280fca6ea81aa18330cee7269d36b", "customer\_id": null, "campaign\_name": "串接測試", "number": "JA87857072", "datetime": "2021-11-09T12:05:36+08:00", "upload\_datetime": "2021-11-29T07:43:26.540452+08:00", "random\_number": "5067", "channel": "師傅萬隆捷運站店", "items": \[ { "description": "檸檬肉桂堅果橘皮", "unit\_price": 65.0, "quantity": 1.0, "amount": 65.0 }, { "description": "烤布丁(2入)", "unit\_price": 105.0, "quantity": 1.0, "amount": 105.0 } ] } }
* Response 200 (text/plain)
  * Body OK

#### SurveyCake Submitted \[POST]

問卷事件詳細資料請參考 [SurveyCake API](https://github.com/SurveyCake/webhook#1-%E5%A1%AB%E7%AD%94%E7%B5%90%E6%9E%9C%E6%9C%83%E6%98%AF%E4%BB%80%E9%BA%BC%E6%A0%BC%E5%BC%8F)

*   Request (application/json; charset=utf-8) 200

    * Attributes (object)
      * `timestamp` (string) - 觸發時間
      * `topic` (string) - 事件類別
      * `data` (object) - 事件資料
        * `line_uid` (string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
        * `customer_id` (string, nullable) - 第三方系統之用戶識別碼
        * `survey_name` (string, nullable) - 問卷名稱
        * `answer_hash` (string) - 問卷內容 hash 值，此欄位可協助查找 SuveyCake 端 log。
        * `answer` (array) - survey 回答
          * (object)
            * `id` (string)
            * `svid` (string) - survey id
            * `title` (string) - survey 標題
            * `status` (string)
            * `submitTime` (string)
            * `mbunq` (string, nullable)
            * `meta` (object)
            * `mbrid` (string, nullable)
            * `alias` (object)
              * your\_alias\_key (array\[string])
            * `result` (array)
              * (object)
                * `subject` (string)
                * `type` (string) - subject type
                * `sn` (string)
                * `label` (string)
                * `alias` (string)
                * `answer` (array\[string])
                * `otherAnswer` (array\[string])
                * `answerLabel` (array\[string])
                * `answerAlias` (array\[string])
    *   Headers

        CrescLab-Idempotency-Key: 191fecc0b2644d3f875ce84b1340b645\
        CrescLab-Signature: 0ff864b8f3bf8353e9a8e0b62f17da3be16cb66adf653561da482be93c836df5
    * Body

    { "timestamp": "2021-11-30T17:51:26.018507+08:00", "topic": "form.surveycake\_submitted", "data": { "line\_uid": "U0123456789abcdef0123456789abcdef", "customer\_id": "12345678", "survey\_name": "survey1", "answer": { "id": 1234, "svid": "abcde", "title": "MAAC 串接", "status": "FINISH", "submitTime": "2021-07-15 07:32:23", "mbunq": null, "meta": { "isolated": { "status": false, "type": null } }, "mbrid": null, "alias": { "maac\_member\_line\_uid": \[ "U0123456789abcdef0123456789abcdef" ], "maac\_member\_name": \[ "CrescLab" ], "maac\_member\_mobile": \[ "0987654321" ], "maac\_member\_birthday": \[ "2021-01-01" ], "maac\_member\_customer\_id": \[ "12345678" ], "maac\_member\_email": \[], "maac\_member\_gender": \[ "female" ] }, "result": \[ { "subject": "LINE UID", "type": "TXTSHORT", "sn": 0, "label": "", "alias": "maac\_member\_line\_uid", "answer": \[ "U0123456789abcdef0123456789abcdef" ], "otherAnswer": \[], "answerLabel": \[], "answerAlias": \[] }, { "subject": "姓名", "type": "TXTSHORT", "sn": 1, "label": "", "alias": "maac\_member\_name", "answer": \[ "CrescLab" ], "otherAnswer": \[], "answerLabel": \[], "answerAlias": \[] }, { "subject": "手機號碼", "type": "TXTSHORT", "sn": 17, "label": "", "alias": "maac\_member\_mobile", "answer": \[ "0987654321" ], "otherAnswer": \[], "answerLabel": \[], "answerAlias": \[] }, { "subject": "生日", "type": "DATEPICKER", "sn": 23, "label": "birth", "alias": "maac\_member\_birthday", "answer": \[ "2021-01-01" ], "otherAnswer": \[], "answerLabel": \[], "answerAlias": \[] }, { "subject": "customer\_id", "type": "TXTSHORT", "sn": 18, "label": "cid", "alias": "maac\_member\_customer\_id", "answer": \[ "12345678" ], "otherAnswer": \[], "answerLabel": \[], "answerAlias": \[] }, { "subject": "Email", "type": "TXTSHORT", "sn": 21, "label": "email,email\_test", "alias": "maac\_member\_email", "answer": \[], "otherAnswer": \[], "answerLabel": \[], "answerAlias": \[] }, { "subject": "Gender", "type": "CHOICEONE", "sn": 22, "label": "", "alias": "maac\_member\_gender", "answer": \[ "女" ], "otherAnswer": \[], "answerLabel": \[ "girl" ], "answerAlias": \[ "female" ] }, { "subject": "Tag", "type": "CHOICEMULTI", "sn": 24, "label": "", "alias": "", "answer": \[ "Tag1", "Tag2" ], "otherAnswer": \[], "answerLabel": \[ "1,2", "" ], "answerAlias": \[ "", "" ] } ] } } }
* Response 200 (text/plain)
  * Body OK

#### SMS+ Message Status Updated \[POST]

*   Request (application/json; charset=utf-8) 200

    * Attributes (object)
      * `timestamp` (string) - 觸發時間
      * `topic` (string) - 事件類別
      * `data` (object) - 事件資料
        * `pnp_setting_id` (number) - 簡訊+ 範本 ID
        * `pnp_setting_name` (string) - 簡訊+ 範本名稱
        * `pnp_message_id` (number) - 簡訊+ 訊息發送 ID。對應至使用單則發送 API 時回傳的 `id` 欄位
        * `event_id` (number) - 訊息主題ID
        * `customized_id` (string, nullable) - 使用者自訂的識別碼
        * `phone_number` (string) - 聯絡人的電話號碼。可能為 E.164 格式（如 `+886912345678`）或 SHA256 雜湊的 E.164 格式（64 個十六進位字元），取決於原始 API 請求使用的格式。
        * `status` (enum) - 訊息發送狀態
          * line\_push\_preparing - 該訊息已進入 Line 訊息發送流程
          * line\_push\_delivered - Line 訊息已送達用戶手中
          * line\_push\_failed - Line 訊息發送失敗
          * line\_push\_undeliverable - Line 訊息無法送達 (可能原因：LINE 訊息額度用完, 聯絡人已封鎖 LINE OA, LINE API 超時).
          * pnp\_preparing - 該訊息已進入 PNP 發送流程
          * pnp\_accepted - LINE 已接收 PNP 發送請求
          * pnp\_delivered - PNP 已送達用戶手中
          * pnp\_failed - PNP 發送失敗
          * pnp\_undeliverable - PNP 無法送達 (ex:封鎖OA)
          * sms\_preparing - 該訊息已進入 SMS 發送流程
          * sms\_accepted - 簡訊商已接收 SMS 發送請求
          * sms\_delivered - SMS 已送達用戶手中
          * sms\_failed - SMS 發送失敗
          * sms\_undeliverable - SMS 無法送達(ex: 訊號不佳、關機)
          * sms\_blocked - SMS 停止發送因該電話在禁止發送清單中
          * sms\_temporary\_error - 因簡訊商暫時錯誤而無法發送時的狀態，MAAC 系統會嘗試重新發送直到重試時間區間結束為止。若重試時間區間已結束但結果仍失敗時，系統會將此狀態轉為 `sms_failed`
          * sms\_callback\_timeout - MAAC 在時限內未收到簡訊的狀態回應
        * `line_push_template_id` (number, nullable) - LINE 訊息範本 ID
        * `line_push_status` (string, nullable) - LINE 訊息發送狀態
        * `line_push_delivered_at` (string, nullable) - 訊息經由 LINE 訊息發送之送達時間 (ISO 8601)
        * `line_push_error_category` (enum, nullable) - LINE 訊息錯誤類別
          * member\_not\_found - LINE 訊息因為無法找到 LINE OA 聯絡人而發送失敗（可能原因：電話號碼找到多名聯絡人或聯絡人已封鎖）
          * reach\_monthly\_limit - LINE 訊息發送額度用罄
          * others - 其他錯誤
        * `pnp_status` (string, nullable) - LINE 通知型訊息發送狀態
        * `pnp_delivered_at` (string, nullable) - 訊息經由 LINE 通知型訊息發送之送達時間 (ISO 8601)
        * `sms_status` (string, nullable) - 簡訊發送狀態
        * `sms_delivered_at` (string, nullable) - 訊息經由簡訊商發送之送達時間 (ISO 8601)
        * `sms_error_category` (enum, nullable) - 簡訊錯誤類別
          * target\_reception\_issue - 因電信商或接收端原因無法送達簡訊 (e.g., 關機、基地台異常)
          * invalid\_phone\_number - 手機號碼格式不符、空號或停用中
          * sensitive\_words - 簡訊內容包含敏感詞彙
          * others - 其他錯誤
    *   Headers

        CrescLab-Idempotency-Key: 191fecc0b2644d3f875ce84b1340b645\
        CrescLab-Signature: 0ff864b8f3bf8353e9a8e0b62f17da3be16cb66adf653561da482be93c836df5
    * Body

    { "timestamp": "2021-11-30T17:51:26.018507+08:00", "topic": "pnp.status\_updated", "data": { "pnp\_setting\_id": 0, "pnp\_setting\_name": "testing name", "pnp\_message\_id": 0, "event\_id": 123, "customized\_id": "AJ1234567890", "phone\_number": "+886912345678", "status": "pnp\_delivered", "line\_push\_template\_id": 1, "line\_push\_status": "line\_push\_failed", "line\_push\_delivered\_at": null, "line\_push\_error\_category": null, "pnp\_status": "pnp\_delivered", "pnp\_delivered\_at": "2021-11-30T17:51:26.018507+08:00", "sms\_status": null, "sms\_delivered\_at": null, "sms\_error\_category": null } }
* Response 200 (text/plain)
  * Body OK

#### SMS+ Profile Updated \[POST]

*   Request (application/json; charset=utf-8) 200

    * Attributes (object)
      * `timestamp` (string) - 觸發時間
      * `topic` (string) - 事件類別
      * `data` (object) - 事件資料
        * `pnp_setting_id` (number) - 簡訊+ 範本 ID
        * `pnp_setting_name` (string) - 簡訊+ 範本名稱
        * `phone_number` (string) - 聯絡人的電話號碼。可能為 E.164 格式（如 `+886912345678`）或 SHA256 雜湊的 E.164 格式（64 個十六進位字元），取決於原始 API 請求使用的格式。
        * `source` (enum) - 事件來源
          * pnp - 來自 PNP 綁定流程的事件
          * sms - 來自 SMS 綁定流程的事件
        * `line_uid` (string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
        * `customer_id` (string, nullable) - 第三方系統之用戶識別碼
    *   Headers

        CrescLab-Idempotency-Key: 191fecc0b2644d3f875ck84b1340b645\
        CrescLab-Signature: 0ff864b8f3bf8353e9a8e0b62f17da3be16cb66adf655361da482be93c836df5
    * Body

    { "timestamp": "2022-05-09T16:51:48.320132+08:00", "topic": "pnp.profile\_updated", "data": { "pnp\_setting\_id": 0, "pnp\_setting\_name": "testing name", "source": "pnp", "phone\_number": "+886912345678", "line\_uid": "U0123456789abcdef0123456789abcdef", "customer\_id": null } }
* Response 200 (text/plain)
  * Body OK

#### Prize Points Added \[POST]

*   Request (application/json; charset=utf-8) 200

    * Attributes (object)
      * `timestamp` (string) - 觸發時間
      * `topic` (string) - 事件類別
      * `data` (object) - 事件資料
        * `prize_name` (string) - 獎項名稱
        * `points_id` (string) - 獎項訊息的唯一識別 ID，可依此識別同一筆點數新增的請求
        * `points_category` (string, nullable) - 點數種類，預設為 null，有在 MAAC 上設定才會有值
        * `line_uid` (string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
        * `customer_id` (string) - 第三方系統之用戶識別碼
        * `points_memo` (string) - 贈點原因
        * `points_count` (number) - 需要派發的點數數值
        * `points_expire_date` (string, nullable) - 點數有效期限，ISO 8601 格式，預設為 null，有在 MAAC 上設定才會有值
    *   Headers

        CrescLab-Idempotency-Key: 191fecc0b2644d3f875ce84b1340b645\
        CrescLab-Signature: 0ff864b8f3bf8353e9a8e0b62f17da3be16cb66adf653561da482be93c836df5
    * Body

    { "timestamp": "2021-11-29T15:43:26.582968+08:00", "topic": "prize.points\_added", "data": { "prize\_name": "Prize Name", "points\_id": "550e8400-e29b-41d4-a716-446655440000", "line\_uid": "U7ee656c217619d09bb51cd0198df98fd", "customer\_id": "xxx", "points\_memo": "reason", "points\_count": 999, "points\_expire\_date": "2022-01-01T00:00:00+08:00", "points\_category": "points category" } }
* Response 200 (text/plain)
  * Body OK

#### Message First Open \[POST]

以 OpenAPI 推送訊息時，必須帶有 `event_id` 才會有此 webhook event。

*   Request (application/json; charset=utf-8) 200

    * Attributes (object)
      * `timestamp` (string) - 觸發時間
      * `topic` (string) - 事件類別
      * `data` (object) - 事件資料
        * `message_type` (string) - 訊息種類，broadcast/openapi
        * `message_id` (number) - 訊息的識別 ID，當 `message_type` 為 openapi 時，此欄位值為 `event_id`
        * `line_uid` (string) - 聯絡人於LINE官方帳號中的唯一用戶ID，長度為33字元
        * `customer_id` (string) - 第三方系統之用戶識別碼
    *   Headers

        CrescLab-Idempotency-Key: 191fecc0b2644d3f875ce84b1340b645\
        CrescLab-Signature: 0ff864b8f3bf8353e9a8e0b62f17da3be16cb66adf653561da482be93c836df5
    * Body

    { "timestamp": "2022-08-31T17:17:13.064761+08:00", "topic": "message.first\_open", "data": { "message\_type": "broadcast", "message\_id": 999, "line\_uid": "U7ee656c217619d09bb51cd0198df98fd", "customer\_id": "xxx" } }
* Response 200 (text/plain)
  * Body OK
