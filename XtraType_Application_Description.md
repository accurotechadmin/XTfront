# XtraType Application Description

---

## Executive summary

XtraType is a **unified contextual record platform**.

Its purpose is to let people create durable, linkable, inspectable records about almost anything: a web page, a quoted passage, a place, a route, a person, a claim, an event, a physical object, or a composite target such as “this sentence on this page at this time” or “this object at this location in this condition.”

It is not just a notes app, browser annotator, field reporting tool, research notebook, moderation dashboard, or publishing layer. It is designed to unify all of those into one product grammar.

The core idea is that users should be able to capture context in the moment, deepen it into a richer record later, organize and review it in workbench-style interfaces, and optionally publish or share it with transparent trust, provenance, workflow, and privacy controls.

A concise way to describe XtraType is:

> **part annotation system + part knowledge-work platform + part research notebook + part field capture tool + part moderation/review workbench + part public context layer**

---

## The core conceptual model

The application is built around five distinct layers:

1. **Target** — what the record is about  
2. **Entry** — what kind of record the user is creating  
3. **Intent** — why the user is creating it  
4. **Context** — where/how it was captured and what situational metadata applies  
5. **Governance** — privacy, trust, provenance, workflow, review, and publication state  

This five-part structure is the defining architectural idea of the product. XtraType insists that:

- what the user is talking about
- what kind of record they are making
- why they are making it
- what capture context applies
- what governance and trust state it carries

must remain visibly distinct.

That separation is what differentiates XtraType from a generic notebook or feed-style application.

---

## What users create

The main authored object in the system is an **entry**, but entries are not treated as one generic note type. The specifications define multiple meaningful entry families, including:

- annotation
- citation
- evidence
- classification
- social/conversational
- workflow
- collection/curation
- media
- assertion

That means a record might represent:

- a note on a page
- a citation tied to a quote
- a photo used as evidence
- a label/classification judgment
- a threaded discussion reply
- a workflow action
- a packet or dossier item
- a standalone claim or assertion

XtraType also treats **intent** as first-class structure. A user may be creating an entry in order to:

- record something
- evaluate something
- provide evidence
- discuss
- organize
- operate a workflow
- report an observation
- link or anchor a record
- correct or dispute something
- save something for memory or later use

Intent is not merely decorative metadata. It is meant to influence what the UI prioritizes, which fields open first, which templates are suggested, and which governance/trust affordances appear.

---

## The overall product experience

The specification describes XtraType with a clear formula:

**capture-first surfaces**  
+ **adaptive composer**  
+ **progressive disclosure**  
+ **target-centric and collection-centric workbenches**  
+ **collections and lenses**  
+ **domain-pack specialization**  
+ **transparent automation**  
+ **visible provenance, trust, workflow, and privacy states**  
= **the XtraType experience**

In practice, that means the product tries to balance two goals:

- make capture fast and low-friction in the moment
- preserve rigor, inspectability, and governance when records become important

A user should be able to save something quickly without being forced into a giant structured form, then later open that draft into a much richer environment that supports evidence, relationships, workflow routing, privacy controls, and publication decisions.

---

## The three major product layers

### 1. Capture layer

This is the quick-entry side of the application. It includes:

- browser capture
- mobile field capture
- manual drafting
- import/share flows
- object scanning
- voice capture
- AR capture
- page overlay / ghost-layer capture

The emphasis here is speed, preservation of context, and minimal interruption.

### 2. Adaptive composer

This is the universal authoring shell. Regardless of where a record starts, it is supposed to converge into the same conceptual editor.

The composer includes:

- a **target bar**
- an **intent rail**
- a **main authoring pane**
- a **save/status strip**

It also includes expandable regions/drawers for:

- support and evidence
- relationships
- workflow and privacy
- metadata and provenance
- templates and taxonomy

The composer is based on **progressive disclosure**, meaning the interface reveals complexity in layers:

1. quick capture  
2. structured enrichment  
3. governance and trust  
4. reuse and system growth  
5. expert/steward tooling  

A user can stop at an early layer and still have a valid draft.

### 3. Workbench and presentation layer

This is where users browse, compare, organize, review, and publish. XtraType supports work centered around:

- a single target
- a collection
- a queue
- a review workflow
- a public presentation surface

This makes the app feel less like a flat note store and more like a multi-mode operating environment for records.

---

## Major frontend surfaces

The specifications describe a wide range of frontend surfaces. These include:

- **Browser extension surface** for page capture, selected text, screenshots, quick saves, and overlay notes
- **Mobile field capture surface** for place-aware and movement-aware capture, media capture, voice notes, scanning, and offline drafting
- **Manual drafting surface** for deliberate authoring in the main application
- **Import/share surface** for files, links, clipboard content, and staged imports
- **Target workbench** for exploring one target and all attached records
- **Collection workbench** for navigating notebooks, queues, packets, map layers, rooms, and boards
- **Reviewer/moderation surfaces** for verification, disputes, corrections, and publication
- **Public read surfaces** for published records and collections
- **Object memory scan surface** for real-world objects resolved via scans or proximity methods
- **Voice-first roaming surface** for hands-busy capture
- **AR spatial surface** for records anchored in physical space
- **Ghost layer / overlay surface** for contextual records shown on top of existing pages
- **Live evidence room** for synchronized collaborative review and analysis
- **Schema commons surface** for templates, vocabularies, and domain packs

This breadth makes XtraType feel more like a product platform than a narrow single-purpose application.

---

## How information is organized

XtraType is both **target-centric** and **collection-centric**.

### Targets

A target is the thing the record is about. It can be:

- a digital resource
- a place
- a time window
- a named entity
- an abstract claim, issue, or policy
- a real-world object
- a composite of multiple of the above

### Collections

Collections are treated as active working surfaces rather than passive folders. They may function as:

- notebooks
- case files
- queues
- dossiers
- evidence packets
- map layers
- route trails
- object fleets
- live rooms
- public layers

### Lenses

The app also supports **saved lenses**, which are reusable filtered views such as:

- my drafts
- needs support
- needs review
- disputed
- verified
- published
- spatial
- temporal
- media-heavy
- unresolved
- high-confidence only

These lenses allow the same underlying records to be seen through different operational perspectives.

---

## Supported views

The canonical view system described in the specifications includes:

- list
- detail/card
- board
- timeline
- map
- graph
- queue
- compare
- gallery
- transcript/thread
- dossier
- matrix

These are not separate apps. They are different ways of seeing the same record universe. For example, the same target or collection might be viewed as:

- a timeline to understand chronology
- a graph to inspect relationships
- a queue for review workflow
- a map for place-based work
- a compare desk for contradictions
- a dossier for compact case reading

---

## Domain packs and specialization

One of the most distinctive concepts in the XtraType specification is the **domain pack**.

A domain pack changes terminology, defaults, templates, preferred views, and affordances **without changing the underlying product grammar**.

The specification recognizes 16 official domain packs:

1. Personal Memory  
2. Research Notebook  
3. Field Observation  
4. Fact-Check and Claim Review  
5. Public Annotation and Publishing  
6. Team Review and Moderation  
7. Civic Place Memory  
8. Classroom and Seminar  
9. Schema Commons  
10. Real-Time Evidence Room  
11. Object Memory  
12. Ghost Layer  
13. Voice-First  
14. AR Spatial  
15. Argument Operating System  
16. Reality Layer  

This means XtraType can present itself differently depending on use case, behaving more like:

- a second-brain memory tool
- a research/evidence notebook
- a mobile field observation system
- a fact-checking and claim-review tool
- a public annotation network
- a moderation and operational review workbench
- a civic/place memory layer
- a classroom evidence app
- a schema/template commons
- a live collaborative evidence room
- an object-history tracker
- a browser overlay layer
- a voice-driven capture system
- an AR annotation tool
- an argument mapping system
- a broad public “reality layer”

This is intentional product scope, not an accidental accumulation of features.

---

## Trust, provenance, workflow, and privacy

One of the strongest themes in the documents is that XtraType treats trust and provenance as first-class UI, not buried metadata.

### Provenance/origin states

The application distinguishes among records that are:

- captured
- asserted
- imported
- inferred/computed
- reviewed/verified

### Trust dimensions

It also exposes trust-related dimensions such as:

- confidence
- verification
- dispute status
- quality
- sensitivity

### Workflow states

Records may move through explicit workflow states such as:

- draft
- review
- moderation
- resolution
- publication
- supersession
- archival

### Privacy and audience states

The system also models privacy and audience scope explicitly, with states like:

- private
- workspace
- restricted group
- review-only
- link-shared
- public
- layer-specific visibility

A major design principle is that these properties must remain conceptually separate. For example:

- confidence is not the same thing as verification
- polish is not the same thing as proof
- a public record may still be disputed
- a private record may still be high-confidence

This suggests the product is trying to be epistemically legible, not just visually polished.

---

## Automation philosophy

The application supports automation and suggestions, but with strict boundaries.

The system may suggest:

- likely target
- likely intent
- likely evidence or source relations
- likely workflow route
- likely privacy posture
- likely template
- likely vocabulary terms
- likely duplicates or related records

However, the specifications explicitly avoid silent system actions for important governance outcomes. The system must not silently:

- publish
- verify
- dispute
- resolve
- supersede
- escalate
- share publicly
- change audience scope
- install shared templates
- change trust state

Automation in XtraType is meant to be visible, explainable, and reversible.

---

## Controlled growth and schema evolution

Another unusual characteristic of XtraType is that it treats taxonomy and structure growth as part of the product itself.

Users can:

- create one-off local structures
- save personal templates
- propose shared workspace structures
- promote vocabularies or concepts into shared reusable assets

So XtraType is not only a record-making application. It is also a system in which users can evolve the structure of the system through templates, vocabularies, proposal queues, stewardship roles, and schema commons interfaces.

That makes it partly a knowledge-work environment and partly a governed schema platform.

---

## What the implementation-oriented materials indicate

The readiness/index materials describe the application as six coordinated zones:

- capture
- composer
- workbench
- public
- management
- frontier

They also enumerate expected screens such as:

- dashboard
- target page
- collection page
- entry detail
- source page
- full composer
- quick composer
- browser mini-capture
- mobile capture
- import staging
- review queue
- moderation board
- compare desk
- graph/map/timeline/gallery views
- live evidence room
- template catalog
- vocabulary management
- proposal queue
- settings
- public target/collection pages
- object scan sheet
- voice transcript cleanup
- AR overlay sheet
- ghost layer sidebar

This reinforces that the pack is a structured frontend design and navigation specification rather than loose prose.

---

## What the centralized inventory shows

The centralized inventory files make the system even more explicit. They normalize the overall concept into a large inventory of defined items. The inventory includes **192 items**, including:

- 16 domain pack classes
- 12 frontend surface classes
- 10 view/lens classes
- 10 intent categories
- 9 entry classes
- 8 composer regions
- 8 automation/suggestion classes

It also includes roles, settings, provenance states, trust states, collection classes, target classes, and workflow classes.

This confirms that XtraType is conceived as a serious platform architecture, not a lightweight feature list.

---

## What each file contributes

### 00 Overview
Defines the overall idea of XtraType and positions it as a unified contextual record platform.

### 01 Foundation and Product Grammar
Defines the semantic core of the system: target, entry, intent, context, and governance.

### 02 Surface Architecture
Describes app surfaces, navigation, layout rules, continuity between surfaces, and how users move across contexts.

### 03 Adaptive Composer
Explains how authoring works, including quick capture, progressive disclosure, suggestions, support panels, and save/status behavior.

### 04 Views, Collections, and Domain Modes
Defines collections, lenses, supported view types, and the domain pack system.

### 05 Taxonomy, Automation, Trust, and Governance UX
Explains schema growth, suggestions, provenance, trust, workflow, moderation, publication, and privacy logic.

### 06 Expansion Atlas
Describes sanctioned expansion directions and frontier surfaces that extend the same product grammar.

### 07 Readiness Index
Provides the most implementation-oriented structure: screens, components, state concepts, and application zones.

### Centralized inventory (`.md` and `.json`)
Provides the normalized inventory of the whole frontend concept and verifies the app’s object model.

---

## Overall product interpretation

The best overall interpretation is that XtraType is a **contextual record operating system**.

It is designed to let users:

- capture context anywhere
- attach it to almost any kind of target
- enrich it into structured records
- connect it through evidence and relationships
- organize it into collections and reusable lenses
- review and govern it with explicit trust, provenance, workflow, and privacy states
- publish or overlay it in public, private, or team contexts
- specialize it through domain packs without breaking the underlying grammar

Rather than being one narrow product, XtraType is a single consistent model expressed across many interfaces.

---

## Bottom line

XtraType is best described as:

> **a unified contextual record platform that combines capture, annotation, evidence management, structured authoring, knowledge organization, moderation/review, and public context publishing under one shared semantic model**

Its distinctive qualities are:

- a strong target/entry/intent/context/governance grammar
- capture-first but rigor-capable workflows
- progressive disclosure instead of form overload
- multi-surface operation across browser, mobile, workbench, public, and frontier modes
- explicit trust, provenance, privacy, and workflow states
- domain-pack specialization without changing the underlying system
- a governed approach to taxonomy and schema evolution

In other words, XtraType is not merely an app for writing things down. It is designed as a system for **capturing, structuring, governing, and presenting contextual knowledge**.
