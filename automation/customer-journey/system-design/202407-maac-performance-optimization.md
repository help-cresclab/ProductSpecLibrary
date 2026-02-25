---
description: >-
  Performance optimization plan for MAAC. Uses Sentry and Datadog metrics plus
  customer pain points to prioritize FE/BE improvements and new APIs.
---

# 202407 MAAC Performance Optimization

Authors: @Xander, @Gideon Pan\
\[PRD]:\
\[ERD]:\
Doc File name: “yyyymm(created\_time)” (e.g. 202010 technical design document template)

### Overview

This doc collects **performance signals** for MAAC and proposes **optimization targets**.

Inputs include:

* FE metrics (Sentry opportunities / web vitals)
* BE metrics (Datadog P95/P99 latency)
* GTM/customer pain points

{% hint style="info" %}
**Keywords**: MAAC performance, loading speed, Sentry web vitals, Datadog latency, P95, P99, pagination, caching, API split, perceived performance
{% endhint %}

## Overview / Background

MAAC application performance is slow in several areas, and we’d like to identify both low-hanging fruit AND high impact targets for improvements. To identify the best optimization targets we will consider FE performance metrics, BE performance metrics, and customer pain points as relayed via GTM team.

Backlog item reference: [MAAC loading speed MVP - broadcast, tag, tracelink](https://www.notion.so/MAAC-loading-speed-MVP-broadcast-tag-tracelink-c4c46ea6f5224f35a57856ba5433453c?pvs=21)

## Problem

MAAC application performance is noticeably slow in some views. We have limited resources. We need to target some areas for improvement.

[FE Performance Metrics](https://www.notion.so/d47b078b47cb4fb8b9b607a3887b89a6?pvs=21)

Note: “opportunity” is calculated by Sentry; it incorporates web vitals and # of pageloads to find areas where optimization could provide the greatest benefit.

### BE Performance Metrics (Datadog)

High latency API with more than 100 requests per month (based on P95)

| Resource Name                                          | Requests | P95 Latency | P99 Latency | importance | possible solution                      | ETA |
| ------------------------------------------------------ | -------: | ----------: | ----------: | ---------- | -------------------------------------- | --- |
| POST accounts/v1/user/(?P\[^/.]+)/notifications/read/$ |    4.45k |      30.3 s |      30.8 s |            |                                        |     |
| GET line/v2/tester/candidates/$                        |    3.05k |      29.8 s |      30.3 s |            | CQS                                    |     |
| GET line/v1/member/$                                   |     104k |      17.3 s |      25.9 s |            | CQS                                    |     |
| GET line/v1/member/metric/$                            |     118k |      13.1 s |      29.8 s |            |                                        |     |
| GET line/v1/guidelink/bindlink/$                       |      428 |      9.47 s |      19.9 s |            |                                        |     |
| GET line/v1/widget/$                                   |    2.68k |      8.50 s |      22.2 s |            |                                        |     |
| GET cdp/v1/tags/$                                      |      285 |      6.43 s |      8.50 s |            |                                        |     |
| GET line/v2/message/pnp\_record/count/$                |      944 |      5.68 s |      26.3 s |            |                                        |     |
| GET line/v1/guidelink/outlink/$                        |    50.2k |      5.50 s |      21.5 s | 1          | add new API for loading metadata       |     |
| TBD                                                    |          |             |             |            |                                        |     |
| GET line/v2/message/pnp\_record/$                      |    2.22k |      4.04 s |      17.6 s |            |                                        |     |
| GET report/v1/overview\_line/member/$                  |    67.2k |      3.35 s |      7.98 s |            |                                        |     |
| GET line/v1/guidelink/outlink/metric/$                 |    29.9k |      2.78 s |      6.33 s |            |                                        |     |
| GET line/v1/broadcast/message/                         |      143 |      2.61 s |      8.11 s |            |                                        |     |
| GET rubato/receipt/receipt/                            |      176 |      2.35 s |      3.30 s |            |                                        |     |
| GET line/v2/richmenu/$                                 |    49.4k |      2.10 s |      3.40 s | 2          | add new API for loading metadata       | TBD |
| PATCH line/v1/widget/(?P\[^/.]+)/$                     |      164 |      2.04 s |      2.31 s |            |                                        |     |
| POST audience/v2/custom\_segment/$                     |      756 |      2.01 s |      5.01 s |            |                                        |     |
| GET tag/v1/tag/$                                       |    19.8k |      1.83 s |      6.23 s | 3          | add pagination                         |     |
| GET line/v1/bot/(?P\[^/.]+)/campaigns/$                |    2.02k |      1.69 s |      8.36 s |            |                                        |     |
| GET report/v1/engagement/daily\_auto\_reply/$          |    4.32k |      1.50 s |      3.05 s |            |                                        |     |
| GET line/v1/message/broadcast/raw\_broadcasts/$        |    33.7k |      1.36 s |      2.35 s | 4          | improve the api performance by caching |     |

Notes:

* The tag manager list view is likely solved by pagination (estimated 0.5d).
* For GET line/v1/message/broadcast/raw\_broadcasts/$: FE does not think this API should be split into search and paginated list for UX reasons (estimated 1d–2d).
* Several rows above currently have empty "importance", "possible solution", or "ETA" and should be prioritized/filled.

### Customer Pain Points

* members list: “It took so long to search the contact with LINE display name.” “It normally shows contact not found for the first search result. Client need to reload the page, and search again.”
* test user: “As well as the privilege management, it hard to add the test user by searching from LINE display name as it will show contact not found.”
* prize management and price performance: “Prize management: We found sometimes it took so long when clicking on this tab. Also, the price performance also took time to load as well.”
* deeplink: “When creating 1st deeplink in MAAC, it will disappear when we save it. We need to refresh page \~2-3 times or switch to another tab then back to deeplink page, so it will show up.”
* insight/dashboard: from Gordon’s initial review ([here](https://www.notion.so/MAAC-loading-speed-MVP-broadcast-tag-tracelink-c4c46ea6f5224f35a57856ba5433453c?pvs=21))
* tag manager: from Gordon’s initial review, also a priority for Xander based on previously existing user experience concerns ([Asana task](https://app.asana.com/0/1206764649948244/1207190393720990/f))
* app marketing: from Gordon’s initial review

## Goal / Requirement

Target outcomes:

* Reduce page load and interaction latency on top user flows.
* Improve perceived performance (loading states, caching, prefetch).
* Reduce P95/P99 latency for high-traffic endpoints.
* Fix UX issues caused by slow data (e.g., list views, metadata fetch).

## Proposed Solution(s)

Solutions will be specific to the performance target, but some solutions may apply to more than one target. Some general approaches:

#### FE-Only Solutions

* Implement pagination with prefetch for list views that already support this (currently only Tracelink and DPM lists).
* Optimize queries, caching, display loading spinners after mutations (might address complaints about Deeplink).
* UX improvements where applicable; adjust data fetching/loading spinner code to increase perceived performance.
* Reduce bundle size (application-wide benefits but subtle).

#### FE-BE Joint Solutions

* Create new API endpoints that split performant and non-performant parts of existing APIs so slow-loading data can be lazy-loaded and perceived performance can improve (potentially useful for Tracelink).
* Implement pagination with prefetch on list views that do not already implement infinite scrolling or pagination (Tag Manager).

#### BE-Only Solutions

* Reduce existing API endpoint response times.
* Database query optimizations.

## Tasks

Prioritization:

* Tracelink
* Rich Menu
* Broadcast metadata (BE only) — FE can also complete React Query integration of all metadata endpoints for FE caching, which will improve performance

## Measurement

* How do you define/measure success?
* How do you monitor/test the health of this project?

(Place monitoring approach here — e.g., track FE web vitals, Sentry opportunity scores, Datadog P95/P99 for targeted APIs, and user-reported times for affected flows. Fill specifics as the implementation plan is defined.)

## Feedback

Section for others to leave feedback and questions.

Example: @George — This is great, but we may need to change the DB schema...

***

If you want, I can:

* Convert any of the Proposed Solutions into a step-by-step implementation stepper.
* Turn the BE metrics table into separate prioritized sections with concrete owners/ETAs.
* Add monitoring checklists (Sentry, Datadog dashboards, synthetic tests) as a measurement plan.
