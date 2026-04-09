# XtraType Expanded Frontend Specification Pack Overview

> The authoritative document set for the ultra-realized, fully expanded XtraType frontend.

| Document status | Finalized and authoritative frontend specification |
| --- | --- |
| System | XtraType |
| Scope | Frontend product architecture, interface behavior, interaction rules, view systems, templates, and governance UX |
| Backend boundary | All authorization, persistence, and server-side operations are assumed to be handled behind a single API-key-backed service boundary; this document set does not define backend architecture |
| Canonical stance | Capture-first entry points + adaptive composer shell + progressive disclosure + target-centric workbench + domain-pack extensibility |


# XtraType Description

> Finalized and authoritative description of the expanded XtraType frontend system.

| System | XtraType |
| --- | --- |
| Document kind | description |
| Scope | Frontend product architecture, interface behavior, view systems, capture systems, templates, domain packs, trust presentation, and public-facing contextual surfaces |
| Backend boundary | All authorization, persistence, and server-side operations are assumed to be handled behind a single API-key-backed service boundary |
| Status | Finalized and authoritative frontend system description |

## What XtraType is

XtraType is a contextual record system. It lets people attach durable, interpretable, linkable records to anything that can be identified, named, located, selected, observed, scanned, derived, or argued about. It is not merely an annotation tool, not merely a note-taking tool, and not merely a publishing layer. It is a broad frontend system for creating, reading, organizing, reviewing, and publishing contextual records across the web, the physical world, collaborative workspaces, and public knowledge layers.

At the core of XtraType is a stable grammar built from five distinct layers: **target**, **entry**, **intent**, **context**, and **governance**. The target is what the record is about. The entry is what is being authored. Intent explains why the record exists. Context explains where and how the record was created and how it should behave. Governance covers workflow, trust, privacy, moderation, publication, and auditability. The frontend preserves those distinctions everywhere so that the system can remain extremely expressive without feeling semantically vague.

XtraType treats all of the following as valid first-class targets: digital resources, spatial/geographic places, temporal spans, named entities, abstract and logical subjects such as claims or issues, physical objects revisited through scan anchors, and composite targets that combine several address types at once. A record may therefore be about a URL, a quoted sentence inside a page, a person, a place and its time window, a claim, a route, a scanned object, or a layered combination of those things. That breadth is fundamental to the product, not an edge case.

## What the frontend must do

The XtraType frontend exists to translate a rich meaning system into humane interfaces. It must make capture immediate, editing legible, organization flexible, review explicit, and publication trustworthy. It does this through a combined operating stance:

**capture-first entry points**  
+ **adaptive composer shell**  
+ **progressive disclosure**  
+ **target-centric and collection-centric workbenches**  
+ **collections and lenses as first-class navigation**  
+ **domain-pack specialization**  
+ **transparent suggestion and automation behavior**  
+ **visible provenance, trust, workflow, and privacy**  
= **a coherent contextual record interface**

The frontend is therefore allowed to be broad. It includes browser capture and overlay tooling, mobile field capture, deliberate manual drafting, import and share flows, target workbenches, collection workbenches, reviewer and moderation surfaces, public read surfaces, object-memory scan flows, voice-first roaming capture, AR spatial surfaces, ghost-layer overlays, live evidence rooms, and schema-commons management surfaces. Each of these surfaces feels different at the point of use, but each still produces and displays the same underlying grammar.

## What users create in XtraType

The primary authored unit in XtraType is the **entry**, but entries come in several genuinely distinct classes. XtraType supports annotation entries, citation entries, evidence entries, classification entries, social and conversational entries, workflow entries, collection and curation entries, media entries, and assertion entries. These are not arbitrary labels: each entry class changes what blocks matter, which relations should be foregrounded, what trust cues should appear, and how the record should be read later.

Intent is equally important. A record may be informational, evaluative, evidentiary, conversational, organizational, operational, observational, referential, corrective, or personal and mnemonic. Intent may be user-selected, suggested by the system, or inferred from context, but it is always visible and always adjustable. The frontend uses intent as its main switchboard to decide which fields are prominent, which drawers are open, which templates are suggested, and what kind of support or governance state should be emphasized.

Entries may be textual, media-based, structured, externally referential, generated or computed, or spatiotemporal in trace-like form. Mixed-modality entries are normal. A user may capture a quote, add commentary, attach a photo, preserve a transcript, include structured tags, and link external sources in the same record. The frontend never lets generated or computed material masquerade as raw authored content: captured, inferred, asserted, imported, and reviewed material remain visibly distinct.

## How the frontend is organized

XtraType has three main experience layers.

The first layer is the **capture-first layer**, where a user does something quickly in context: highlight text in a page, save a URL with a purpose, record a field observation, snap evidence in a place, scan an object, speak while moving, import a file, or place a contextual marker in an AR or overlay mode. These surfaces are deliberately lightweight and interruption-tolerant.

The second layer is the **adaptive composer**, a universal authoring shell that changes its feel based on target, intent, support requirements, workflow/privacy posture, capture surface, and domain pack. Its always-visible regions are the target bar, intent rail, main authoring pane, and save/status rail. Its expandable regions include the support drawer, workflow/privacy drawer, metadata/provenance drawer, and relationship tray. The composer supports progressive disclosure so that users can start with a quick capture, deepen into structured support, move into governance and trust, and then, when needed, promote patterns into reusable taxonomy or template structures.

The third layer is the **workbench and presentation layer**, where users browse, curate, compare, review, and publish. Workbench views may center on a target or on a collection. Collections are not just folders; they are working surfaces such as notebooks, boards, queues, dossiers, packets, and map or overlay layers. The frontend supports list, card/detail, board, timeline, map, graph, queue, compare, gallery, and dossier-style views, plus public presentation views, embeddable cards, public map/timeline presentations, and visible revision-history presentations.

## Domain packs and the sanctioned expansion universe

XtraType is designed to feel specialized without fragmenting into separate products. It does this through **domain packs**, which bundle templates, vocabulary, defaults, view preferences, terminology, and surface behaviors around a shared core grammar. Sanctioned packs include Personal Memory, Research Notebook, Field Observation, Fact-Check and Claim Review, Public Annotation and Publishing, Team Review and Moderation, Civic Place Memory, Classroom and Seminar, Schema Commons, Real-Time Evidence Room, Object Memory, Ghost Layer, Voice-First, AR Spatial, Argument Operating System, and Reality Layer.

This means XtraType is already allowed to function as a personal memory system, source-aware research notebook, field and inspection tool, fact-checking environment, public annotation network, moderation workbench, civic memory layer, classroom evidence environment, schema and template commons, synchronous evidence room, object-memory system, contextual overlay over the web, voice-first roaming recorder, AR annotation layer, argument operating system, and broad contextual reality layer. These are all legitimate product territory inside the frontend system description.

## Trust, provenance, privacy, and governance

XtraType treats trust and provenance as first-class visible surfaces. The frontend can show creation provenance, technical capture metadata, integrity metadata, suggestion provenance, and transformation provenance. It can render confidence, verification, dispute, quality, and sensitivity states. It can also expose workflow, review, moderation, resolution, publication, visibility, audience, and action-gating states. All of this is frontend-visible even though authorization and persistence live behind the single API-key-backed service boundary.

The system’s stance on automation is explicit. Suggestions may help choose intent, resolve targets, attach support, recommend templates, propose taxonomy growth, suggest audience posture, or recommend workflow routing. However, automation must remain explainable, reversible, and never quietly state-changing in sensitive areas such as publish, verify, moderate, promote, or expose-to-public actions. Granular settings may exist at the user, capture-context, domain-pack, template, and automation levels.

## Controlled growth

XtraType is a growing system by design. Controlled growth is therefore part of the frontend, not an external administrative afterthought. Users may create local ad hoc shapes, save personal templates, propose workspace or pack-level structures, and participate in promotion flows for shared vocabularies, templates, and types. Visible stewardship roles — contributor, reviewer, moderator, publisher, workspace steward, domain curator, and system steward — help the frontend explain how expansion becomes shared structure without collapsing into chaos.

## Final definition

XtraType is best understood as an infrastructure for contextual records and contextual layers. It allows people to leave meaningful, durable, navigable, evidence-aware records on top of pages, documents, places, routes, events, objects, claims, issues, and public or private knowledge spaces. It is broad enough to overlay the web and the world, but disciplined enough to remain legible, explainable, and trustworthy at the point of capture, during deep work, and in public presentation.

The mature XtraType frontend is therefore not a single app screen or a single mode of use. It is a unified interface system that can behave like a memory tool, a research environment, a field recorder, a review workbench, a publishing layer, an object-memory layer, an overlay system, a live evidence room, a schema commons, or a spatial contextual layer — while still preserving one coherent product grammar underneath.




## Purpose of this pack

This pack defines XtraType as a mature frontend system rather than a preliminary concept. It assumes that every major expansion previously surfaced is legitimate product territory: personal memory, source-aware research, field observation, moderation and review, civic place memory, classroom evidence work, object memory, browser overlays, real-time evidence rooms, schema commons, voice-first capture, AR overlays, argument-centric workflows, and the broad “reality layer” interpretation of the platform.

This pack is intentionally written without release sequencing. It treats the entire design universe as sanctioned. Future planning can decide what belongs in which iteration, but these documents establish the whole design territory now.

## Product definition

XtraType is a contextual record system. It lets users attach durable, interpretable, linkable records to anything that can be identified, named, located, selected, observed, derived, or argued about. The frontend is responsible for making that power feel immediate at the moment of capture, legible during editing, navigable during exploration, and trustworthy during review.

The frontend must therefore support three simultaneous truths:

1. XtraType is broad enough to describe the web, the world, and abstract concepts.
2. XtraType must still feel lightweight at the point of capture.
3. XtraType must remain inspectable and explicit when trust, evidence, workflow, or public interpretation matter.

## Frontend operating assumptions

- The backend is out of scope for this pack except as a single API boundary.
- Authentication, authorization, persistence, and file handling are assumed to be resolved by that boundary.
- The frontend may render audience rules, verification states, moderation controls, provenance records, and role-aware affordances, but this pack does not define how those permissions are enforced server-side.
- The frontend is responsible for state clarity, view logic, interaction design, draft handling, suggestion disclosure, and user trust.

## Experience equation

XtraType is defined by the following combined experience equation:

**capture-first surfaces**  
+ **adaptive composer shell**  
+ **progressive disclosure**  
+ **target-centric workbench**  
+ **collections and lenses**  
+ **domain packs**  
+ **transparent automation**  
+ **trust and provenance visibility**  
= **a coherent contextual record interface**

## Reading order

| Document | Function |
| --- | --- |
| 01 — Frontend Foundation and Product Grammar | Defines the semantic and interaction grammar the frontend must honor. |
| 02 — Frontend Surface Architecture | Defines the major surfaces, navigation structures, and cross-surface behaviors. |
| 03 — Adaptive Composer, Capture, and Disclosure | Defines how authoring and capture work in every context. |
| 04 — Views, Collections, and Domain Modes | Defines the browsing universe, domain packs, and specialized operating modes. |
| 05 — Taxonomy, Automation, Trust, and Governance UX | Defines growth, suggestions, provenance, trust, workflow, privacy, and policy-facing UI. |
| 06 — Expansion Atlas | Defines the full sanctioned expansion universe, from practical extensions to ambitious frontier modes. |
| 07 — Frontend Implementation Readiness Index | Defines the screen inventory, component inventory, state boundaries, API assumptions, and readiness artifacts. |

## Authoritative design doctrine

- The target is always distinct from the entry.
- The entry is always distinct from intent, support, context, and governance.
- Every surface must be able to save a valid draft without requiring full completion.
- Captured, inferred, asserted, imported, and reviewed data must remain visually distinguishable.
- Evidence and sources are first-class surfaces, not hidden metadata.
- Relationships are first-class navigational and interpretive structures.
- Collections are working surfaces, not only folders.
- Templates and vocabularies are core product structures, not add-ons.
- Automation must be explainable, reversible, and never quietly state-changing.
- Trust, privacy, workflow, and publication must always be inspectable.
- The frontend should make advanced rigor available without making casual capture feel bureaucratic.

## Sanctioned frontend universe

The XtraType frontend is explicitly allowed to include all of the following:

- browser extension and inline overlay tools
- mobile field capture and route-aware observation tools
- manual drafting in a full workbench
- share/import flows
- public read and publishable record surfaces
- team review, moderation, and evidence queues
- personal knowledge and memory modes
- research and citation workspaces
- object memory through QR, barcode, NFC, or scan anchors
- real-time collaborative evidence rooms
- template and schema commons
- voice-first roaming capture
- AR spatial record layers
- argument-centric operating modes
- large-scale contextual layers over pages, places, claims, and events