---
description: >-
  Unify customer contact profiles in MAAC across LINE and SMS using CDH Customer
  360. Covers identity matching, profile merging logic, segment filters, tags,
  phone handling, migration, and audit logs.
---

# PRD — Contact Profile Unification (MAAC)

## Contact Profile Unification in MAAC (LINE + SMS)

Unify customer contact profiles across **LINE** and **SMS** inside **MAAC**, powered by **CDH Customer 360**.

This work enables:

* **Identity resolution / identity stitching** across channels (LINE UID, phone, customer ID).
* **Deduplicated messaging** (avoid sending LINE + SMS twice to the same person).
* **Omnichannel segmentation** and **personalized customer journeys** with a single unified profile.

### Related specs (recommended reading)

* Cross-product PRD: [PRD Profile unification (CAAC & CDH)](prd-profile-unification-caac-and-cdh.md)
* System design: [Profile unification](../system-design/profile-unification.md)
* Contact matching logic (import/update): [Feature Description｜Contact Field Explanation and Matching Logic – Crescendo Lab Help Center](../feature-overview/feature-description-contact-field-explanation-and-matching-logic-crescendo-lab-help-center.md)

### Key terms used in this PRD

* **Unified contact profile**: one person’s Customer 360 profile.
* **Channel entity**: channel-level identity (e.g., LINE user, SMS/phone).
* **Unify keys**: identifiers used for matching (e.g., `line_uid`, phone, `customer_id`, `connect_id`).
* **Profile merge / unification logic**: rules that decide when entities become one profile.
* **Syncing / coalesce rules**: field-level and tag-level merge behavior after unification.

***

For cross-product profile unification across **CAAC + CDH**, see:

* [PRD Profile unification (CAAC & CDH)](prd-profile-unification-caac-and-cdh.md)
* (Legacy Google Doc) https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit

This PRD will only focus on the contact profile unification in MAAC - mapping profiles across channels in MAAC.

| **PM owner** [Lydia Hou](mailto:lydia.hou@cresclab.com)**Eng owner** [Jalex Chang](mailto:jalex.chang@cresclab.com)**PD owner** [Johny Hsieh](mailto:johny.hsieh@cresclab.com) | **💬Slack channel**\*\*⏱️Asana\*\*\*\*📂Notion\*\* |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------- |

**Version history**

| Version | Date       | Description                                                                                                                                                 | Editor                                     |
| ------- | ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| Ver. 1  | 2024-04-16 | Draft done                                                                                                                                                  | [Lydia Hou](mailto:lydia.hou@cresclab.com) |
| Ver. 2  | 2024-06-05 | Adjusted whole PRD to fit [new MAAC process](https://docs.google.com/document/d/1G3-92hP_-e4T5jVDeF3PsxW4kolFBQE-lrBd60NYEGI/edit#bookmark=id.jhi0qxfy138b) | [Lydia Hou](mailto:lydia.hou@cresclab.com) |

**Release notes**

Contact profile unification provides a 360-degree understanding of your customer across communication channels (e.g. LINE, SMS). Help brands to build continuous customer journeys and engage customers with full context and personalization.

![Customer 360: unified contact profile across LINE and SMS in MAAC](<../../../.gitbook/assets/Unknown image (148)>)

**Product Goal**

* Our ultimate goal in MAAC is to build an omnichannel MA, which could provide a seamless marketing engagement with contacts across channels, products, and 3rd party tools.
* To achieve the product goal, contact profile unification is a foundation for **CDH segment** for both **broadcast** and **journey.**
* These features emphasize personalization, which will be\*\* a highlight feature in Next Level MAAC\*\*.

**Overall scope**

**What needs to be considered**

To have a unified contact profile (stored in CDH), we need to consider below:

1. Types of unification: Determination of data mapping scope, 5 types
2. no merge
3. CAAC has unified profile, not synced to MAAC \[UI: [CAAC UI](https://www.figma.com/design/k0XwP83RAV16nVdyFx7crb/Omnichannel-inbox?node-id=6781-36205\&t=SnUy9bRr5jTJRcJi-4)] → supported in Q2
4. **MAAC has unified profile, not synced to CAAC \[UI: MAAC UI] → M TBD → M1（**[**Thread**](https://chatbotgang.slack.com/archives/C0774K3DEQP/p1718602389991849)**）** 1. Need migration UI/flow → [Johny Hsieh](mailto:johny.hsieh@cresclab.com)to design → BE to scope
5. b+c, separately
6. CL has unified profile (across CAAC and MAAC) \[UI: [CDH module](https://www.figma.com/design/k0XwP83RAV16nVdyFx7crb/Omnichannel-inbox?node-id=6781-34792\&t=SnUy9bRr5jTJRcJi-4)] \[default onboarding] → M1 BE
7. Syncing logic
8. **SMS+LINE** 1. Contact/Profile → M1 QA [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit) 2. Field → M1 QA [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit) 3. Tag→ M1 BE 4. Phone → M1 BE
9. MAAC+CAAC 1. Contact/Profile → M2 [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit) 2. Field → M2 [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit) 3. Tag→ M2 4. Phone → M2
10. Contact import logic
11. \*\*Import via UI →\*\*M1
12. Import via API → [PRD - Profile API](https://docs.google.com/document/d/1JNTwiI0hXYqHeHEo3rZaWE7m4m9rCcO6LOk-TphACL4/edit)
13. Migration/ admin changes
14. **SMS+LINE** 1. New client flow → default on [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit) → M1 QA 2. Migration flow → progress status [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit) → M1 QA 3. Ways to change profile merging logic for future profiles → M1 QA 4. Ways to undo merged profiles → by day by brand snapshot restore 工單 \[CS] → M1 QA
15. MAAC+CAAC 1. New client flow → default on [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit) → M2 QA 2. Migration flow → progress status [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit) → M2 QA 3. Ways to change profile merging logic for future profiles → M2 QA 4. Ways to undo merged profiles → by day by brand snapshot restore 工單 \[CS] → M2 QA
16. Behavior for existing features
17. Display profile fields 1. Display in current MAAC fields (including tag design) → M2 2. Remove CDH tag tab → M2 3. Display all [CL customer](https://docs.google.com/spreadsheets/d/15yRH-nOc0z4ikZpJoLDD8x9AuPWQNWmqfzcDSFvZtkg/edit#gid=937614967) columns in MAAC → M TBD
18. Search for contact by profile fields (include tag) → covered by CQS, desired → M TBD
19. Apply in segments → use MAAC for now, future to read CDH segment 1. Remove CDH filter → M2 2. Add LINE UID filter in segment → M1 FE 3. Add tag created source on UI in segment & tag management →M2 4. Add Region, City, age, birthday, gender, company, account manager, member\_levelfilter in segment → M TBD
20. Trigger and action with CDH profile (journey and richmenu) 1. Using tag for trigger journey and richmenu → M2 QA 2. Add tag created source on UI in journey and richmenu → M2
21. Visualization for dashboard and reports → M TBD
22. Data 1. **Import & Export via UI →**
    1. Import: M1 keep using separate contact import for LINE and SMS → M TBD? or M1?
    2. Export: M1 keep using segment as workaround → M TBD? or M1? 2. Import & Export via API\&BQ → [PRD - Profile API](https://docs.google.com/document/d/1JNTwiI0hXYqHeHEo3rZaWE7m4m9rCcO6LOk-TphACL4/edit) 3. Import & Export via Native integration → M TBD
23. Data exports (webhook event) 1. CDH tag add/remove webhook → M2 BE
24. Edge cases
25. Error handling when we couldn’t unify some profiles 1. support manually unify with connect\_id [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit#heading=h.7z5imn1sorpi) M1 QA
26. When it’s unified wrongly, what can/should users do? 1. supported by audit log with [metabase](https://play.cresclab.com/dashboard/128-cdh-auditlog?date_range=2024-04-23~2024-05-03\&maacbotid=1\&maaclineuid=U463c4fc03e3b9493c3fe8b1b37b4343f\&caac_channelid=3\&caac_memberuid=\&known_member_id=) \[CS] → M1

**User story**

1. \[M1] As a marketer, I want to deliver regular marketing campaign information but prevent repeat msgs across different channels to the same contact, to ensure my budget doesn’t waste on repeated information and prevent increasing blocking rate due to too bother contacts.
2. Use case breakdown ([Reference for details](prd-contact-profile-unification-maac.md#_rijja85hhteb)) 1. Case 1: As a marketer, I want to reach entities, who have blocked my LINE OA, through SMS to increase the active LINE friends. 2. Case 2: As a marketer, I want to reach entities, who haven't been reached through a LINE campaign, through SMS, to increase the LINE engagement（wake up sleeping friends) 3. Case 3: As a marketer, I want to reach entities, who receive a LINE message but don't open it yet, through SMS, to ensure the important message deliver to the consumer.
3. capability 1. Send SMS but exclude the segment that already sends LINE msg 2. Send LINE but exclude the segment that already sends SMS msg
4. \[M2] As a marketer, I want to broadcast but prevent wasting my budget on the black contact list 黑名單 from service/sales agents in CAAC.
5. capability 1. CDH tag filter in segment for broadcast
6. \[M2] As a marketer, when the contact join LINE OA from specific store, I want to auto send CAAC store specific prize to encourage the contact to shop in store again.
7. capability 1. CDH tag trigger journey
8. \[M1] As a marketer, I want to map the phone number from CRM (import via API/UI) with MAAC LINE friends with phone number to get a more complete profile to better segmentation, so that I could enlarge marketing performance (increase click rate with a more personalized message) with both SMS and LINE.
9. capability 1. import phone via API/UI and mapping with LINE contact
10. \[M1] As a PM in CL, I want to map the phone and LINE contact and use the contact tier pricing (instead of LINE contact tier), so that I could better reflect the contact tier pricing and increase the TTL revenue.
11. capability 1. map the phone and line entity to 1 contact
12. \[M2] As a marketer, I want to easily find the tags created from CAAC/API in the **segment**, so that I could choose correctly when I am creating a segment for service/sales purposes or a segment for CRM/CDP purpose(via API).
13. For example 1. \[CAAC] after-service/sales care, \[API] VIP in EC
14. capability 1. show tag-created source in segment
15. \[M2] As a marketer, I want to easily identify the tag-created source in the **tag management**, so that I won’t wrongly delete the tag which is service/sales purposed or 3rd-party tools generated via API.
16. capability 1. show tag-created source in tag management
17. \[M2] As a CS, I don’t want to let marketers see a repeated tag tab after profile unification, which might created a great confusion.
18. capability 1. contact profile with 1 tag tab
19. \[M TBD] As a marketer, I want to add/remove tag batch
20. capability 1. search and filter by tag on contact page
21. Gordon’s random notes 1. contacts page: search and filter by tag -> export for further analysis \[segment可解] 2. contacts page: search and filter by tag -> update tag to do data clean up \[]
22. \[M TBD] As a marketer, I want to detect someone blocked LINE OA and wish there’s a way to win them back.
23. block OA trigger + send SMS in journey + SMS delivered
24. \[M TBD] As a marketer, I want to send the msgs with auto channel fallback during Black Friday, Strawberry season to maximize engagement
25. … LINE unread after X period → send SMS
26. … LINE read but no conversion after X period → send SMS
27. \[M TBD] As a marketer, I want to send the msgs with manually choosing channel to minimize cost / maximize engagement, but at the same time ensure the information deliver to contacts.
28. contact has both SMS anl → send via that channel
29. \[M TBD] As a marketer, I want to show different richmenu to different member level contacts, to let VIP experience a sense of honor, and common contact have incentives to level up.
30. memd LINE → select 1 to send by cost (LINE) or engagement (SMS)
31. contact only has 1 channeber level to trigger richmenu change
32. \[M TBD] As a marketing manager, I want to see the performance of profile mapping rate across MAAC x CAAC, so that I could better plan for marketing strategy on channels (1 contact have LINE/FB/IG/SMS channel reachable or not)
33. Admin center to show mapping rate
34. \[M TBD] As a marketing manager, I want to know the performance of marketing campaign more precisely (not 1 contact be counted repeatedly in different channels)
35. after profile unification: we could identify same Lydia
36. timeline 1. before: line UID + 3p customer id 2. now: phone # vs line uid + 3p customer id 3. future: + FB, + IG, (+ WhatsApp), (+web behaviour)

**Milestone 1 LINExSMS profile unification**

**User story**

* 1, 4, 5

**Goal**

* Contact profile unification across phone and LINE contact to increase the contact base of sending both LINE and SMS msg, which could be **an upselling point of SMS to existing MAAC clients**.

**Background**

* After [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit), we already have the structure of contact profile unification and we need to pick up the cross-channel level within MAAC (LINExSMS) to enlarge the value within MAAC.

**Success metric**

* Adoption
  * ## of unique organizations enabled contact profile unification rule setting on MAAC
* Usage (with benchmark before & after usage growth)
  * ## of segment using LINE\_uid and LINE following status filter

**Milestone 2 MAAC x CAAC profile unification**

**User story**

* 2, 3, 6, 7, 8

**Goal**

* Contact profile unification across MAAC and CAAC to leverage cross-product to empower the bundle use case, which could be **a selling point of the bundle to existing MAAC clients/new CAAC clients**.

**Background**

* After [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit), we already have the structure of contact profile unification and we need to apply it to MAAC to complete the cross-product level across MAAC and CAAC to enlarge the value of bundle.

**Success metric**

* Adoption
  * ## of unique organizations enabled contact profile unification rule setting on admin center
* Usage (with benchmark before & after usage growth)
  * ## of CDH tags using for journey, richmenu, segment

**Feature spec**

## 1c. MAAC has a unified profile, not synced to CAAC

**\[UI: MAAC UI 待補]**

* We decided to have a separate setting in MAAC to set up the profile unification rule in MAAC.
* This setting is for the unification between LINE and Phone contact within MAAC

## 1e. Types of unification: CL has a unified profile (across CAAC and MAAC) \[default onboarding]

* Contact profile unification logic followed:
  * [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit#heading=h.d1tylm7bclh0) feature spec B) Contact profile unification logic
  * [CL Customer 360](https://docs.google.com/spreadsheets/d/15yRH-nOc0z4ikZpJoLDD8x9AuPWQNWmqfzcDSFvZtkg/edit#gid=389794410)Unification logic tab
* We decided (aligned w/PM and eng) to apply 全域設定 of CDH to MAAC. And to encourage clients to complete the setting, we have the redirect behavior as below form.

| The button in MAAC appstore                                                                                                                                                               | ![](<../../../.gitbook/assets/Unknown image (149)>) |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| If the client haven’t activate CDH, then the button in MAAC appstore will redirect users to CDH setting.                                                                                  | ![](<../../../.gitbook/assets/Unknown image (150)>) |
| If the client already activate CDH, then the button in MAAC appstore will redirect users to [CDH Channel unification rule setting](https://platformstaging.cresclab.com/applications/cdh) | ![](<../../../.gitbook/assets/Unknown image (151)>) |

## 2ai. Syncing logic: Contact/Profile

As 1e. mentioned, the contact profile unification logic follows:

* [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit#heading=h.d1tylm7bclh0) feature spec B) Contact profile unification logic

## 2aii. Syncing logic: Field

As 1e. mentioned, the field unification logic follows:

* [CL Customer 360](https://docs.google.com/spreadsheets/d/15yRH-nOc0z4ikZpJoLDD8x9AuPWQNWmqfzcDSFvZtkg/edit#gid=389794410) Unification logic tab

## 2aiii. Syncing logic: Tag

As 1e. mentioned, the field unification logic follows:

* [CL Customer 360](https://docs.google.com/spreadsheets/d/15yRH-nOc0z4ikZpJoLDD8x9AuPWQNWmqfzcDSFvZtkg/edit#gid=389794410) Unification logic tab

## 2aiv. Syncing logic: Phone

* Context:
  * Before phone handling, we directly sync phone in the “display\_phone” field.
  * However, after we defined [CL customer 360](https://docs.google.com/spreadsheets/d/15yRH-nOc0z4ikZpJoLDD8x9AuPWQNWmqfzcDSFvZtkg/edit#gid=1977650793) and we had SMS as a new channel, we need to consider both “original\_phone” & “display\_phone” field.
* Summary:
  * Overall create member with both original & display phone, update rule have some exceptions, and follow below rule:
    * If the system can recognize that the phone has been updated from LINE, update only the LINE original phone and follow the original LINE phone process.
      * If the display\_phone does not exist, then update the display\_phone, e.g., LIFF/PNP binding, SMS bindlink (with PNP).
    * Update contact API, or agent Manual update only update display\_phone
* Details pls refer to [notion](https://www.notion.so/cresclab/Unification-of-MAAC-phone-field-b05de72954a940f28fc9c4c40e521419?pvs=4#17989c8da7814896bfbce217684641b3) , Tech ref.: [Phone handling scoping](https://app.asana.com/0/1206764649948244/1207218464794586/f)

## 3a. Contact import logic: Import via UI

* Since the import key via UI are phone, LINE\_uid, Customer\_id, and phone merging will impact on different merging logic, so we separate as below:
  * import key is phone: If the same display\_phone cannot be found, then create a new contact.
  * import key isn’t phone: If the same contact can be identified, then update the display\_phone.
* Details pls refer to [notion](https://www.notion.so/cresclab/Unification-of-MAAC-phone-field-b05de72954a940f28fc9c4c40e521419?pvs=4#17989c8da7814896bfbce217684641b3) , Tech ref.: [Phone handling scoping](https://app.asana.com/0/1206764649948244/1207218464794586/f)

## 4ai. Migration/ admin changes: New client flow

* Same as [**PRD - Profile unification (CAAC & CDH)**](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit)

## 4aii.Migration/ admin changes: progress status

* Same as [**PRD - Profile unification (CAAC & CDH)**](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit)

## 4aiii. Migration/ admin changes: Ways to change profile merging logic for future profiles

* Same as 1c. Clients could directly change the profile merging logic in MAAC, after setting, the new profile merging logic will follow new rule. \[UI: MAAC UI 待補]
* Same as 1e. Clients could directly change the profile merging logic in admin center, after setting, the new profile merging logic will follow new rule.

| [CDH Channel unification rule setting](https://platformstaging.cresclab.com/applications/cdh) in admin center | ![](<../../../.gitbook/assets/Unknown image (151)>) |
| ------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |

## 4aiv. Migration/ admin changes: Ways to undo merged profiles

* Already have the snapshot for profile, CS could create 工單 ticket for restore the profile to a certain timestamp.
* Follow the same rule, ensure MAAC profile unification also have the snapshot.

## 5c. Behavior for existing features: Apply in segments → use MAAC for now, future to read CDH segment

* Add “LINE Contacts status” as a new filtering condition
  * There will be 2 filters need to be added:
    1. Filter - LINE status:
    2. is following
    3. is not following
    4. Filter - LINE\_uid have data or not:
    5. all LINE contact （LINE\_uid have data or not）
    6. follow current all phone contact filter design
  * The Info Box with the content “Time interval is not valid for this filter” is needed.

| Add “LINE Contacts status” as a new filtering condition (After) [Design→](https://www.figma.com/design/9Aai2ZaP9iQGo62vGl9qAR/MAAC_Segment?node-id=1686-38552\&t=QiQBwusGFRZZegzr-11) |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![](<../../../.gitbook/assets/Unknown image (152)>)                                                                                                                                   |
| Detail settings for "LINE Contacts Status” filter (After) [Design→](https://www.figma.com/design/9Aai2ZaP9iQGo62vGl9qAR/MAAC_Segment?node-id=1686-39282\&t=QiQBwusGFRZZegzr-11)       |
| ![](<../../../.gitbook/assets/Unknown image (153)>)                                                                                                                                   |

## 6b. Edge cases: When it’s unified wrongly, what can/should users do?

* Already supported by audit log with [metabase](https://play.cresclab.com/dashboard/128-cdh-auditlog?date_range=2024-04-23~2024-05-03\&maacbotid=1\&maaclineuid=U463c4fc03e3b9493c3fe8b1b37b4343f\&caac_channelid=3\&caac_memberuid=\&known_member_id=)
* Follow the same rule, ensure MAAC profile unification also have the audit log with [metabase](https://play.cresclab.com/dashboard/128-cdh-auditlog?date_range=2024-04-23~2024-05-03\&maacbotid=1\&maaclineuid=U463c4fc03e3b9493c3fe8b1b37b4343f\&caac_channelid=3\&caac_memberuid=\&known_member_id=)

## 2biii. Syncing logic: Tag

* Since tag will have many actions in MAAC, so we separate the tag into inherited tag and tag to better deal with merging:
* _**inherited**_**&#x20;tag**: _tags created during unifying profiles in CDH. They are redundant and exist for UX-consistent purposes._
* _**tag**: the normal tags sent from CDH to applications._
* Tech ref.: [Tag handling scoping](https://app.asana.com/0/1206764649948244/1207218467273303/f)

|                | tag\_name does not exist                     | tag does not exist                                                                                               |
| -------------- | -------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| tags           | create tag\_tag with: 1. source: maac \|caac | create tag\_linember with: 1. source: maac \|caac 2. ref\_type: CDH 3. created\_at: now()                        |
| inherited tags | create tag\_tag with: 1. source: maac \|caac | create tag\_linember with: 1. source: maac \|caac 2. ref\_type: 'CDH\_INHERITED' 3. created\_at: copy from event |

## 5a. Behavior for existing features: Display profile fields (include tag)

* With contact profile unification:
  * In MAAC, we decided to cancel **CDH tag in profile and segment** to decrease the confusion
  * Profile

| Customer 360 (Before)                               | Customer 360 (After) [Design→](https://www.figma.com/design/4izQy6bC4QxfvTOxuFotIl/MAAC_Contacts?node-id=1072-288\&t=tNhvYHa5FsRvAuyY-11) |
| --------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| ![](<../../../.gitbook/assets/Unknown image (154)>) | ![](<../../../.gitbook/assets/Unknown image (155)>)                                                                                       |

* After contact profile unification:
  * CAAC tag could trigger journey, richmenu, and also be used in segment on MAAC, which could help bundle synergy across MAAC and CAAC.

## 5c. Behavior for existing features: Apply in segments → use MAAC for now, future to read CDH segment

* Mask CDH tag filter in Segment ([thread](https://chatbotgang.slack.com/archives/C04EDDSEV08/p1718277440001489))

| Select a way to create segment (Before)             | Select a way to create segment (After) [Design→](https://www.figma.com/design/9Aai2ZaP9iQGo62vGl9qAR/MAAC_Segment?node-id=1649-30555\&t=QiQBwusGFRZZegzr-11) |
| --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ![](<../../../.gitbook/assets/Unknown image (156)>) | ![](<../../../.gitbook/assets/Unknown image (157)>)![](<../../../.gitbook/assets/Unknown image (157)>)                                                       |

* Show the tag-created source (MAAC, CAAC, API) on **Tag Manager** list, to help clients easily identify the tag.
  * context: After learned user scenarios of 典華, agent will manually tagging on CAAC, and marketer will use CDH tag segment for using CAAC created tags. It’s important for marketers to quickly identify the tag created source on MAAC UI ([thread](https://chatbotgang.slack.com/archives/C04EDDSEV08/p1718277440001489))

| Add a “Source” column in the Tag Management list (After) [Design→](https://www.figma.com/design/cmBetlG0lD5NgzjRlGPUxN/MAAC_Tag-Manager?node-id=420-4297\&t=G6OQ7rnuYqpXJov0-11) |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![](<../../../.gitbook/assets/Unknown image (158)>)                                                                                                                              |

* Show the tag-created source (MAAC, CAAC, API) **Segment** settings, to help clients easily identify the tag.

| Add a “Source” column in the Tag Management list (After) [Design→](https://www.figma.com/design/9Aai2ZaP9iQGo62vGl9qAR/MAAC_Segment?node-id=1686-28560\&t=QiQBwusGFRZZegzr-11) |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ![](<../../../.gitbook/assets/Unknown image (159)>)                                                                                                                            |

## 5d. Behavior for existing features: Trigger and action with CDH profile (Customer Journey and Richmenu)

* Using CDH tag for trigger Customer Journey → this could be done after [2c](prd-contact-profile-unification-maac.md#_djj2v756e3n2)

| Add {Tag Source} and “Tag filtering feature” in the Tag dropdown menu for Customer Journey settings (After) [Design→](https://www.figma.com/design/ASd9RNCXm5fRW4YV0tloZK/MAAC_Customer-Journey_Handoff?node-id=5546-465\&t=2wnxgmI6fJUsh1nZ-11) |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ![](<../../../.gitbook/assets/Unknown image (160)>)                                                                                                                                                                                              |

* Using CDH tag for trigger Richmenu → this could be done after [2c](prd-contact-profile-unification-maac.md#_djj2v756e3n2)

| Add {Tag Source} and “Tag filtering feature” in the Tag dropdown menu for Richmenu settings (After) [Design→](https://www.figma.com/design/WV506pJ8jVITZCOKlD2YBC/MAAC_Richmenu-personalization?node-id=2350-32587\&t=rRSIHH4NAKrSNbBA-11) |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ![](<../../../.gitbook/assets/Unknown image (161)>)                                                                                                                                                                                        |

#### 5g. Behavior for existing features: Data exports (webhook event)

* Using CDH tag for webhook event → this could be done after [2c](prd-contact-profile-unification-maac.md#_djj2v756e3n2)

|               | CDH tag add webhook ([apidoc](https://doc.user360.cresclab.com/cdh.html#tag/Webhook/operation/contact.tag.add)) | CDH tag remove webhook ([apidoc](https://doc.user360.cresclab.com/cdh.html#tag/Webhook/operation/contact.tag.remove)) |
| ------------- | --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| tag           | o source: maac                                                                                                  | o source: maac                                                                                                        |
| inherited tag | x                                                                                                               | x                                                                                                                     |

### **Release plan**

#### **Pricing plan**

* MAAC x CAAC: no add-on pricing
* Multiple organizations: as [Crescendo Lab - New Pricing Master Sheet (2024)](https://docs.google.com/spreadsheets/d/1L0Y_gH4SSIo5ZtXSQnbgP9s5R9q5ytE9bpRZ_inP9iw/edit#gid=9243120\&range=A1)

#### **Release region**

Please check the gray out feature list ([Link)](https://www.notion.so/cresclab/Product-Availability-e9e275930be946c2b471077b02f7556e)

| - TW | - TH | - JP |
| ---- | ---- | ---- |

#### **GTM plan**

**How do users adopt**

* self-serve
  * Admin center for setting ([1e.](prd-contact-profile-unification-maac.md#_nveqdnoth54s))

**How do users troubleshoot**

* raise to CS/enable & ops \[insert steps and the info provided to troubleshoot (eg metabase)
  * [metabase](https://play.cresclab.com/dashboard/128-cdh-auditlog?date_range=2024-04-23~2024-05-03\&maacbotid=1\&maaclineuid=U463c4fc03e3b9493c3fe8b1b37b4343f\&caac_channelid=3\&caac_memberuid=\&known_member_id=)

###

### **Development Documents**

#### **Planning docs**

* [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit#heading=h.7z5imn1sorpi)

#### **Design docs**

* [CAAC\_Profile unification](https://www.figma.com/design/k0XwP83RAV16nVdyFx7crb/Omnichannel-inbox?node-id=4653-25760\&t=TGlZEvCDPJsl0emN-0)
* [MAAC\_Customer 360](https://www.figma.com/design/4izQy6bC4QxfvTOxuFotIl/MAAC_Customer-360-and-Segment_Handoff-\(CDH-Partial\)?node-id=1070-37617\&t=VC1DPXZ4b7sVRbgM-0)
* [MAAC\_segment](https://www.figma.com/design/9Aai2ZaP9iQGo62vGl9qAR/MAAC_Segment?node-id=1649-30555\&t=mT6GogLpJrrAu0sg-11)

#### **Technical docs**

* [Tag handling scoping](https://app.asana.com/0/1206764649948244/1207218467273303/f)
* [Phone handling scoping](https://app.asana.com/0/1206764649948244/1207218464794586/f)

#### **QA docs**

* [Test Case - Profile unification (MAAC)\_240612](https://docs.google.com/spreadsheets/d/19878BU_XqFtlAP_1Ro0WFiBroyiJ_w3HXQDFSGpLQZE/edit#gid=502134957)

###

### **Discussion and open questions**

**Gordon’s playground**

**Problem alignment**

Our clients collect their customer data (contact profile) from MAAC, CAAC, and 3rd party integrations. Currently Lydia from MAAC, Lydia from CAAC, Lydia’s phone number, Lydia from Facebook, and Lydia from Salesforce are treated as different contacts in both MAAC and CAAC. They should be the same Lydia profile. When data of the same “Lydia” is scattered, it makes it hard for precision marketing, or nor allowing CAAC agents to optimize interaction with this contact’s full engagement history.

![](<../../../.gitbook/assets/Unknown image (148)>)

**What needs to be considered**

In order to have a unified contact profile (stored in CDH), we need to consider 4 things

1. Types of unification: Determination of data mapping scope, 5 types
2. no merge
3. CAAC has unified profile \[UI: CAAC UI]
4. MAAC has unified profile \[UI: MAAC UI] → Lydia says don’t support, Gordon says need discussion
5. b+c, separately
6. CL has unified profile (across CAAC and MAAC) \[UI: CDH module] \[default onboarding]

* Merging logic
  * Contact/Profile merging logic → [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit)
  * Field merging logic → [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit)
  * Tag merging logic
  * Phone merging logic
* Contact import logic
  * Import via UI
  * Import via API → [PRD - Profile API](https://docs.google.com/document/d/1JNTwiI0hXYqHeHEo3rZaWE7m4m9rCcO6LOk-TphACL4/edit)
* Migration/ admin changes
  * New client flow → default on [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit) A
  * Migration flow → progress Status (Time estimation for profile data sync：10K contact/min, 2M contact/200 min) [PRD - Profile unification (CAAC & CDH)](https://docs.google.com/document/d/1mfj3p1ZMtFEacPB0L2WhSo5ieoHss2-JSoEJ1bZ6TsM/edit) B![](<../../../.gitbook/assets/Unknown image (162)>)
  * Ways to change profile merging logic for future profiles
  * Ways to undo merged profiles → snapshot restore 工單 \[CS] → need to ensure MAAC snapshot
* Behavior for existing features
  * Display profile fields (include tag)
  * Search for contact by profile fields (include tag) → covered by CQS, desired
  * Apply in segments → use MAAC for now, future to read CDH segment
    1. Remove CDH filter
    2. Add LINE UID filter in segment
  * Trigger and action with CDH profile (journey and richmenu) → tag workaround for now, future to use CDH field
  * Visualization for dashboard and reports → Not in scope
  * Data exports and imports (BQ, API, native integrations) → in profile API scope
* Edge cases
  * Error handling when we couldn’t unify some profiles
    1. connect id
  * When it’s unified wrongly, what can/should users do?
    1. supported by audit log with [metabase](https://play.cresclab.com/dashboard/128-cdh-auditlog?date_range=2024-04-23~2024-05-03\&maacbotid=1\&maaclineuid=U463c4fc03e3b9493c3fe8b1b37b4343f\&caac_channelid=3\&caac_memberuid=\&known_member_id=) \[CS] → need to ensure MAAC audit log

**Scope**

**Before vs after**

1. Merging logic
2. Profile merging logic: by phone, email, customer\_id, connect\_id, LINE\_id
3. Tag merging logic: 1. **inherited tag**: tags created during unifying profiles in CDH. They are redundant and exist for UX-consistent purposes. So after merging, it will show on the profile and could be used in segment. 2. **tag**: the normal tags sent from CDH to applications. so after merging, it could trigger journey, richmenu
4. Phone merging logic: 1. Overall create member with both original & display phone 2. Updated rule have some exceptions, and follow below rule:
   1. If the system can recognize that the phone has been updated from LINE, update only the LINE original phone and follow the original LINE phone process.
   2. If the display\_phone does not exist, then update the display\_phone, e.g., LIFF/PNP binding, SMS bindlink (with PNP).
   3. Import contact (via file/API)
   4. import key is phone: If the same display\_phone cannot be found, then create a new contact.
   5. import key isn’t phone: If the same contact can be identified, then update the display\_phone.
   6. Update contact API, or agent Manual update only update display\_phone
5. Field merging logic: show the newest data
6. Contact import logic: follow 1b, 1c, 1d login
7. Migration/ admin changes
8. Migration flow for first-time 1. Clients without contact profile unification rule setting in admin center, then nothing happen. 2. Clients with contact profile unification rule setting in admin center,
   1. will merge the LINE channel entity with phone channel entity
9. Ways to change profile merging logic for future profiles 1. Clients change the contact profile unification rule setting in admin center.
10. Ways to undo merged profiles → cannot do so
11. Behaviour for existing features
12. Search for contact by profile fields (include tag)
13. Display profile fields (include tag)
14. Search and display for segments → use MAAC for now, future to read CDH segment
15. Trigger and action with CDH profile (journey and richmenu) → tag workaround for now, future to use CDH field
16. Visualization for dashboard and reports → Not in scope
17. Data exports and imports (BQ, API, native integrations) → in profile API scope
18. Edge cases
19. Error handling when we couldn’t unify some profiles 1. connect id
20. When it’s unified wrongly, what can/should users do?

—-no use

* Dependency user stories:
  * 億進:
    * Avoid sending both SMS and LINE messages to the same user who has already interacted. Manually remove the interacted parties before sending.
  * 美科:
    * Brief type (sending LINE and SMS synchronously, sending SMS once again the day after sending LINE); Send SMS again if there is no interaction on LINE for several days.
    * Hope to send LINE first and then SMS to save costs. (Currently divided into two packages for operation)
  * ASO:
    * Expecting to use Journey to send LINE first, then send SMS according to the value of customer repurchase.
    * Hope to track the number of clicks on short URLs and store consumption records, and send a second SMS to those without behavior tracking.

####

####

#### Solution of User Story 1 (by Jalex)

![](<../../../.gitbook/assets/Unknown image (163)>)

**Who could be collected in a segment?**

1. Entity which follows Line OA => A, B
2. Entity which has phone => B, C, D

Therefore, all possible segment outputs are {A, B, C, D}.

There is no such thing called F & G in the segment because MAAC doesn't know which LINE entity and Phone entity are unified.

**User story 1:**

As a marketer, I want to deliver regular marketing campaign information but prevent repeat msgs across different channels to the same contact, to ensure my budget doesn’t waste on repeated information and prevent increasing blocking rate due to too bother contacts.

**Use cases:**

* Case 1: As a marketer, I want to reach entities, who have blocked my LINE OA, through SMS to increase the active LINE friends.
* Case 2: As a marketer, I want to reach entities, who haven't been reached through a LINE campaign, through SMS, to increase the LINE engagement（wake up sleeping friends)
* Case 3: As a marketer, I want to reach entities, who receive a LINE message but don't open it yet, through SMS, to ensure the important message deliver to the consumer.

| Use Case | Filter Condition                                                                                                                                                          | Expected Segment Output |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------- |
| Case 1   | (1) Block Line OA AND (2) Has Phone                                                                                                                                       | D                       |
| Case 2   | (1) Has Phone AND (2) exclude Line Entity Only segment (\*1).                                                                                                             | C, D                    |
| Case 3   | sol1: (1) Line Entity Only AND (2) Has Phone AND (3) exclude Open XXX message segment (2).sol2: (1) Line Entity Only AND (2) Has Phone AND (3) NOT Open XXX message (\*3) | B                       |

\*1: Excluding a line entity only segment is a must-have. Otherwise, the final output may miss some Phone entities (C in the excluded segment).

\*2: Segment doesn't provide a filter condition for "NOT Open XXX message". Therefore, we need to create another segment to make it possible.

\*3: We add another filter condition to filter "NOT Open XXX message" directly instead of excluding another segment, which is much more user-friendly.

Solution:

To achieve the user story and its 3 use cases, the segment needs to have the capability to:

1. Collect Line entity only.
2. Collect Blocked Line entity.
3. Collect NOT Open XXX message (Optional) → since will revamp segment in Q4, so not to add it now

**Meeting notes 2024-06-21**

Decisions to be aligned

1. MAAC's m2 scope (and where it needs data team help)
2. 原本 M1 7/16: 要完成 MAAC x CAAC, LINE x SMS
3. 現在 拆成 M1 M2 1. M1: LINE x SMS 2. M2: MAAC x CAAC
4. M2 MAAC x CAAC - syncs events from CDH (not direct R/W)
5. Scope: 1. 先做到 CDH tag 可以 trigger MAAC 機制，先做到 bundle (沒有 migration 的版本) 2. 跨系統可以同名，但 MAAC 要顯示 source 3. MAAC 擋掉所有 other source 的 tag deleted/created/update，僅支援 tag attach add/remove
6. 標籤重複的處理： 1. admin center 可以選擇開始合併 2. 開啟 CDH 時，針對 CAAC 重複的標籤名稱，自動加上 postfix 3. 後續，MAAC CAAC 不能建立重複的標籤
7. Tag manager: 因要考量的議題多，因此不在 Profile unification M2 處理
8. Action 1. [Poga Po](mailto:poga.po@cresclab.com)help to check if MAAC 有吃從 CDH 來的 tag source → created via, attached via 2. [Gordon Chang](mailto:gordon@cresclab.com)to prepare a list MAAC/CAAC <> deleted/created/update/tag attach add/tag attach remove 3. [Gordon Chang](mailto:gordon@cresclab.com)to ask Jalex to get data team to help on sync tag postfix 4. [Gordon Chang](mailto:gordon@cresclab.com)([Lydia Hou](mailto:lydia.hou@cresclab.com)) to 盤點是否有因為 latency 10mins 會造成的問題 5. [Gordon Chang](mailto:gordon@cresclab.com) to drive CDH tag 未來的整合和規劃

Note:

1. 未來直接讀 CDH tag
2. Data effort: Tag mgmt 的 API 需要 data 的工，其他 tag (deleted, created, attached, removed) 已有
3. 未來 Tag manager
4. \[current] tag name, contact count, expiry
5. \[new] created via, tagged via
6. 要確認 1. data 有存 created via, tagged via 2. app 端可以接收資訊
7. M2 timeline (when do maac and data team build this)
8. Caac’s timeline to reflect

Decisions aligned

Action items

Notes
