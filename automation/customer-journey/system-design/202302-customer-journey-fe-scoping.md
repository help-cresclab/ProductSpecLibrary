---
description: >-
  Front-end scoping notes for Customer Journey V2 (canvas, editor, form, and
  report). Includes Phase 1-1 task breakdown, risks, and deferred work.
---

# 202302 Customer Journey FE Scoping

{% hint style="warning" %}
⚠️ Out of date (kept for historical context).

* Owner: @Xander
* Status: draft, not ready for review
* Main references:
  * [202302 Journey Architecture & Design](202302-journey-architecture-and-design.md)
  * [Customer Journey V2 overview (Asana)](https://app.asana.com/0/1203488823893405/overview)
{% endhint %}

## Purpose

Customer Journey is our workflow automation product for multi-step messaging. This doc scopes the **front-end work** for V2. It focuses on the **create/edit form**, **editor**, and **flow canvas**.

{% hint style="info" %}
**Keywords**: Customer Journey V2, frontend scoping, flow canvas, React Flow, node editor, trigger menu, conditions UI, journey report, performance
{% endhint %}

### Goals and approach

{% stepper %}
{% step %}
### Lay a solid foundation

Ship clean and maintainable foundations. Optimize for future iterations.
{% endstep %}

{% step %}
### Ensure flow canvas performance

Keep the flow canvas smooth. Avoid performance cliffs.
{% endstep %}

{% step %}
### UI standardization

Standardize shared components. Modernize UI patterns.
{% endstep %}

{% step %}
### Ship MVP quickly

Ship an MVP fast. Defer non-critical work post-launch.
{% endstep %}
{% endstepper %}

### Risks and unknowns

* Flow canvas scope is hard to estimate.
* State management is undecided (form + canvas).
* Some node settings and APIs are still not specified.
* End-to-end workflow mocking is expensive.
* Many small UI details require fast iteration.
* Design changes can invalidate estimates.
* QA process is new for this module.

***

## Phase 1-1 (V2.0) — task breakdown

This is the Phase 1-1 checklist. Items are grouped by area.

### List view

* [ ] List view needs tooltip text update
* [x] Need to review exactly when edit button is displayed

### Create/edit form

* [ ] **Zustand reset state function**. State is not cleared on navigation. Old data can leak into create/edit. \[[Asana](https://app.asana.com/0/1203488823893405/1204520373993727/f)]
* [x] Publish (Step 2). Convert form data into mutation payload.
* [x] Redirect when edit is disallowed.

### Node editor

* [ ] **Trigger menu / selection state**. Define how the menu opens. ⭐ \[[Asana](https://app.asana.com/0/1203488823893405/1204520376565844/f)]
* [ ] **Tag Added node fields** \[[Asana](https://app.asana.com/0/1203488823893405/1204520376565848/f)]
  * [ ] Fix Tag form item wiring (bug).
* [ ] **GA Page View node fields** \[[Asana](https://app.asana.com/0/1203488823893405/1204520376565852/f)]
* [ ] **GA Purchase node fields** \[[Asana](https://app.asana.com/0/1203488823893405/1204520376565854/f)]
* [ ] **Time delay node fields** \[[Asana](https://app.asana.com/0/1203488823893405/1204520376565868/f)]
* [ ] **Yes/No branch node fields**. Impacts canvas. Needs more scoping. ⭐
* [ ] **LINE Message node fields** \[[Asana](https://app.asana.com/0/1203488823893405/1204520376565875/f)]
* [ ] **LINE Message editor integration** \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888312/f)]
* [x] **Editor form validation handling**
* [ ] **Filters / conditions UI** \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888318/f)]
* [ ] Autosave UI. Needs icon + animation trigger. \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888267/f)]
* [x] Mock node mutation services (only if BE APIs are delayed).
* [x] Delete node confirmation modal (includes descendants). \[[Asana](https://app.asana.com/0/1203488823893405/1204520376565880/f)]
* [ ] Create/update node mutation. Transform flat form data to nested API shape. \[[Asana](https://app.asana.com/0/1203488823893405/1204520376565884/f)]
* [x] Sleep mode time validation (wontfix). UX edge cases exist.
* [ ] Source/target node arguments. Decide API shape. ⭐
* [ ] Editor ↔ canvas coordination (cancel, deselect, etc.). ⭐

### Flow canvas

* [x] **Layout algorithm lifecycle**
* [x] **Node context menu: all we have right now is a placeholder file**
* [ ] **Edge functionality: everything to do with this**
* [ ] **Yes/no branch implementation**
* [x] **Exit nodes: everything to do with this**
* [ ] **Freeze canvas while editing**. Disable non-active nodes. Limit interactions until delete/cancel/save. \[[Asana](https://app.asana.com/0/1203488823893405/1204520376565888/f)]
* [ ] Node info display per spec. Current is rough. \[[Asana](https://app.asana.com/0/1203488823893405/1204520376565892/f)]
  * [ ] Related bug: i18next::interpolator: missed to pass in variable time for interpolating Wait \{{time\}} minutes
* [ ] Currently users can select more than one node on the canvas but we might only want a single selection to be allowed

### Report view

* [ ] API implementation
* [ ] Data card layout
* [ ] Some additional work needs to be done to abstract some common components from the Dashboard project to lay out the report page in the same way
* [ ] Canvas integration
* [ ] Date range picker

### Templates

* [ ] Everything to do with templates; literally haven’t spared a moment to even look into these requirements, so we should probably officially defer this functionality \[defer to 1-2?]

### Welcome

* [ ] Everything to do with the welcome page \[defer to 1-2?]
* [ ] double check which

### General

* [ ] Query key invalidation will need to be examined at some point; since we are still building out APIs and relying on mock data this is currently being handled in an ad hoc fashion
* [ ] Confirm API data structure with BE for node settings, branch\_settings, and conditions; there are many details here that we have yet to fully spec out
* [x] Decision: do we need the get individual node and create individual node APIs anywhere?
* [ ] GA user event tracking; we already have a draft version of a hook for handling this, still need to integrate
* [ ] Translation keys are currently a huge mess because of reuse and disorganization; we need to clean this up a bit at some point, just for the dev experience to remain sane

***

## Future phases — deferred from Phase 1-1

These tasks were deferred from phase 1-1.

### General

* [ ] Additional UI enhancements; design team updated several of our common components while producing design mockups for this project but we deferred some of these due to time constraints. At some point it will be worth circling back to complete these enhancements:
  * [ ] List view: table enhancements
  * [ ] List view: filter tabs enhancements
  * [ ] List view: search bar enhancements
  * [ ] Form view: form steps enhancements
  * [ ] Form view: form fields enhancements
  * [ ] Form view: notice box enhancements

### Canvas

* [ ] Canvas: dynamic node sizing (related to the layout algorithm)
* [ ] Node toolbar delete button, showing a trash can icon; since this duplicates functionality already provided in the node editor we are pushing off to phase 1-2

### Editor

* [ ] Node editor menu and drag-and-drop functionality; since the context menu is sufficient for operating the module we deferred the implementation of drag-and-drop
  * [ ] Proximity sensor; we want to be able to show users where items can be dropped or interacted with, and luckily this seems to be built into Reactflow
  * [ ] Placeholder for nodes to be dropped into
* [ ] DPM message editor integration

### Types/Schemas

* [ ] Zodios integration; we’re currently using Zod schemas on this project, but not Zodios itself, as we’re short on time. It would be good to circle back to this in future phases after we hammer out some conventions for using Zodios in the Grazioso codebase.
* [ ] Improved Zod date parsing; currently we’re using coerced dates but the implementation feels a little tricky and prone to problems.
* [ ] Improved Zod schemas with discriminated unions; currently we’re held up by the Zod API being in flux, but it would be helpful to better organize schemas with better unions.

***

<details>

<summary><strong>Task Breakdown 1.0 (Obsolete) ☠️☠️☠️ — (click to expand)</strong></summary>

Everything below here is only for reference…

#### Fundamentals

These are the tasks that are easily surfaced from the PRD and design mockups in their present state. This work can proceed without much delay, but finalizing some aspects may have to wait on decisions made by stakeholders.

* [x] Scaffolding: folder structure, file naming conventions, boilerplate for types, services, queries, data-fetching hooks, pages, etc. ([Asana](https://app.asana.com/0/1203488823893405/1203975222068835/f))
* [x] Initial feature flag ([Asana](https://app.asana.com/0/1203488823893405/1203975222068835/f))
* [x] Integrate custom SVG icons \[in progress]
* [ ] Zod and Zodios integration for API specifications and services; currently we’re using an assortment of Zod schemas for type safety but we’ll want to make this more robust by adopting the Zodios solution ViPro implemented in Zeffiroso (or something like it anyway); luckily I think we can address this a little later on \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888273/f) / 3 d?]
  * [ ] Parse dates with Zod; currently we’re using coerced dates but the implementation feels a little tricky and prone to problems \[0.5 d]
  * [ ] New Switch API will be very helpful for node data; upgrade from Zod’s discriminated unions when this feature is released \[1 d]

#### List View \[7-10 days?]

* [ ] List page UI adjustments: we’re updating a bunch of shared components in this project according to specs prepared by PDs; these tasks are lower priority and can be put off to the end of Phase 1-1 \[[Asana](https://app.asana.com/0/1203488823893405/1203998432692644/f)]
  * [ ] Filter Tabs; design mockups show several visual changes \[[Asana](https://app.asana.com/0/0/1203998432692649/f) / 1 d]
  * [ ] Table; this one has more parts and requires more effort and coordination with PDs \[[Asana](https://app.asana.com/0/0/1203998432692651/f) / 2+ d]
  * [ ] Searchbar; minor visual changes, can put this off until later \[[Asana](https://app.asana.com/0/0/1203998432692647/f) / 0.5 d]
  * [x] Table cell toggle components; might not be too troublesome to implement \[1? d]
  * [x] Table cell pill components; these seem to be a minor adjustment of existing UI components \[0.5? d]
* [x] List page implementation: layout, business logic, services, hooks, mock data, types, etc., many of which are already scaffolded and require refinement \[[Asana](https://app.asana.com/0/1203488823893405/1203998432692671/f) / 3 d]
  * [x] Mock data / types
  * [x] Pagination; if I’m not mistaken we can launch with infinite scroll but should implement pagination at some point? Update: infinite scrolling was implemented

#### Create/Edit Form View

* [ ] Form page UI adjustments: some shared components here will also be updated in this project ([Asana](https://app.asana.com/0/1203488823893405/1203998432692660/f))
  * [ ] Form steps; design mockups have a number of visual changes to this component \[[Asana](https://app.asana.com/0/0/1203998432692664/f) / 1 d]
  * [x] Form field toggles \[in progress]
  * [ ] Form fields; only some minor adjustments needed here \[[Asana](https://app.asana.com/0/0/1203998432692667/f) / 0.5 d]
  * [ ] Notice box; another component qualifying for an upgrade to the shared path after minor cleanup \[[Asana](https://app.asana.com/0/1203488823893405/1204263652427870/f) / 0.5 d]
* [x] Form page implementation: this is best split into several parts, the easy steps and the flow canvas \[?]
  * [x] Basic settings scaffolding \[in progress]
  * [x] Message sending options, rough draft \[in progress]
* [ ] Form autosave functionality \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888267/f) / ? d]
* [ ] Form state management \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888270/f) / still to research]

#### Workflow Canvas

Note: workflow canvas is primarily a component of the create/edit form, but it will also be reused to display workflows in the report view, with some modifications.

* [x] Evaluate libraries ([Asana](https://app.asana.com/0/1203488823893405/1203998433260050/f))
* [x] Layout algorithm \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888276/f)]
  * [x] Evaluation of libraries (d3-hierarchy, d3-dag); the former seems to work, but I’m still curious about whether the latter produces better results; both are a bit awkward to work with and not entirely type-safe but there doesn’t seem to be anything better/more modern to work with \[2 d?]
  * [x] Implementation; initial evaluation suggests some technical challenges related to node placement, because our nodes will vary in size, and most algorithms assume a fixed size; most people seem to overcome this issue by handling layout in two passes, rendering once to obtain node size, and then rendering again after measurements have taken place \[3 d?]
* [ ] Drag and drop functionality; not an intrinsic feature of Reactflow, will require more investigation and experimentation \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888264/f) / 5? d]
  * [ ] Proximity sensor; we want to be able to show users where items can be dropped or interacted with, and luckily this seems to be built into Reactflow \[1? d]
  * [ ] Placeholder for nodes to be dropped into
* [ ] Workflow panel; already in progress
  * [ ] Scaffolding; put these components in place without completing all details \[[Asana](https://app.asana.com/0/1203488823893405/1204222675445043/f) / in progress]
  * [ ] Select Trigger
  * [ ] Edit Trigger
  * [ ] Add node
  * [ ] Filters/conditions
    * [ ] Basic scaffolding, just to get it working \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888300/f) / 2 d?]
    * [ ] Details, of which there are many \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888318/f) / 3 d?]
* [x] Scrolling/zooming functionality; this appears to be built-in to Reactflow but will need to study design mockups and evaluate whether everything is being met
  * [x] Basic implementation
  * [x] UI enhancements (zoom to center, zoom on update, etc.)
* [ ] Nodes \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888297/f) / 3 d?]
  * [ ] Triggers
  * [ ] Rules
    * [ ] Yes/no branch
  * [ ] Actions
    * [ ] LINE Message editor integration \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888312/f)]
    * [ ] DPM Message editor integration \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888314/f)]
  * [ ] Exit nodes; still need to evaluate how these should be implemented
* [ ] Edges \[some unknowns here]
  * [ ] Context menu; shouldn’t be too hard once everything else is in place, this is a simple/compact version of the Add Node menu on the Panel \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888308/f) / 2 d?]
* [ ] Unsaved changes handling \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888303/f)]

#### Report View

This also uses the flow canvas to display content, so it makes sense to design the canvas with this dual functionality in mind

* [ ] Report page implementation; hooks, services, types, etc. \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888284/f) / 2 d]
* [ ] Report page workflow canvas integration \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888286/f) / ? d]
* [ ] Date range picker integration
* [x] Shared DataCard component \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888279/f) / in progress]

#### Cleanup

Various tasks to keep in mind for later on.

* [ ] UI translation key cleanup \[[Asana](https://app.asana.com/0/1203488823893405/1204263652888290/f) / 2 d]
* [ ] GA user event tracking; we’re fortunate in that the existing Journey module has a wide assortment of tracking hooks, but some work needs to be done to see if we’re going to just copy these over 1:1, or if some require modification, and if we’d like to add any more ([Asana](https://app.asana.com/0/1203998432692652/f))

#### Speculative & Not Yet Scoped

Additional research and time estimates still required for these items

* [ ] List page announcement banner; this looks new, and we’ll have to discuss where the announcement data are coming from (built-in to the UI, pulled from the back-end, etc.) ([Asana](https://app.asana.com/0/1203998432692650/f))
* [ ] Template system; haven’t really looked into this too deeply yet; are templates supposed to be configurable? Or all predefined?
* [ ] Welcome page

#### Flow Canvas Library Review \[Outdated]

Currently Customer Journey uses a custom solution for drawing a canvas and placing nodes. This approach won’t scale as we invest more heavily in Journey functionality. For this reason, it makes sense to review available libraries ([Asana](https://app.asana.com/0/1203998433260050/f)).

* [React Flow](https://reactflow.dev/): this is the one to beat, by the looks of it. Modern, updated, customizable. The [showcase](https://reactflow.dev/showcase/) has some good examples. It is already being used for Customer Journey implementations. Chosen 🏆
* [GGEditor](https://github.com/alibaba/GGEditor): made by Alibaba; the implementation seems very basic and the aesthetic isn’t very good. Last updated 2020 🙅‍♂️
* [React Diagrams](https://github.com/projectstorm/react-diagrams): ugly aesthetic
* [React Flow Diagram](https://github.com/DrummerHead/react-flow-diagram): ugly, old, outdated 🙅‍♂️

#### Layout Algorithm Library Review \[Outdated]

* d3-hierarchy is standard but only works on tree data
* d3-dag has potential but is complicated to use, still investigating this one
* d3-force seems like overkill but is sometimes used for network graphs
* Ant Design has a graphing library that is really outdated
* Cytoscape has some useful utilities but it seems hard to extract the relevant algorithm
* Dagre is a popular library (and used in reactflow examples) but it is long deprecated
* I suspect many companies developing workflows with controlled layouts rip code out of an old library and update it for their needs, but this will be a significant chunk of work

</details>

***

## Future Phases \[Notes]

* Flow canvas: do we need the ability to create/edit segments within this view? (Tags will not be too difficult) \[not in this phase]
* Flow canvas: is there any limit to the number of (horizontal) branches we need to support? \[5-10]

## Flow Canvas Design

Presently we roll a custom solution for the Customer Journey workflow canvas (flow canvas for short). For V2 we decided to use a library to handle the more complicated and customizable UI we plan to implement. This library, React Flow, provides many of the visual primitives necessary to build a flow canvas with a performant mix of SVG and regular HTML elements.

By default React Flow is configured to allow nodes and edges to be fully interactive; users can drag and drop nodes anywhere, connect nodes, etc. Customer Journey requires a more strictly regimented layout: nodes must appear at specific locations, and not every node can be connected to each other. Rather, our use of a node tree is mostly for visual layout purposes, and we don’t plan to use more powerful means of manipulating nodes and edges. For this we need a layout engine of some kind, of which d3-hierarchy emerged as the most suitable (as other candidates were either far too large, abandoned, or otherwise poorly supported).

### Still to do

* [ ] Center canvas after data fetching/rendering
* [ ] Center canvas on newly created node
* [ ] 2-step node layout: first we need to compute default arrangement, then re-compute based on rendered node sizes

***

## Maintenance notes

This page is long. If we keep using it, split it into:

* Scope and goals
* Phase 1-1 checklist
* Deferred work
* Obsolete reference
