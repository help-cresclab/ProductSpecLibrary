# Customer Journey PRD\_Phase 1 2

Phase 1: Unblock JP with more triggers, rules and actions (conversion)

Phase 1-2: Provide 1st conversion scenario — Cart drop — with basic templates and a beta version to get more pilot users

Roadmap driver: Lydia\
Contributors: PM team\
Slack channel: [#proj-maac-journey-v2](https://chatbotgang.slack.com/archives/C04305BTUBE)\
Overview version: [Roadmap for Customer Journey across channels](https://docs.google.com/presentation/d/10SLeF-xOn-EQFJpJekGrxj9CHaF8zyuZZHZxdWRmhjo/edit#slide=id.p)

Description / references:

* Customer Journey purpose, background and roadmap overview: [Roadmap for Customer Journey across channels](https://docs.google.com/document/d/1uPBUSxNSdAzuZnD6oDQ7VI7BVjMcP2ZECx80wmQ8P00/edit#heading=h.ohkn51128mkc)
* Customer Journey phase 1 overall planning: [Customer Journey PRD\_Phase 1](https://docs.google.com/document/d/1xzO9-7TlaObaxMfVldyIInyuATR9jjM48GSQY5KzloM/edit)
* This document focuses on Journey Phase 1-2.

Version table

| Version   | Timeline  | Description  | Owner |
| --------- | --------- | ------------ | ----- |
| Version 1 | 2023.1.24 | Overall plan | Lydia |

***

## Aim & Objective

Customer Journey phase 1 aims to automatically generate engagement and conversion with one-time settings and optimize marketing performance with AI features.

This helps unblock the Japan enterprise market.

After phase 1-1 we provided an MVP.

Phase 1-2 scope:

* Provide 1st conversion scenario — Cart drop
* Provide basic templates

(See Phase 1 doc for full plan & pricing: [Customer Journey PRD\_Phase 1](https://docs.google.com/document/d/1xzO9-7TlaObaxMfVldyIInyuATR9jjM48GSQY5KzloM/edit#bookmark=id.i2naqmmm3dhv))

Release notes (phase 1-2)

* Release in production and show the welcome page in the customer-journey beta version.
* Pilot clients:
  * Top 10 clients could use Journey V2 at **$2500/month** for the first **6 months** (promotion; may be more than 10).
  * Pilot clients must share a success story or take part in an interview with Crescendo lab.
  * If clients start using V2, they cannot use re-targeting 購物車再行銷, DPM 商品推薦訊息, customer journey 自動旅程.

***

## Metrics & Key Results

* Deal close (business impact): Number of clients who pay to be customer-journey pilot users.

***

## 0. Feature overview

(See phase 1-1 \~ 1-4 feature overview in Phase 1 doc linked above.)

* Provide 1st conversion scenario — Cart drop
* Provide basic templates

***

## 1. 1st conversion scenario — Cart drop

### Purpose

To let clients engage high-conversion-potential customers automatically and focus on the first conversion scenario — cart drop.

### User story

As a marketer, I want to send messages to customers who drop their cart and have an automatic flow, so I can detect customer behavior and trigger related actions automatically.

### Description

* Trigger (start point)
  * GA event — add to cart
* Action
  * Send a cart-drop message with product name and pictures
* Notes about GA4 data delay
  * GA4 data delay threads:
    * [Thread for data](https://chatbotgang.slack.com/archives/C04FK64DJLS/p1673514542518909)
    * [Thread for discussion](https://chatbotgang.slack.com/archives/C03CQLN6HGR/p1672388311802949)
  * Provide information explaining the GA4 delay problem and the current mechanism.
  * Option: set action after receiving the delayed event using Exclude rule. (See bookmark: https://docs.google.com/document/d/1Xxhdv1tFvAF7jfDJJO5ADx\_XPhpjloJnWDcgSbZorLI/edit#bookmark=id.inikwvia8pnk)

***

## 2. Basic templates (-> cancelled)

> Note: this item is cancelled for Phase 1-2 — kept here for reference.

### Purpose

Provide basic templates to help clients set up customer journeys faster.

### User story

As a marketer, I want to understand and complete basic scenarios quickly so I can set up the customer journey efficiently.

### Description (ideas / notes)

From current client usage (observed): prizes, games, invite-friends, member cultivation, purchase flows.

Example templates (ideas — detail TBD with PM / PMM):

* Coupon reminder
  * Trigger: When a member is tagged by clicking the coupon message. Exclude members with a redeem coupon tag.
  * Wait: 7 days
  * Action: send reminder message
* Loyalty program
  * Trigger: new members are tagged as a member
  * Action: greeting message
  * Wait: 14 days
  * Branch:
    * purchase → action: send message
    * not purchase → action: send prize
* Cart drop
  * Trigger: customer adds product to cart
  * Wait: 3 days
  * Action: send cart-drop reminder message
  * Branch:
    * purchase → action: send message
    * not purchase → action: send prize

***

## 3. Welcome page (-> cancelled)

> Note: this item is cancelled for Phase 1-2 — kept here for reference.

### Purpose

Provide a welcome page to attract beta trial clients and collect feedback.

### User story

As a product manager, I want as much feedback as possible to inform optimization decisions for the next phases.

### Description (ideas / notes)

* Welcome page:
  * Show introduction about Customer Journey
  * Suggested wording (TBD by PD / PMM)
    * Customer journey
    * Automatically generate engagement and conversion with one-time settings; optimize with AI features.
    * "Welcome to the Customer Journey beta"
    * "Please note..."
* Settings page:
  * Let clients experience setup but prevent publish.
  * Contact a specialist → open Zendesk to reach CS.

***

If you'd like, I can:

* Convert the "1st conversion scenario" description into a stepper (Purpose → User story → Trigger → Actions → GA4 notes).
* Produce ready-to-import GitBook blocks (stepper, tabs, hint blocks) for any section you want to be more interactive.
* Draft message templates (copy) for the cart-drop flow (subject, body, product placeholders) suitable for sending via chat/email.
