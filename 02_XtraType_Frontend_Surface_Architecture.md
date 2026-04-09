# XtraType Frontend Surface Architecture

> The full surface model for XtraType across capture, editing, exploration, publication, review, and frontier modes.

| Document status | Finalized and authoritative frontend specification |
| --- | --- |
| System | XtraType |
| Scope | Frontend product architecture, interface behavior, interaction rules, view systems, templates, and governance UX |
| Backend boundary | All authorization, persistence, and server-side operations are assumed to be handled behind a single API-key-backed service boundary; this document set does not define backend architecture |
| Canonical stance | Capture-first entry points + adaptive composer shell + progressive disclosure + target-centric workbench + domain-pack extensibility |


## 1. Experience layers

XtraType operates as one product with several expression layers:

| Layer | Function |
| --- | --- |
| Capture surfaces | Get from encounter to durable draft in the fewest meaningful steps |
| Adaptive composer | Turn a draft into a structured, interpretable, governable record |
| Workbench | Explore, compare, organize, govern, and evolve the record universe |
| Public / publishable surfaces | Expose selected records or layers for reading, embedding, or overlay |
| Management surfaces | Handle templates, vocabularies, domain packs, saved lenses, and system configuration |
| Frontier surfaces | Voice, object memory, AR, live rooms, ghost layers, and high-context overlays |

These are not separate products. They are coordinated frontend expressions over the same grammar.

## 2. Surface inventory

### 2.1 Browser extension surface
Used for page-linked capture, quote-linked capture, screenshot evidence, inline comments, citations, flags, personal saves, and lightweight overlays.

Core features:
- selected text capture
- URL and page metadata capture
- quick intent chips
- mini-composer
- inline target preview
- screenshot and quote blocks
- one-click save to current collection or workspace
- open-in-workbench escalation

### 2.2 Mobile field capture surface
Used for observations, inspections, place notes, route events, media capture, voice notes, incident records, and object scans.

Core features:
- location lock or live position
- route or movement-aware capture
- media and voice capture
- field-intent shortcuts
- offline draft queue
- object scan / QR / NFC entry
- place/event/object target creation

### 2.3 Manual drafting surface
Used when the user begins from deliberate intent inside the main app.

Core features:
- target search or target creation
- template-first or blank-authoring start
- full composer shell
- domain pack awareness
- support and relation building
- collection placement

### 2.4 Import and share surface
Used when content enters through share sheets, clipboard, drag-and-drop, pasted URLs, uploaded files, or external references.

Core features:
- import classification
- source-vs-entry decision support
- quick save as source, evidence, or draft
- file/library tray
- batch import staging

### 2.5 Target workbench
Used to explore one target and everything attached to it.

Core features:
- target header and summary
- related entries
- source/evidence chains
- timeline, map, graph, or thread lenses
- trust and workflow strips
- collection membership
- activity feed
- compare and filter

### 2.6 Collection workbench
Used to navigate projects, notebooks, case files, queues, rooms, or curated sets.

Core features:
- multiple collection views
- saved filters and lenses
- grouping and ordering modes
- bulk operations
- collaboration surfaces
- queue and review tools

### 2.7 Reviewer and moderation surfaces
Used for evidence review, moderation, verification, publication, dispute handling, and correction flow.

Core features:
- queue boards
- comparison panes
- workflow action strips
- trust badges
- evidence chain inspection
- publish/unpublish or supersede actions
- dispute and resolution panels

### 2.8 Public read surfaces
Used for published records, shared collections, embeddable layers, and public target pages.

Core features:
- target page
- public entry cards
- support and provenance visibility
- public trust badges
- public filters
- read-only graph or timeline views where appropriate

### 2.9 Object memory scan surface
Used for real-world objects anchored through scan codes or proximity tools.

Core features:
- scan-to-target resolution
- object state summary
- new observation or maintenance record
- condition media capture
- route/history lens
- object dossier

### 2.10 Voice-first roaming surface
Used for hands-busy or movement-heavy contexts.

Core features:
- voice note capture
- auto-segmented record suggestions
- route and timestamp association
- confirm-and-save cards
- later cleanup in composer

### 2.11 AR spatial surface
Used for spatially anchored overlays and place/object record discovery.

Core features:
- anchored markers
- place/object/event layer filters
- add record in space
- on-demand support preview
- conflict and density controls

### 2.12 Ghost layer / page overlay surface
Used to reveal contextual records over existing pages or digital surfaces.

Core features:
- page-linked annotations
- source warnings or support markers
- personal, team, or public overlay modes
- density controls
- hover summaries and expand-on-demand panels

### 2.13 Live evidence room surface
Used for synchronized collaborative analysis.

Core features:
- shared target or case view
- evidence board
- live updates
- compare pane
- discussion thread
- queue and decision history

### 2.14 Schema commons surface
Used to browse, install, fork, propose, and promote templates, vocabularies, and domain packs.

Core features:
- catalog search
- preview cards
- install/fork flows
- proposal review
- version comparison
- dependency visibility

## 3. Global navigation model

XtraType navigation should not be organized solely around files or flat feeds. It should expose several primary ways into the system:

| Navigation layer | Primary question |
| --- | --- |
| Targets | What is this about? |
| Collections | Where is this organized? |
| Activity | What changed or needs attention? |
| Domains | What mode of work am I in? |
| Templates | What structure should I start from? |
| Saved lenses | How do I want to see this right now? |
| Publishing / public layers | What is exposed outward? |
| Management | How is the system itself shaped? |

## 4. Layout model

The default workbench layout should support target-centric, collection-centric, and queue-centric work with a shared structural language.

Recommended desktop layout:
- left rail: navigation, recent items, domain packs, collections, saved lenses
- center workspace: list, board, graph, map, timeline, detail, or compare view
- right inspector: target details, provenance, support chain, trust strip, relation details
- bottom or modal composer: quick actions or inline edit expansion

Recommended mobile layout:
- tab or segmented navigation
- stacked cards
- drawer-based inspectors
- floating quick-capture button
- context-sensitive bottom sheets for intent, support, and visibility

## 5. View system

The frontend must support several canonical view types:

| View type | Primary use |
| --- | --- |
| List | general browsing, search results, dense review |
| Detail | focused reading and editing |
| Grid / gallery | media-heavy and object-heavy browsing |
| Board | workflow stages, moderation, assignments, curation |
| Timeline | temporal targets, events, revisions, route history |
| Map | spatial targets, field observations, civic place layers |
| Graph | relationship exploration, support/dispute networks, schema maps |
| Queue | review, moderation, verification, inbox, unresolved work |
| Compare | claims, versions, evidence items, templates, conflicts |
| Transcript / thread | conversational and voice-origin flows |
| Matrix | evaluation, classification, or educational analysis |
| Dossier / packet | compact export-style review and case reading |

### View rules

- Views are lenses over the same objects, not separate data silos.
- A collection or target may support multiple view types simultaneously.
- Templates and domain packs may set preferred default views.
- The user may save custom lenses and return to them.

## 6. Domain-pack switching

Domain packs are a frontend-level mode of interpretation, terminology, default views, and template priority. Switching domain packs should never rewrite the core semantics of the underlying records. It may change language, field prominence, default intents, review affordances, and recommended views.

The frontend must therefore support:
- domain-aware labels
- pack-specific empty states
- pack-specific starter templates
- pack-specific suggested intents
- pack-specific view presets
- pack-specific public presentation styles

## 7. Accessibility and responsiveness

The expanded XtraType frontend must remain usable across dense and lightweight contexts.

Minimum expectations:
- keyboard-first operation in desktop workbench
- touch-first operation in mobile and scan flows
- clear focus order
- visible status language instead of icon-only semantics
- color-independent trust and workflow signals
- collapsible density in graph, map, and overlay views
- readable provenance summaries
- low-cognitive-load quick capture

## 8. Cross-surface continuity rules

- The same record should feel recognizable across extension, mobile, workbench, and public views.
- A draft created in a quick surface must open cleanly in the full composer without data translation anxiety.
- Target identity and support chains must survive surface transitions.
- Domain-pack context should travel with the record unless intentionally changed.
- Public or shared presentation should never hide the existence of support, provenance, or trust states.
