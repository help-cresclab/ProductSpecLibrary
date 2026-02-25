# Customer Journey PRD\_Phase 1 1

**Phase1 Unblock JP with more triggers, rules and actions. (conversion)**

**Phase 1-1 Building the foundation and Supporting GA event and branching**

**Roadmap driver**: Lydia

**Contributors**: pm team

**Slack channel**: [#proj-maac-journey-v2](https://chatbotgang.slack.com/archives/C04305BTUBE)

**Overview version**: [Roadmap for Customer Journey across channels](https://docs.google.com/presentation/d/10SLeF-xOn-EQFJpJekGrxj9CHaF8zyuZZHZxdWRmhjo/edit#slide=id.p)

**Description**:

* Customer Journey purpose, background and roadmap overview, pls refer to [Roadmap for Customer Journey across channels](https://docs.google.com/document/d/1uPBUSxNSdAzuZnD6oDQ7VI7BVjMcP2ZECx80wmQ8P00/edit#heading=h.ohkn51128mkc)
* Customer Journey phase 1 overall planning, pls refer to [Customer Journey PRD\_Phase 1](https://docs.google.com/document/d/1xzO9-7TlaObaxMfVldyIInyuATR9jjM48GSQY5KzloM/edit)
* This document will focus on Journey Phase 1-1

| Version   | Timeline | Description  | Owner |
| --------- | -------- | ------------ | ----- |
| Version 1 | 2023.1.4 | Overall plan | Lydia |

## Aim & Objective

Customer journey phase 1 aims to automatically generate engagement, and conversion with one-time setting and optimize the marketing performance with AI features.

This will let us have a stronger competitive advantage, and help us to unblock Japan enterprise market.

In phase 1-1, we’ll focus on use MVP to get pilot client(agencies) feedback, so we build the main features as below:

1. Build the foundation of new customer journey
2. Overall UX with trigger, rule, action and branching (including existing features)
3. Support basic trigger and rules for Japan requirements
4. Trigger: GA triggers
5. Rule: And/or/exclude operator
6. Provide basic report
7. Report: journey result with time span

##

## Release plan

When we complete the whole phase 1, then we’ll have the final release (Release in production and available to all clients.)

Overall release plan & pricing, pls refer to [Customer Journey PRD\_Phase 1](https://docs.google.com/document/d/1xzO9-7TlaObaxMfVldyIInyuATR9jjM48GSQY5KzloM/edit#bookmark=id.i2naqmmm3dhv)

In phase 1-1, we’ll release in production and only available to pilot clients.

We’ll have several JP agencies for the pilot to gain some feedback for better optimization.

## Metrics & Key Results

* Gain at least 3 pilot clients' feedback.

## 0. Feature overview

See phase 1-1\~1-4 feature overview, pls refer to [Customer Journey PRD\_Phase 1](https://docs.google.com/document/d/1xzO9-7TlaObaxMfVldyIInyuATR9jjM48GSQY5KzloM/edit#bookmark=id.artr5gtbsquo)

* Overall UX with trigger, rule, action and branching (including existing features)
* Trigger: GA triggers
* Rule: And/or/exclude operator
* Report: journey result with time span

## 1. Overall UX with trigger, rule, action and branching (including existing features)

#### Purpose

*
  * Make users easily use customer journey to increase the usage and decrease the barrier.
  * Build the foundation of new customer journey.

#### User story

*
  * As a marketer, I hope to understand the journey logic without too much thinking, so that I could set the customer journey with efficiency.

#### Description

*
  * Basic setting:
    * Journey name
    * Start time - End time
    * Journey triggers setting
      * Unlimited trigger times
      * Each member can join the journey N times
    * Message sending setting
      * No limit
      * Maximum N paid message(s) sent
    * Sleep mode: Postpone the sending time after sleeping time slot
  * Trigger(start point):
    * Tag
  * Rule:
    * condition with Branching logic
      * yes/no
    * Sending time setting
      * Waiting time for immediately / N minutes / N hours / days
  * Action:
    * Send LINE message

| **Description**                                                                                       | **Current**                                        | **Future (示意圖)**                                   |
| ----------------------------------------------------------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| - Simple and straightforward UI: Show componets directly to let users have an overview with a glance. | ![](<../../../.gitbook/assets/Unknown image (58)>) | ![](<../../../.gitbook/assets/Unknown image (59)>) |

## 2. Trigger: GA triggers

#### Purpose

*
  * Provide GA event as a trigger to make clients have more chances to engage with the high conversion potential customers.

#### User story

*
  * As a marketer, I hope to automatically detect which customer view which page and purchase which product, so that I could automatically engage with them.

#### Description

*
  * Trigger(start point):
    * Page view:
      * Any page
      * Specific page (Support multi-options)
      * \[optional] Detect how long users stay on the page (seconds) 秒
    * Purchase:
      * Any Item
      * Specific item (Support multi-options)

## 3. Rule: And/or/exclude operator

#### Purpose

*
  * Enrich rules with and/or/exclude operator to enhance the scenario flexibility.

#### User story

*
  * As a marketer,
    * I hope to automatically detect which customer view page A **and** view page B,
    * I hope to automatically detect which customer view page A **or** view page B,
    * I hope to automatically detect which customer purchase item A **but not** purchase item B,
  * so that I could automatically engage with them.
* Description
  * The limitation of the rule is up to 50.
    * Considering clients would like to detect customers view specific pages (top 30, top 50 hot sell products), and automatically start the following customer journey.

## 4. Report: journey result with time span

weekly report via email

#### Purpose

*
  * Provide basic reports to help marketers evaluate the result.

#### User story

*
  * As a marketer, I want to have a basic report, so that I could evaluate the result.

#### Description

*
  * Pls check [Customer Journey PRD\_Phase 1](https://docs.google.com/document/d/1xzO9-7TlaObaxMfVldyIInyuATR9jjM48GSQY5KzloM/edit#bookmark=id.uktc8ub9rky2)

## \*5. Autosave(-> phase 1-1)

#### Purpose

*
  * Provide autosave to increase user-friendliness.

#### User story

*
  * As a marketer, I hope that MAAC could automatically save the current setting when I am setting the overall journey, so that I won’t struggle if some unexpected accident happened.

#### Description

*
  * Autosave when user completes one setting/ one node.
  * If the timeline is urgent, choose alternative option first, and add it into backlog
    * Save the draft without investigating machism.
