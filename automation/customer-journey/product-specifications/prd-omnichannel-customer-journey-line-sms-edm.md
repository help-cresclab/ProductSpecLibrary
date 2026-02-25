# PRD — Omnichannel Customer Journey (LINE / SMS / EDM)

## PRD - Omnichannel Customer Journey

MAAC

Omnichannel Customer Journey (LINE / SMS / EDM) PRD

Automate customer journeys that seamlessly orchestrate LINE, SMS, and EDM in one flow

PM owner: [Jean Liu](mailto:jean.liu@cresclab.com)\
Eng owner: [Gideon Pan](mailto:gideon.pan@cresclab.com)\
PD owner: [Patty Hsu](mailto:patty.hsu@cresclab.com)

💬 Slack channel: [#proj-journey](https://chatbotgang.slack.com/archives/C08JZHN576Z)

***

### Version history

| Version | Date       | Description                                                   | Editor                                   |
| ------- | ---------- | ------------------------------------------------------------- | ---------------------------------------- |
| Ver. 0  | 2025-08-15 | TF kick-off (see 0818 discussion)                             | [Jean Liu](mailto:jean.liu@cresclab.com) |
| Ver. 1  | 2025-08-26 | Part 1 (Omnichannel journey + SMS) PRD draft – tech alignment | [Jean Liu](mailto:jean.liu@cresclab.com) |

***

### 🆕 AI Collaboration log

| Date       | Summary                                                           | Status     | AI Prompt (recommend)                                                                                                                                                |
| ---------- | ----------------------------------------------------------------- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2025-07-23 | User stories & test case generation                               | Resolved   | [LINK - Generate test cases](https://www.notion.so/cresclab/AI-Coding-Task-Force-1f38ce158938809ba1faea6796b8a1d3?source=copy_link#2398ce1589388013a3defc4253fd3dfd) |
| 2025-07-23 | Test case updated based on MM/DD discussion (link to the section) | Resolved   | [LINK - PRD Update](https://www.notion.so/cresclab/AI-Coding-Task-Force-1f38ce158938809ba1faea6796b8a1d3?source=copy_link#2238ce158938802b835dff0ecf599e3f)          |
| Date       |                                                                   | Unresolved |                                                                                                                                                                      |

***

### Release notes

Engage customers seamlessly across LINE, SMS, and Email with Omnichnanel Customer Journey

* Expanded Triggers: Support tags, website behaviors, and channel engagements as journey triggers to engage with customer intent.
* Channel Branching: Route users to the most cost-effective or likely-to-engage path by checking channel status in the journey.
* Multi-channel Messaging: Orchestrate and send messages across LINE, SMS, and Email.
* Omnichannel Reporting: Review omnichannel journey performance in one dashboard.

***

### Goal

Customer Value

* Cost Efficiency: Prioritize low-cost channels before utilizing paid channels (eg. EDM → LINE → SMS).
* Optimal Reach & Engagement: Connect with members on their preferred channel, ensuring messages are delivered and engaged.

Business Value

* AI MA foundation: Becoming true omnichannel MA and lay a foundation for AI journey in Q4.
* Expand Market Position & Get Ready for Mid-Large clients: fulfill multichannel automation needs.
* Diversify Revenue Streams: Include volume-based messaging service (SMS & EDM) in core features.

***

### Background

* Strategic Importance of Customer Journey
  * Customer Journey is a core feature to deepen product usage and increase retention.
  * Only 12% of clients adopt the Customer Journey. Key barriers:
    * Limited Channel Support: LINE-only.
    * Insufficient Triggers & Conditions.
    * Inflexible Configuration.
* Foundation for AI Journey
  * Omnichannel upgrade is a critical step toward AI Journey.
* Competitor Analysis

| Competitor | Supported Channels                                                              | AI journey-like features                                                           | Reference                                                                                     |
| ---------- | ------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Insider    | Web/App, Email, SMS, WhatsApp, FB/Google ad audience                            | [Smart Journey Creator](https://academy.useinsider.com/docs/smart-journey-creator) | [HC: Architect Journeys](https://academy.useinsider.com/docs/introduction-to-architect)       |
| Appier     | AIQUA: Web/App, Email, SMS; BotBonnie: LINE, FB, WhatsApp, Webchat, Viber, Zalo | [Journey Copilot](https://zh.docs.enterprise.appier.com/docs/journey-copilot)      | [AIQUA journey](https://zh.docs.enterprise.appier.com/docs/getting-started-with-journey-maps) |
| Bebit      | Web/App, Email, SMS, FB/Google ad audience                                      | \[AI journey] (internal link)                                                      | \[Sales deck] (internal link)                                                                 |
| Omnichat   | FB, IG, LINE, WhatsApp                                                          | \[AI Marketing Campaign Agent] (internal link)                                     | \[HC: Customer Journey] (public link)                                                         |

***

### Strategy

See Journey - From 2.1 to 3.0+ [strategy doc](https://docs.google.com/document/d/1KqJZiEJ6vPRVUS_SGh4Z_SGLCLxbqD1sjBLWsyWxmso/edit?tab=t.0#heading=h.lr7eh2ss3xgz)

#### Product Strategy

Why Important

* Evolve MAAC from single-channel LINE tool into true Omnichannel MA.
* Foundation for AI Journey.

Why Now

* Defense: support core marketing channels to reduce churn risk.
* Offense: attract new multi-channel clients.
* New Revenue: volume-based messaging unlocks growth.

How We Win

* M1: provide accessible omnichannel solution for mid-market, surpassing some direct competitors and prepping AI Journey.

#### Roadmap

* Phase 1: Omnichannel foundation (Q3) — this PRD
  * Org-level architecture, integrate LINE, SMS, EDM.
  * Support WebSDK standard events as website behavior triggers & conditions.
* Phase 2: True unification & Use cases expansion (Q4)
  * Omnichannel Segment, Channel expansion (JP & SG TBC), WhatsApp & Webchat.
* Phase 3: AI Journey MVP (Q4)
  * Prompt-to-journey & insight-to-action.

***

### TA & Problem-to-solve

| TA                        | Problem to solve                                                                                                                           |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Marketer / CRM Specialist | Managing journeys across separate platforms is inefficient; lack of real-time website event triggers; lack of multi-channel orchestration. |
| Marketing / CRM Managers  | Lack of unified dashboard for ROI; unable to automatically win-back via alternative channels.                                              |

***

### Solutions (high-level)

| Problems                                    | Existing Solutions                    | Proposed Solutions                                                 |
| ------------------------------------------- | ------------------------------------- | ------------------------------------------------------------------ |
| Managing journeys across separate platforms | Separate platforms for LINE, SMS, EDM | Unified journey canvas for LINE, SMS, and EDM                      |
| Lacks real-time triggers                    | Rely on delayed GA events             | Real-time SDK triggers based on website behavior                   |
| Lacks orchestration                         | Uncoordinated messages per platform   | Branching node to route message based on channel reachability      |
| Lacks unified dashboard                     | Manual consolidation from platforms   | Unified dashboard for omnichannel journey performance              |
| Unable to win-back automatically            | Manual exports for one-off campaigns  | Channel Attributes change as journey triggers to automate win-back |

***

### Selling points & Combine features

| TA                        | Selling points                                                                      | Combine features                                                |
| ------------------------- | ----------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| Marketer / CRM Specialist | Orchestrate automated customer journeys across LINE, SMS, Email from single canvas. | \[future] AI Content Generation; \[future] Dynamic product card |
| Marketing / CRM Managers  | Gain a complete view of campaign ROI and automatically maximize CLV.                | GA4 performance tracking; \[future] SDK Custom events           |

***

### User story

As a Marketer (MAAC users)...

* I want to design a single journey that contains message nodes for LINE, SMS, and Email on the same canvas, so that I can manage the entire customer flow in one place without switching tools. -> M1
* I want to set up branching rules that check a user's real-time channel status so that I can automatically route them to the most suitable and cost-effective communication channel. -> M2
* I want to trigger a journey when a user completes an action on our website so that I can send them a follow-up via the best available channel. -> M2
* I want to use an imported list of email addresses as the starting audience for a journey so that I can nurture email subscribers. -> M2
* I want the system to automatically manage email list status (subscriptions, unsubscribes, bounces, spam reports) in real-time so that journeys target valid lists. -> M2+

As a Marketing Manager...

* I want to see a consolidated performance report for a single journey across LINE, SMS, and Email, so that I can understand overall ROI and channel effectiveness. -> M2
* I want to design optimal cross-channel journeys to increase reach and reduce drop-offs. -> M1+M2

***

### Scope

Hint: Guardrails — clearly define "do" vs "not do" in bullet lists.

#### In-scope

* Omnichannel Journey Architecture
  * Org-level journey entities (not channel-bound).
  * Simulated omnichannel experience by requesting CDH contact channel entity IDs in real-time.
* Channel Integration
  * LINE (existing), SMS (new), EDM (new).
* Journey Triggers
  * Tags, Website behavior via SDK, Channel-specific events (LINE: Follow/Unfollow; EDM: Subscribe/Unsubscribe/Open (TBC)).
* Journey Nodes
  * Message nodes: SMS editor, EDM editor.
  * Branching nodes: Channel status reachability check.
* Contact & Data Management (MAAC UI & OpenAPI)
  * EDM contacts on Contacts page, import/export EDM contact lists.
  * Tagging for SMS and EDM contacts.
  * Real-time email event processing.
* Reporting
  * Omnichannel dashboard: overall + per-channel breakdown.
  * Node performance includes SMS and EDM.
* Tracking
  * SDK events as journey triggers & node conditions.
  * Shorten URLs (maac.io) in SMS/EDM to attribute website events to a user and channel.
* EDM Channel Onboarding (Ops-managed in M2)
  * Admin Center visibility (read-only in M2), credit top-up & sender setup, IP warm-up flow (Ops-run).

#### Out-of-scope

* Channel unification (Omnichannel segment).
* Omnichannel Bindlink.
* SMS-based triggers.
* GA events as journey triggers or rules for SMS & EDM (TBC).
* EDM self-serve onboarding (Ops-managed in M2).

#### Dependency check

* Affected teams: DAAC (CDH), MAAC pod2 (Journey & SDK).
* Dependencies to be confirmed with PICs listed in original content.

***

### Success metric

Overall Journey Adoption

* ## of Orgs actively using Customer Journey increase by 20% (target \~96 Orgs from baseline \~80).

Multi-channel Journey Adoption

* ## of Orgs actively using a journey that includes more than 2 channels — Target ≥ 10 Orgs.

New channel onboarding

* ## of Orgs who completed EDM onboarding and enabled EDM in journeys — Target ≥ 3 clients.

***

### Glossary definition

| Area | Product term               | Code term | Definition                                                                            |
| ---- | -------------------------- | --------- | ------------------------------------------------------------------------------------- |
| EDM  | Sender Policy Framework    | SPF       | DNS TXT record declaring allowed senders/IPs.                                         |
| EDM  | DomainKeys Identified Mail | DKIM      | Private key signature + DNS public key to verify message integrity and authorization. |
| EDM  | DMARC Policy               | DMARC (p) | Policy for mail receivers when SPF/DKIM not aligned (none/quarantine/reject).         |
| EDM  | Double Opt-In              | DOI       | User confirms subscription via email before being considered a subscriber.            |
| EDM  | Single Opt-In              | SOI       | Immediate subscription upon signup (faster growth, higher risk).                      |

Reminder: Update the [Product Dictionary](https://www.notion.so/cresclab/08666630ee444b44b349bdb60ec40c19?v=2281968133d64b11b25d206dd86780d4\&pvs=4)

***

### Feature list (opt.)

**\[M1] Omnichannel Journey Infrastructure & SMS Integration**

* A. Omnichannel Journey Infrastructure
  * A-1. Org-Level Journey Architecture
  * A-2. Cross-channel Contact Query
  * A-3. Website Tracking SDK integration
* B. Journey Canvas & Setting
  * B-1. Journey setting
  * B-2. Trigger: Tag
  * B-3. Trigger: Channel Event
  * B-4. Trigger: Website Behavior
  * B-5. Message Node: send SMS
  * B-6. Branching node: Check Reachability
* C. Contact & Data
  * C-1. EDM Contact & SMS Contact Logic
  * C-2. SMS Contact Tagging
  * C-3. SMS Short URL Tracking
* D. Reporting & Analytics
  * D-1. Omnichannel Journey Performance Report
  * D-4. SMS Message Nodes Error Logs & Alerts

**\[M2] EDM Integration**

* E. EDM Onboarding & Configuration
  * E-1. Channel Integration & Admin Settings
  * E-2. Credit & Usage Management
  * E-3. Sender Reputation & Data Hygiene Management
* F. Journey Canvas & Setting (EDM)
  * F-1. Trigger by EDM Events
  * F-2. Message Node: send EDM
  * F-2a. Pre-send Compliance (Activation Gate)
  * F-3. Branching node: Reachability (EDM)
* G. Contact & Data (EDM)
  * G-1. EDM Contact Management
  * G-2. EDM Contact Tagging
  * G-3. Real-time EDM Contact Status Sync
  * G-4. Short URL Tracking & GA4-based triggers/filters (EDM & SMS)
  * G-5. Identity & Web SDK (Q1 target)
* H. Reporting & Analytics (EDM)
  * H-1. Journey Performance Report (EDM)
  * H-2. Node Performance (EDM)
  * H-3. Email Sent Failure Report

***

## Feature spec

The sections below provide feature-level user stories, acceptance criteria, business logic, system flow, and notes for discussion. They are organized by M1 and M2 features (A–H). Please review the specific subsections for detailed ACs and flows.

> Note: The PRD contains many detailed sub-sections. For import into GitBook, keep each major subsection as its own page/anchor and use the following blocks:
>
> * Use Stepper for multi-step user flows in the Journey builder (where numbered steps exist).
> * Use Expandable (details/summary) for long meeting logs, Q\&A, and FAQ-like sections.
> * Use Tabs for package-manager code snippets (not present in this document).
> * Use hint blocks for cautions (e.g., "Do-Not-Disturb" behavior, suspension thresholds).

Key excerpts and important implementation highlights are included below. (Full feature spec content retained in source — when importing to GitBook, break the long PRD into multiple pages by section: M1 - Infrastructure, M1 - Canvas, M1 - Contact & Data, M1 - Reporting, M2 - EDM Onboarding, M2 - EDM Canvas, M2 - Contact & Data, M2 - Reporting.)

***

### \[M1] Highlights

#### A - Omnichannel Journey infrastructure

A-1. Org-level Journey architecture

* Upgrade from channel-specific entity to org-level journey.
* User stories: unified journey list page, channel column with channel icons, channel filter including conditional "SMS" option based on Org SMS vendor setup.
* Business logic: journeys are org-level entities; channel filter shows integrated channels; "SMS" filter only visible if Org has SMS vendor configured.

A-2. Cross-channel Contact query

* Simulated omnichannel routing using CDH to look up related channel entity IDs from any known ID (LINE UID, email, phone).
* Reachability definitions:
  * LINE: user has followed LINE OA.
  * SMS: valid E.164 phone number.
  * EDM: subscribed and not suppressed (bounce/complaint).
* Ambiguity resolution: select most recently updated contact profile; log ambiguous cases.
* Latency goal: query/response optimized to support journey latency goal (< 10s).

A-3. Website Tracking SDK integration

* Capture standard SDK events and identifiers (WCCS ID, email, phone).
* WCCS <> email/phone binding persists; SDK events attributed to bound contact.
* Trigger throttling: SDK-based triggers limited to once per 1 hour per contact (legacy GA-based triggers keep 24-hour limit).
* Business logic: persistent binding, WCCS cookie 30 days, SDK identify(email) only processed if Admin toggle enabled (see G-5).

***

#### B - Journey Canvas & Setting

B-1. Journey Setting

* Global settings: message sending limits per channel (LINE, SMS, EDM), contact trigger limit (per True Contact), Do-Not-Disturb (journey-level).
* Monitor & notifications: warning icon when message sending limit reached, tooltip/explanations in UI.
* Business logic: message sending limit applied per-channel across nodes; contact trigger limit computed on True Contact.

B-2. Trigger: Tag

* Org-level tag trigger; once per hour per contact throttling.

B-3. Trigger: Channel Event

* Channel event trigger for LINE (Follow, Unfollow, Open) and EDM events (to be defined in M2).
* Allow multi-channel selection (eg., multiple LINE OAs) with OR logic.

B-4. Trigger: Website Behavior

* Website Behavior (SDK) category: list of SDK & GA standard events.
* Web Channel selector per Org; if Org has not installed SDK or plan not eligible, SDK triggers are disabled with CTA/upgrade badge.
* For Page View filters, require path (e.g., /products/sale) as property for clarity.

B-5. Message node: send SMS

* SMS message editor similar to SMS Broadcast editor: real-time character counter, Short link modal for UTM & tag-on-click.
* Pre-send balance check: show non-blocking top-up banner if org SMS balance <= 0.
* Implicit reachability: skip contacts without E.164 phone number; skip is non-blocking and logged in node performance.
* Feature gating: disabled "Send SMS" node if org has not configured SMS vendor.

B-6. Branching node: Check Reachability

* New "Check Reachability" branching node with ordered channels priority list; dynamically generates outputs per added channel + final "Not Reachable".
* Exclusive routing: first reachable channel wins.
* Max channels selectable: 5.

***

#### C - Contact & Data

C-1. EDM Contact & SMS Contact Logic

* EDM contacts are distinct entity type; displayed as "Email {@domain}" in Contacts list.
* SMS contacts follow existing "Others" logic; a contact is SMS-reachable if a valid phone number exists.
* CDH unification used; email and phone are default unify keys.

C-2. SMS Contact Tagging

* Org-level tags apply to SMS contacts; Apply/Remove Tag action node supports SMS contacts.
* Tags triggered by maac.io click assigned to the unified contact (CDH tags / MAAC tags sync behavior defined in Notes).

C-3. SMS Short URL Tracking

* maac.io short links for SMS with UTM support and non-PII contact token to feed GA4 & SDK attribution.
* On click: log with contact, journey, node; trigger tags; redirect with UTM + maac identifier for SDK / GA4.

***

#### D - Reporting & Analytics

D-1. Omnichannel Journey Performance Report

* Overview: aggregated KPIs across channels + GA4 e-commerce metrics.
* Per-channel breakdown view with channel-specific metrics and tooltips.
* Definitions for Message Sent, Open Rate, CTR, Unique CTR (weighted across channels), Items Added to Cart, Orders, Revenue (GA4).

D-2. SMS Message Nodes Error Logs & Alerts

* Downloadable failure report CSV for SMS nodes (Phone number, Display name, LINE ID, Email address, Timestamp, Failure reason).
* Systemic errors (eg. insufficient balance) trigger in-app warnings and one-time fatal email alert; UI icons on Journey List and Canvas.

***

### \[M2] Highlights (EDM)

#### E - EDM Onboarding & Configuration

E-1. Channel Integration & Admin Settings

* Ops-managed SendGrid subuser provisioning, API key rotation, Event Webhook with signed events, per-sender domain authentication (SPF/DKIM checks) and Sender Profiles (From name, From email, Reply-To).
* Admin Center: read-only Email channel row showing Sender Domain health and Sender Profiles; activation checklist.
* Per-domain gating: block sending when SPF/DKIM fails (alignment requirement).

E-2. Credit & Usage Management

* Per-org price per unit (EDM), share MAAC points balance with SMS & PNP.
* Billing event (default: accepted) used to deduct points; T+24 credit-back for hard bounces.

E-3. Sender Reputation & Data Hygiene Management

* Suppression rules: hard\_bounce and spam\_report => immediate global suppression; soft\_bounce thresholds => suppression per rules.
* MX check during import; import hygiene bar; rolling 24H suspension and warning policies (thresholds defined in PRD).
* Global hard bounce list to block imports/sends.

***

#### F - Journey Canvas & Setting (EDM)

F-1. Trigger by EDM Events

* Add Channel Event triggers for Email Clicked (maac.io short link clicks), Email Opened (low confidence), Email Unsubscribed.
* Email Clicked only triggers on maac.io short links (not generic ESP clicks).

F-2. Message Node: send EDM

* Select Sender Profile (Ops-managed).
* WYSIWYG & Paste HTML editor (sanitize scripts/iframes). Support per-link maac.io short links, per-link tags and UTM fields if GA4/SDK connected.
* Mandatory unsubscribe headers + {unsubscribe\_link} placeholder required on save; unsubscribe links MUST NOT be shortened or tracked.
* Pre-send activation gate (F-2a): check domain auth (SPF/DKIM alignment), Sender Profile active, unsubscribe method, balance, and channel health warnings; block activation if suspension conditions met.

F-2a. Pre-send Compliance (Activation Gate)

* Activation must verify: SPF/DKIM alignment, verified Sender Profile, unsubscribe method present, sufficient balance.
* Domain Health = Warning is advisory (activation allowed), Suspended blocks activation/execution.

F-3. Branching node: Reachability (EDM)

* Email reachability true if subscribed=true AND unsubscribed=false AND suppressed=false for the Brand Domain.
* Branch checks per Brand Domain (Channel selection per Brand Domain).

***

#### G - Contact & Data (EDM)

G-1. EDM Contact Management (Import & Update)

* EDM Channel Contacts per email address under Brand Domain; support CSV & OpenAPI upsert with hygiene checks including MX record validation.
* CSV import template: required columns: email, messaging\_status; optional: display\_name, customer\_id, mobile, gender, birthday, tag, consent\_source, consent\_at.
* Import rules: cannot re-subscribe an unsubscribed or suppressed contact via CSV; reject rows failing MX checks; update existing contact metadata but protect strict states (unsubscribed/suppressed).

G-2. EDM Contact Tagging

* Support tags via maac.io click, journey action, contact profile, bulk update, and (planned) OpenAPI.
* Tags sync to True Contact profile.

G-3. Real-time EDM Contact Status Sync

* SendGrid Event Webhooks for unsubscribes, bounces, complaints; external ESP CSV fallback for status sync.
* Suppression rules mapped to SendGrid events and internal suppression logic.
* Support manual CSV status updates UI.

G-4. Short URL Tracking & GA4/SDK Integration

* maac.io short links for EDM & SMS append UTM parameters (when GA4 connected) and a non-PII contact token for GA4/SDK attribution.
* Web SDK reads maac.io token on landing to bind a browser session to email contact.

G-5. Identity & Web SDK (Q1 target)

* Admin feature toggle to enable Website User Identification per Web Channel.
* SDK exposes enable(), identify(email), track(...), optOut().
* identify(email) binding only processed if Admin toggle enabled; binding persists 30 days.
* SDK identify(email) takes precedence over maac.io token identity.

***

#### H - Reporting & Analytics (EDM)

H-1. Journey Performance Report (EDM)

* Include EDM metrics in Overview: Delivered, Open rate (low confidence), CTR, Unique CTR (with GA4), and GA4 commerce metrics attributed to EDM nodes.
* Per-channel rows include EDM-specific metrics: Bounced, Bounce rate, Complaints, Complaint rate, Unsubscribes, Unsubscribe rate.

H-2. Node Performance (EDM)

* EDM node-level metrics include bounces, complaints, unsubs; provide Delivery Failure report link (timepicker + downloadable CSV).

H-3. Email Sent Failure Report

* Downloadable CSV columns: Email | Status | display\_name | gender | customer\_id | mobile | birthday | tag | undeliverable\_reason | time\_stamp.
* Undeliverable reasons categorize system checks (Insufficient balance, Suppressed, Rejected by ESP, Hard bounce, Soft bounce, Rate-limited, Technical error).

***

### Non-Functional Requirements (selected)

* Journey trigger latency: target sub-100s (99th percentile) for end-to-end trigger-to-action in typical flows.
* Cross-channel contact query: high-perf target; load-test CDH unification endpoints to meet RPS & latency goals.
* SendGrid webhook processing: P90 latency < 10s for processing status events.
* Contact import: handle large CSVs (100k rows) within acceptable background processing time (target monitored).
* PII handling: no PII in URLs; maac.io tokens must be non-PII; PII at rest encrypted as per security standards.

***

### Release plan & GTM

* Release phases aligned by region/plan gating and ops-managed EDM onboarding.
* Ops onboarding steps documented (DNS package, SendGrid provisioning, Sender Profiles, Re-check DNS).
* GTM: self-serve + Ops-assisted onboarding; prepare Help Center copy and in-product CTAs.

***

### Meetings, Decisions & Logs (selected)

Use Expandable blocks in GitBook to include the long meeting log. Below are summaries and links to key decisions and action items.

<details>

<summary>AI Collaboration &#x26; Meeting Logs (select highlights)</summary>

* 2025-12-09 — Test case review M6: discussed Email Channel warning & suspended thresholds (Hard bounce rate/count; Spam report threshold).
* 2025-12-01 — Test case review M5: unsubscribe header insertion issue and editor validation.
* 2025-11-26 — Hygiene Validation spec adjustments: sampling approach proposal, global hard bounce list, rolling 24H suspension policy.
* 2025-11-06 — Daily standup: journey basic settings reminders & items to confirm.
* 2025-10-31 — Test cases review part 2: unification rules and editor scope.
* 2025-10-23 — Design review: Send from & reply-to as Sender Profile, personalization placeholder behavior.
* 2025-09-19 — M2 solution review: EDM onboarding & editor survey; action items for Ops & engineering.
* 2025-09-16 — TF sprint meeting: Milestone breakdown and demo planning.
* 2025-08-18 — TF kickoff: direction, strategy, and initial milestones.

(Full chronological logs retained in source document; consider moving each meeting note to GitBook "Updates" or "Meeting notes" page using Expandable blocks.)

</details>

***

### Test Cases & QA

A set of user stories and test cases (M1 & M2) were generated and reviewed. These cover:

* Org-level journey list and filters.
* Cross-channel contact queries and ambiguity handling.
* SDK event triggers and throttling semantics.
* Journey settings: message limits, contact trigger limit, Do-Not-Disturb.
* Send SMS node: editor, short URL generation, balance warnings, failure skip logic.
* Check Reachability node: dynamic output paths, priority evaluation, exclusive routing.
* EDM onboarding (SendGrid): domain auth, webhook provisioning, Sender Profiles, rate limits.
* EDM node: editor modes, per-link short URL, unsubscribe handling, pre-send compliance checks.
* Contact import hygiene (MX check), suppression rules, webhook adapters.
* Reporting: omnichannel overview, per-channel breakdown, EDM-specific metrics, delivery failure reports.

These test cases map directly to ACs in the feature spec. For GitBook, each feature page should include the relevant test cases as an Expandable block or link to QA docs.

***

### Open Discussion & Action Items (selected)

* EDM approach:
  * M1: focus on omnichannel + SMS in journey; M2: EDM onboarding & editor.
  * Two architectural options for EDM: M1 adapter to existing customer ESP templates (rapid MVP for large clients) vs M2 self-hosted editor + SendGrid (broader coverage for small/medium clients). Recommendation: support both paths long-term; prioritize Ops-managed SendGrid integration (M2) based on TF discussion.
* Contact unification:
  * Use CDH unification; email & phone set as unify keys; ambiguous lookup resolves to most recently updated profile (log ambiguity).
* Trigger pause types:
  * Support "Journey Pause" (pause active journey sends) and "Trigger Pause" (prevent new entries while letting existing contacts complete). Implementation and UX decisions in scope for M1 minor enhancement (ticketed).
* Hygiene & suppression:
  * Implement MX checks on import; global hard bounce list; rolling 24H warning & suspension policies; credit-back for hard bounces.
* SDK identity & consent:
  * Admin toggle per Web Channel to enable SDK identify(email); SDK requires enable() to process identify()/track() (consent).

Action owners and tickets are recorded in original document for follow-up.

***

### Development Documents & QA

* Design prototypes (refer to internal Figma link in source).
* Backend design docs and BE design review (internal).
* QA test case spreadsheet and templates referenced in PRD.

***

If you want, I can:

* Produce a GitBook-ready split into pages (M1 — Infrastructure, Canvas, Contact & Data, Reporting; M2 — EDM Onboarding, Canvas, Contact & Data, Reporting), and convert the meeting logs into Expandable entries and the long ordered "How-to" flows into Stepper blocks.
* Generate a shortened executive summary or a one-page TL;DR for stakeholders.

**\[M1 – Omnichannel journey with SMS]**

Figma: [UI mockup](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=5140-30169\&t=Rz7cN5XDO8AkEqcm-0)

| **Section**[**Figma**](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=5140-30169\&t=Rz7cN5XDO8AkEqcm-0) | **UI mockup**                                                                                                                            | **Note**                                                                                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Journey List                                                                                                                                      | ![](<../../../.gitbook/assets/Unknown image (22)>)                                                                                       | - Org-level omnichannel structure                                                                                                                                                                                                           |
| Basic Settings                                                                                                                                    | ![](<../../../.gitbook/assets/Unknown image (23)>)                                                                                       | - Message sending limits by platform                                                                                                                                                                                                        |
| Journey Settings – Trigger node                                                                                                                   | ![](<../../../.gitbook/assets/Unknown image (24)>)                                                                                       | - SDK standard events are supported - Page View - _Note: Not yet supports view counts & timespan_ - Add-to-cart - Purchase - _Note: EDM channel events are not included in M1_                                                              |
| Journey Settings – Trigger node > Web SDK events                                                                                                  | (Use Page View as an example)![](<../../../.gitbook/assets/Unknown image (25)>)                                                          | - Can select Any or Specific Web channel(s) footprint - Max: 5 web channels                                                                                                                                                                 |
| Journey Settings – Trigger node > Channel events                                                                                                  | (Use Open LINE message as an example)![](<../../../.gitbook/assets/Unknown image (26)>)                                                  | - Can select Any or Specific LINE OA Broadcast message(s) - Max: 5 channels                                                                                                                                                                 |
| Journey Settings – Add node                                                                                                                       | ![](<../../../.gitbook/assets/Unknown image (27)>)                                                                                       | - Newly support: - Message node - SMS - EDM (M2) - Split node - Channel Reachability - _Note: “Yes/No branch” renamed to “Event condition"_                                                                                                 |
| Journey Settings – Branch node                                                                                                                    | (Initial setting)![](<../../../.gitbook/assets/Unknown image (28)>) (Complete setting)![](<../../../.gitbook/assets/Unknown image (29)>) | (Only support to add one channel at this stage) - Send message based on channel priority with reachability check - max: 5 channels routing                                                                                                  |
| Journey Settings – Message node (SMS)                                                                                                             | LINE message node![](<../../../.gitbook/assets/Unknown image (30)>) SMS message node![](<../../../.gitbook/assets/Unknown image (31)>)   | - Send LINE node - Need to select a LINE channel - Send SMS - Short link support UTM tracking                                                                                                                                               |
| Reporting – Overview                                                                                                                              | ![](<../../../.gitbook/assets/Unknown image (32)>)                                                                                       | Metrics definition see [here](prd-omnichannel-customer-journey-line-sms-edm.md#_gmsk2rsp5na)                                                                                                                                                |
| Reporting – SMS Node performance                                                                                                                  | ![](<../../../.gitbook/assets/Unknown image (33)>)                                                                                       | - Metrics specific to SMS node - Message unit - Delivery failure - If non-zero, the failure report link will be clickable for download. - Failure report only provides records for the last 2 months. - _Note: SMS do not support Open (%)_ |

**\[M2 – Omnichannel journey with EDM]**

Figma: [UI mockup](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=5140-30169\&t=Rz7cN5XDO8AkEqcm-0)

| **Section**  | **UI mockup**                                                                                                                                                                              | **Note**                                                                                                |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------- |
| Admin Center | Ref: [figma](https://www.figma.com/design/xB2NgsE5wYz2NfXRnhIQsl/Email-channel?node-id=125-3\&p=f\&t=JTNifv8qT5Hi5Ucc-0) \[Channel List]![](<../../../.gitbook/assets/Unknown image (34)>) | \[Channel list] - Shows **Email channel by brand domain** and status (Connected / Not set / Suspended). |

_Status definition please see Note \[M2] #3._- “Activation” field shows the overview of the channel configuration status.

* If channel status is “**Not set”** or **Suspended”**, email sending will be blocked in Journey until Users/Ops fixes it.

\| | \[Email channel configuration page]![](<../../../.gitbook/assets/Unknown image (35)>) | \[Email channel configuration page] - Read-only for MAAC users; used to check domain authentication and sender profiles.

* Sender domain table shows **Verified / Warning / Failed** based on SPF/DKIM.

_Status definition please see Note \[M2] #3._- Sender profiles section lists all “From names/emails & Reply-to emails” and status; “Failed” profiles cannot be used in “Send EDM” nodes.

\| | \[Email Cahnel is managed-serve by PO only]![](<../../../.gitbook/assets/Unknown image (36)>) | | | Contacts | Ref: [figma](https://www.figma.com/design/4izQy6bC4QxfvTOxuFotIl/MAAC_Contacts?node-id=1232-27236\&p=f\&t=dqTtfE7tktfPpjjF-0) \[Contact list]![](<../../../.gitbook/assets/Unknown image (37)>) | \[Contact List] - Email contacts are shown in the Contacts list once imported.

* **Email channel reachability:** - _Reachable_ = subscribed - _Not reachable_ = unsubscribed OR suppressed (bounced, spam report, or hygiene invalid.

\| | | \[Email Contact Profile]![](<../../../.gitbook/assets/Unknown image (38)>) | | | Contacts- Import EDM Contacts | Ref: [figma](https://www.figma.com/design/4izQy6bC4QxfvTOxuFotIl/MAAC_Contacts?node-id=1265-39210\&t=dqTtfE7tktfPpjjF-0) \[Import data manually – step 1]![](<../../../.gitbook/assets/Unknown image (39)>) | \[Import data manually – step 1] - Select an email channel to import contacts.

* Choose “Email” as key value - Import new contact - Update existing contact | | \[Import by Email - step 2]![](<../../../.gitbook/assets/Unknown image (40)>) Import CSV template: [LINK](https://docs.google.com/spreadsheets/d/1_ClwDup8Jagw8kyY6B5b-7NVuPm1Aq5iHVFBDdMmwnc/edit?gid=0#gid=0) | \[Import by Email - step 2] - Download CSV tempalte ([ref](https://docs.google.com/spreadsheets/d/1_ClwDup8Jagw8kyY6B5b-7NVuPm1Aq5iHVFBDdMmwnc/edit?gid=0#gid=0)) - Required fields - Email - Messaging status (subscribed, unsubscribed, suppressed\_{type}) - EDM specific fields (optional for audit use) - consent source - consent at \[Import result] - Import/Update result will show in the notification dropdown with a “import failure report” download link.

\| | Journey Settings – Trigger node | Ref: [figma](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=6795-84712\&t=ZmIHnOUkFDWyMKRA-0)![](<../../../.gitbook/assets/Unknown image (41)>) | EDM trigger node supports: - Email open - from email sent via MAAC - Email click - from [maac.io](http://maac.io/) short link - Email unsubscribe - from MAAC hosted unsub link | | Journey Settings – Branch node (EDM) | ![](<../../../.gitbook/assets/Unknown image (42)>) | Email channel reachability follows contact’s “channel reachable” status.

\| | Journey Settings – Message node (EDM) | Ref: [figma](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=6804-89930\&t=ZmIHnOUkFDWyMKRA-0) \[Edit - Basic Setting]![](<../../../.gitbook/assets/Unknown image (43)>) | \[Edit - Basic Setting] - Select “email channel” (brand domain), then “sender profile” - Edit email subject line - Choose the EDM editor: - Drag & Drop - HTML (not supported in this phase) | | \[Edit - Message (Drag & Drop editor)]![](<../../../.gitbook/assets/Unknown image (44)>) | \[Edit - Message (Drag & Drop editor)] - Build EDM content with the drag-and-drop editor (text, image, button blocks, etc.).

* Quick inset “links” - maac.io short links - Unsubscribe link placeholder → the unsubscribe link will be configured on each email send | | \[Select EDM Template]![](<../../../.gitbook/assets/Unknown image (45)>) | \[Select EDM Template] - Select a pre-saved **EDM template** from template library.

\| | \[Template Library]![](<../../../.gitbook/assets/Unknown image (46)>) | \[Template Library] - Create and manage EDM templates directly fromthe Template library.

\| | Reporting – Overview | Ref: [figma](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=6804-97063\&t=ZmIHnOUkFDWyMKRA-0)![](<../../../.gitbook/assets/Unknown image (47)>) | - Journey overview report aggregates performance across LINE, SMS, and EDM nodes.

* Channel performance is break down by message node.
* EDM-specific metrics are included in total metrics (bounce, complaint, unsubscribe).

\| | Reporting – EDM Node performance | Ref: [figma](https://www.figma.com/design/7yomMrvFPs9J268IlckbFG/MAAC_Customer-Journey_Design?node-id=6831-77736\&t=ZmIHnOUkFDWyMKRA-0)![](<../../../.gitbook/assets/Unknown image (48)>) | - EDM Node performance shows EDM-specific metrics.

* Download the failure report within 2 months.

|

### Note & FAQ

#### Note

\[**M1 – Omnichannel journey with SMS**]

1. _**\[For internal communication only]**_**&#x20;Contact Unification**: For this release, the system uses real-time lookups based on shared identifiers (like phone or email) to create a "simulated" unified view of a contact across channels. This allows for immediate cross-channel journey orchestration. A fully unified contact data model ("Omnichannel Segment") is a separate project planned for a future phase.
2. \*\* GA4 Trigger Limitation\*\* : As a reminder, using a GA event as a journey trigger will only work for LINE contacts who entered website from a LINE source. For all other use cases, please use the Web SDK trigger.
3. **Channel Onboarding**: Activating SMS and EDM channels is not self-serve at this stage. It requires configuration by POs. Please direct clients to their CSM for setup.
4. **SMS Phone Number Format**: For SMS messages to be sent successfully, the contact's phone number must be in the valid E.164 international format. MAAC will not auto-correct the invalid phone formats.
5. **Trigger Throttling Rules**: different triggers have different re-entry limitations for the same journey:

* **Web SDK Events**: Once per hour per true contact (unified contact).
* **GA Events**: Once per 24 hours per true contact (unified contact).

\[**M2 – Omnichannel journey with EDM**]

1. **EDM channel onboarding (PO manage-serve)**

* The client must provide their **brand domain** (eg. [cresclab.com](http://cresclab.com/)), **sender domain(s)** (eg. [marketing.creslab.com](http://marketing.creslab.com/)), **sender profile(s)** ( eg. “CL Newsletter” < [edm@marketing.creslab.com](mailto:edm@marketing.creslab.com)>), and **Reply-to** email (must be a real inbox).
* PO provisions Sendgrid subuser and generate DNS records → Client IT updates DNS → PO re-check DNS and create sender profiles.
* Email channel will be displayed in the Admin center and will be read-only. If any issues, they need to contact support.
* (Note: PO will instruct detailed onboarding flow & playbook.)

2. **Email channel hierarchy**

* Email channel = Brand domain (subscription status is stored at this level, e.g. brand.com).
* One Email channel can have multiple Sender Domains (e.g. news.brand.com, promo.brand.com).
* Each Sender Domain can have multiple Sender Profiles (Brand News [news@news.brand.com](mailto:news@news.brand.com)).
* Every Sender Domain must be DNS-verified before it can send EDM.

3. **Email Channel & Sender Domain status definition**

* Email channel status
  1. Connected (green): At least **one Sender Profile = Active**.
  2. Not set (grey): **No active Sender Profile** (e.g. none created, or all tied to unhealthy domains).
  3. User cannot send EDM until setup is completed.
  4. Action: client provides/fixes correct domain/sender info → Ops re-check domain verification + sender profiles.
  5. Suspended (orange): Email Channel is\*\* temporarily disabled\*\* by system policy (eg. high hard-bounce / complaint rate)
  6. All EDM sends are blocked
  7. Action: clean list, review sending practice, then request Ops to unsuspend.
* Sender Domain health
  1. Verified (green): all fields (CNAME/DKIM/DMARC) are pass → good to send
  2. Warning (yellow): some fields are fail → still allowed to send, but there is a deliverability risk.
  3. Action: Suggest the client IT check and fix the DNS settings.
  4. Failed (red): all fields (CNAME/DKIM/DMARC) are fail → block send.
  5. Action: Client IT must update DNS records.

4. **Shared IP & list quality**

* EDM uses a\*\* shared IP\*\*. One bad sender can hurt all clients.
* Clients must use consented, opt-in lists only. No purchased lists, no scraped lists.

5. **EDM contact subscription, unsubscribe & suppression**

* MAAC does not provide subscription methods at this phase. (Will support subscription in EDM broadcast project.)
* Every EDM should include an **unsubscribe link**, directly\*\*\*\*inserted from the EDM editor; clients cannot use their own unsubscribe link.
* We will manage a suppression list, including hard bounce, multiple soft bounces, spam report…etc.
* CSV import **cannot** override suppression satus, meaning user cannot “re-subscribe” those contacts by import.
* “Suppressed” and “Unsubscribed” contacts are treated as “Not Reachable”.

6. **Unsubscribe link is mandatory**

* Every EDM must contain a **system unsubscribe link/block** (generated from editor).
* If the unsubscribe link is missing, the editor will **block Save.**
* If the user inserts their only unsubscribe link, the system will auto-replace it with the MAAC-generated unsubscribe link.

7. **Contact import (CSV) – domain checks**

* To protect overall send reputation and shared IPs, during CSV import, the system checks:
  1. If the email domain exists (MX record) → import success
  2. If the domain is in a global hard bounce / blocked list → import fail

8. **Rolling 24H hard bounce monitoring – suspension & re-activation**

* If bounce / spam rate passes our internal threshold in the past 24 hours, the email channel will be suspended and sending will be paused immediately, without prior notice.
* To resume sending, the client must clean their list (using 3rd party hygiene tool) → Pass Ops review (check the status change logs) → Wait for Ops to manually re-activate the Email channel.
* If the client request, we can help clean the list via the Sendgrid hygiene tool. This is an add-on service, client need to pay extra fee. (Will be conducted offline, not productized yet)

9. **Email channel interaction events**

* **Email Open**：Opens are tracked with a tracking pixel. Might be affected by Apple Mail Privacy, image blocking, prefetch, etc. Therefore, **open numbers can be over- or under-counted**.
* **Email Click**：Clicks are tracked only when links are converted to **maac.io short links**.

10. **M2 does not yet support the following items:**

* “Web SDK to capture visitor email” and monitor on-site behavior to trigger journey.
  1. Target Q1 for development.
* “HTML editor” to let user directly import html code to build message.
  1. Target Q1 for development (include in EDM broadcast project)

#### FAQ

Q1: **How does the system decide which channel to use if a customer is on LINE, SMS, and Email?**

* **A:** Through the "Check Reachability" node in the journey canvas. You can create a prioritized list of channels (e.g., 1. LINE, 2. Email, 3. SMS). The system checks the first channel; if the contact is reachable, it sends them down that path. If not, it checks the second, and so on. This gives you full control over channel priority and cost.

Q2: **What happens if my journey runs out of SMS credits?**

* **A:** The system will stop sending SMS messages from that journey, but other actions (like sending LINE) will continue to run. You will be proactively notified: a warning icon will appear on the journey list and the affected SMS node, and a system alert email will be sent to your organization's designated contacts for MAAC points balance insufficient alert.

Q3: **Can the same person trigger a journey multiple times if they are identified by different channels?**

* **A:** No, we prevent this. The "Contact Trigger Limit" setting applies to the unified "True Contact," not the individual channel profile. If a user's LINE profile triggers the journey, their entire unified profile (including their email and phone identities) is considered to have entered, preventing them from being spammed via another channel for the same journey.

Q4: **What does enabling "CDH Contact Unification" mean for clients and who sets it up?**

* **A:** Contact Unification is essential for the omnichannel journey to work. It allows MAAC to link a customer's different profiles (eg. their LINE account and email address) into a single "True Contact" using shared keys like an **email address** or **phone number**. This is necessary to track a user's journey across channels and avoid sending them redundant messages. This feature is enabled by our internal team during client onboarding, not by the client themselves. **(Default on: LINE/IG/FB ID, Phone, Email)**

Q5: **If one LINE profile is linked to multiple phone numbers, how does the system decide which one to act on?**

* **A:** In cases of ambiguity where one identifier is linked to multiple profiles, the system will default to selecting the contact profile that has the **most recently updated activity timestamp**.

Q6: **When a journey applies a tag to a channel contact, does it sync to their other profiles?**

* **A:** Yes, the tag is applied to the entire unified "True Contact," so all associated profiles will get the tag. The synchronization happens near real-time, typically within a few seconds. On the contact's profile page, the tag will be visible under the "MAAC tag" source, indicating it was applied by an action within the MAAC platform, such as a journey.

\[**M2 – Omnichannel journey with EDM**]

Q7: **Which clients are a good fit for EDM in Journey, given the current M2 scope?**

* **A:** MAAC’s positioning at this phase is to help clients automate workflow across multiple platforms/channels, not replacing their primary ESP.
  * Good fits:
    * Mid-size brands with **membership / loyalty programs** that run birthday, renewal, or VIP journeys.
    * Clients who use a standalone ESP for bulk newsletters, but are looking to **combine cross-channel behavior in one flow** (tags, purchases, engagement across LINE/SMS/EDM) without data breaks.
  * Less ideal (for now):
    * EC clients who rely heavily on cart retargeting and real-time web events.

Q8: **How is EDM charged in Journey? Do clients need a separate EDM quota?**

* **A:** (TBC) Each plan includes an email quota. For overage charges, EDM uses the same CL points pool as SMS/MMS; there is no separate “EDM-only” points pool. For the billing report, there will be an EDM type to calculate the usage and cost.

Q9: **What does the client need to prepare before EDM channel onboarding?**

* **A:** They must provide: brand domain, sender domain(s), sender profile(s), and a real reply-to inbox. They also need IT support to add DNS records (SPF/DKIM, etc.) on their domain. (_Detailed onboarding training will be provided by Product Ops._)

Q10: **What are the key product limitations in this M2 release that I must remind clients of?**

* **A:**
  * No HTML editor yet – only drag-and-drop templates are supported. (should be include in Q1 EDM broadcast)
  * Web SDK cannot yet capture visitor email to trigger EDM journeys directly from on-site behavior. (plan in Q1 SDK optimization)
  * Subscription-center style management is not in this release; we only support unsubscribe + suppression. (should be include in Q1 EDM broadcast)

Q11: **What happens if a client’s email contact list quality is poor and the email channel gets suspended?**

* **A:**
  * MAAC monitors hard bounce / spam rate over a rolling 24-hour window. If it exceeds our threshold (suppression counts > 20 AND suppression rate >5%), system will pause the email channel immediately to protect shared IP reputation.
  * To resume sending, the client must clean the list (eg. hygiene tool): update the entire email contact list.
  * Notify Ops to review the update log (number of contacts change status to suppressed) → Ops re-activate the channel.
  * If the client asks, we can also help them do list-cleaning via Sendgrid hygiene is a one-time add-on service.

**Questions from GTM training**

Q: “Support shorten URLs (maac.io) in SMS and EDM messages to attribute website events back to the correct user and channel.” 這個現在的階段就有了嗎？如有得話，想要理解為 Customer Journey 訊息 [maac.io](http://maac.io/) 連結才會做網站身份整合，還是所有功能的 [maac.io](http://maac.io/) 連結都會？- Catherine

A: 客戶若有安裝SDK，所有有帶入 UTM 的 [maac.io](http://maac.io/) 連結 (不限 customer journey 產出的短網址) 都可以關聯到網站訪客身份識別。

Q: 想多問一點是指例如我今天沒有完成網站導流工具的身份整合，一樣點擊 [maac.io](http://maac.io/)，後續如果有加入購物車、瀏覽網頁等等行為，就會被購物車再行銷 2.0 和自動旅程新增 SDK trigger 偵測到，且如果追蹤機制還在，毋需做網站導流工具的身份整合，一樣有效追蹤對嗎？等於從 LINE [maac.io](http://maac.io/) 出發，用 SDK 就可以達成網站導流工具的身份整合從網頁來的效果，和在 CAAC 對話邀請送出整合代碼的效果～？- Catherine

A: 是的，不過這種做法會有一個風險是如果 member A 將 [maac.io](http://maac.io/) 短網址分享給其他人，member A 就會關聯到其他人的網站行為。SRT 和 CAAC 整合代碼的身份整合是更準確的。

Q: TW Region 為 Growth plan 以上且有開通任一 SMS 相關功能，且有儲值，就可以使用對嗎？- Catherine

A: 是的，只要有開通 SMS 功能且有儲值，即可以在 Customer Journey 發送 SMS

\[**M2 – Omnichannel journey with EDM**]

Q: 如果是一個 Web 匿名 Contact，在 Website 上面提供 Email，目前是沒有任何機制，MAAC 會接到，並且開始走 Email Journey 對嗎？未來會有什麼樣相關的規劃嗎？ - Catherine

A: 目前沒有支援取得 subscribe 的機制；會在 EDM broadcast 專案一起規劃 subscription flow 與訂閱狀態更新

Q: Email contact 進到 Website 上的行為追蹤，也是利用像 LINE contact 點擊 MAAC links 的 im 技術機制嗎？- Catherine

A: 是的！

### Setting (For CSM)

Instruction for CSM to set the function for customers. Ex: Django setting…

Please insert screenshots or refer links to Google Slides or Figma links

### Reference

Put related documents here. ex: related product intro

**Pricing Table**

## Feature Pricing Rollout Notice

### Product Name: MAAC

### Feature Name: Email Pricing (EDM in Journey)

### Feature Summary

MAAC now natively integrates **EDM (via SendGrid)** as a channel within the Customer Journey. This allows clients to orchestrate cross-channel communication (LINE, SMS, Email) in a single flow.

**Capabilities:**

* **Email Editor:** Supports both Drag-and-Drop editing. (Note: HTML editor will be supported in Q1)
* **Orchestration:** Includes "Check Reachability" branching to prioritize high-engagement channels while ensuring scalable reach. (eg. Send LINE first → Fallback to Email).
* **Analytics:** Unified reporting for delivery, open rates, and clicks (with GA4 integration), and email-specific metrics (eg. bounce, unsubscribe, report spam).

**Limitations (Current Phase):**

* **Standalone Sender Infrastructure:** Does not support integration with client's existing ESP (eg. Mailchimp). Clients must import email contact lists (via CSV) to MAAC to utilize the service. Integration with mainstream ESPs will be implemented gradually based on client demand.
* **Automation Only:** Currently supports Journey automation triggers only. EDM Broadcast is scheduled in 26’Q1.
* **Managed-serve Onboarding:** Requires manual provisioning by Product Ops. No self-serve setup yet.

###

### Pricing Scope

This rollout establishes the pricing model for **Email volume usage**, including future EDM broadcast.

* **Email Volume:** Charges apply **only to the volume of emails sent** (via Free Quota or Overage).
* **Journey Feature:** The capability to use Email nodes within Customer Journeys is included in the existing MAAC subscription plans. There is NO additional feature fee for enabling Email within Journeys.

### HQ Pricing & Charge Mode > PM

| Market | Feature      | Pricing                                                                                                                                           | Pricing model                                                        | Recurring / One-time fee |
| ------ | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- | ------------------------ |
| HQ     | Email Volume | **Free Quota:** • Growth: 2,000 /month • Professional: 10,000 /month • Corporate: 20,000 /month**Email unit price (overage):** • 0.06 NTD / email | Plan includes a free quota (reset every month) + Usage-based overage | Monthly usage            |

###

### Feature name translation > PM

|              | TW       | EN            | TH                      | JP                      |
| ------------ | -------- | ------------- | ----------------------- | ----------------------- |
| Feature name | Email 服務 | Email Service | (need local team input) | (need local team input) |

###

### Local Market Pricing & Charge Mode > Local Manager

The cost for CL, including the fee to SendGrid (sending vendor), the exchange rate, and our own maintenance buffer, is US$0.0013. To maintain at least a 30% margin, the email unit price should be at least US$0.0017.

* **What we need to decide:** unit price per email & free quota for each pricing plan

TBC with local GMs _(TH market - due date Jan 9)_

1. Whether to follow HQ’s model: plan-based unit baseline (unit × US$0.0013 < 2% of MRR) & overage fee
2. How much free quota should be included in the current plans?
3. How much does it cost when a client sends more than the quota?

| Market | Feature      | Pricing model(Plan-based / Add-on )                                                                                                                                          | Pricing(Please give the currency) | Recurring / One-time fee                          |
| ------ | ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------- | ------------------------------------------------- |
| TW     | Email Volume | Plan-based (free quota included in each plan tier)• Growth: 2,000 units / month • Professional: 10,000 units / month • Corporate: 20,000 units / month                       | NTD 0                             | -                                                 |
| TW     | Overage      | Add-on (email unit price)                                                                                                                                                    | NTD 0.06                          | CL points deducted based on monthly overage usage |
| TH     | Email Volume | Use the packages on the website as the calculation base: • Basic: 1000 units / month • CRM: 4000 units / month • Engagement: 4000 units / month • Growth: 7000 units / month |                                   |                                                   |
| TH     | Overage      |                                                                                                                                                                              | THB 0.06                          |                                                   |
| JP     | Email Volume | (need local team input)                                                                                                                                                      |                                   |                                                   |
| JP     | Overage      |                                                                                                                                                                              | (need local team input) JPY 0.3?  |                                                   |
| SG     |              |                                                                                                                                                                              |                                   |                                                   |

###

### Exception Notes

### Expected Release Timeline

Release market：TW / TH / JP / SG

Release date：

* 12/31: TW L1 & L2 & SG
* 1/7: TW L3+ & TH
* 1/14: JP

### Attachments

* PRD ： [PRD - Omnichnnel Customer Journey (LINE/SMS/EDM)](https://docs.google.com/document/d/1E9NGB9pEtL91J88mokQl-thkFtxo1wVjLyTr_1ScdbI/edit?tab=t.0#heading=h.7z5imn1sorpi) (EDM is covered in M2 scope)
* Pricing Strategy Discussion Record：n/a
* Confirmation Emails from Each Market (if any)：
  * [TW slack thread](https://chatbotgang.slack.com/archives/C03CX4LSRPG/p1764561748374729)
  * JP slack thread
  * TH slack thread
* Consideration for pricing：

#### \[ZH] 「現階段」價格設計方向與目標

* 策略目標與定位
  * 挑戰：在產品功能尚未完全到位（缺乏 EDM Broadcast）的情況下，說服客戶開始使用 MAAC 發送 Email
  * 定位：「跨渠道 Orchestration 的輔助角色」而非「取代客戶主要發信平台 (ESP)」
  * 目標：極大化採用率，優先培養客戶在 MAAC 發送自動化信件的習慣
* 定價策略
  * 採取 「低門檻、用量計費、價值導向」 的滲透策略（Penetration Pricing）
  * 計費模型： 混合制 (Freemium + Flat Overage Rate)。
    * 方案內含額度：降低客戶開啟功能的心理門檻（有免費額度）
    * 單一超額費率：現階段不設複雜級距價格，降低業務溝通成本
* 方案設計＆成本計算

| 方案 (Plan)        | 月費 (MRR)    | 建議每月免費額度 (封） | 對外價格 (封) | 額度價值 (對客戶) | 實際成本 (對 MAAC) | 成本佔營收比    |
| ---------------- | ----------- | ------------ | -------- | ---------- | ------------- | --------- |
| **Growth**       | $3,325 (起)  | **2000**     | 0.06 NTD | $120       | $66           | **2.4%**  |
| **Professional** | $19,375 (起) | **10000**    | 0.06 NTD | $600       | $330          | **1.70%** |
| **Corporate**    | $39,600 (起) | **20000**    | 0.06 NTD | $1,200     | $660          | **1.67%** |

* 免費額度成本占營收比 < 2%
* 最低底價：0.04 NTD / 封 (含 SendGrid 費用 0.033 NTD/封 + 20% 匯率/維運 Buffer)
* 財務風險評估
  * 免費額度成本僅佔該方案 MRR 的 1.67% \~ 1.98% (均低於 2%) → 換取客戶的長期黏著度與未來的用量營收

**\[EN] Current Phase: Pricing Design Direction & Goal**

* Strategic Goals & Positioning
  * Challenge: Drive Email channel adoption despite currently lacking EDM Broadcast features.
  * Positioning: Focus on "Cross-channel Orchestration Support," not replacing primary ESPs. (Email Sending Provider)
  * Goal: Maximize adoption; cultivate the habit of using MAAC for multichannel automation.
* Pricing Strategy
  * Approach: "Low barrier, Usage-based, Value-driven" Penetration Pricing.
    * Model: Hybrid (Freemium + Flat Overage Rate).
    * Free Quota: Lowers psychological barrier to entry (free quota, why not?)
    * Flat Rate: No complex tiered unit price; simplifies sales communication.
* Plan Design & Cost Structure

| Plan             | MRR            | Monthly free quota (email） | Unit Price (to client) | Value estimation (to client) | Actual cost (to MAAC) | Cost-to-Revenue ratio |
| ---------------- | -------------- | -------------------------- | ---------------------- | ---------------------------- | --------------------- | --------------------- |
| **Growth**       | $3,325 (from)  | **2000**                   | 0.06 NTD               | $120                         | $66                   | **1.98%**             |
| **Professional** | $19,375 (from) | **10000**                  | 0.06 NTD               | $600                         | $330                  | **1.70%**             |
| **Corporate**    | $39,600 (from) | **20000**                  | 0.06 NTD               | $1,200                       | $660                  | **1.67%**             |

* Cost Impact: Free quota cost < 2% of total revenue.
* Minimum price: 0.04 NTD / email (SendGrid fee 0.033 NTD / email + 20% Ops buffer).
* Financial Risk Assessment
  * Free quota cost is merely 1.67% \~ 1.98% of MRR (all < 2%) → to secure long-term retention and future volume revenue.

### To-Do by Stakeholders

**RevOps (Sales Pricing and Reporting Alignment)**

* Update the **Price Master Sheet**
* Define **Sales Process rules** (plan mapping, add-on eligibility)
* Adjust **KPI / Revenue Reports** accordingly

**ProductOps (Feature Access and Configuration Setup)**

* Configure **plan / add-on access control**
* Implement **feature toggle or backend configuration items**
* Conduct **QA checks** to ensure feature access is correctly restricted based on plan level

###

### Check List

| Owner        | Item                                | Status      | Note                                                                                                                                |
| ------------ | ----------------------------------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| PM           | Pricing confirmed with HQ leader    | Finish      | This pricing plan is intended for the short term and may be adjusted for the overall CL product suite pricing revamp. (by 2026/4/1) |
| Local enable | Pricing confirmed with Local leader | In progress |                                                                                                                                     |
| ProductOps   | Feature setting SOP                 | Not start   |                                                                                                                                     |
| RevOps       | Sales process                       | Not start   |                                                                                                                                     |

### Appendix

| ESP 競品                | 計價模型                                                              | 價格分析                                                                                                |
| --------------------- | ----------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| Mailchimp             | 依聯絡人數量計費 (Contact-based Subscription) + 超額發送費                     | 計費基準：5,000 聯絡人 月費：$59 USD / 月 (約 1,920 TWD) 場景換算： 若該月自動化只發了 5,000 封 換算單價：0.38 TWD / 封               |
| 點數儲值制 (Pay-as-you-go) | 購買 5,000 Credits 大約需要 $75 - $100 USD。 換算單價：約 TWD 0.48 - 0.65 / 封。 |                                                                                                     |
| 電子豹 (TW)              | 點數儲值制 (Pay-as-you-go)                                             | 購買 100,000 封 (點數)：價格約 18,000 TWD 單價（依級距）：約 TWD 0.09 - 0.40 / 封                                      |
| Blastmail (JP)        | 依聯絡人數量計費 (Contact-based Subscription)                             | 初期費用： 10,000 JPY 月費： 3,000 個 email contacts → 3,300 JPY/月 場景換算： 若該月自動化只發了 3,000 封 隱含單價： JPY 1.1 / 封 |
| Taximail (TH)         | 點數儲值制 (Pay-as-you-go)                                             | 官方定價： 100,000 Credits = 14,000 THB 單價（依級距）： 約 THB 0.08 - 0.22 / 封                                   |

[**Holly Chang**](mailto:holly.chang@cresclab.com)\*\* JP local player research\*\*

| **Platform**                                            | **Pricing Structure**                          | **Pricing Details**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| ------------------------------------------------------- | ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Benchmark](https://www.benchmarkemail.com/jp/pricing/) | Plan-based (Number of contacts)                | Price: Starts at ¥4,700 / month (for 2,500 contacts). Price increases based on the number of contacts. Contacts: Starts from 2,500 up to 100,000. Sends: 10x your contact limit (e.g., 25,000 sends for the entry tier).**-> If a client only sends one time per month, the cost per email (Monthly Cost ÷ Contact Limit) is:¥1.88 / email**                                                                                                                                                                       |
| [blastmail](https://blastmail.jp/price/)                | Initial Cost + Plan-based (Number of contacts) | Initial Cost: ¥10,000 (One-time fee). Price: Starts at ¥4,000 / month (Light Plan) or ¥8,000 / month (Standard Plan). Contacts: Light Plan covers up to 5,000 contacts; Standard Plan ranges from 10,000 to 50,000 contacts. Sends: Unlimited (Send as many emails as you want with no extra cost). Note: Minimum contract period is 3 months. Price increases based on the number of contacts.**-> If a client only sends one time per month, the cost per email (Monthly Cost ÷ Contact Limit) is:¥0.8 / email** |
| [cuenote FC](https://www.cuenote.jp/fc/price/)          | Initial Cost + Plan-based (Number of contacts) | Initial Cost: From ¥30,000 (One-time fee). Price: Starts at ¥5,000 / month (for 2,000 contacts). Contacts: Starts from 2,000 contacts. Sends: Unlimited (Send as many emails as you want with no extra cost). Note: Price increases based on the number of unique email addresses. Minimum contract period is 6 months.**-> If a client only sends one time per month, the cost per email (Monthly Cost ÷ Contact Limit) is:¥2.5 / email**                                                                         |

**Journey TF Kick-off \[M1]]**

### 👉 討論結論以這份 [整理](https://docs.google.com/document/d/1bjiRa1W-PS12kc_ynjoy0KrzOfIyG6OXzpz_TJ8nRgA/edit?tab=t.svduok6yxwoh#heading=h.cpcly17k2cho)為主

### Omnichannel Customer Journey - TF Kickoff

#### Concept scope

**Project Goal**

*
  * 將 LINE-only 單一渠道自動旅程，升級為支援 LINE, WhatsApp , EDM, SMS 的**全渠道**自動旅程
  * 同步需更新聯絡人頁面，加入 WhatsApp EDM 聯絡人

**M1 Scope**

*
  * **架構升級：Org-level Customer journey – 實現跨渠道協作**
    * 階段任務：旅程在運行時，需具備跨渠道查詢能力：即使渠道聯絡人尚未在底層完全整合，系統也能透過共享 ID（手機號碼, email）動態查找同一用戶在其他渠道的狀態
    * 目標：在 Q4 Omnichannel Segment 實作前，仍可模擬出全渠道的旅程體驗，實現核心行銷場景
  * **新增渠道：支援 SMS & WhatsApp EDM**
    * 在編輯器中，新增「發送 WhatsApp EDM」和「發送 SMS」兩個獨立的訊息節點
    * Note： WhatsApp EDM 範本管理不在此次的 Scope；EDM 先串第三方，暫不自建
  * **多渠道數據＆互動事件處理**
    * 用戶互動事件通用化，例如：LINE open = WA read = EDM open = 「開封」
    * 加入渠道 (SMS & WA EDM) 限定事件，例如： WA opt-in , EDM subscribe / unsubscribe
    * 能基於跨渠道即時查詢結果「分支判斷」旅程流程

**Omnichannel journey use case**

*
  * From interview 常用情境：
    * (美科) 綁定訊息、優惠卷使用提醒、購物車未結
      * 渠道許願：若支援 SMS/EDM 高機率轉來 MAAC
        * EDM 目前 SL 後台直接發送， SMS 同時在 MAAC/Every8d 發送，一個月大約 2 W
        * 好處：追蹤完整數據，比 SF 更方便（需要去第三方連結確認數據)
    * (中租銀角零卡) 發送 EDM/SMS → 導引加入好友、撈取商機受眾 → 引導進件
      * 渠道應用：通路依序為 App → Line → SMS（視推播成本而定），也會使用 edm 但觸及率較低
    * (Vitabox) 購物車未結、14 天歡迎旅程、參與（意願貼標觸發，活動前通知 → 活動中持續互動）→ 完成 (獎項派發) → 持續互動 (推播產品知識)
      * 以「不打擾用戶」和「節省成本」為前提設計，分時段逐步發送 EDM、LINE、SMS
      * 若 60 天無興趣則不再進入旅程；素材會隨時間更新，維持「品牌持續有服務感」
      * 渠道許願：偏好能整合 SMS、EDM 平台，目前也有運用 Web channel (pop-up, banner, inline)
    * (味全龍) 太過業態限定：結合 beacon 到場打卡發放點數，旅程希望有三次溝通：買票完歡迎信（purchase date)、賽前 (date)、賽後
      * 渠道應用：通路偏好以 LINE 為主，因互動強、高開信率；EDM 詳盡如傳單；Web push 干擾性強，不偏好
      * SMS 已經淡出規劃，如果可以放入連結就可以重新放回行銷，簡訊是 cybe 發的
  * **M1 目標達成情境示範**
    * 情境 1 標籤觸發旅程 (優惠券提醒使用、引導留名單、OMO)
      * 示範：優惠卷提醒使用
        * \*\*觸發：\*\*貼上 \[優惠卷] 標籤
        * **延遲** #1：等待 2 天 (優惠券到期前 5 天)
        * **分支判斷 1-1**： 未領取用戶是否擁有可用的 WhatsApp 渠道？

\*\*條件篩選：\*\*排除 \[已領取] 標籤

是 (WA 用戶路徑)：發送 WhatsApp「優惠卷使用提醒」訊息模板

否：進入分支判斷 1-2

*
  *
    *
      *
        * **分支判斷 1-2：** 該用戶是否擁有可用的 LINE 渠道？

是 (LINE 用戶路徑)：發送 LINE「優惠卷使用提醒」 訊息

否：進入分支判斷 1-3

*
  *
    *
      *
        * **分支判斷 1-3：** 該用戶是否擁有 Phone number？

是 (SMS 用戶路徑)：\*\*\*\*發送 SMS「優惠卷使用提醒」 訊息

否：結束旅程

*
  *
    *
      *
        * \*\*延遲 (各別分支）：\*\*等待 4 天 (優惠券到期前 1 天)
        * \*\*分支判斷 2：\*\*用戶是否已被貼上 \[已領取] 標籤？

是：結束旅程

否：LINE / WA / SMS 發送 \[優惠卷最終提醒] 訊息/訊息模板 → 結束旅程

*
  *
    * 情境 2 網站行為觸發旅程 (購物車未結、售後關懷、回購提醒）
      * 示範：售後關懷與回購提醒
        * **觸發：**\[完成購買] 事件觸發 (GA / SDK)
        * **分支判斷 1-1**： 該用戶是否擁有可用的 LINE (可置換 WA) 渠道？

是 (LINE 用戶路徑)：發送 LINE 「感謝購買」訊息

否：進入分支判斷 1-2

*
  *
    *
      *
        * **分支判斷 1-2**：該用戶是否擁有 Phone number？

是 (SMS 用戶路徑)：發送 SMS 「感謝購買」訊息

否：結束旅程

*
  *
    *
      *
        * **延遲：** 等待 30 天
        * **動作 (各別分支)**：LINE (WA) / SMS 發送「關懷訊息＋滿意度調查」訊息
        * \*\*延遲：\*\*等待 60 天
        * **動作 (各別分支)**：LINE (WA) / SMS 發送「回購提醒」訊息 → 結束旅程
    * 情境 3 渠道行為觸發旅程 (流失客喚回、新好友綁定)
      * 示範：流失客喚回
        * **觸發：**\[LINE OA 封鎖] 渠道事件觸發 (可置換為 \[WA 封鎖] )
        * \*\*動作：\*\*貼 \[已封鎖顧客] 標籤 (後續應用：匯出至廣告平台再觸及)
        * \*\*延遲：\*\*等待 24 小時
        * **分支判斷 1-1**： 該用戶是否擁有 email (subscribed)？

是：發送 EDM「專屬折扣碼」email

否：進入下一步

*
  *
    *
      *
        * \*\*延遲：\*\*等待 3 天
        * **分支判斷 1-2：** 該用戶是否擁有 Phone number？

\*\*條件篩選：\*\*排除 \[已領取] 標籤

是：發送 SMS 「專屬折扣碼」訊息

否：結束旅程

**User Flow 與 UIUX 操作設計**

*
  * M1 核心架構原則
    * 模擬 Omnichannel: 聯絡人資料仍為 Multichannel。但在旅程的執行當下，系統可透過共享 ID (手機號碼, email) 即時查詢用戶在不同渠道的狀態做分支判斷。
    * 設計彈性: 系統需具備足夠的彈性，讓使用者可以自由搭建「渠道互斥 (避免干擾)」和「渠道排序 (最佳成本)」情境
  * Overall user flow
    1. 瀏覽旅程列表： 列表頁呈現旅程觸發類型、渠道、旅程狀態
    2. 建立旅程：
    * Step 1. 基本設定： 設定旅程名稱、排程、勿擾模式，以及符合 Omnichannel 需求的發訊限制（上限＆訊息發送量）
    * Step 2. 設定旅程觸發： 選擇旅程進入點 (觸發)。若選擇渠道行為，則必須指定對應的渠道帳號
    * Step 3. 編輯旅程節點：
      * 新增「渠道屬性」於分支判斷節點中，設計分流邏輯
      * 添加獨立的 LINE/ WA /EDM/SMS 訊息節點至旅程畫布
      * 「發訊息」節點中，選擇 (預設帶入) 發訊息的帳號並編輯內容/拉取訊息模板
    3. 發布與啟用
    4. 查看成效報表： 進入報表頁，查看總覽與各渠道成效，並可查看節點成效。
  * UIUX 操作設計 (As-is & To-be)

| Section     | As-is                                                                                  | To-be                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| ----------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 基本設定        | 1. 訊息發送限制：單一數值輸入框![](<../../../.gitbook/assets/Unknown image (49)>) 1. 觸發限制：單一渠道聯絡人的上限 | 1. 訊息發送限制： 可以「總計上限」或「渠道上限」 1. 總計上限**訊息發送限制** \[ ] 無限制 \[V] 達訊息發送上限後強制結束 設定方式: (◎) 總計上限 ( ) 分渠道上限 \* 總計上限: \[ 7,500,000 ]  - 1. 渠道上限**訊息發送限制** \[ ] 無限制 \[V] 達訊息發送上限後強制結束 設定方式: ( ) 總計上限 (◎) 分渠道上限\*\*\*\*\* LINE 上限: \[ 5,000,000 ] \* WhatsApp 上限: \[ 2,000,000 ] \* SMS 上限: \[ 500,000 ]****1. 觸發限制：增加 tooptip 說明「_針對單一「渠道身份」計算_」                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| 旅程設定 – 觸發條件 | 1. 觸發條件是扁平化列表 2. 渠道事件僅支援 LINE ![](<../../../.gitbook/assets/Unknown image (50)>)       | 1. 將觸發條件依調整為階層式分類： 1. 用戶標籤 2. 網站行為 (GA) 3. 渠道行為 (e.g LINE 開封、follow/block、opt-in) 2. 新增 WhatsApp 觸發選項 (例如：訂閱） 第一層： ┌────────────────────┐ \| 👤 用戶標籤 (Contact Tag) \| └────────────────────┘ ┌────────────────────┐ \| 🌐 網站行為 (Website Behavior) \| └────────────────────┘ ┌────────────────────┐ \| 📱 渠道行為 (Channel Behavior) \| └────────────────────┘  第二層 – 渠道行為： 渠道行為 > 觸發條件 ┌──────────────────────────┐ \| 當用戶於 \[渠道選擇 ▼] \[選擇事件 ▼] 時進入旅程 \| └──────────────────────────┘  - 渠道：LINE OA {bot} / WA {account} / SMS - 事件：開封訊息 (LINE) / 首次對話 (LINE\&WA) / 加入好友 (LINE) /訂閱帳號 (WA) / 封鎖帳號 (LINE\&WA)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| 旅程節點 – 分支判斷 | 判斷條件僅支援「標籤」與「GA 行為」![](<../../../.gitbook/assets/Unknown image (51)>)                  | 新增「**渠道屬性**」判斷類型： User 選擇 特定渠道帳號 進行檢查 條件：渠道屬性如果聯絡人在 \[渠道選擇 ▼] 的狀態是 \[條件選擇 ▼]  - 渠道：LINE OA {bot} / WA {account} / SMS - 事件：可觸及 / 封鎖帳號 (LINE\&WA) / 訂閱帳號 (WA) / 24小時內互動 (WA)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| 旅程節點 – 訊息發送 | 僅支援 LINE 訊息發送![](<../../../.gitbook/assets/Unknown image (52)>)                        | 1. 提供三個獨立的訊息節點：\[發送 LINE]、\[發送 WhatsApp]、\[發送 SMS] - 訊息節點需要選擇 \[發送的渠道] - 預設引導 (防呆)： 若旅程由 {LINE OA 1} 觸發，則「發送 LINE 訊息」節點的帳號下拉選單會預設選中 {LINE OA 1} 並提示為觸發來源 1. \[M1] WA 不支援訊息編輯器 1. 拉取 WABA 的訊息範本名稱＆審核狀態 → user 選擇範本 2. (TBC) 後端抓取範本變數 → user 填入變數內容 ┌────────────────────────┐ \| 設定 WhatsApp 訊息 \| \|──────────────────────────────\| \| \| \| 選擇發送帳號\* \| \| \[ WA Account 1 (觸發來源) ▼] \| \| \| \| 訊息類型 \| \| \[●] 範本訊息 (Template) \[○] 自由回覆訊息 (註1) \| \| (註1) 僅限用戶 24 小時內曾互動時使用。 \| \| \| \| 選擇訊息範本\* \| \| \[ Coupon\_Expire\_Reminder\_V2 (Approved) ▼] \| \| \| \| 範本變數設定 \| \| (系統已自動根據您選擇的範本生成對應欄位) \| \| \| \| **Body 變數** \| \| +-------------------------------------------+ \| \| \| 變數 1 \[ 顧客姓名 ▼ ] \| \| \| +-------------------------------------------+ \| \| +-------------------------------------------+ \| \| \| 變數 2 \[ 100元折扣券 ] \| \| \| +-------------------------------------------+ \| \| \| \| **Button 變數** \| \| +-------------------------------------------+ \| \| \| 變數 1 (URL) \[ https://... ] \| \| \| +-------------------------------------------+ \| \| \| \| \[ 取消 ] \[ 儲存 ] \| └─────────────────────────────┘  |
| 成效總覽        | 單渠道旅程成效數據                                                                              | 1. Omnichannel 儀表版：Overall & by channel (可參考 auto-reply) 2. 節點成效：需要包含 WA & SMS                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| 聯絡人頁面       | 包含 LINE, FB, IG, Others (SMS) 聯絡人                                                      | 加入 WA 聯絡人 - 支援 WA 渠道篩選、WA ID 搜尋 - Chat icon redirect to CAAC WA contact inbox - 匯出 WA 聯絡人 - (TBC) 支援 WA 聯絡人匯入                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

#### Milestone timeline

Week 1 (8/19 - 8/25)

* 8/19 (Tue) TF Sprint kick-off
* Milestone breakdown – set weekly demo goals [Gideon Pan](mailto:gideon.pan@cresclab.com)
* PD design hand-off (part 1: Omnichannel journey) [Patty Hsu](mailto:patty.hsu@cresclab.com)
* EDM solution confirm [Jean Liu](mailto:jean.liu@cresclab.com)

Week 2 (8/26 - 9/1)

* PRD Prat 1+2 ready (Omnichannel + SMS) [Jean Liu](mailto:jean.liu@cresclab.com)
* Part 1+2 User stories & Test cases alignment [Jean Liu](mailto:jean.liu@cresclab.com)
* Milestone Check #1 demo (scope TBC)

Week 3 (9/2 - 9/9)

* PD design hand-off (part 1: addional + part 2: SMS node) [Patty Hsu](mailto:patty.hsu@cresclab.com)
* PRD Prat 3 ready ( WA EDM in journey) [Jean Liu](mailto:jean.liu@cresclab.com)
* Part 3 User storues & Test cases alignment [Jean Liu](mailto:jean.liu@cresclab.com)
* Milestone Check #2 demo (scope TBC)

Week 4 (9/9 - 9/15)

* PD design hand-off (part 3: WA EDM node + contacts) [Patty Hsu](mailto:patty.hsu@cresclab.com)
* Milestone Check #3 demo (scope TBC)

Week 5 (9/16 - 9/18)

* Milestone Check #4 demo (scope TBC)
* ENG release

Target release (note: 9/22-9/25員旅)

* Testing: 9/26-10/1
* Tier 1 release: 10/2

#### TF Cadence

* Weekly Sprint：**每週二 3:00-4:00** milestone demo
* Daily Standup：**每日 2:15-2:30** 快速同步進度與風險
* PRD review & Test cases alignment 會另約會議討論

####

#### Risk

1. [Gideon Pan](mailto:gideon.pan@cresclab.com) profile unification non-funtional requirement (RPS 600) 是否可以滿足、event trigger 後，鎖定是哪些 entity 可執行 journey action
2. [Jhenyi Jhan](mailto:jhenyi.jhan@cresclab.com) EDM 未知性比較高
3. [Joseph Chang](mailto:joseph.chang@cresclab.com) 不同渠道的事件統一（eg. open) 可能會影響到其他模組/report 的計算
4. [Noel Lo](mailto:noel.lo@cresclab.com) EDM +1
5. [Tracy Weng](mailto:tracy.weng@cresclab.com) SMS/EDM 算不算一個 contact entity? 只是發送 channel？
6. [David Chou](mailto:david.chou@cresclab.com) EDM pricing 也要思考 (設計 SOP)、跨渠道 data report 整理/呈現（migration plan)
7. [Jalex Chang](mailto:jalex.chang@cresclab.com) EDM 現階段會不會是 long-term solution、多渠道下 contact 的轉換辨識＆判斷流程（排錯流程）
8. [Patty Hsu](mailto:patty.hsu@cresclab.com) 員旅後 OOO 之後的支援需要討論
9. [Peter Su](mailto:peter.su@cresclab.com) 報表呈現設計 / 新舊報表切換

####

#### 待釐清問題

From ENG (ticket comment)

**Q1: 跨渠道條件篩選的需求**

Journey 觸發條件 (filter) 是否支援跨渠道條件判斷，還是個別渠道內判斷？

舉例： Line Jalex 有 broadcast open 條件 A, FB Jalex 有 GA 條件 B，如果 filter 設定為 broadcast open 條件 A + GA 條件 B，算觸發還是不算？

**→ M1 的觸發節點條件篩選可為 單一渠道聯絡人；跨渠道的條件判斷，可以透過分支判斷節點來實現**

**Q2: Profile Unification API 容量與一致性**

Journey 會透過 CDH API 做 profile unification 確認，找到符合條件的其他渠道的人對他執行 node action。

→ 若發送對象有不確定性，是否能被接受？會不會讓客戶覺得混亂？

舉例：在一個渠道內找到 unified 的 N 個人，是否都要對特定每一位執行？還是隨機一位即可？

**→ 兩種做法討論：(1) 選擇「選擇最近更新」的渠道資料作為發送渠道 (2) 當結果不是「唯一且確定」時，終止旅程並加入錯誤日誌**

**Q3: Trigger 與效能策略**

Journey Trigger 從 Channel 改為 Org Level 後，會多一層檢查邏輯與 Cache。

→ 請提供對「觸發延遲」的容忍度（毫秒/秒級）目前標準是 end-to-end latency 10s in p99，是否維持？

**→ 目標維持，不同旅程設計可以有不同目標：**

* **若 Action 節點前 有 \[延遲]、\[排程] 節點 → 1 分鐘內的延遲**
* **若 Action 節點前 無 \[延遲]、\[排程] 節點 → 10 秒內的延遲**

**Q5: 多次發送與訊息限制**

多個 Sending Node 的情境下：

發送限制是依據 渠道 還是 member？

若同一個 member 在不同渠道同時符合條件，是否允許多次發送？

→ 需要產品提供使用者體驗上的期待與限制規則。

**→ M1 觸發限制（聯絡人進入旅程上限）是以 單一渠道聯絡人 計算，同一 member 在不同渠道都會觸發**

From PM

1. GA 事件是否可作為全渠道旅程的觸發事件/分支條件
2. 是需要透過 [maac.io](http://maac.io/) 進入網站才會追蹤到嗎？ 是（目前只有支援 LINE，SMS 沒有）
3. 以下情境是否可做到？ 1. 情境 1：直接從網站進入觸發 GA 事件，進入旅程 發送 LINE / WA / SMS → 透過 SRT 則可以（SDK only) 只支援 LINE 2. 情境 2：從 LINE 點擊 [maac.io](http://maac.io/) 進入網站觸發 GA 事件，進入旅程 發送 SMS → 可 3. 情境 3：從 SMS 點擊 [maac.io](http://maac.io/) 進入網站觸發 GA 事件，進入旅程 發送 LINE / WA → 不可 4. 情境 4：從 WA/EDM 點擊 [maac.io](http://maac.io/) 進入網站觸發 GA 事件，進入旅程 發送 SMS → 不可
4. Scope 要包含 SMS, EDM 短網址追蹤 GA 事件 1. Actoin: [Jean Liu](mailto:jean.liu@cresclab.com) 確認要支援哪一個方式 (ETA: 下週二前) → [Gideon Pan](mailto:gideon.pan@cresclab.com) [Jhenyi Jhan](mailto:jhenyi.jhan@cresclab.com) 估一下 effort (ETA: 下週四前）
   1. SDK scope: SRT + SDK event
   2. GA scope: (1) 可以組出 UTM 短網址 (2) 收回來 GA 事件可識別 (need infrom DAAC)
   3. Priority: EDM > SMS
5. SMS 互動事件可以作為「觸發」嗎？例如：送達、點擊 [maac.io](http://maac.io/) → 可！
6. SMS 聯絡人可貼標嗎？ 可
7. 另外問：SMS 聯絡人是否要進入 Contacts
8. WA & SMS & EDM 聯絡人如何綁定會員？綁定機制需要多做什麼？
9. 目前支援 LINE 綁定電話號碼、Cutomer ID
10. Out-of-scope: 需要做 Omnichannel Bindlink
11. Migration Plan 為何？ A: 理想上是上下相容，無痛轉換 (舊的 journey 繼續用，擴充新的節點）--> 先看UIUX設計再決定
12. 是否採用「舊的旅裎」不作變更的方式（若舊旅程有 omnichannel 需求，則以「複製」的方式建立新版旅程）
13. 舊旅程報表：仍以新版報表呈現，無數據欄位則顯示 -
14. 錯誤處理機制如何設計？
15. 可 retry 的錯誤 （例如：API 暫時無回應、流量塞車、Timeout) → Retry 幾次 / 間隔多久？最終仍失敗如何處理？
16. 不可 retry 的錯誤（例如：無效手機號碼、用戶封鎖、範本被拒絕、帳戶餘額不足）→ 如何通知 User？
17. 失敗處理：是否在成效報表中加入錯誤日誌（類似 SMS+) ？
18. 系統架構需考量未來擴充性：
19. 渠道擴張：EDM、Web channel
20. AI 功能：智慧渠道、智慧發送、DPM
21. 節點條件篩選是否可以調高至 10? (渠道變多、用戶輪廓變複雜，應要支援更細緻的分眾，為 AI journey 打底)
22. Non-functional requirement
23. 目前的 throughput 1. 流量定義：同時在旅程內的人數？同時觸發量？
24. 目標提高 throughput 1. **目標 throughput = 過去一年峰值 x 1.5 (客戶量成長) x 1.2 (新功能流量成長) x 1.5 (Buffer)**
25. 延遲容忍度目標，是否合理？ 1. 若 Action 節點前 有 \[延遲]、\[排程] 節點 → 1 分鐘內的延遲 2. 若 Action 節點前 無 \[延遲]、\[排程] 節點 → 5 秒內的延遲
26. 在「模擬 Omnichannel」架構下，聯絡人各渠道資料同步頻率為何？是否也會影響旅程延遲？
27. ESP adepter 可行性
28. adapter 架構設計是否可在 TF 時程內完成？反正會用好擴充的方式來設計（？）依照 [Joseph Chang](mailto:joseph.chang@cresclab.com) POC 結果來設計
29. 未來要擴充需要的工是多少？
30. (0820) 跨渠道 GA 成效追蹤
31. EDM 點擊 連結 追蹤點擊＆進站成效
32. SMS 點擊 連結 追蹤點擊＆進站成效
33. (0820) EDM 觸發情境
34. 加入購物車 → 觸發 EDM (在哪裡取得 email) 1. EC 平台回傳事件 2. Pixels / SDK?
35. 完成網站註冊後 → 發送 EDM (邀請加入好友) → 從 EDM deeplink/bindlink 綁定 LINE <> Email
36. (0820) contact profile unification
37. 目前看起來只能從 LINE 出發添加其他 channel info 來綁定 email, phone
38. phone, email contact 如何綁定 LINE?

產品問題（現行機制）

1. 旅程若暫停，在旅程中的聯絡人會繼續走完嗎？
2. 若 LINE 訊息發送失敗，如何處理？
3. SMS 可以選 vendor 嗎？客戶如何串接？可否 Self-serve (Admin > Channel integration)？

####

#### Appendix: Customer Journey - 現行規格

* 僅支援 LINE 單一渠道（bot)
* 每個 Org 可同時運行 350 組旅程
* 每個旅程最多設定 30 個節點（包含出口）
* 觸發限制
  * 標籤觸發：每位聯絡人 1 小時內僅能觸發一次
  * GA 行為觸發：每位聯絡人 24 小時內僅能觸發一次
* 自動旅程設定

| 區塊                       | 設定                                                                                                                                       | 選項                                     | 備註/限制                 |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------- | --------------------- |
| 自動旅程 - 基本設定              | 自動旅程名稱                                                                                                                                   | -                                      |                       |
| 運行排程                     | - 無期限 - 指定期間 (YYYY-MM-DD, mm:ss)                                                                                                         | 旅程發布後排程結束時間只能延長                        |                       |
| 觸發限制                     | - 無期限 - 每位聯絡人進入旅程的次數上限 (max 999)                                                                                                         | 旅程發布後數量將只能增加                           |                       |
| 訊息發送限制                   | - 無期限 - 達訊息發送上限後強制結束 (max 10,000,000)                                                                                                    | 旅程發布後數量將只能增加                           |                       |
| 勿擾模式                     | - 無限制時段 - 指定期間不發送訊息 (mm:ss)                                                                                                              |                                        |                       |
| 旅程設定 - Trigger(只能設定一個觸發) | 標籤觸發                                                                                                                                     | 選擇 MAAC & CAAC 標籤                      |                       |
| LINE 事件                  | - 開封訊息 - 指定訊息 → 選擇分眾廣播 - 任何訊息 - 加入好友 - 封鎖 OA                                                                                             |                                        |                       |
| 網站行為事件                   | - GA 瀏覽網頁 {X} 次 {Y} 秒 (max 999) - 指定網頁 - 任何網頁 - GA 加入購物車 - 指定商品 - 名稱包含 {product name} - 任何商品 - GA 購買 - 指定商品 - 名稱包含 {product name} - 任何商品 |                                        |                       |
| (以上觸發事件)+ 聯絡人條件篩選        | - 標籤 (有/沒有；指定/任何) - GA 行為 (有/沒有；指定/任何)                                                                                                   | 最多加入五個條件 (符合所有 or 任一）                  |                       |
| 旅程設定 - Rule              | 分支判斷 (Yes / No)                                                                                                                          | - 標籤 (有/沒有；指定/任何) - GA 行為 (有/沒有；指定/任何) | 最多加入五個條件 (符合所有 or 任一） |
| 延遲時間                     | 等待 {X} 分鐘 / 小時 / 天 / 週 (max 999)                                                                                                         |                                        |                       |
| 排程時間                     | 等待直到 每天 mm:ss / 每週 星期 {N} mm:ss (max 7) / 每月 {N} 號 mm:ss (max 30)                                                                        |                                        |                       |
| 旅程設定 - Action            | 發送 LINE 訊息                                                                                                                               | -                                      |                       |
| 貼標籤 / 移除標籤               | -                                                                                                                                        |                                        |                       |

* Reporting

| 區塊   | 類型                                                              | 數據                                                                      |
| ---- | --------------------------------------------------------------- | ----------------------------------------------------------------------- |
| 成效總覽 | -                                                               | - 推播訊息數 / 開封率 (開封數) - 點擊率 (點擊數) / 不重複點擊率 (不重複點擊數) - 加入購物車商品數 / 訂單數 / 營收 |
| 節點成效 | 非訊息節點                                                           | - 流量 (進入節點次數) - 不重複人數                                                   |
| 訊息節點 | - 流量 (進入節點次數) - 不重複人數 - 開封數 - 點擊數 - 不重複點擊數 - 加入購物車次數 - 訂單數 - 營收 |                                                                         |

UI reference

![](<../../../.gitbook/assets/Unknown image (53)>)

![](<../../../.gitbook/assets/Unknown image (54)>) ![](<../../../.gitbook/assets/Unknown image (55)>)

![](<../../../.gitbook/assets/Unknown image (56)>)

![](<../../../.gitbook/assets/Unknown image (57)>)

To-study

1. Current structure
2. Requirement backlog
3. Competitors
4. Must-have use cases
