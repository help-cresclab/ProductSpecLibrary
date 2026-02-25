# Customer Journey PRD\_Phase 1 4

Phase 1 Unblock JP with more triggers, rules and actions. (conversion)

Phase 1-4 combine AI feature to be a WOW feature to attract users and make automation more user-friendly to avoid blocking rate

Roadmap driver: Lydia\
Contributors: pm team\
Slack channel: [#proj-maac-journey-v2](https://chatbotgang.slack.com/archives/C04305BTUBE)\
Overview version: [Roadmap for Customer Journey across channels](https://docs.google.com/presentation/d/10SLeF-xOn-EQFJpJekGrxj9CHaF8zyuZZHZxdWRmhjo/edit#slide=id.p)

Description:

* Customer Journey purpose, background and roadmap overview, pls refer to [Roadmap for Customer Journey across channels](https://docs.google.com/document/d/1uPBUSxNSdAzuZnD6oDQ7VI7BVjMcP2ZECx80wmQ8P00/edit#heading=h.ohkn51128mkc)
* Customer Journey phase 1 overall planning, pls refer to [Customer Journey PRD\_Phase 1](https://docs.google.com/document/d/1xzO9-7TlaObaxMfVldyIInyuATR9jjM48GSQY5KzloM/edit)
* This document will focus on Journey Phase 1-4

| Version   | Timeline  | Description  | Owner |
| --------- | --------- | ------------ | ----- |
| Version 1 | 2023.1.24 | Overall plan | Lydia |

***

## Aim & Objective

Customer journey phase 1 aims to automatically generate engagement and conversion with one-time setting, and optimize the marketing performance with AI features.

This will let us have a stronger competitive advantage, and help us to unblock Japan enterprise market.

In phase 1-4, the main features are:

* Smart sending
* Exclude Rule

***

## Release plan

When we complete the whole phase 1, then we’ll have the final release (Release in production and available to all clients.)

Overall release plan & pricing, pls refer to [Customer Journey PRD\_Phase 1](https://docs.google.com/document/d/1xzO9-7TlaObaxMfVldyIInyuATR9jjM48GSQY5KzloM/edit#bookmark=id.i2naqmmm3dhv)

{% stepper %}
{% step %}
### Overall release approach

* Run V1 and V2 in **parallel** for **6 months**. End of Sep.
* Customer journey V1, DPM, and retargeting will be closed after V2 release for **6 months**.
* In phase 1-4, we’ll release in production and show beta version.
* If clients are interested in V2, then inform them that once they transit to V2, they cannot use V1.
{% endstep %}

{% step %}
### Transition & pricing

* They can use free version and also pay for paid module. See more: [Customer Journey PRD\_Phase 1](https://docs.google.com/document/d/1xzO9-7TlaObaxMfVldyIInyuATR9jjM48GSQY5KzloM/edit#bookmark=id.yz0pg5kfnpus)
{% endstep %}

{% step %}
### Pilot plan close criteria

* If we already have 10 pilot clients, then stop pilot program and start to charge the full price $5,000. If not, continue the plan below.
* In phase 1, we want to gain some pilot clients:
  * Top 10 clients could use journey V2 with **$2500**/month in the first **6** months.
    * “Top 10 clients” is just for promotion; there could be more than 10 pilot clients.
  * Pilot clients have to share a success story / have an interview with Crescendo lab.
  * If clients start to use V2, they cannot use re-targeting 購物車再行銷, DPM 商品推薦訊息, customer journey 自動旅程.
{% endstep %}
{% endstepper %}

***

## Metrics & Key Results

Pls refer to [Customer Journey PRD\_Phase 1 — Metrics & Key Results](https://docs.google.com/document/d/1xzO9-7TlaObaxMfVldyIInyuATR9jjM48GSQY5KzloM/edit#bookmark=id.em3be1fw82v6)

***

## 0. Feature overview

See phase 1-1 \~ 1-4 feature overview, pls refer to [Customer Journey PRD\_Phase 1](https://docs.google.com/document/d/1xzO9-7TlaObaxMfVldyIInyuATR9jjM48GSQY5KzloM/edit#bookmark=id.artr5gtbsquo)

* Smart sending
* Exclude Rule
* Free version template

***

## 1. Smart sending

### Purpose

* To let clients have better potential to engage with customers to increase marketing results.
* To combine AI feature to be a WOW feature to attract users.

### User story

* As a marketer, I want to send journey messages with smart sending time to increase marketing performance.

### Description

* Rule
  * Sending time setting
    * Waiting time for smart sending time
* If smart sending time conflicts with a sleep mode time span
  * Smart sending first needs information on UI (so user can decide)

***

## 2. Exclude Rule

### Purpose

* Provide exclude rules to prevent sending too many messages and increase the block rate.

### User stories

* As a marketer, I don’t want to bother users too much, so that I could prevent increasing the block rate.
* As a marketer, I need to know how many users are excluded by the exclude rule in this journey, so that I could optimize the journey setting.

### Description

* Trigger condition for exclude
  * Trigger limitation: Set a maximum times that each friend can join the journey.
  * Frequency: If the user has completed this journey within N days, then exclude this user. (Do-not-disturb Interval)
* Message sending
  * Message sending limitation: The client could set a maximum limitation of paid message sent. Journey will be ended when the limitation is reached.
  * Sleep mode: Postpone the sending time after sleeping time slot.
  * Do not disturb: _ENG TBD_ If the user receives more than N broadcast messages (push) within N days, then exclude this user.
* Time-delayed triggers
  * If the event trigger is late after the next action time, within N hours, we still need to send the message; otherwise, skip that event.
    * GA4 has delay problems; we choose to let clients make the decision.
* Exclude result
  * Show the exclude number in report.

### Discussion (research / backlog)

<details>

<summary>How many times a week does the average person receive a message? (平均一個人平均一週收到幾次訊息）</summary>

* Why:
  * For exclude rule setting reference
  * Let client have an overview of current status of brand engagement with users
* CTA: already add a [backlog item](https://www.notion.so/cresclab/Product-Backlogs-2252ee2085b942d08acb484740fb6b21?p=702f58e5e0444c8e8dfdcbf20b1b1e13\&pm=s), need more research for the business impact.

</details>

<details>

<summary>Exclude specific segment</summary>

* Not in this phase; planned with backlog item: [Trigger by date and time -> target specific segment , exclude specific segment](https://www.notion.so/cresclab/Customer-Journey-TBD-Trigger-by-date-and-time-e3a837570ba0487aad604d1f7994b0b5)

</details>

<details>

<summary>Scenario — Trigger: when a specific customer did not do a specific action for a certain period of time</summary>

* Not in this phase; planned with backlog item: [Trigger: when a specific customer did not do a specific action for a certain period of time](https://www.notion.so/cresclab/Product-Backlogs-2252ee2085b942d08acb484740fb6b21?p=39cd26d672314a69ace7e720a57fc41f\&pm=s)
* e.g. Wake up a sleeping customer

</details>

***

## 3. Free version (cancelled)

> Note: This free version plan is marked as cancelled.

We would provide only 5 fixed templates with no branch feature (to replace V1 features).

|    | Trigger          | Rule                                                                             | Action                                                                                             |
| -- | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| 1. | **Join LINE OA** | - Join LINE OA （確認phase2） - **immediately**（Push） - N minutes / N hours / N days | - Send LINE messages - send retargeting message (only current ver. no product details.) - Send DPM |
| 2. | **Tag**          | - Tag                                                                            |                                                                                                    |
| 3. | **DPM**          | - X                                                                              |                                                                                                    |
| 4. | **Add to cart**  | - GA-Cart drop event                                                             |                                                                                                    |
| 5. | **Purchase**     | - GA-Purchase event                                                              |                                                                                                    |

* Need some attractive anime, picture or result numbers to attract clients who use free version to upgrade to paid version.

***

## 4. Autosave (-> phase 1-1)

### Purpose

* Provide autosave to increase user-friendliness.

### User story

* As a marketer, I hope that MAAC could automatically save the current setting when I am setting the overall journey, so that I won’t struggle if some unexpected accident happened.

### Description

* Autosave when user completes one setting / one node.
* If the timeline is urgent, choose an alternative option first and add it into backlog
  * Save the draft without investigating mechanism.

***
