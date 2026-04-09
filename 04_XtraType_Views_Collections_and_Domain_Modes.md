# XtraType Views, Collections, and Domain Modes

> The browsing, organizational, and specialized-mode universe of the XtraType frontend.

| Document status | Finalized and authoritative frontend specification |
| --- | --- |
| System | XtraType |
| Scope | Frontend product architecture, interface behavior, interaction rules, view systems, templates, and governance UX |
| Backend boundary | All authorization, persistence, and server-side operations are assumed to be handled behind a single API-key-backed service boundary; this document set does not define backend architecture |
| Canonical stance | Capture-first entry points + adaptive composer shell + progressive disclosure + target-centric workbench + domain-pack extensibility |


## 1. Collections are working surfaces

In XtraType, collections are not passive folders. They are live containers with lensing, ordering, collaboration, and interpretation behavior. A collection may be a notebook, case file, evidence room, map layer, incident folder, curriculum set, object fleet, moderation queue, or public layer.

### Collection types

| Collection type | Primary use |
| --- | --- |
| Notebook | general accumulation and reflection |
| Case file | issue-centered investigation or tracking |
| Dossier / packet | compact review package around a target, event, or claim |
| Review queue | moderation, verification, editorial, or team workflow |
| Map layer | spatial grouping and public or private overlays |
| Timeline set | event and revision tracking |
| Board / workspace | workflow staging and team handling |
| Gallery / media set | media-heavy curation |
| Route trail | movement or sequence-based record history |
| Domain library | reusable sources, templates, or vocabulary assets |
| Public layer | outward-facing set of selected records |
| Object fleet | grouped real-world assets and their histories |
| Live room | active collaborative analysis session |

## 2. Lens system

Every collection and many targets should support multiple saved lenses.

Common lenses:
- All records
- My drafts
- Needs support
- Needs review
- Verified
- Disputed
- Published
- Spatial
- Temporal
- Media-heavy
- Assertions only
- Sources only
- Corrections only
- Recent activity
- Unresolved items
- High-confidence only
- Low-confidence watchlist

## 3. Canonical view types

### List view
Dense, sortable, filterable, appropriate for most administrative and review tasks.

### Card/detail view
Readable, rich, suitable for individual records and public reading.

### Board view
Kanban-like, ideal for workflow states, assignments, moderation, and curation lanes.

### Timeline view
Ideal for temporal targets, event reconstruction, revision history, route logs, and case chronology.

### Map view
Ideal for place-based notes, field inspections, civic memory, object fleets, and AR-linked work.

### Graph view
Ideal for relationship exploration, support/dispute chains, schema previews, and target networks.

### Queue view
Ideal for reviewer inboxes, unresolved items, duplicate candidates, conflict lists, and moderation flows.

### Compare view
Ideal for contradictory entries, competing sources, revisions, template diffs, and object-state changes.

### Gallery view
Ideal for media sets, object inspections, visual field notes, and public exhibits.

### Transcript/thread view
Ideal for conversations, interviews, voice capture, and collaborative evidence-room chat.

### Dossier view
Ideal for compact multi-panel review of a single target, event, object, or claim.

## 4. Domain-pack catalog

The frontend officially recognizes the following domain packs as first-class product territory.

### 4.1 Personal Memory Pack
Primary goal: help a person remember what they encountered, thought, saved, or noticed.

- primary targets: pages, places, people, products, ideas, events
- primary intents: personal, referential, informational, organizational
- default views: notebook list, timeline, map, target page
- notable UI: quick-save chips, memory trails, resurfacing cards, “why I saved this” prompts

### 4.2 Research Notebook Pack
Primary goal: support source-aware synthesis and claim building.

- primary targets: documents, quotes, topics, claims, authors, datasets
- primary intents: evidentiary, informational, corrective, organizational
- default views: source library, claim board, graph, compare, dossier
- notable UI: source chains, quote extraction, support/contradiction links, citation-first blocks

### 4.3 Field Observation Pack
Primary goal: support mobile documentation of places, routes, objects, incidents, and conditions.

- primary targets: places, routes, objects, events
- primary intents: observational, evidentiary, operational
- default views: map, route timeline, media gallery, condition board
- notable UI: glove-friendly capture, scan entry, quick evidence blocks, environmental badges

### 4.4 Fact-Check and Claim Review Pack
Primary goal: examine assertions and their support or contradiction.

- primary targets: claims, people, organizations, documents, events
- primary intents: evidentiary, corrective, evaluative
- default views: claim dossier, source compare, review queue, graph
- notable UI: claim blocks, evidence ladders, contradiction ribbons, verification states

### 4.5 Public Annotation and Publishing Pack
Primary goal: reveal contextual posts publicly over web pages, targets, or collections.

- primary targets: pages, entities, places, topics, claims
- primary intents: informational, conversational, corrective, evidentiary
- default views: public target page, ghost overlay, public collection page
- notable UI: public badges, reader filters, layer toggles, density controls

### 4.6 Team Review and Moderation Pack
Primary goal: support operational handling of content, incidents, evidence, and policy workflow.

- primary targets: entries, claims, media items, users, events
- primary intents: operational, evaluative, corrective, evidentiary
- default views: queue, board, compare, audit timeline
- notable UI: reviewer actions, resolution strips, assignment chips, escalation controls

### 4.7 Civic Place Memory Pack
Primary goal: layer local memory, observation, and supporting context onto places.

- primary targets: places, routes, landmarks, neighborhoods, civic events
- primary intents: observational, informational, corrective
- default views: map, timeline, gallery, public layer
- notable UI: place pages, before/after compare, local issue trails, community trust cues

### 4.8 Classroom and Seminar Pack
Primary goal: structure learning around claims, sources, evidence, discussion, and revision.

- primary targets: readings, claims, topics, assignments, events
- primary intents: evidentiary, conversational, evaluative, personal
- default views: notebook, compare, graph, classroom queue
- notable UI: guided citation prompts, discussion threads, revision lineage, rubric blocks

### 4.9 Schema Commons Pack
Primary goal: expose reusable templates, vocabularies, and domain packs as frontend-visible assets.

- primary targets: templates, vocabularies, domain packs, shared concepts
- primary intents: organizational, operational, informational
- default views: catalog, compare, dependency graph, proposal queue
- notable UI: install/fork/share, version previews, stewardship panels

### 4.10 Real-Time Evidence Room Pack
Primary goal: coordinate live collaborative analysis around a claim, event, case, or incident.

- primary targets: case files, evidence items, claims, events
- primary intents: evidentiary, conversational, operational
- default views: live board, compare, chat/transcript, dossier
- notable UI: presence, live updates, decision history, evidence staging lanes

### 4.11 Object Memory Pack
Primary goal: treat real-world objects as durable targets with contextual histories.

- primary targets: objects, assets, equipment, rooms, installations
- primary intents: observational, operational, informational
- default views: object dossier, gallery, timeline, map if relevant
- notable UI: scan surfaces, condition history, maintenance trails, object relations

### 4.12 Ghost Layer Pack
Primary goal: overlay contextual record layers on top of already-existing digital surfaces.

- primary targets: webpages, documents, messages, interfaces
- primary intents: informational, corrective, evidentiary, conversational
- default views: overlay, side panel, target page
- notable UI: inline anchors, density controls, private/team/public overlay selectors

### 4.13 Voice-First Pack
Primary goal: minimize friction for roaming capture and conversational note creation.

- primary targets: route segments, places, moments, interview fragments, ideas
- primary intents: observational, personal, informational
- default views: transcript/thread, timeline, draft cleanup
- notable UI: confirm cards, auto-segmentation, hands-free save, summary cleanup queue

### 4.14 AR Spatial Pack
Primary goal: reveal and author contextual records in the physical environment.

- primary targets: places, objects, landmarks, event zones
- primary intents: observational, informational, corrective
- default views: spatial overlay, map, target sheet
- notable UI: anchored markers, line-of-sight controls, spatial density settings

### 4.15 Argument Operating System Pack
Primary goal: formalize claims, supports, disputes, amendments, and reasoning chains.

- primary targets: claims, propositions, policies, decisions
- primary intents: evidentiary, corrective, evaluative
- default views: graph, claim dossier, compare, argument matrix
- notable UI: relation builders, contradiction highlighting, formal claim cards

### 4.16 Reality Layer Pack
Primary goal: operate XtraType as a broad public or semi-public context layer across pages, places, objects, and claims.

- primary targets: all target classes
- primary intents: all major intent families
- default views: ghost layer, map, graph, timeline, public collection pages
- notable UI: layer switching, scale controls, trust filters, public/private segmentation, high-context target pages

## 5. Cross-pack UI rules

- Domain packs change the presentation and defaults, not the underlying object grammar.
- Pack switching must preserve existing records without semantic loss.
- Packs may add views, blocks, and vocabulary sets, but must not redefine target, entry, intent, context, or governance itself.
- A user may work across multiple packs at once; the frontend should expose pack context without hard walls.

## 6. Specialized working surfaces inside packs

Additional specialized surfaces that may appear across packs:

- quote extraction tray
- evidence packet builder
- route recorder
- issue triage queue
- claim compare desk
- object condition strip
- vocabulary quick-add tray
- template proposal panel
- correction chain viewer
- duplicate resolution desk
- event reconstruction timeline
- public layer moderation queue
- public trust legend
- scan history log
- saved lens manager

## 7. Public and private coexistence

Any pack may have:
- strictly private views
- team-only views
- review-only views
- public-ready views
- embedded or overlay views

The frontend must make it clear which layer the user is looking at. A ghost layer or public record should never visually masquerade as a private workspace artifact.
