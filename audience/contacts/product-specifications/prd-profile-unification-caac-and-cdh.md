# PRD   Profile unification (CAAC & CDH)

Profile unification (CAAC\&CDH) PRD

Mapping profiles across channels and products

| **PM owner** [Jenny Chin](mailto:jenny.chin@cresclab.com)**Eng owner** [TY C](mailto:ty@cresclab.com)**PD owner** [Saha Chuang](mailto:saha.chuang@cresclab.com) | **💬Slack channel** [#proj-customer360](https://chatbotgang.slack.com/archives/C04EDDSEV08)**⏱️Asana** [CDH](https://app.asana.com/0/1204010721938900/1204023124119594)**📂Notion** |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

**Version history**

| Version | Date       | Description                                                                                                                                                                                                                                                 | Editor                                       |
| ------- | ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| Ver. 1  | 2023-12-16 | Template draft                                                                                                                                                                                                                                              | [Jenny Chin](mailto:jenny.chin@cresclab.com) |
| Ver. 2  | 2024-01-03 | Unification logic and user flow aligned. Content updated according to discussions                                                                                                                                                                           | [Jenny Chin](mailto:jenny.chin@cresclab.com) |
| Ver. 3  | 2024-03-26 | Cancel unification import in this PRD. Move it to [PRD - Profile API](https://docs.google.com/document/d/1JNTwiI0hXYqHeHEo3rZaWE7m4m9rCcO6LOk-TphACL4/edit#heading=h.7z5imn1sorpi)                                                                          | [Jenny Chin](mailto:jenny.chin@cresclab.com) |
| Ver. 4  | 2024-04-23 | Cancel ‘change unified profile’ Update note data structure to avoid merge conflict. The note optimization spec is in [PRD - Note optimization](https://docs.google.com/document/d/14-FKj5JPAdnUw83xd-4xqen63BHxdgj1ElptNg9EJr4/edit#heading=h.wp4lywq1pi6a) | Person                                       |

**Release notes**

Profile unification provides a 360-degree understanding of your customer across communication channels and systems. Help brands to build continuous customer journeys and engage customers with full context and personalization.

**Goal**

* Support Apps (MAAC, CAAC) multichannel synergy value
* Improve CL product’s Enterprise readiness by providing cross-org profile unification
* Build a flexible foundation of future CDP product

**Background**

* Profile unification is a must-have when we provide omnichannel service since users expect contextual management of contacts' engagement across channels, not on independent channels.
* This was a sub-project under [PRD - Omnichannel - FB/IG](https://docs.google.com/document/u/0/d/1cf3VeGZO6C6HTw3y6NT-E2Fbbc_cdqgYoGUZT2B89XM/edit). During the project's progress, we separated it as an independent project considering its complexity and Eng ownership differences.

**Strategy**

* As the CL product suite’s complexity increased, we have more than 1 product and are growing to add more modules. We need a platform layer for efficient data exchange and management.
* The top priority of data consolidation and management would be customer data since personalization is a core value for all CL’s products. That’s why we built CDH.
* CDH’s short-term to mid-term goal:
  * short-term: internal product for supporting CL product suite’s contact data management and acting as a segment engine.
  * mid-term: an independent CDP product
  * long-term: in discussion.
* Break down the short-term goal, the themes include:
  * Contact data sharing across CL products to enhance product bundle value
  * Support profile unification for omnichannel strategy
  * Consolidate and exchange engagement data from CL products to support personalized engagement on Apps
  * Enable data exchange with 3rd party systems to support more personalized engagement on Apps
  * Provide diverse filters and AI models for segmentation and export to CL Apps or 3rd party system for personalized engagement
* This PRD scope is under Theme 2, please see [PRD - Omnichannel - FB/IG](https://docs.google.com/document/u/0/d/1cf3VeGZO6C6HTw3y6NT-E2Fbbc_cdqgYoGUZT2B89XM/edit) for omnichannel strategy and details

**Scope**

* In scope
  * Profile unification within single product by up to 3 unify keys
  * Profile unification across two products by up to 3 unify keys
  * Profile unification across multiple orgs and two products by up to 3 unify keys
  * Provide profile change audit log through CS/Metabase
  * Cross-products “application > CDH” page
* Out of scope (future extension)
  * More than 3 unify keys
  * Probabilistic mapping
  * Display profile change audit log on UI
  * Profile unification (MAAC) [PRD - Profile unification (MAAC)](https://docs.google.com/document/d/1-H6hKZ1Y8OV5_OHpl1ATiBCemVIS5DcCTIpXeG4Fmfw/edit)

**User story**

* As a service agent, I want to interact with customers with full context across channels and systems, so I can tailor the service for better customer satisfaction
* As a marketer, I want to use 360-degree profile data to facilitate cross-channel personalized customer journeys to enhance marketing ROI

**Success metric**

* Adoption
  * ## of unique orgs enabled unification rule setting on CAAC
  * ## of unique orgs enabled unification rule setting on CDH
  * ## of orgs import unify key data through OpenAPI
  * **Success criteria: 20% unique org adopted profile unification**

**Glossary definition**

Reminder: Update the [Product Dictionary](https://www.notion.so/cresclab/08666630ee444b44b349bdb60ec40c19?v=2281968133d64b11b25d206dd86780d4\&pvs=4)

| **Product term** | **Code term** | **Definition**                                                                                                                |
| ---------------- | ------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| unify\_scope\_id |               | Each CAAC organization or MAAC organization has its own "unify\_scope\_id" which is used to define the scope mapping profiles |
| Unify Key        |               | 1\~3 profile columns chosen by users used to mapping profile                                                                  |
| Contact profile  |               | Org-level unified contact profile that has been consolidated from multiple channel entities.                                  |
| Channel entity   |               | Channel-level contact data                                                                                                    |
| Unmerge profile  |               | The action used to clean all unify keys in an entity profile and make it an independent contact profile.                      |

**Feature spec**

**A) Profile unification architecture**

* **CDH as the profile unification center**
  * Both CAAC and MAAC use CDH as profile unification center by mapping \<unify\_scope\_id> and
    * unify\_scope\_id: an org-level value to define unify scope which is stored in CDH
    * unify key: 1\~3 profile columns chosen by users used to mapping profile
    * distinct key: 1 optional choice from the selected unify keys. This is the distinct value to specify different contacts even if they share other unify keys.(cancel due to technical complexity)
  * This is a default enabled function for both product users. (no need to switch on)
  * Note: This will not affect the future extension for CDH to become an independent product. It's standalone sales depend on features accessibility

![](<../../../.gitbook/assets/Unknown image (142)>)

* **Determination of data mapping scope**
  * CDH uses \<unify\_scope\_id> to define the unification scope.
    * For single organization
      * MAAC and CAAC have their own unify\_scope\_id for single app profile unification
      * If a user integrates apps with CDH, the system updates both apps with the same unify\_scope\_id.
      * If a user disconnects apps with CDH, the system updates each app with different unify\_scope\_id.
    * For multiple organizations
      * If users want to sync profile data across multiple organizations, this should be confirmed through contract, then CS creates a support ticket to identify the organizations. The progress for unification from ticket-request would be notified by CS manually.
      * Data team will manually update all the identified orgs with the same unify\_scope\_id.

![](<../../../.gitbook/assets/Unknown image (143)>)

**B) Profile unification logic**

* **unify scope and Unify key**
  * unify\_scope\_id: an org-level value to define unify scope which is stored in CDH
  * unify key: 1\~3 profile columns chosen by users used to mapping profile
* **Unification**
  * CDH specifies the same contact, by mapping \<unify\_scope\_id> and , and unifies their profile data.
  * After unification, all the data updates will be synced across these channel entity profiles
  * **Time estimation for profile data sync：10K contact/min, 2M contact/200 min**

![](<../../../.gitbook/assets/Unknown image (144)>)

* **Profile Coalesce Preference**
  * During the case that\*\* one contact profile\*\* consists of **multiple channel entities**, we handle the coalesce by
    * Priority:

1. Pick Not NULL values instead of recentest-but-NULL values
2. Pick the later coming one. That is, priority is given to the data value which was updated most recently

* workflow use case:
  * When there are two entities merged into one contact profile. The process takes preference on the not null value first, then later updated value.
  * When the user edits on the UI which displays two channel entities, I can erase the specific attribute to be NULL. The process erases the two entities' attributes.
* when does the workflow works:
  * CAAC or MAAC : fetches profile for any reason (re-initial member profile after unification changed, contact profile api)
  * CDH : does initial member
* **De-sync**
  * **Unmerge profile 取消合併**
    * Users can use “unmerge profile” to clean all unify keys (except LINE uid) in an entity profile and make it an independent contact profile.
    * After profile unmerged, all profile columns remain the same except unify keys.
    * Flow: click “unmerge profile” -> confirm clean up all unify keys -> become an independent contact profile with empty unify keys
*
  * \*\* Change unified profile 更改合併聯絡人 (Canceled)\*\*
    * Users can remove a channel entity from an existing profile and merge it with another existing profile.
    * The action will remove all column data except channel entity data to merge with the other profile.
    * Flow: click “change unified profile” -> choose the unify key column (except LINE uid) for mapping -> enter the unify key value -> merge with another existing profile.

![](<../../../.gitbook/assets/Unknown image (145)>) ![](<../../../.gitbook/assets/Unknown image (146)>)

**C) Contact profile change**

* Adjust display name rule
  * Default {display\_name} is empty. Insert original name to show on display name column. When {display\_name} is empty, unified contact profile will show the channel's original name.
  * When edit {display\_name}, this column will be unified. So each unified profile will show the same name.
* Add column to contact profile
  * Connect id: a manual input column can be used as an unify key to specify which channel entities are the same contact.
  * Permission
    * CAAC: follow existing [role permission](https://docs.google.com/spreadsheets/d/15F7k29bXL98UPI0AihHOM93h2_AKb-r_G89j3_ml2t8/edit?pli=1#gid=203101028), only primary agent and above roles can edit.
    * MAAC: out of scope. add it when 2024Q2 deal with MAAC profile unification. So does the connect\_id display profile.
* Update contact profile layout by org-level contact profile with channel entity data
  * Org-level contact profile
    * The unified data do describe a contact’s 360-degree information. See [Customer 360](https://docs.google.com/spreadsheets/u/0/d/15yRH-nOc0z4ikZpJoLDD8x9AuPWQNWmqfzcDSFvZtkg/edit)-Contact profile tab for columns.
    * **This level’s data editing will affect all connected channel entities**
    * **Note: If user change unify\_key attribute’s value. Apps cannot modify its db, it should leave CDH to handle it.**
  * Channel entity data
    * Each channel entity profile keeps the channel-original data and unify keys.
    * See [Customer 360](https://docs.google.com/spreadsheets/u/0/d/15yRH-nOc0z4ikZpJoLDD8x9AuPWQNWmqfzcDSFvZtkg/edit)-Channel entity tab for columns.

![](<../../../.gitbook/assets/Unknown image (147)>)

**D) Unification rule settings**

* **CAAC unification rule setting**
  * This setting applies to CAAC only.
  * **CAAC: Org setting > Channel > Unification**
    * Unify key: user can choose up to 3 unify keys, contact profiles mapped by each one of them will be unified.
      * Drop down menu selection: No, Phone, email, customer id, LINE uid, Connect id
      * Default = no
    * Setting confirmation: When saving the editing, pop up an alert modal to confirm with user
* MAAC unification rule
  * setting: out of scope. add it when 2024Q2 deal with MAAC profile unification
  * Plan: Add “Data” to account setting
* **CDH unification rule setting**
  * This setting will overwrite the setting on each app and apply to both apps.
  * Add a cross-product “application” page for all application settings and management. CDH will be the first app on this page.
  * **Setting flow: Cross-product application page > CDH module > Unification rule setting**
    * First time installation
      * User click CDH module > install
      * Complete installation steps with unify key setting
      * When all installation steps are completed, the CDH is connected with a user-defined unify key setting. This setting will overwrite the setting on each app.
    * Change unification rule setting
      * User click CDH module > details
      * User click Unification rule setting > edit
      * When users apply the new unify key settings, the system merges the profiles by new defined unify keys.
  * **Disconnect flow:**
    * User click CDH module > details
    * User click Disconnect
* When users confirm the disconnection, the used-to-been-connected-orgs still share the same unify\_keys but under different unify\_ scope\_id. That is, all used-to-been-connected-orgs are intra-org unified.

**F) Audit log for profile unification**

* In scope accessibility - Provide by CS
  * [Audit log](https://play.cresclab.com/dashboard/128-cdh-auditlog?date_range=2024-04-23~2024-05-03\&maacbotid=1\&maaclineuid=U463c4fc03e3b9493c3fe8b1b37b4343f\&caac_channelid=3\&caac_memberuid=\&known_member_id=) includes , ,
  * When client’s have needs, they raise request to CS with timeframe needed
  * Eng create a metabase dashboard for CS to check (export csv)
* Future accessibility - Visible on UI
  * Add \<changed by whom/which event>
  * Out of scope. Need further discussion and planning.

**Release plan**

**Release region**

Please check the gray out feature list ([Link)](https://www.notion.so/cresclab/Product-Availability-e9e275930be946c2b471077b02f7556e)

| - TW | - TH | - JP |
| ---- | ---- | ---- |

**Development Documents**

**Design docs**

* Design doc
  * [Profile unification](https://www.figma.com/file/k0XwP83RAV16nVdyFx7crb/Omnichannel-inbox?type=design\&node-id=4765%3A41125\&mode=design\&t=BHmMrRrff4H0gYDa-1) (20240207)
* Prototype

**Technical docs**

* BE design doc
  * Latency
    * Modify contact profile: 3 \~ 5 seconds
    * Modify unify key:
      * Overall update org’s profile (estimating)
      * Query specific 1 profile: < 1 min
    * Unmerge entities:
      * < 1 mins
    * Change unify key value of the member
      * Overall update org’s profile (estimating)

**References**

* [unification logic candidates](https://chatbotgang.slack.com/archives/C04EDDSEV08/p1702453311876849)
* [existing products](https://chatbotgang.slack.com/archives/C04EDDSEV08/p1702471946244039)

**QA docs**

* [Test case](https://docs.google.com/spreadsheets/d/1iz28JaHglO0DaHSmTPb98777x6wbgRU7srsoAeu_Y9I/edit#gid=502134957)

**Discussion and open questions**

**Keep Distinct Key or not**

* Test Cases:
* setting: distinct\_key(c\_id), unify\_key(mobile)
  * A : dk(c\_id=1), mobile=0911
  * B : dk(c\_id=2), mobile=0911
  * C : dk(c\_id=NULL), mobile=0911
  * D : dk(c\_id=NULL), mobile=0911
* worflow：
  * C shows (c\_id =NULL, mobile=0911)
  * A shows (c\_id=NULL, mobile=NULL)
  * A sets (c\_id = x)
  * A sets (mobile = 0911)
* (Distinct Key) Based on TreasureData: trustable table has a unique ID, and two IDs in the table shouldn't be merged, even if other kinds of IDs indicate that they should be merged.
* **Is the distinct key a good solution?**
  * SMB:
    * might use multiple unify\_key （with OR to compose）
    * not likely to have connect\_id or CRM
  * Enterprise:
    * might have CRM and managed connect\_id
    * just use the only `connect_id` as unify key instead distinct key
