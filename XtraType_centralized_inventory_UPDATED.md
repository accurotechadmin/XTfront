# XtraType Centralized Inventory

- **System:** XtraType
- **Document kind:** inventory
- **Format:** human-friendly markdown inventory
- **Schema version:** 1.0.0
- **Inventory status:** authoritative_frontend_expanded
- **Generated on:** 2026-04-09
- **Design scope:** Authoritative frontend product grammar, surfaces, view systems, templates, domain packs, automation UX, governance UX, public presentation modes, and the full sanctioned expansion universe.

## How to read this inventory

Each item below includes the same normalized fields as the JSON source of truth:

- **id** — Stable unique identifier for the inventory item.
- **section** — Major grouping used in the human-readable inventory.
- **kind** — Normalized item class within the inventory model.
- **name** — Canonical display name.
- **slug** — Machine-friendly identifier candidate.
- **parent_id** — Immediate parent concept when the item participates in a hierarchy.
- **maturity** — Implementation maturity and breadth within the frontend universe.
- **ui_visibility_hint** — How often the item should surface in user-facing interfaces.
- **summary** — Stable concise description.
- **purpose** — Why the concept belongs in the product and what it unlocks.
- **representative_examples** — Illustrative non-exhaustive examples.
- **depends_on** — Related concepts that should exist or be understood first.
- **implementation_notes** — Short specification-oriented notes for downstream component and flow design.

## Maturity scale

- **core** — Foundational concept required across the mature frontend system.
- **recommended** — Broadly expected concept in normal XtraType deployments and surfaces.
- **advanced** — Expanded concept that is fully sanctioned in the product universe and may appear in more specialized packs or surfaces.
- **optional** — Useful in select interfaces or deployments but not required in every surface.

## UI visibility scale

- **always_available** — Should usually be present in the visible creation or reading interface.
- **context_driven** — Should appear when the current target, intent, pack, workflow, or surface warrants it.
- **admin_or_system** — Usually managed through configuration, stewardship, or deeper management surfaces rather than casual creation flows.
- **derived_or_internal** — Captured or inferred by the system and primarily revealed through inspectors, badges, or detail views.

## Section index

- **01. Core Layers** — 5 items
- **02. High-Level Object Families** — 10 items
- **03. Target Classes** — 7 items
- **04. Entry Classes** — 9 items
- **05. Intent Categories** — 10 items
- **06. Content Modality Classes** — 6 items
- **07. Context Classes** — 6 items
- **08. Source and Evidence Classes** — 5 items
- **09. Relationship Classes** — 6 items
- **10. Identity and Authorship Classes** — 5 items
- **11. Workflow and Lifecycle Classes** — 6 items
- **12. Visibility and Permissions Classes** — 5 items
- **13. Provenance and Capture Metadata Classes** — 5 items
- **14. Taxonomy and Schema Classes** — 6 items
- **15. Trust, Uncertainty, and Verification Classes** — 5 items
- **16. Collection and Organization Classes** — 6 items
- **17. Event and Activity Classes** — 4 items
- **18. Context-Driven UI Decision Axes** — 6 items
- **19. Frontend Surface Classes** — 12 items
- **20. Capture Flow Classes** — 7 items
- **21. Composer Region Classes** — 8 items
- **22. View and Lens Classes** — 10 items
- **23. Domain Pack Classes** — 16 items
- **24. Suggestion and Automation Classes** — 8 items
- **25. Role and Stewardship Classes** — 7 items
- **26. Settings and Personalization Classes** — 6 items
- **27. Public Presentation Classes** — 6 items

## Core Layers

### XT-LAY-001 — Target

- **kind:** core_layer
- **slug:** `target`
- **parent_id:** —
- **maturity:** core
- **ui_visibility_hint:** admin_or_system
- **summary:** Anchor object that an entry refers to, overlays, or is attached to.
- **purpose:** Keeps the subject of reference distinct from authored content so one target can support many records, views, and public or private interpretations.
- **representative_examples:** URL; GPS point + radius; person; claim; scanned object
- **depends_on:** —
- **implementation_notes:**
  - Target identity must remain stable across capture, editing, overlay, and publication surfaces.
  - Composite targets are first-class targets, not temporary frontend hacks.

### XT-LAY-002 — Entry

- **kind:** core_layer
- **slug:** `entry`
- **parent_id:** —
- **maturity:** core
- **ui_visibility_hint:** always_available
- **summary:** User-created unit of content attached to a target or another entry.
- **purpose:** Provides the universal authored record container for notes, evidence, citations, observations, workflow actions, media, and publishable contextual posts.
- **representative_examples:** comment; citation; flag; observation; assertion
- **depends_on:** XT-LAY-001
- **implementation_notes:**
  - Every surface must be able to produce a valid draft entry.
  - Entries may begin lightweight and deepen over time without losing identity.

### XT-LAY-003 — Intent

- **kind:** core_layer
- **slug:** `intent`
- **parent_id:** —
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Declared, suggested, or inferred purpose of an entry.
- **purpose:** Drives field emphasis, validation cues, drawer behavior, template defaults, review semantics, and downstream interpretation.
- **representative_examples:** comment; cite; flag; classify; observe
- **depends_on:** XT-LAY-002
- **implementation_notes:**
  - Intent must stay editable in one click.
  - The same entry class may support multiple intents.

### XT-LAY-004 — Context

- **kind:** core_layer
- **slug:** `context`
- **parent_id:** —
- **maturity:** core
- **ui_visibility_hint:** derived_or_internal
- **summary:** Situational frame that explains where, how, and under what conditions an entry was created and is being used.
- **purpose:** Allows the frontend to adapt capture, view logic, template choice, automation, privacy cues, and disclosure by surface and domain.
- **representative_examples:** browser capture; mobile field note; team review; public overlay
- **depends_on:** XT-LAY-002
- **implementation_notes:**
  - Captured facts and inferred domain context should remain visually distinguishable.
  - Context changes the surface feel without changing the underlying grammar.

### XT-LAY-005 — Governance

- **kind:** core_layer
- **slug:** `governance`
- **parent_id:** —
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Control layer for trust, privacy, workflow, moderation, publication, and auditability.
- **purpose:** Keeps an ultra-flexible contextual record system coherent, reviewable, explainable, and safe in private, team, and public settings.
- **representative_examples:** visibility; verification; review state; audit trail; publication mode
- **depends_on:** XT-LAY-002, XT-LAY-004
- **implementation_notes:**
  - Governance is additive to authoring and should not dominate lightweight capture.
  - Important state changes must be inspectable and reversible from the frontend.

## High-Level Object Families

### XT-OBJ-001 — Target Family

- **kind:** object_family
- **slug:** `target-family`
- **parent_id:** —
- **maturity:** core
- **ui_visibility_hint:** admin_or_system
- **summary:** Top-level family for all things that can be referenced, addressed, overlaid, or revisited.
- **purpose:** Provides the common abstraction across digital, spatial, temporal, named, abstract, object-memory, and composite subjects.
- **representative_examples:** webpage; place; event; device-tagged object
- **depends_on:** —
- **implementation_notes:**
  - Families are independently extensible without changing the core grammar.

### XT-OBJ-002 — Entry Family

- **kind:** object_family
- **slug:** `entry-family`
- **parent_id:** —
- **maturity:** core
- **ui_visibility_hint:** admin_or_system
- **summary:** Top-level family for all user-authored content units.
- **purpose:** Unifies notes, claims, citations, evidence, classifications, workflow actions, packets, and publishable contextual posts.
- **representative_examples:** annotation; citation; report; assertion
- **depends_on:** —
- **implementation_notes:**
  - Entry family items share one adaptive composer shell.

### XT-OBJ-003 — Relationship Family

- **kind:** object_family
- **slug:** `relationship-family`
- **parent_id:** —
- **maturity:** core
- **ui_visibility_hint:** admin_or_system
- **summary:** Top-level family for explicit links between targets, entries, sources, collections, and states.
- **purpose:** Supports support, contradiction, reply, supersession, attribution, containment, aliasing, and graph-aware navigation.
- **representative_examples:** supports; replies to; same as; contained in
- **depends_on:** —
- **implementation_notes:**
  - Relationships are first-class product structures, not hidden metadata.

### XT-OBJ-004 — Source Family

- **kind:** object_family
- **slug:** `source-family`
- **parent_id:** —
- **maturity:** core
- **ui_visibility_hint:** admin_or_system
- **summary:** Top-level family for materials that can be cited, extracted, or treated as evidence.
- **purpose:** Keeps source identity and evidence support distinct from commentary and target identity.
- **representative_examples:** book; webpage; dataset; scan; transcript
- **depends_on:** —
- **implementation_notes:**
  - Sources must remain inspectable and reusable across many entries.

### XT-OBJ-005 — Context Record Family

- **kind:** object_family
- **slug:** `context-record-family`
- **parent_id:** —
- **maturity:** recommended
- **ui_visibility_hint:** admin_or_system
- **summary:** Top-level family for captured situational metadata and environmental traces.
- **purpose:** Preserves time, device, geospatial, session, route, overlay, and import facts without bloating entry bodies.
- **representative_examples:** user agent; GPS radius; route trace; timezone
- **depends_on:** —
- **implementation_notes:**
  - Context records power trust and continuity across surfaces.

### XT-OBJ-006 — Identity and Authorship Family

- **kind:** object_family
- **slug:** `identity-and-authorship-family`
- **parent_id:** —
- **maturity:** recommended
- **ui_visibility_hint:** admin_or_system
- **summary:** Top-level family for actors, attribution modes, and visible roles.
- **purpose:** Handles named, pseudonymous, anonymous, organizational, public, reviewer, and system participation.
- **representative_examples:** display name; verified user; system actor; public reader
- **depends_on:** —
- **implementation_notes:**
  - Display identity and trust identity must remain conceptually distinct.

### XT-OBJ-007 — Workflow and Moderation Family

- **kind:** object_family
- **slug:** `workflow-and-moderation-family`
- **parent_id:** —
- **maturity:** recommended
- **ui_visibility_hint:** admin_or_system
- **summary:** Top-level family for operational states, routes, queues, and review actions.
- **purpose:** Supports drafting, review, moderation, escalation, publication, assignment, and resolution lifecycles.
- **representative_examples:** needs review; flagged; published; assigned
- **depends_on:** —
- **implementation_notes:**
  - Workflow state is a visible dimension of records, not an afterthought.

### XT-OBJ-008 — Permissions and Audience Family

- **kind:** object_family
- **slug:** `permissions-and-audience-family`
- **parent_id:** —
- **maturity:** recommended
- **ui_visibility_hint:** admin_or_system
- **summary:** Top-level family for audience boundaries, access scopes, and action capabilities.
- **purpose:** Lets the frontend explain who can see, edit, publish, review, export, or reuse a record or target.
- **representative_examples:** private; workspace-only; public; role-gated
- **depends_on:** —
- **implementation_notes:**
  - The frontend renders permissions even though enforcement lives behind the API boundary.

### XT-OBJ-009 — Taxonomy and Schema Family

- **kind:** object_family
- **slug:** `taxonomy-and-schema-family`
- **parent_id:** —
- **maturity:** recommended
- **ui_visibility_hint:** admin_or_system
- **summary:** Top-level family for controlled vocabularies, templates, packs, and front-end field structures.
- **purpose:** Enables growth without chaos by making type systems and template systems visible, editable, and governable.
- **representative_examples:** label set; template; domain pack; entry type
- **depends_on:** —
- **implementation_notes:**
  - Controlled growth is a core frontend feature.

### XT-OBJ-010 — Provenance and Trust Family

- **kind:** object_family
- **slug:** `provenance-and-trust-family`
- **parent_id:** —
- **maturity:** recommended
- **ui_visibility_hint:** admin_or_system
- **summary:** Top-level family for origin, integrity, confidence, verification, and dispute signals.
- **purpose:** Supports explainability and trust decisions for everyday capture as well as public or evidentiary use.
- **representative_examples:** source-backed; AI-assisted; verified; challenged
- **depends_on:** —
- **implementation_notes:**
  - Captured, inferred, asserted, imported, and reviewed data must remain visually distinct.

## Target Classes

### XT-TGT-001 — Digital Resource Target

- **kind:** target_class
- **slug:** `digital-resource-target`
- **parent_id:** XT-OBJ-001
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Target addressed through a digital locator or application-level identifier.
- **purpose:** Covers web pages, documents, messages, records, files, and API-addressable resources.
- **representative_examples:** URL; file; message; API resource
- **depends_on:** XT-LAY-001
- **implementation_notes:**
  - Support canonicalization, aliasing, snapshots, and quote anchoring.

### XT-TGT-002 — Spatial / Geographic Target

- **kind:** target_class
- **slug:** `spatial-geographic-target`
- **parent_id:** XT-OBJ-001
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Target anchored in physical space or geographic coordinates.
- **purpose:** Enables field observations, routes, geofences, site records, and place-based public layers.
- **representative_examples:** GPS point; address; geofence; route
- **depends_on:** XT-LAY-001
- **implementation_notes:**
  - Point, area, and path should behave as compatible spatial primitives.

### XT-TGT-003 — Temporal Target

- **kind:** target_class
- **slug:** `temporal-target`
- **parent_id:** XT-OBJ-001
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Target defined by a point, span, offset, or recurring window in time.
- **purpose:** Supports event moments, historical periods, meeting windows, media offsets, and route timing.
- **representative_examples:** timestamp; time range; historical period; clip offset
- **depends_on:** XT-LAY-001
- **implementation_notes:**
  - Absolute and relative time should remain distinguishable.

### XT-TGT-004 — Named Entity Target

- **kind:** target_class
- **slug:** `named-entity-target`
- **parent_id:** XT-OBJ-001
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Target identified primarily by canonical identity, alias, or public name.
- **purpose:** Handles people, organizations, projects, products, topics, classrooms, devices, and locations with name-based identity.
- **representative_examples:** person; organization; topic; project
- **depends_on:** XT-LAY-001
- **implementation_notes:**
  - Allow aliases, external IDs, and display-name variants.

### XT-TGT-005 — Abstract / Logical Target

- **kind:** target_class
- **slug:** `abstract-logical-target`
- **parent_id:** XT-OBJ-001
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Target that is conceptual rather than directly locational.
- **purpose:** Lets users attach records to claims, issues, policies, requirements, decisions, and arguments.
- **representative_examples:** claim; issue; decision; policy
- **depends_on:** XT-LAY-001
- **implementation_notes:**
  - These targets usually require stronger relationship modeling than address-only targets.

### XT-TGT-006 — Object-Memory Target

- **kind:** target_class
- **slug:** `object-memory-target`
- **parent_id:** XT-OBJ-001
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Target representing a physical object or item that can be revisited over time.
- **purpose:** Powers scan-based memory, maintenance history, field inspection, and place-object linkage.
- **representative_examples:** QR-tagged object; barcode item; equipment; artifact
- **depends_on:** XT-LAY-001
- **implementation_notes:**
  - Should support scan anchors, serial references, and physical context overlays.

### XT-TGT-007 — Composite Target

- **kind:** target_class
- **slug:** `composite-target`
- **parent_id:** XT-OBJ-001
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Layered target composed from more than one addressing primitive or target class.
- **purpose:** Supports the real-world cases where meaning is attached to a combination of page, quote, time, place, object, or event.
- **representative_examples:** URL + quote; place + event window; object + route + condition
- **depends_on:** XT-LAY-001
- **implementation_notes:**
  - Composite targets are a core part of the product, not an exceptional edge case.

## Entry Classes

### XT-ENT-001 — Annotation Entry

- **kind:** entry_class
- **slug:** `annotation-entry`
- **parent_id:** XT-OBJ-002
- **maturity:** core
- **ui_visibility_hint:** always_available
- **summary:** Local commentary attached to a target context.
- **purpose:** Supports lightweight remarks, contextual notes, and inline interpretation without forcing rigorous structure.
- **representative_examples:** comment; margin note; overlay note
- **depends_on:** XT-LAY-002
- **implementation_notes:**
  - Optimized for fast capture and later deepening.

### XT-ENT-002 — Citation Entry

- **kind:** entry_class
- **slug:** `citation-entry`
- **parent_id:** XT-OBJ-002
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Entry whose main role is source-aware attribution or reference.
- **purpose:** Makes evidence and supporting sources explicit and reusable.
- **representative_examples:** source citation; quote citation; reference note
- **depends_on:** XT-LAY-002, XT-OBJ-004
- **implementation_notes:**
  - Needs bibliographic, excerpt, and relation-friendly blocks.

### XT-ENT-003 — Evidence Entry

- **kind:** entry_class
- **slug:** `evidence-entry`
- **parent_id:** XT-OBJ-002
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Entry that presents support material, proof, or a captured artifact.
- **purpose:** Provides a durable unit for source-backed reasoning, moderation support, inspection evidence, or public substantiation.
- **representative_examples:** photo evidence; excerpt; measurement; document proof
- **depends_on:** XT-LAY-002
- **implementation_notes:**
  - Should foreground provenance, integrity, and support relations.

### XT-ENT-004 — Classification Entry

- **kind:** entry_class
- **slug:** `classification-entry`
- **parent_id:** XT-OBJ-002
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Entry used to label, categorize, or route a target or another entry.
- **purpose:** Supports filing, triage, batch processing, and domain-specific controlled vocabulary actions.
- **representative_examples:** tag; status label; category assignment
- **depends_on:** XT-LAY-002, XT-OBJ-009
- **implementation_notes:**
  - Often high-speed and often template-driven.

### XT-ENT-005 — Social / Conversational Entry

- **kind:** entry_class
- **slug:** `social-conversational-entry`
- **parent_id:** XT-OBJ-002
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Entry used for discussion, reply, question, or collaborative exchange.
- **purpose:** Lets XtraType support conversational interpretation and teamwork without collapsing into generic chat.
- **representative_examples:** reply; question; discussion note
- **depends_on:** XT-LAY-002
- **implementation_notes:**
  - Requires thread context and relation visibility.

### XT-ENT-006 — Workflow Entry

- **kind:** entry_class
- **slug:** `workflow-entry`
- **parent_id:** XT-OBJ-002
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Entry whose primary role is to move work through a process.
- **purpose:** Supports assignment, routing, moderation actions, approval states, and review outcomes.
- **representative_examples:** assign; escalate; approve; return for review
- **depends_on:** XT-LAY-002, XT-LAY-005
- **implementation_notes:**
  - Workflow actions should read as actions, not hidden metadata.

### XT-ENT-007 — Collection / Curation Entry

- **kind:** entry_class
- **slug:** `collection-curation-entry`
- **parent_id:** XT-OBJ-002
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Entry representing curation, grouping, ordering, or dossier assembly.
- **purpose:** Lets users build notebooks, case files, boards, packets, and exhibit-like views.
- **representative_examples:** collection note; ordering move; dossier item
- **depends_on:** XT-LAY-002, XT-OBJ-009
- **implementation_notes:**
  - Collections are working surfaces, not just folders.

### XT-ENT-008 — Media Entry

- **kind:** entry_class
- **slug:** `media-entry`
- **parent_id:** XT-OBJ-002
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Entry primarily centered on media objects or mixed-media capture.
- **purpose:** Handles screenshots, photos, clips, recordings, transcripts, and AR or scan artifacts.
- **representative_examples:** image note; audio log; clip record; screenshot
- **depends_on:** XT-LAY-002
- **implementation_notes:**
  - May include generated blocks such as OCR or transcript content.

### XT-ENT-009 — Assertion Entry

- **kind:** entry_class
- **slug:** `assertion-entry`
- **parent_id:** XT-OBJ-002
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Entry that stands as a claim, statement, proposition, or declared interpretation.
- **purpose:** Provides a stable unit for claim review, argument mapping, corrections, and public challenge/support workflows.
- **representative_examples:** claim; finding; stated interpretation
- **depends_on:** XT-LAY-002
- **implementation_notes:**
  - Should surface support, contradiction, confidence, and verification prominently.

## Intent Categories

### XT-INT-001 — Informational Intent

- **kind:** intent_category
- **slug:** `informational-intent`
- **parent_id:** XT-LAY-003
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Intent focused on recording or explaining something.
- **purpose:** Optimizes the UI for note-taking, summarizing, and communicating context.
- **representative_examples:** record; explain; summarize
- **depends_on:** XT-LAY-003
- **implementation_notes:**
  - Usually body-forward and support-optional.

### XT-INT-002 — Evaluative Intent

- **kind:** intent_category
- **slug:** `evaluative-intent`
- **parent_id:** XT-LAY-003
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Intent focused on judgment, assessment, or appraisal.
- **purpose:** Supports inspections, reviews, ratings, and qualitative or comparative assessments.
- **representative_examples:** assess; rate; judge
- **depends_on:** XT-LAY-003
- **implementation_notes:**
  - Often pairs with structured fields and evidence blocks.

### XT-INT-003 — Evidentiary Intent

- **kind:** intent_category
- **slug:** `evidentiary-intent`
- **parent_id:** XT-LAY-003
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Intent focused on support, proof, or substantiation.
- **purpose:** Prioritizes source attachment, provenance display, and support relations.
- **representative_examples:** support; document; prove
- **depends_on:** XT-LAY-003
- **implementation_notes:**
  - Should open support surfaces by default.

### XT-INT-004 — Conversational Intent

- **kind:** intent_category
- **slug:** `conversational-intent`
- **parent_id:** XT-LAY-003
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Intent focused on replying, asking, discussing, or debating.
- **purpose:** Helps the UI emphasize thread context and social continuity.
- **representative_examples:** reply; ask; discuss
- **depends_on:** XT-LAY-003
- **implementation_notes:**
  - Needs thread and relation awareness.

### XT-INT-005 — Organizational Intent

- **kind:** intent_category
- **slug:** `organizational-intent`
- **parent_id:** XT-LAY-003
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Intent focused on filing, grouping, saving, or arranging.
- **purpose:** Supports collection work, memory workflows, batch classification, and curation.
- **representative_examples:** save; file; group
- **depends_on:** XT-LAY-003
- **implementation_notes:**
  - May minimize body text and foreground chips or collection controls.

### XT-INT-006 — Operational Intent

- **kind:** intent_category
- **slug:** `operational-intent`
- **parent_id:** XT-LAY-003
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Intent focused on moving work through action and process.
- **purpose:** Supports queue routing, review movement, assignments, and moderation operations.
- **representative_examples:** assign; route; escalate
- **depends_on:** XT-LAY-003
- **implementation_notes:**
  - Often appears alongside workflow entry classes.

### XT-INT-007 — Observational Intent

- **kind:** intent_category
- **slug:** `observational-intent`
- **parent_id:** XT-LAY-003
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Intent focused on reporting what was seen, measured, heard, or encountered.
- **purpose:** Supports field note UX, route-aware capture, environment display, and scan/voice flows.
- **representative_examples:** observe; measure; report
- **depends_on:** XT-LAY-003
- **implementation_notes:**
  - Often pairs with spatial, temporal, and media blocks.

### XT-INT-008 — Referential Intent

- **kind:** intent_category
- **slug:** `referential-intent`
- **parent_id:** XT-LAY-003
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Intent focused on pointing, anchoring, or linking without extensive commentary.
- **purpose:** Useful for lightweight saves, cross-links, and contextual pointers.
- **representative_examples:** link; point to; anchor
- **depends_on:** XT-LAY-003
- **implementation_notes:**
  - Great for quick-save and overlay flows.

### XT-INT-009 — Corrective Intent

- **kind:** intent_category
- **slug:** `corrective-intent`
- **parent_id:** XT-LAY-003
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Intent focused on amending, disputing, correcting, or superseding.
- **purpose:** Powers error correction, dispute workflows, and public revision histories.
- **representative_examples:** correct; challenge; amend
- **depends_on:** XT-LAY-003
- **implementation_notes:**
  - Should foreground prior state and relationship semantics.

### XT-INT-010 — Personal / Mnemonic Intent

- **kind:** intent_category
- **slug:** `personal-mnemonic-intent`
- **parent_id:** XT-LAY-003
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Intent focused on saving something for later personal recall.
- **purpose:** Supports personal memory and lightweight retention without forced publication or rigor.
- **representative_examples:** remember; save for later; bookmark with context
- **depends_on:** XT-LAY-003
- **implementation_notes:**
  - Often pairs with minimal friction and private visibility defaults.

## Content Modality Classes

### XT-MOD-001 — Textual Modality

- **kind:** content_modality_class
- **slug:** `textual-modality`
- **parent_id:** XT-LAY-002
- **maturity:** core
- **ui_visibility_hint:** always_available
- **summary:** Typed or pasted language content used as the main authored body.
- **purpose:** Provides the most universal input mode across every surface.
- **representative_examples:** body text; quote block; summary; caption
- **depends_on:** XT-LAY-002
- **implementation_notes:**
  - Text blocks should remain composable with all other modalities.

### XT-MOD-002 — Media Modality

- **kind:** content_modality_class
- **slug:** `media-modality`
- **parent_id:** XT-LAY-002
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Images, audio, video, clips, screenshots, and visual artifacts.
- **purpose:** Enables richly contextual capture across browser, field, object, AR, and public workflows.
- **representative_examples:** photo; audio note; video clip; screenshot
- **depends_on:** XT-LAY-002
- **implementation_notes:**
  - Media should support metadata, preview, and derivative generated blocks.

### XT-MOD-003 — Structured Modality

- **kind:** content_modality_class
- **slug:** `structured-modality`
- **parent_id:** XT-LAY-002
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Form-like, taxonomic, measured, matrix, or checklist content.
- **purpose:** Supports inspections, templates, domain packs, and controlled vocabularies.
- **representative_examples:** checklist; measurement; taxonomy field; matrix
- **depends_on:** XT-LAY-002, XT-OBJ-009
- **implementation_notes:**
  - Structure may be template-defined or ad hoc.

### XT-MOD-004 — External Reference Modality

- **kind:** content_modality_class
- **slug:** `external-reference-modality`
- **parent_id:** XT-LAY-002
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** External identifiers, URLs, bibliographic handles, imported references, and linked records.
- **purpose:** Lets entries remain connected to outside systems and source materials.
- **representative_examples:** link; DOI; external ID; import handle
- **depends_on:** XT-LAY-002
- **implementation_notes:**
  - Should support preview and integrity-aware referencing.

### XT-MOD-005 — Generated / Computed Modality

- **kind:** content_modality_class
- **slug:** `generated-computed-modality`
- **parent_id:** XT-LAY-002
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Content derived by OCR, transcription, geocoding, extraction, or AI assistance.
- **purpose:** Makes automation useful while keeping system-generated material inspectable and separable from user-authored content.
- **representative_examples:** OCR text; transcript; geocode; AI draft
- **depends_on:** XT-LAY-002, XT-LAY-005
- **implementation_notes:**
  - Must always carry provenance and reversibility cues.

### XT-MOD-006 — Spatial / Temporal Trace Modality

- **kind:** content_modality_class
- **slug:** `spatial-temporal-trace-modality`
- **parent_id:** XT-LAY-002
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Captured route, movement, path, time-series, or spatiotemporal trace content.
- **purpose:** Supports field observation, roaming voice capture, AR anchoring, and reality-layer history.
- **representative_examples:** route trace; movement path; time series
- **depends_on:** XT-LAY-002, XT-LAY-004
- **implementation_notes:**
  - Should render cleanly in map, timeline, and detail views.

## Context Classes

### XT-CTX-001 — Capture Context

- **kind:** context_class
- **slug:** `capture-context`
- **parent_id:** XT-LAY-004
- **maturity:** core
- **ui_visibility_hint:** derived_or_internal
- **summary:** Describes where the record began and what the initiating surface provided.
- **purpose:** Lets the UI adapt to browser, mobile, workbench, import, scan, voice, overlay, or AR initiation.
- **representative_examples:** browser capture; mobile capture; voice capture
- **depends_on:** XT-LAY-004
- **implementation_notes:**
  - Capture context determines default blocks and disclosure level.

### XT-CTX-002 — Domain Context

- **kind:** context_class
- **slug:** `domain-context`
- **parent_id:** XT-LAY-004
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Describes the operating domain or pack shaping terms, templates, and views.
- **purpose:** Makes the same grammar feel native to research, fieldwork, moderation, classroom, public annotation, and other domains.
- **representative_examples:** research; field; moderation; public annotation
- **depends_on:** XT-LAY-004
- **implementation_notes:**
  - Domain context changes feel, not semantic backbone.

### XT-CTX-003 — Environmental Context

- **kind:** context_class
- **slug:** `environmental-context`
- **parent_id:** XT-LAY-004
- **maturity:** recommended
- **ui_visibility_hint:** derived_or_internal
- **summary:** Describes environmental and situational facts surrounding capture or use.
- **purpose:** Preserves time, movement, weather-like situational notes, device state, and route facts when relevant.
- **representative_examples:** timezone; movement state; device state; route conditions
- **depends_on:** XT-LAY-004
- **implementation_notes:**
  - Environmental context is not always visible but should remain inspectable.

### XT-CTX-004 — Privacy Context

- **kind:** context_class
- **slug:** `privacy-context`
- **parent_id:** XT-LAY-004
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Describes the audience posture and publication expectations around a record.
- **purpose:** Shapes warnings, publication affordances, visibility defaults, and overlay/public read behavior.
- **representative_examples:** private; shared; workspace; public
- **depends_on:** XT-LAY-004, XT-LAY-005
- **implementation_notes:**
  - Privacy context must remain visible whenever audience matters.

### XT-CTX-005 — Collaboration Context

- **kind:** context_class
- **slug:** `collaboration-context`
- **parent_id:** XT-LAY-004
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Describes whether the current work is solo, synchronous team, asynchronous review, or public conversation.
- **purpose:** Adapts threads, presence indicators, queue actions, and review affordances.
- **representative_examples:** solo drafting; team review; live evidence room; public discussion
- **depends_on:** XT-LAY-004
- **implementation_notes:**
  - Useful for live rooms, moderation queues, and classroom modes.

### XT-CTX-006 — Presentation Context

- **kind:** context_class
- **slug:** `presentation-context`
- **parent_id:** XT-LAY-004
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Describes whether the record is being authored, inspected, published, embedded, or overlaid.
- **purpose:** Lets the frontend switch between editing, review, public read, ghost layer, and embeddable presentations cleanly.
- **representative_examples:** authoring; review; public read; overlay
- **depends_on:** XT-LAY-004
- **implementation_notes:**
  - Presentation context should not mutate record meaning.

## Source and Evidence Classes

### XT-SRC-001 — Source Type

- **kind:** source_evidence_class
- **slug:** `source-type`
- **parent_id:** XT-OBJ-004
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Class of origin material that can be cited, excerpted, or examined.
- **purpose:** Standardizes how the frontend presents books, webpages, scans, datasets, clips, transcripts, and imported records.
- **representative_examples:** webpage; book; dataset; scan
- **depends_on:** XT-OBJ-004
- **implementation_notes:**
  - Source cards should remain reusable across entries.

### XT-SRC-002 — Evidence Type

- **kind:** source_evidence_class
- **slug:** `evidence-type`
- **parent_id:** XT-OBJ-004
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Class of supporting artifact or proof unit.
- **purpose:** Lets the UI distinguish images, excerpts, observations, measurements, testimonies, and system-derived evidence blocks.
- **representative_examples:** photo; measurement; excerpt; transcript
- **depends_on:** XT-OBJ-004
- **implementation_notes:**
  - Evidence type should affect preview and trust cues.

### XT-SRC-003 — Source Relation Type

- **kind:** source_evidence_class
- **slug:** `source-relation-type`
- **parent_id:** XT-OBJ-004
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Relation that explains how a source connects to a claim, target, or entry.
- **purpose:** Makes support, contradiction, attribution, translation, derivation, and citation semantics explicit.
- **representative_examples:** supports; contradicts; attributes; derives from
- **depends_on:** XT-OBJ-003, XT-OBJ-004
- **implementation_notes:**
  - These relations must read in plain language.

### XT-SRC-004 — Evidence Packet

- **kind:** source_evidence_class
- **slug:** `evidence-packet`
- **parent_id:** XT-OBJ-004
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Curated bundle of sources and evidence blocks assembled for review or publication.
- **purpose:** Supports moderation cases, dossiers, fact-check packets, field reports, and public proof bundles.
- **representative_examples:** case packet; review packet; public support dossier
- **depends_on:** XT-OBJ-004
- **implementation_notes:**
  - Packets are collection-like but support-centric.

### XT-SRC-005 — Evidence Chain

- **kind:** source_evidence_class
- **slug:** `evidence-chain`
- **parent_id:** XT-OBJ-004
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Ordered chain showing how support flows from source material to extracted evidence to claim.
- **purpose:** Provides reviewer-friendly trust navigation and public legibility for contested or rigorous records.
- **representative_examples:** source -> quote -> claim; photo -> observation -> report
- **depends_on:** XT-OBJ-003, XT-OBJ-004
- **implementation_notes:**
  - Should have chain, compare, and graph-friendly renderings.

## Relationship Classes

### XT-REL-001 — Entry-to-Target Relationship

- **kind:** relationship_class
- **slug:** `entry-to-target-relationship`
- **parent_id:** XT-OBJ-003
- **maturity:** core
- **ui_visibility_hint:** derived_or_internal
- **summary:** Relationship connecting an authored record to its subject.
- **purpose:** Expresses attachment, anchoring, address, and contextual overlay semantics.
- **representative_examples:** attached to; about; anchored in
- **depends_on:** XT-LAY-001, XT-LAY-002
- **implementation_notes:**
  - Must survive movement across surfaces and views.

### XT-REL-002 — Entry-to-Entry Relationship

- **kind:** relationship_class
- **slug:** `entry-to-entry-relationship`
- **parent_id:** XT-OBJ-003
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Relationship connecting one record to another.
- **purpose:** Supports replies, amendments, support, contradiction, duplicates, supersession, and thread continuity.
- **representative_examples:** replies to; amends; supports; duplicates
- **depends_on:** XT-LAY-002
- **implementation_notes:**
  - Should work in list, thread, graph, and compare views.

### XT-REL-003 — Target-to-Target Relationship

- **kind:** relationship_class
- **slug:** `target-to-target-relationship`
- **parent_id:** XT-OBJ-003
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Relationship between two targets.
- **purpose:** Supports aliasing, part-of, near, same-as, contained-in, related-topic, and route/place connections.
- **representative_examples:** same as; part of; near; related to
- **depends_on:** XT-LAY-001
- **implementation_notes:**
  - Important for entity resolution and contextual exploration.

### XT-REL-004 — Source-to-Claim Relationship

- **kind:** relationship_class
- **slug:** `source-to-claim-relationship`
- **parent_id:** XT-OBJ-003
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Relationship connecting a source or evidence unit to an assertion or claim.
- **purpose:** Provides explicit support, contradiction, attribution, derivation, or translation semantics.
- **representative_examples:** supports; contradicts; attributes
- **depends_on:** XT-OBJ-004
- **implementation_notes:**
  - This is a key relation in research and fact-check modes.

### XT-REL-005 — Collection-Membership Relationship

- **kind:** relationship_class
- **slug:** `collection-membership-relationship`
- **parent_id:** XT-OBJ-003
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Relationship connecting targets or entries to collections, boards, dossiers, queues, or notebooks.
- **purpose:** Makes organization and curation first-class and queryable.
- **representative_examples:** member of; ordered in; queued in
- **depends_on:** XT-OBJ-009
- **implementation_notes:**
  - Membership must carry ordering and role semantics when needed.

### XT-REL-006 — Supersession / Revision Relationship

- **kind:** relationship_class
- **slug:** `supersession-revision-relationship`
- **parent_id:** XT-OBJ-003
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Relationship describing how one record replaces, revises, or retires another.
- **purpose:** Supports corrections, public revision histories, moderation outcomes, and claim evolution.
- **representative_examples:** supersedes; retracts; corrects; revises
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Revision lineage must be visible and human-readable.

## Identity and Authorship Classes

### XT-IDN-001 — Identity Mode

- **kind:** identity_authorship_class
- **slug:** `identity-mode`
- **parent_id:** XT-OBJ-006
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Visible mode in which an actor appears in the interface.
- **purpose:** Supports named, pseudonymous, anonymous, organizational, and system-generated participation.
- **representative_examples:** named; pseudonymous; anonymous; organization
- **depends_on:** XT-OBJ-006
- **implementation_notes:**
  - Display identity and verified identity may differ.

### XT-IDN-002 — Authorship Attribute

- **kind:** identity_authorship_class
- **slug:** `authorship-attribute`
- **parent_id:** XT-OBJ-006
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Attribution-related property describing how a record was authored or reviewed.
- **purpose:** Keeps authored, co-authored, imported, generated, reviewed, and published contributions legible.
- **representative_examples:** authored; reviewed; imported; generated
- **depends_on:** XT-OBJ-006
- **implementation_notes:**
  - Useful for trust surfaces and history views.

### XT-IDN-003 — Reputation / Trust Attribute

- **kind:** identity_authorship_class
- **slug:** `reputation-trust-attribute`
- **parent_id:** XT-OBJ-006
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Attribute summarizing visible trust or standing around an actor or role.
- **purpose:** Provides reader cues without replacing item-level trust semantics.
- **representative_examples:** trusted reviewer; verified publisher; new contributor
- **depends_on:** XT-OBJ-006, XT-OBJ-010
- **implementation_notes:**
  - Must never override record-level evidence and provenance.

### XT-IDN-004 — Role Display Attribute

- **kind:** identity_authorship_class
- **slug:** `role-display-attribute`
- **parent_id:** XT-OBJ-006
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Visible role label rendered beside an actor in the UI.
- **purpose:** Helps users understand whether someone is contributing, reviewing, moderating, curating, or publishing.
- **representative_examples:** reviewer; moderator; domain curator
- **depends_on:** XT-OBJ-006
- **implementation_notes:**
  - A display role is not the same thing as backend authorization.

### XT-IDN-005 — Presence / Participation Attribute

- **kind:** identity_authorship_class
- **slug:** `presence-participation-attribute`
- **parent_id:** XT-OBJ-006
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Attribute showing whether an actor is active in a live collaboration context.
- **purpose:** Supports evidence rooms, live review, classroom sessions, and synchronous moderation.
- **representative_examples:** active; watching; editing; reviewing live
- **depends_on:** XT-OBJ-006
- **implementation_notes:**
  - Presence is surface-specific and should degrade gracefully.

## Workflow and Lifecycle Classes

### XT-WFL-001 — Draft State

- **kind:** workflow_lifecycle_class
- **slug:** `draft-state`
- **parent_id:** XT-OBJ-007
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** State indicating that a record exists but is not yet finalized for its current context.
- **purpose:** Makes lightweight capture safe and recoverable across every surface.
- **representative_examples:** quick draft; saved draft; in-progress
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Every surface must support draft save.

### XT-WFL-002 — Review State

- **kind:** workflow_lifecycle_class
- **slug:** `review-state`
- **parent_id:** XT-OBJ-007
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** State indicating whether a record needs, is in, or has passed review.
- **purpose:** Supports reviewer flows, moderation work, classroom checking, and trust-sensitive publication.
- **representative_examples:** needs review; under review; reviewed
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Review state should be visible in queues and detail views.

### XT-WFL-003 — Moderation State

- **kind:** workflow_lifecycle_class
- **slug:** `moderation-state`
- **parent_id:** XT-OBJ-007
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** State indicating moderation posture or intervention.
- **purpose:** Supports hidden, flagged, restricted, challenged, restored, or escalated content handling.
- **representative_examples:** flagged; restricted; restored
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Moderation should be explicit when it affects visibility or trust.

### XT-WFL-004 — Resolution State

- **kind:** workflow_lifecycle_class
- **slug:** `resolution-state`
- **parent_id:** XT-OBJ-007
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** State indicating whether an issue, claim, or workflow matter is open, resolved, or superseded.
- **purpose:** Provides closure for cases, disputes, corrections, and action workflows.
- **representative_examples:** open; resolved; superseded
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Particularly important in operational and corrective modes.

### XT-WFL-005 — Publication State

- **kind:** workflow_lifecycle_class
- **slug:** `publication-state`
- **parent_id:** XT-OBJ-007
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** State indicating whether a record is private, staged, published, embedded, or archived for presentation.
- **purpose:** Supports public read surfaces, overlays, dossiers, and shareable collections.
- **representative_examples:** private; staged; published; archived
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Publication state should be clear but not conflated with visibility alone.

### XT-WFL-006 — Assignment / Routing State

- **kind:** workflow_lifecycle_class
- **slug:** `assignment-routing-state`
- **parent_id:** XT-OBJ-007
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** State describing responsibility, queue placement, or route ownership.
- **purpose:** Supports team review, moderation, classroom feedback, and operational routing.
- **representative_examples:** assigned; queued; returned; escalated
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Useful in reviewer strips and queue views.

## Visibility and Permissions Classes

### XT-PER-001 — Visibility Class

- **kind:** visibility_permissions_class
- **slug:** `visibility-class`
- **parent_id:** XT-OBJ-008
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Audience visibility posture rendered by the frontend.
- **purpose:** Makes it clear whether a record is private, shared, workspace-visible, public, or selectively exposed.
- **representative_examples:** private; workspace; public
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Visibility should always be legible before publishing or sharing.

### XT-PER-002 — Permission Class

- **kind:** visibility_permissions_class
- **slug:** `permission-class`
- **parent_id:** XT-OBJ-008
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Action capability class rendered to explain what can be done in the current interface.
- **purpose:** Helps users understand edit, review, moderate, publish, export, and curate affordances.
- **representative_examples:** edit; review; publish; export
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - The frontend explains permissions even if enforcement is external.

### XT-PER-003 — Inheritance / Scope Rule

- **kind:** visibility_permissions_class
- **slug:** `inheritance-scope-rule`
- **parent_id:** XT-OBJ-008
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Rule showing whether a setting is local, inherited, overridden, or collection-bound.
- **purpose:** Prevents confusion when records live inside workspaces, collections, queues, or published bundles.
- **representative_examples:** inherits collection scope; local override
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Users should always know why a visibility or action rule is present.

### XT-PER-004 — Audience Class

- **kind:** visibility_permissions_class
- **slug:** `audience-class`
- **parent_id:** XT-OBJ-008
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Named audience target used in public, team, classroom, and overlay publication flows.
- **purpose:** Makes the act of addressing an audience explicit in the UI.
- **representative_examples:** self; team; class; public readers
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Audience is related to but distinct from visibility.

### XT-PER-005 — Action Gating Class

- **kind:** visibility_permissions_class
- **slug:** `action-gating-class`
- **parent_id:** XT-OBJ-008
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Frontend-visible class describing whether a meaningful action is allowed, restricted, or approval-bound.
- **purpose:** Supports safe workflow handling around publish, verify, moderate, and promote actions.
- **representative_examples:** allowed; approval required; restricted
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Action gating should appear inline, not only as an error after click.

## Provenance and Capture Metadata Classes

### XT-PRV-001 — Creation Provenance

- **kind:** provenance_capture_class
- **slug:** `creation-provenance`
- **parent_id:** XT-OBJ-010
- **maturity:** core
- **ui_visibility_hint:** derived_or_internal
- **summary:** Record of how a target or entry came into existence.
- **purpose:** Makes the frontend transparent about manual creation, import, scan, browser capture, voice capture, or generated derivation.
- **representative_examples:** manual; browser capture; import; voice
- **depends_on:** XT-LAY-004, XT-LAY-005
- **implementation_notes:**
  - Creation provenance should be concise in cards and deep in inspectors.

### XT-PRV-002 — Technical Capture Metadata

- **kind:** provenance_capture_class
- **slug:** `technical-capture-metadata`
- **parent_id:** XT-OBJ-010
- **maturity:** recommended
- **ui_visibility_hint:** derived_or_internal
- **summary:** Technical details captured at creation time.
- **purpose:** Preserves device, client, time, locator, quote, selection, scan, and route details that support trust and continuity.
- **representative_examples:** client metadata; selected text; GPS radius; timestamp
- **depends_on:** XT-LAY-004
- **implementation_notes:**
  - Metadata should be available without overwhelming the primary authoring flow.

### XT-PRV-003 — Integrity Metadata

- **kind:** provenance_capture_class
- **slug:** `integrity-metadata`
- **parent_id:** XT-OBJ-010
- **maturity:** advanced
- **ui_visibility_hint:** derived_or_internal
- **summary:** Metadata supporting content integrity and chain awareness.
- **purpose:** Enables hashes, snapshot references, edit lineage, and other trust-supporting signals.
- **representative_examples:** hash; snapshot; edit lineage
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Integrity signals matter most in evidence and public trust flows.

### XT-PRV-004 — Suggestion Provenance

- **kind:** provenance_capture_class
- **slug:** `suggestion-provenance`
- **parent_id:** XT-OBJ-010
- **maturity:** recommended
- **ui_visibility_hint:** derived_or_internal
- **summary:** Provenance describing why a suggestion appeared and what input produced it.
- **purpose:** Keeps automation explainable and reversible.
- **representative_examples:** inferred from quote; derived from location; template recommendation
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Suggestions should say why they were suggested.

### XT-PRV-005 — Transformation Provenance

- **kind:** provenance_capture_class
- **slug:** `transformation-provenance`
- **parent_id:** XT-OBJ-010
- **maturity:** advanced
- **ui_visibility_hint:** derived_or_internal
- **summary:** Record of meaningful transformations applied to content blocks.
- **purpose:** Supports OCR, transcription, summarization, geocoding, extraction, redaction, and other computed steps.
- **representative_examples:** OCR applied; transcribed; summarized; geocoded
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Transforms must never masquerade as raw capture.

## Taxonomy and Schema Classes

### XT-TAX-001 — System-Level Type

- **kind:** taxonomy_schema_class
- **slug:** `system-level-type`
- **parent_id:** XT-OBJ-009
- **maturity:** core
- **ui_visibility_hint:** admin_or_system
- **summary:** Canonical type defined as part of the base XtraType grammar.
- **purpose:** Provides stable semantics that survive across packs and surfaces.
- **representative_examples:** assertion entry; spatial target; visibility class
- **depends_on:** XT-OBJ-009
- **implementation_notes:**
  - System-level types should change rarely and deliberately.

### XT-TAX-002 — Domain-Level Type

- **kind:** taxonomy_schema_class
- **slug:** `domain-level-type`
- **parent_id:** XT-OBJ-009
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Type specialized for a domain pack while staying compatible with the core grammar.
- **purpose:** Allows research, field, moderation, classroom, civic, and object-memory workflows to feel native.
- **representative_examples:** fact-check claim; field observation; moderation case
- **depends_on:** XT-OBJ-009
- **implementation_notes:**
  - Domain-level types should inherit clearly from system-level types.

### XT-TAX-003 — Vocabulary Class

- **kind:** taxonomy_schema_class
- **slug:** `vocabulary-class`
- **parent_id:** XT-OBJ-009
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Controlled vocabulary or label system surfaced in templates and classification flows.
- **purpose:** Keeps fast capture consistent without sacrificing extensibility.
- **representative_examples:** status set; topic labels; inspection categories
- **depends_on:** XT-OBJ-009
- **implementation_notes:**
  - Should support suggestion, governance, and deprecation.

### XT-TAX-004 — Template Class

- **kind:** taxonomy_schema_class
- **slug:** `template-class`
- **parent_id:** XT-OBJ-009
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Reusable field and layout arrangement applied to authoring and review flows.
- **purpose:** Turns the adaptive composer into a domain-native experience without breaking the core grammar.
- **representative_examples:** field note template; citation template; claim review template
- **depends_on:** XT-OBJ-009
- **implementation_notes:**
  - Templates may change disclosure, defaults, and blocks.

### XT-TAX-005 — Domain Pack

- **kind:** taxonomy_schema_class
- **slug:** `domain-pack`
- **parent_id:** XT-OBJ-009
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Bundle of templates, vocabulary, defaults, views, and terminology for a mode of work.
- **purpose:** Lets the same product feel native across very different use cases.
- **representative_examples:** research pack; field pack; object memory pack
- **depends_on:** XT-OBJ-009
- **implementation_notes:**
  - Packs specialize feel and structure, not semantics.

### XT-TAX-006 — Proposal / Promotion Class

- **kind:** taxonomy_schema_class
- **slug:** `proposal-promotion-class`
- **parent_id:** XT-OBJ-009
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Class representing a suggested new type, template, vocabulary, or pack element moving through controlled growth.
- **purpose:** Enables expansion without chaos by making growth visible and governable from the frontend.
- **representative_examples:** new field suggestion; template proposal; vocabulary promotion
- **depends_on:** XT-OBJ-009, XT-LAY-005
- **implementation_notes:**
  - Growth should move from local shape to shared concept through explicit steps.

## Trust, Uncertainty, and Verification Classes

### XT-TRU-001 — Confidence Class

- **kind:** trust_verification_class
- **slug:** `confidence-class`
- **parent_id:** XT-OBJ-010
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Visible indicator of certainty or uncertainty around a record or claim.
- **purpose:** Helps users separate tentative, observational, inferred, and strongly supported records.
- **representative_examples:** low confidence; tentative; high confidence
- **depends_on:** XT-OBJ-010
- **implementation_notes:**
  - Confidence should be intelligible to casual readers.

### XT-TRU-002 — Verification Class

- **kind:** trust_verification_class
- **slug:** `verification-class`
- **parent_id:** XT-OBJ-010
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Visible verification posture indicating whether a record has been checked and by whom or how.
- **purpose:** Supports public trust, review flows, and evidentiary rigor.
- **representative_examples:** unverified; reviewed; verified
- **depends_on:** XT-OBJ-010
- **implementation_notes:**
  - Verification is not the same as truth or popularity.

### XT-TRU-003 — Dispute Class

- **kind:** trust_verification_class
- **slug:** `dispute-class`
- **parent_id:** XT-OBJ-010
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Visible state indicating challenge, disagreement, or unresolved conflict.
- **purpose:** Lets readers and reviewers understand contested records without erasing them.
- **representative_examples:** challenged; in dispute; contested
- **depends_on:** XT-OBJ-010
- **implementation_notes:**
  - Dispute views should expose the conflict structure.

### XT-TRU-004 — Quality Class

- **kind:** trust_verification_class
- **slug:** `quality-class`
- **parent_id:** XT-OBJ-010
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Visible assessment of completeness, clarity, or readiness of a record.
- **purpose:** Supports review queues, template hygiene, and public presentation quality cues.
- **representative_examples:** incomplete; usable; high quality
- **depends_on:** XT-OBJ-010
- **implementation_notes:**
  - Quality should not hide underlying provenance or evidence gaps.

### XT-TRU-005 — Sensitivity Class

- **kind:** trust_verification_class
- **slug:** `sensitivity-class`
- **parent_id:** XT-OBJ-010
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Indicator showing whether a record deserves extra caution in presentation or reuse.
- **purpose:** Supports privacy-aware, safety-aware, and context-sensitive frontend behavior.
- **representative_examples:** sensitive; restricted context; needs caution
- **depends_on:** XT-OBJ-010, XT-LAY-005
- **implementation_notes:**
  - Sensitivity affects presentation and warnings more than basic semantics.

## Collection and Organization Classes

### XT-COL-001 — Collection Type

- **kind:** collection_organization_class
- **slug:** `collection-type`
- **parent_id:** XT-OBJ-009
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Named grouping surface that gathers targets or entries into usable working contexts.
- **purpose:** Supports notebooks, boards, dossiers, queues, map layers, cases, and public bundles.
- **representative_examples:** notebook; board; dossier; queue
- **depends_on:** XT-OBJ-009
- **implementation_notes:**
  - Collections are active working surfaces.

### XT-COL-002 — Membership Relationship Type

- **kind:** collection_organization_class
- **slug:** `membership-relationship-type`
- **parent_id:** XT-OBJ-009
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Relationship explaining how an item belongs to a collection.
- **purpose:** Lets the frontend distinguish ordinary membership, ordered placement, pinned inclusion, or evidentiary bundling.
- **representative_examples:** member; ordered member; pinned; exhibit item
- **depends_on:** XT-OBJ-003
- **implementation_notes:**
  - Important for compare, queue, and dossier views.

### XT-COL-003 — Ordering Mode

- **kind:** collection_organization_class
- **slug:** `ordering-mode`
- **parent_id:** XT-OBJ-009
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Mode describing how a collection is sequenced.
- **purpose:** Supports manual ordering, time ordering, trust ordering, route ordering, evidentiary ordering, and more.
- **representative_examples:** manual; chronological; spatial; priority
- **depends_on:** XT-OBJ-009
- **implementation_notes:**
  - Ordering is a first-class curation action.

### XT-COL-004 — Saved Lens

- **kind:** collection_organization_class
- **slug:** `saved-lens`
- **parent_id:** XT-OBJ-009
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Reusable filtered or perspective-driven view into a collection or target set.
- **purpose:** Lets users move between memory, review, trust, public, spatial, or argument lenses quickly.
- **representative_examples:** map lens; review lens; public lens; graph lens
- **depends_on:** XT-OBJ-009
- **implementation_notes:**
  - Lenses are often more important than folders in a rich system.

### XT-COL-005 — Dossier / Packet Collection

- **kind:** collection_organization_class
- **slug:** `dossier-packet-collection`
- **parent_id:** XT-OBJ-009
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Collection optimized for assembled evidence, case material, or publishable packets.
- **purpose:** Supports fact-check dossiers, moderation cases, classroom packets, and public proof bundles.
- **representative_examples:** case file; evidence packet; report bundle
- **depends_on:** XT-OBJ-009
- **implementation_notes:**
  - Should support narrative and evidentiary ordering.

### XT-COL-006 — Layered Overlay Collection

- **kind:** collection_organization_class
- **slug:** `layered-overlay-collection`
- **parent_id:** XT-OBJ-009
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Collection optimized for overlaying many records on a page, place, route, or object.
- **purpose:** Supports ghost layers, AR layers, map layers, and contextual public overlays.
- **representative_examples:** page overlay layer; map layer; AR layer
- **depends_on:** XT-OBJ-009
- **implementation_notes:**
  - Layer visibility and density control are central.

## Event and Activity Classes

### XT-EVT-001 — Event Type

- **kind:** event_activity_class
- **slug:** `event-type`
- **parent_id:** XT-LAY-005
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Class for occurrences in the world or in the record universe that may themselves become targets.
- **purpose:** Supports incidents, meetings, observations, changes, and public timelines.
- **representative_examples:** incident; meeting; observation event; publication event
- **depends_on:** XT-LAY-001
- **implementation_notes:**
  - Event targets often combine spatial and temporal properties.

### XT-EVT-002 — Activity Log Type

- **kind:** event_activity_class
- **slug:** `activity-log-type`
- **parent_id:** XT-LAY-005
- **maturity:** recommended
- **ui_visibility_hint:** derived_or_internal
- **summary:** Class for recorded actions taken in the system.
- **purpose:** Provides inspectable trails for edits, reviews, promotions, publications, and moderation actions.
- **representative_examples:** edited; reviewed; published; promoted
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Activity logs describe actions, not reality claims.

### XT-EVT-003 — Session Event

- **kind:** event_activity_class
- **slug:** `session-event`
- **parent_id:** XT-LAY-005
- **maturity:** advanced
- **ui_visibility_hint:** derived_or_internal
- **summary:** Event describing a meaningful boundary in a capture or collaboration session.
- **purpose:** Supports live evidence rooms, roaming capture sessions, and recovery after interruptions.
- **representative_examples:** capture session started; room joined; route resumed
- **depends_on:** XT-LAY-004
- **implementation_notes:**
  - Helpful for continuity across complex surfaces.

### XT-EVT-004 — Publication Event

- **kind:** event_activity_class
- **slug:** `publication-event`
- **parent_id:** XT-LAY-005
- **maturity:** advanced
- **ui_visibility_hint:** derived_or_internal
- **summary:** Event marking meaningful changes in public-facing presentation state.
- **purpose:** Supports public revision histories, overlay updates, and published collection histories.
- **representative_examples:** record published; collection updated; overlay revised
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Useful for public trust and embeddable history.

## Context-Driven UI Decision Axes

### XT-UIA-001 — Target Axis

- **kind:** ui_decision_axis
- **slug:** `target-axis`
- **parent_id:** XT-LAY-004
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** UI axis answering what the record is about.
- **purpose:** Determines target headers, address display, re-anchoring UI, and target-centric navigation.
- **representative_examples:** page; place; claim; object
- **depends_on:** XT-LAY-001
- **implementation_notes:**
  - Always visible somewhere in the composer.

### XT-UIA-002 — Intent Axis

- **kind:** ui_decision_axis
- **slug:** `intent-axis`
- **parent_id:** XT-LAY-004
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** UI axis answering what the user is trying to do.
- **purpose:** Drives defaults, visible fields, open drawers, and suggested actions.
- **representative_examples:** observe; cite; correct; save
- **depends_on:** XT-LAY-003
- **implementation_notes:**
  - Intent is the main UI switchboard.

### XT-UIA-003 — Support / Evidence Axis

- **kind:** ui_decision_axis
- **slug:** `support-evidence-axis`
- **parent_id:** XT-LAY-004
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** UI axis answering what support exists or is required.
- **purpose:** Controls source trays, evidence prompts, trust cues, and claim substantiation flows.
- **representative_examples:** no support; source attached; packet attached
- **depends_on:** XT-OBJ-004
- **implementation_notes:**
  - Particularly important in assertion and review modes.

### XT-UIA-004 — Workflow / Privacy Axis

- **kind:** ui_decision_axis
- **slug:** `workflow-privacy-axis`
- **parent_id:** XT-LAY-004
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** UI axis answering what audience and process posture applies.
- **purpose:** Shapes visibility cues, review actions, publication affordances, and warnings.
- **representative_examples:** private draft; team review; public publish
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Often shown as a visible strip rather than a hidden settings form.

### XT-UIA-005 — Capture Surface Axis

- **kind:** ui_decision_axis
- **slug:** `capture-surface-axis`
- **parent_id:** XT-LAY-004
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** UI axis answering where the flow started and what affordances are native there.
- **purpose:** Lets the system feel lightweight in browser/mobile while staying coherent in the workbench.
- **representative_examples:** browser; mobile; voice; scan; AR
- **depends_on:** XT-LAY-004
- **implementation_notes:**
  - Surface affects feel, not the core semantics.

### XT-UIA-006 — Domain Pack Axis

- **kind:** ui_decision_axis
- **slug:** `domain-pack-axis`
- **parent_id:** XT-LAY-004
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** UI axis answering which pack or working mode shapes language and structure.
- **purpose:** Allows one product to feel like many specialized tools without fragmenting the model.
- **representative_examples:** research; field; ghost layer; argument OS
- **depends_on:** XT-OBJ-009
- **implementation_notes:**
  - Domain pack switching should preserve the current record when possible.

## Frontend Surface Classes

### XT-SFC-001 — Browser Extension Surface

- **kind:** frontend_surface_class
- **slug:** `browser-extension-surface`
- **parent_id:** XT-LAY-004
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Capture-first surface for acting directly on webpages and digital resources.
- **purpose:** Makes selection, quick note, citation, overlay, and save actions immediate in context.
- **representative_examples:** selection capture; quick annotation; quote citation
- **depends_on:** XT-LAY-004
- **implementation_notes:**
  - Must be fast, lightweight, and draft-safe.

### XT-SFC-002 — Mobile Field Capture Surface

- **kind:** frontend_surface_class
- **slug:** `mobile-field-capture-surface`
- **parent_id:** XT-LAY-004
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Capture-first surface for geospatial, observational, camera, and movement-aware work.
- **purpose:** Powers field notes, site inspection, roaming memory, and route-aware observation.
- **representative_examples:** field note; photo observation; route capture
- **depends_on:** XT-LAY-004
- **implementation_notes:**
  - Optimized for one-hand, interrupted, real-world use.

### XT-SFC-003 — Manual Drafting Surface

- **kind:** frontend_surface_class
- **slug:** `manual-drafting-surface`
- **parent_id:** XT-LAY-004
- **maturity:** core
- **ui_visibility_hint:** always_available
- **summary:** Focused authoring surface for deliberate creation and editing.
- **purpose:** Provides a fuller editor without requiring the complexity of the full workbench.
- **representative_examples:** new record; long-form claim; manual citation
- **depends_on:** XT-LAY-002
- **implementation_notes:**
  - Useful when capture does not begin from a context.

### XT-SFC-004 — Import and Share Surface

- **kind:** frontend_surface_class
- **slug:** `import-share-surface`
- **parent_id:** XT-LAY-004
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Surface for turning shared or imported material into structured records.
- **purpose:** Supports paste, share-sheet, upload, drag-drop, and imported external references.
- **representative_examples:** shared URL; uploaded file; pasted text
- **depends_on:** XT-LAY-004
- **implementation_notes:**
  - Should quickly extract a valid target and draft entry.

### XT-SFC-005 — Target Workbench

- **kind:** frontend_surface_class
- **slug:** `target-workbench`
- **parent_id:** XT-LAY-004
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Deep exploration surface centered on one target and everything attached to it.
- **purpose:** Lets users move between records, evidence, relationships, views, history, and public/read states.
- **representative_examples:** page workbench; place workbench; claim workbench
- **depends_on:** XT-LAY-001
- **implementation_notes:**
  - A target can support many lenses and many entry classes.

### XT-SFC-006 — Collection Workbench

- **kind:** frontend_surface_class
- **slug:** `collection-workbench`
- **parent_id:** XT-LAY-004
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Deep working surface centered on a collection, board, case, notebook, queue, or packet.
- **purpose:** Supports curation, ordering, review, batching, comparison, and publishable assembly.
- **representative_examples:** notebook; board; dossier; queue
- **depends_on:** XT-OBJ-009
- **implementation_notes:**
  - Collections are a major navigation surface.

### XT-SFC-007 — Reviewer and Moderation Surface

- **kind:** frontend_surface_class
- **slug:** `reviewer-moderation-surface`
- **parent_id:** XT-LAY-004
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Surface optimized for checking, routing, approving, challenging, or moderating records.
- **purpose:** Supports queues, side-by-side comparison, trust inspection, and action trails.
- **representative_examples:** review queue; moderation panel; approval screen
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Should make state transitions explicit and legible.

### XT-SFC-008 — Public Read Surface

- **kind:** frontend_surface_class
- **slug:** `public-read-surface`
- **parent_id:** XT-LAY-004
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Presentation surface for shareable records, collections, overlays, and evidence bundles.
- **purpose:** Lets XtraType function as a public contextual publishing layer without exposing authoring complexity.
- **representative_examples:** record permalink; public dossier; public collection
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Public read must foreground trust, provenance, and revision context.

### XT-SFC-009 — Object Memory Scan Surface

- **kind:** frontend_surface_class
- **slug:** `object-memory-scan-surface`
- **parent_id:** XT-LAY-004
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Scan-first surface for attaching context to physical objects.
- **purpose:** Enables object history, maintenance memory, field inspection, and situated notes.
- **representative_examples:** QR scan; barcode scan; NFC touch
- **depends_on:** —
- **implementation_notes:**
  - Should handle low-friction repeat visits to the same object target.

### XT-SFC-010 — Voice-First Roaming Surface

- **kind:** frontend_surface_class
- **slug:** `voice-first-roaming-surface`
- **parent_id:** XT-LAY-004
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Capture surface optimized for spoken notes and movement.
- **purpose:** Supports hands-busy or roaming workflows while preserving place, time, and observational context.
- **representative_examples:** spoken field note; walking memory capture
- **depends_on:** XT-LAY-004
- **implementation_notes:**
  - Voice capture must remain editable and inspectable afterward.

### XT-SFC-011 — AR Spatial Surface

- **kind:** frontend_surface_class
- **slug:** `ar-spatial-surface`
- **parent_id:** XT-LAY-004
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Surface for viewing and placing contextual records in spatial alignment with the environment.
- **purpose:** Supports spatial overlays, place memory, guided inspection, and future reality-layer interactions.
- **representative_examples:** anchored place note; object overlay; spatial evidence marker
- **depends_on:** XT-LAY-004
- **implementation_notes:**
  - AR is a valid XtraType surface even if iterated later.

### XT-SFC-012 — Ghost Layer / Overlay Surface

- **kind:** frontend_surface_class
- **slug:** `ghost-layer-overlay-surface`
- **parent_id:** XT-LAY-004
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Surface that overlays contextual records on pages, places, routes, or objects without entering a full workbench.
- **purpose:** Makes XtraType feel like a living context layer over existing experiences.
- **representative_examples:** page overlay; map overlay; object overlay
- **depends_on:** XT-LAY-004
- **implementation_notes:**
  - Overlay density and trust readability are critical.

## Capture Flow Classes

### XT-CAP-001 — Browser Capture Flow

- **kind:** capture_flow_class
- **slug:** `browser-capture-flow`
- **parent_id:** XT-LAY-004
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Flow beginning from a page, quote, or selection inside the browser surface.
- **purpose:** Optimized for fast contextual capture with later escalation to deeper rigor.
- **representative_examples:** selection -> quick note; selection -> citation
- **depends_on:** XT-LAY-004, XT-SFC-001
- **implementation_notes:**
  - Should auto-build a draft with target context already attached.

### XT-CAP-002 — Mobile Capture Flow

- **kind:** capture_flow_class
- **slug:** `mobile-capture-flow`
- **parent_id:** XT-LAY-004
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Flow beginning from place, camera, route, or observation in the mobile surface.
- **purpose:** Optimized for field use, interruption tolerance, and sensor- or place-aware context.
- **representative_examples:** place -> observation; camera -> evidence; route -> log
- **depends_on:** XT-LAY-004, XT-SFC-002
- **implementation_notes:**
  - Save must be possible with minimal typed input.

### XT-CAP-003 — Manual Draft Flow

- **kind:** capture_flow_class
- **slug:** `manual-draft-flow`
- **parent_id:** XT-LAY-004
- **maturity:** core
- **ui_visibility_hint:** always_available
- **summary:** Flow beginning from a deliberate new-entry action rather than a captured context.
- **purpose:** Supports deeper creation, structured authoring, and thoughtful composition.
- **representative_examples:** new claim; new dossier note
- **depends_on:** XT-SFC-003
- **implementation_notes:**
  - Should offer target creation and target lookup as peers.

### XT-CAP-004 — Import / Share Flow

- **kind:** capture_flow_class
- **slug:** `import-share-flow`
- **parent_id:** XT-LAY-004
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Flow beginning from pasted, shared, or uploaded content.
- **purpose:** Quickly transforms imported material into targets, sources, drafts, or evidence blocks.
- **representative_examples:** share URL; upload photo; paste text
- **depends_on:** XT-SFC-004
- **implementation_notes:**
  - Import suggestions should remain editable and attributable.

### XT-CAP-005 — Voice-First Flow

- **kind:** capture_flow_class
- **slug:** `voice-first-flow`
- **parent_id:** XT-LAY-004
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Flow beginning from spoken capture while moving or operating hands-free.
- **purpose:** Lets users generate observational drafts without losing contextual fidelity.
- **representative_examples:** spoken observation; roaming memory note
- **depends_on:** XT-SFC-010
- **implementation_notes:**
  - Must preserve transcript provenance and editability.

### XT-CAP-006 — Object Scan Flow

- **kind:** capture_flow_class
- **slug:** `object-scan-flow`
- **parent_id:** XT-LAY-004
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Flow beginning from scanning or tapping a real-world object anchor.
- **purpose:** Supports repeatable object memory and scan-native inspection behavior.
- **representative_examples:** scan -> object history; scan -> new object note
- **depends_on:** XT-SFC-009
- **implementation_notes:**
  - Should immediately resolve or create an object target.

### XT-CAP-007 — AR Placement Flow

- **kind:** capture_flow_class
- **slug:** `ar-placement-flow`
- **parent_id:** XT-LAY-004
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Flow beginning from the user placing or opening a record in spatial alignment.
- **purpose:** Supports future spatially anchored public or private contextual layers.
- **representative_examples:** place marker; open anchored note
- **depends_on:** XT-SFC-011
- **implementation_notes:**
  - AR placement must still end in an inspectable normal record.

## Composer Region Classes

### XT-CMP-001 — Target Bar

- **kind:** composer_region_class
- **slug:** `target-bar`
- **parent_id:** XT-LAY-002
- **maturity:** core
- **ui_visibility_hint:** always_available
- **summary:** Always-visible region summarizing what the record is about.
- **purpose:** Provides stable target context during authoring, review, and conversion.
- **representative_examples:** target chip; target card header
- **depends_on:** XT-LAY-001
- **implementation_notes:**
  - Users should never lose sight of the target.

### XT-CMP-002 — Intent Rail

- **kind:** composer_region_class
- **slug:** `intent-rail`
- **parent_id:** XT-LAY-002
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Region for selecting or inspecting why the entry exists.
- **purpose:** Turns intent into an accessible switchboard rather than a hidden field.
- **representative_examples:** intent chips; purpose selector
- **depends_on:** XT-LAY-003
- **implementation_notes:**
  - Must remain editable in one click.

### XT-CMP-003 — Main Authoring Pane

- **kind:** composer_region_class
- **slug:** `main-authoring-pane`
- **parent_id:** XT-LAY-002
- **maturity:** core
- **ui_visibility_hint:** always_available
- **summary:** Primary authoring region where entry content blocks live.
- **purpose:** Hosts the body-first or structured-first editing experience depending on context.
- **representative_examples:** body editor; block stack; template fields
- **depends_on:** XT-LAY-002
- **implementation_notes:**
  - The main pane must support mixed modalities.

### XT-CMP-004 — Support Drawer

- **kind:** composer_region_class
- **slug:** `support-drawer`
- **parent_id:** XT-LAY-002
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Expandable region for sources, citations, evidence, and support relations.
- **purpose:** Keeps support first-class without overwhelming lightweight capture.
- **representative_examples:** source tray; evidence drawer
- **depends_on:** XT-OBJ-004
- **implementation_notes:**
  - Should open by default in evidentiary contexts.

### XT-CMP-005 — Workflow / Privacy Drawer

- **kind:** composer_region_class
- **slug:** `workflow-privacy-drawer`
- **parent_id:** XT-LAY-002
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Expandable region for workflow state, audience, publication, and review actions.
- **purpose:** Exposes governance without forcing every user into governance work immediately.
- **representative_examples:** visibility controls; review actions; publish actions
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Must show state clearly before any state-changing action.

### XT-CMP-006 — Metadata / Provenance Drawer

- **kind:** composer_region_class
- **slug:** `metadata-provenance-drawer`
- **parent_id:** XT-LAY-002
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Expandable region for capture facts, transformations, and technical details.
- **purpose:** Makes provenance inspectable without bloating the main authoring pane.
- **representative_examples:** capture metadata; transformation log
- **depends_on:** XT-LAY-004, XT-LAY-005
- **implementation_notes:**
  - Should clearly distinguish raw capture from computed content.

### XT-CMP-007 — Relationship Tray

- **kind:** composer_region_class
- **slug:** `relationship-tray`
- **parent_id:** XT-LAY-002
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Expandable region for reply, support, contradiction, supersession, and other relations.
- **purpose:** Lets users express record graph structure without entering a dedicated graph editor.
- **representative_examples:** reply relation; support relation; supersedes relation
- **depends_on:** XT-OBJ-003
- **implementation_notes:**
  - Needs human-language labels and sensible defaults.

### XT-CMP-008 — Save / Status Rail

- **kind:** composer_region_class
- **slug:** `save-status-rail`
- **parent_id:** XT-LAY-002
- **maturity:** core
- **ui_visibility_hint:** always_available
- **summary:** Persistent region showing draft state, unsaved changes, and meaningful record state.
- **purpose:** Provides confidence that lightweight capture is safe and deeper work is not lost.
- **representative_examples:** saved draft; unsaved changes; reviewed
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Must work consistently across all surfaces.

## View and Lens Classes

### XT-VIW-001 — List View

- **kind:** view_lens_class
- **slug:** `list-view`
- **parent_id:** XT-OBJ-009
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Dense sequential view of records or targets.
- **purpose:** Supports quick scanning, filtering, batching, and memory retrieval.
- **representative_examples:** feed; search results; collection list
- **depends_on:** XT-OBJ-009
- **implementation_notes:**
  - A universal fallback view.

### XT-VIW-002 — Card / Detail View

- **kind:** view_lens_class
- **slug:** `card-detail-view`
- **parent_id:** XT-OBJ-009
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Focused view showing one item as a meaningful record card or detail page.
- **purpose:** Provides the main reading unit across workbench and public read surfaces.
- **representative_examples:** entry detail; target detail
- **depends_on:** XT-OBJ-009
- **implementation_notes:**
  - Must expose target, intent, support, and governance clearly.

### XT-VIW-003 — Board View

- **kind:** view_lens_class
- **slug:** `board-view`
- **parent_id:** XT-OBJ-009
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Spatial or columnar arrangement for grouped workflow or curation states.
- **purpose:** Supports moderation, triage, classroom review, and manual organization.
- **representative_examples:** workflow board; topic board
- **depends_on:** XT-OBJ-009
- **implementation_notes:**
  - Best when status or grouping is central.

### XT-VIW-004 — Timeline View

- **kind:** view_lens_class
- **slug:** `timeline-view`
- **parent_id:** XT-OBJ-009
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Chronological view of events, records, or revisions.
- **purpose:** Supports event reconstruction, field logs, publication history, and memory review.
- **representative_examples:** activity timeline; route timeline; claim history
- **depends_on:** XT-TGT-003
- **implementation_notes:**
  - Should handle both record time and target time gracefully.

### XT-VIW-005 — Map View

- **kind:** view_lens_class
- **slug:** `map-view`
- **parent_id:** XT-OBJ-009
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Spatial view of targets, observations, routes, and overlays.
- **purpose:** Supports fieldwork, civic memory, object/place work, and spatial public layers.
- **representative_examples:** site map; route map; layer map
- **depends_on:** XT-TGT-002
- **implementation_notes:**
  - Needs density and layer controls.

### XT-VIW-006 — Graph View

- **kind:** view_lens_class
- **slug:** `graph-view`
- **parent_id:** XT-OBJ-009
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Relational view emphasizing links among records, targets, sources, and claims.
- **purpose:** Supports deeper exploration without making graph interaction mandatory everywhere.
- **representative_examples:** claim graph; target graph
- **depends_on:** XT-OBJ-003
- **implementation_notes:**
  - A specialized but important view.

### XT-VIW-007 — Queue View

- **kind:** view_lens_class
- **slug:** `queue-view`
- **parent_id:** XT-OBJ-009
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Task- and workflow-oriented view optimized for review and processing.
- **purpose:** Supports moderation, approvals, classroom feedback, and operational routing.
- **representative_examples:** review queue; moderation queue
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Queue rows should surface trust and workflow state.

### XT-VIW-008 — Compare View

- **kind:** view_lens_class
- **slug:** `compare-view`
- **parent_id:** XT-OBJ-009
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Side-by-side or diff-like view for examining multiple records together.
- **purpose:** Supports review, correction, contradiction, duplicate handling, and evidence comparison.
- **representative_examples:** before/after; claim vs support; duplicate compare
- **depends_on:** XT-OBJ-003
- **implementation_notes:**
  - Particularly useful in review-heavy modes.

### XT-VIW-009 — Gallery View

- **kind:** view_lens_class
- **slug:** `gallery-view`
- **parent_id:** XT-OBJ-009
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Visual-heavy view for browsing media-rich records.
- **purpose:** Supports field capture, object memory, public dossiers, and media-driven exploration.
- **representative_examples:** photo gallery; screenshot wall
- **depends_on:** —
- **implementation_notes:**
  - Should still preserve trust and provenance cues.

### XT-VIW-010 — Dossier View

- **kind:** view_lens_class
- **slug:** `dossier-view`
- **parent_id:** XT-OBJ-009
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Narrative or packet-like assembled view for curated record bundles.
- **purpose:** Supports case files, evidence packets, publishable collections, and classroom bundles.
- **representative_examples:** case dossier; evidence packet; public bundle
- **depends_on:** —
- **implementation_notes:**
  - Mixes narrative ordering with evidence structure.

## Domain Pack Classes

### XT-DPK-001 — Personal Memory Pack

- **kind:** domain_pack_class
- **slug:** `personal-memory-pack`
- **parent_id:** XT-TAX-005
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Domain pack optimized for personal recall, contextual bookmarking, and lightweight retention.
- **purpose:** Makes XtraType feel like a provenance-aware second memory layer.
- **representative_examples:** remember this page; save this place; future me note
- **depends_on:** XT-TAX-005
- **implementation_notes:**
  - Domain packs specialize feel, defaults, templates, and views without replacing the core grammar.

### XT-DPK-002 — Research Notebook Pack

- **kind:** domain_pack_class
- **slug:** `research-notebook-pack`
- **parent_id:** XT-TAX-005
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Domain pack optimized for source-backed reading, claims, citations, and evidence chains.
- **purpose:** Turns the system into a structured research and synthesis environment.
- **representative_examples:** claim + sources; reading notes; citation record
- **depends_on:** XT-TAX-005
- **implementation_notes:**
  - Domain packs specialize feel, defaults, templates, and views without replacing the core grammar.

### XT-DPK-003 — Field Observation Pack

- **kind:** domain_pack_class
- **slug:** `field-observation-pack`
- **parent_id:** XT-TAX-005
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Domain pack optimized for geospatial notes, measurements, media, and route-aware capture.
- **purpose:** Makes the mobile and map-heavy system feel native to fieldwork.
- **representative_examples:** site observation; route note; inspection log
- **depends_on:** XT-TAX-005
- **implementation_notes:**
  - Domain packs specialize feel, defaults, templates, and views without replacing the core grammar.

### XT-DPK-004 — Fact-Check and Claim Review Pack

- **kind:** domain_pack_class
- **slug:** `fact-check-and-claim-review-pack`
- **parent_id:** XT-TAX-005
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Domain pack optimized for assertions, support, contradiction, and verification workflows.
- **purpose:** Supports claim review, public trust display, and corrective lineage.
- **representative_examples:** claim review; support packet; correction trace
- **depends_on:** XT-TAX-005
- **implementation_notes:**
  - Domain packs specialize feel, defaults, templates, and views without replacing the core grammar.

### XT-DPK-005 — Public Annotation and Publishing Pack

- **kind:** domain_pack_class
- **slug:** `public-annotation-and-publishing-pack`
- **parent_id:** XT-TAX-005
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Domain pack optimized for public read, shareable records, overlays, and publication state.
- **purpose:** Lets XtraType function as a contextual publishing layer.
- **representative_examples:** public record; publish overlay; public collection
- **depends_on:** XT-TAX-005
- **implementation_notes:**
  - Domain packs specialize feel, defaults, templates, and views without replacing the core grammar.

### XT-DPK-006 — Team Review and Moderation Pack

- **kind:** domain_pack_class
- **slug:** `team-review-and-moderation-pack`
- **parent_id:** XT-TAX-005
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Domain pack optimized for queues, assignments, moderation states, and reviewer actions.
- **purpose:** Supports operations-heavy collaborative workflows.
- **representative_examples:** review queue; moderation board; approval flow
- **depends_on:** XT-TAX-005
- **implementation_notes:**
  - Domain packs specialize feel, defaults, templates, and views without replacing the core grammar.

### XT-DPK-007 — Civic Place Memory Pack

- **kind:** domain_pack_class
- **slug:** `civic-place-memory-pack`
- **parent_id:** XT-TAX-005
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Domain pack optimized for public or community place-based memory and layered local context.
- **purpose:** Supports events, histories, observations, and public place layers.
- **representative_examples:** place history; local issue; site memory
- **depends_on:** XT-TAX-005
- **implementation_notes:**
  - Domain packs specialize feel, defaults, templates, and views without replacing the core grammar.

### XT-DPK-008 — Classroom and Seminar Pack

- **kind:** domain_pack_class
- **slug:** `classroom-and-seminar-pack`
- **parent_id:** XT-TAX-005
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Domain pack optimized for guided evidence work, collaborative reading, and feedback.
- **purpose:** Turns XtraType into a structured learning and seminar environment.
- **representative_examples:** seminar note; evidence assignment; discussion review
- **depends_on:** XT-TAX-005
- **implementation_notes:**
  - Domain packs specialize feel, defaults, templates, and views without replacing the core grammar.

### XT-DPK-009 — Schema Commons Pack

- **kind:** domain_pack_class
- **slug:** `schema-commons-pack`
- **parent_id:** XT-TAX-005
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Domain pack optimized for templates, vocabularies, proposals, and controlled growth.
- **purpose:** Makes type evolution and template stewardship an explicit working mode.
- **representative_examples:** template proposal; vocabulary review; pack management
- **depends_on:** XT-TAX-005
- **implementation_notes:**
  - Domain packs specialize feel, defaults, templates, and views without replacing the core grammar.

### XT-DPK-010 — Real-Time Evidence Room Pack

- **kind:** domain_pack_class
- **slug:** `real-time-evidence-room-pack`
- **parent_id:** XT-TAX-005
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Domain pack optimized for synchronous collaboration around cases, claims, or target sets.
- **purpose:** Supports live review, presence, and coordinated evidence handling.
- **representative_examples:** live room; shared review session; co-analysis
- **depends_on:** XT-TAX-005
- **implementation_notes:**
  - Domain packs specialize feel, defaults, templates, and views without replacing the core grammar.

### XT-DPK-011 — Object Memory Pack

- **kind:** domain_pack_class
- **slug:** `object-memory-pack`
- **parent_id:** XT-TAX-005
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Domain pack optimized for scan-based revisiting of physical items and their histories.
- **purpose:** Supports maintenance, inspection, artifact memory, and place-object linkage.
- **representative_examples:** scan item history; maintenance note; object dossier
- **depends_on:** XT-TAX-005
- **implementation_notes:**
  - Domain packs specialize feel, defaults, templates, and views without replacing the core grammar.

### XT-DPK-012 — Ghost Layer Pack

- **kind:** domain_pack_class
- **slug:** `ghost-layer-pack`
- **parent_id:** XT-TAX-005
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Domain pack optimized for overlaying records on pages, places, and objects without leaving context.
- **purpose:** Makes XtraType feel like a living contextual layer over existing environments.
- **representative_examples:** page overlay; place overlay; object overlay
- **depends_on:** XT-TAX-005
- **implementation_notes:**
  - Domain packs specialize feel, defaults, templates, and views without replacing the core grammar.

### XT-DPK-013 — Voice-First Pack

- **kind:** domain_pack_class
- **slug:** `voice-first-pack`
- **parent_id:** XT-TAX-005
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Domain pack optimized for spoken capture, route-aware memory, and roaming observation.
- **purpose:** Supports low-friction capture while preserving place, time, and trust context.
- **representative_examples:** spoken memory note; roaming observation
- **depends_on:** XT-TAX-005
- **implementation_notes:**
  - Domain packs specialize feel, defaults, templates, and views without replacing the core grammar.

### XT-DPK-014 — AR Spatial Pack

- **kind:** domain_pack_class
- **slug:** `ar-spatial-pack`
- **parent_id:** XT-TAX-005
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Domain pack optimized for spatially anchored contextual records in augmented reality.
- **purpose:** Supports future place-layer and object-layer experiences.
- **representative_examples:** anchored marker; spatial overlay; AR note
- **depends_on:** XT-TAX-005
- **implementation_notes:**
  - Domain packs specialize feel, defaults, templates, and views without replacing the core grammar.

### XT-DPK-015 — Argument Operating System Pack

- **kind:** domain_pack_class
- **slug:** `argument-operating-system-pack`
- **parent_id:** XT-TAX-005
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Domain pack optimized for claims, supports, contradictions, and interpretive structure.
- **purpose:** Turns XtraType into a rigorous argument and reasoning environment when desired.
- **representative_examples:** argument map; support chain; debate graph
- **depends_on:** XT-TAX-005
- **implementation_notes:**
  - Domain packs specialize feel, defaults, templates, and views without replacing the core grammar.

### XT-DPK-016 — Reality Layer Pack

- **kind:** domain_pack_class
- **slug:** `reality-layer-pack`
- **parent_id:** XT-TAX-005
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Domain pack optimized for large-scale layered context spanning pages, places, events, claims, and objects.
- **purpose:** Represents the broadest sanctioned interpretation of XtraType as a contextual layer over the web and the world.
- **representative_examples:** place + claim layer; public context layer; reality map
- **depends_on:** XT-TAX-005
- **implementation_notes:**
  - Domain packs specialize feel, defaults, templates, and views without replacing the core grammar.

## Suggestion and Automation Classes

### XT-AUT-001 — Intent Suggestion

- **kind:** suggestion_automation_class
- **slug:** `intent-suggestion`
- **parent_id:** XT-LAY-005
- **maturity:** recommended
- **ui_visibility_hint:** derived_or_internal
- **summary:** Suggestion proposing the likely purpose of the current record.
- **purpose:** Speeds capture while preserving one-click override of the most important UI switchboard.
- **representative_examples:** looks like observation; likely citation
- **depends_on:** XT-LAY-003, XT-LAY-005
- **implementation_notes:**
  - Suggestions must say why they appeared.

### XT-AUT-002 — Target Suggestion

- **kind:** suggestion_automation_class
- **slug:** `target-suggestion`
- **parent_id:** XT-LAY-005
- **maturity:** recommended
- **ui_visibility_hint:** derived_or_internal
- **summary:** Suggestion proposing the best target identity or target refinement.
- **purpose:** Helps resolve imported, scanned, selected, or ambiguous context into a usable target.
- **representative_examples:** possible page target; matching object target; resolved entity
- **depends_on:** XT-LAY-001
- **implementation_notes:**
  - Must remain editable and rejectable.

### XT-AUT-003 — Support / Evidence Suggestion

- **kind:** suggestion_automation_class
- **slug:** `support-evidence-suggestion`
- **parent_id:** XT-LAY-005
- **maturity:** recommended
- **ui_visibility_hint:** derived_or_internal
- **summary:** Suggestion proposing sources, excerpts, or evidence blocks that likely belong with the current record.
- **purpose:** Makes evidentiary work faster without hiding source boundaries.
- **representative_examples:** attach selected quote; use uploaded image as evidence
- **depends_on:** XT-OBJ-004
- **implementation_notes:**
  - Support suggestions should open the support drawer, not silently attach.

### XT-AUT-004 — Template Suggestion

- **kind:** suggestion_automation_class
- **slug:** `template-suggestion`
- **parent_id:** XT-LAY-005
- **maturity:** recommended
- **ui_visibility_hint:** derived_or_internal
- **summary:** Suggestion proposing a template, pack default, or field layout.
- **purpose:** Lets the composer adapt intelligently without turning into a hidden rules engine.
- **representative_examples:** switch to field-note template; use claim-review template
- **depends_on:** XT-TAX-004
- **implementation_notes:**
  - Template suggestions should be obvious and reversible.

### XT-AUT-005 — Taxonomy Suggestion

- **kind:** suggestion_automation_class
- **slug:** `taxonomy-suggestion`
- **parent_id:** XT-LAY-005
- **maturity:** advanced
- **ui_visibility_hint:** derived_or_internal
- **summary:** Suggestion proposing a new field, label, branch, or shared structure.
- **purpose:** Supports controlled growth from local friction points.
- **representative_examples:** create new type; add new field; propose label
- **depends_on:** XT-TAX-006
- **implementation_notes:**
  - Local suggestion and global promotion must remain distinct.

### XT-AUT-006 — Privacy / Audience Suggestion

- **kind:** suggestion_automation_class
- **slug:** `privacy-audience-suggestion`
- **parent_id:** XT-LAY-005
- **maturity:** recommended
- **ui_visibility_hint:** derived_or_internal
- **summary:** Suggestion proposing a likely audience posture or publication boundary.
- **purpose:** Helps prevent accidental oversharing while speeding routine behavior.
- **representative_examples:** keep private; workspace only; ready to publish
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Privacy suggestions should always be conservative and explicit.

### XT-AUT-007 — Workflow Routing Suggestion

- **kind:** suggestion_automation_class
- **slug:** `workflow-routing-suggestion`
- **parent_id:** XT-LAY-005
- **maturity:** advanced
- **ui_visibility_hint:** derived_or_internal
- **summary:** Suggestion proposing a next review, queue, or moderation action.
- **purpose:** Supports operational efficiency in reviewer- and team-heavy modes.
- **representative_examples:** send to review; assign to queue; mark for moderation
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Must never silently perform high-stakes state changes.

### XT-AUT-008 — Automation Boundary

- **kind:** suggestion_automation_class
- **slug:** `automation-boundary`
- **parent_id:** XT-LAY-005
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Explicit frontend rule describing what the system may suggest, prefill, stage, or auto-apply.
- **purpose:** Prevents unwanted automation and preserves user trust in a highly adaptive interface.
- **representative_examples:** suggest only; prefill; auto-save draft
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Automation must be explainable, reversible, and not quietly state-changing.

## Role and Stewardship Classes

### XT-ROL-001 — Contributor Role

- **kind:** role_stewardship_class
- **slug:** `contributor-role`
- **parent_id:** XT-OBJ-006
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Primary role for people creating and editing records.
- **purpose:** Anchors the everyday authoring experience across solo and collaborative modes.
- **representative_examples:** author; note taker; observer
- **depends_on:** XT-OBJ-006
- **implementation_notes:**
  - The baseline user-facing role.

### XT-ROL-002 — Reviewer Role

- **kind:** role_stewardship_class
- **slug:** `reviewer-role`
- **parent_id:** XT-OBJ-006
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Role centered on checking records, support, and trust semantics.
- **purpose:** Supports research, moderation, classroom, and publication workflows.
- **representative_examples:** reviewer; checker
- **depends_on:** XT-OBJ-006, XT-LAY-005
- **implementation_notes:**
  - Reviewer affordances should be visible but not universal.

### XT-ROL-003 — Moderator Role

- **kind:** role_stewardship_class
- **slug:** `moderator-role`
- **parent_id:** XT-OBJ-006
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Role centered on managing disputes, restrictions, and policy-sensitive states.
- **purpose:** Supports public layers, team governance, and high-trust environments.
- **representative_examples:** moderator; policy reviewer
- **depends_on:** XT-OBJ-006, XT-LAY-005
- **implementation_notes:**
  - Moderation visibility should remain explicit.

### XT-ROL-004 — Publisher Role

- **kind:** role_stewardship_class
- **slug:** `publisher-role`
- **parent_id:** XT-OBJ-006
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Role centered on public presentation, bundling, and publication transitions.
- **purpose:** Supports public read, overlay publication, and public collection management.
- **representative_examples:** publisher; editorial publisher
- **depends_on:** XT-OBJ-006, XT-LAY-005
- **implementation_notes:**
  - Useful where publication is distinct from authorship.

### XT-ROL-005 — Workspace Steward Role

- **kind:** role_stewardship_class
- **slug:** `workspace-steward-role`
- **parent_id:** XT-OBJ-006
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Role centered on maintaining order inside a workspace or team context.
- **purpose:** Supports shared defaults, template curation, and visibility hygiene.
- **representative_examples:** workspace steward; team maintainer
- **depends_on:** XT-OBJ-006, XT-LAY-005
- **implementation_notes:**
  - A visible UI role for growth without chaos.

### XT-ROL-006 — Domain Curator Role

- **kind:** role_stewardship_class
- **slug:** `domain-curator-role`
- **parent_id:** XT-OBJ-006
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Role centered on managing pack-level templates, vocabularies, and domain semantics.
- **purpose:** Supports controlled specialization across many packs.
- **representative_examples:** research curator; field pack curator
- **depends_on:** XT-OBJ-006, XT-TAX-005
- **implementation_notes:**
  - Distinct from backend system admin.

### XT-ROL-007 — System Steward Role

- **kind:** role_stewardship_class
- **slug:** `system-steward-role`
- **parent_id:** XT-OBJ-006
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Role centered on the shared canonical grammar and system-level structures.
- **purpose:** Supports promotion, deprecation, and consistency across the whole frontend universe.
- **representative_examples:** system steward; schema steward
- **depends_on:** XT-OBJ-006, XT-TAX-001
- **implementation_notes:**
  - Visible mainly in schema commons and governance-heavy surfaces.

## Settings and Personalization Classes

### XT-SET-001 — User Defaults

- **kind:** settings_personalization_class
- **slug:** `user-defaults`
- **parent_id:** XT-LAY-005
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Persistent frontend preferences applied at the personal level.
- **purpose:** Lets users tune capture behavior, disclosure, and routine defaults without changing shared semantics.
- **representative_examples:** default privacy; default pack; default lens
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - User defaults are the most important personalization surface.

### XT-SET-002 — Capture-Context Settings

- **kind:** settings_personalization_class
- **slug:** `capture-context-settings`
- **parent_id:** XT-LAY-005
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Settings scoped to where a flow starts.
- **purpose:** Lets browser, mobile, voice, scan, and import surfaces feel appropriate without one giant settings page.
- **representative_examples:** browser capture defaults; mobile capture defaults
- **depends_on:** XT-LAY-004
- **implementation_notes:**
  - Capture-context settings should be discoverable in place.

### XT-SET-003 — Domain-Pack Settings

- **kind:** settings_personalization_class
- **slug:** `domain-pack-settings`
- **parent_id:** XT-LAY-005
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Settings scoped to a pack or working mode.
- **purpose:** Lets research, field, classroom, and public modes maintain different defaults and emphases.
- **representative_examples:** research defaults; field defaults
- **depends_on:** XT-TAX-005
- **implementation_notes:**
  - Domain settings tune feel without changing base semantics.

### XT-SET-004 — Template Settings

- **kind:** settings_personalization_class
- **slug:** `template-settings`
- **parent_id:** XT-LAY-005
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Settings embedded in or attached to templates.
- **purpose:** Let templates control disclosure, required blocks, and suggested behaviors.
- **representative_examples:** required evidence; open support drawer
- **depends_on:** XT-TAX-004
- **implementation_notes:**
  - Template settings should remain visible during authoring.

### XT-SET-005 — Automation Settings

- **kind:** settings_personalization_class
- **slug:** `automation-settings`
- **parent_id:** XT-LAY-005
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Settings governing suggestion intensity and auto-apply boundaries.
- **purpose:** Let users control proactivity without disabling useful assistance entirely.
- **representative_examples:** suggest only; auto-save draft; low automation
- **depends_on:** —
- **implementation_notes:**
  - Automation settings must be granular and clearly explained.

### XT-SET-006 — Accessibility and Display Settings

- **kind:** settings_personalization_class
- **slug:** `accessibility-display-settings`
- **parent_id:** XT-LAY-005
- **maturity:** core
- **ui_visibility_hint:** context_driven
- **summary:** Settings governing readability, density, motion, contrast, and assistive behavior.
- **purpose:** Ensures the expanded XtraType universe remains usable across devices and needs.
- **representative_examples:** high contrast; reduced motion; compact density
- **depends_on:** —
- **implementation_notes:**
  - Accessibility is a first-class frontend concern.

## Public Presentation Classes

### XT-PUB-001 — Public Record Presentation

- **kind:** public_presentation_class
- **slug:** `public-record-presentation`
- **parent_id:** XT-SFC-008
- **maturity:** recommended
- **ui_visibility_hint:** context_driven
- **summary:** Public-facing presentation of a single record.
- **purpose:** Turns an authored record into a durable, readable, trust-aware public page.
- **representative_examples:** record permalink; public claim page
- **depends_on:** XT-SFC-008
- **implementation_notes:**
  - Public view must expose provenance and revision cues.

### XT-PUB-002 — Public Collection Presentation

- **kind:** public_presentation_class
- **slug:** `public-collection-presentation`
- **parent_id:** XT-SFC-008
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Public-facing presentation of a curated set of records or targets.
- **purpose:** Supports published notebooks, dossiers, evidence bundles, and place layers.
- **representative_examples:** public collection; public dossier
- **depends_on:** XT-SFC-008
- **implementation_notes:**
  - Collection narrative and trust structure both matter.

### XT-PUB-003 — Overlay Presentation

- **kind:** public_presentation_class
- **slug:** `overlay-presentation`
- **parent_id:** XT-SFC-008
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Contextual presentation layered on top of an existing page, place, or object.
- **purpose:** Makes XtraType visible without forcing full navigation away from the underlying target.
- **representative_examples:** page overlay; map overlay; AR overlay
- **depends_on:** XT-SFC-012
- **implementation_notes:**
  - Overlay density and legibility must be carefully controlled.

### XT-PUB-004 — Embeddable Card Presentation

- **kind:** public_presentation_class
- **slug:** `embeddable-card-presentation`
- **parent_id:** XT-SFC-008
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Compact public presentation intended for embedding elsewhere.
- **purpose:** Lets records and collections travel while preserving a minimum trust and provenance frame.
- **representative_examples:** embedded claim card; embedded evidence card
- **depends_on:** XT-SFC-008
- **implementation_notes:**
  - Must remain attributable and traceable back to canonical views.

### XT-PUB-005 — Public Map / Timeline Presentation

- **kind:** public_presentation_class
- **slug:** `public-map-timeline-presentation`
- **parent_id:** XT-SFC-008
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Public-facing spatial or chronological presentation of contextual layers.
- **purpose:** Supports civic memory, route stories, event reconstructions, and reality-layer views.
- **representative_examples:** public place map; public event timeline
- **depends_on:** XT-SFC-008
- **implementation_notes:**
  - Needs strong filtering and context explanations.

### XT-PUB-006 — Public Revision / History Presentation

- **kind:** public_presentation_class
- **slug:** `public-revision-history-presentation`
- **parent_id:** XT-SFC-008
- **maturity:** advanced
- **ui_visibility_hint:** context_driven
- **summary:** Presentation focused on visible change over time.
- **purpose:** Supports trust by showing corrections, supersessions, publication events, and major review milestones.
- **representative_examples:** revision history; correction trace; publication log
- **depends_on:** XT-LAY-005
- **implementation_notes:**
  - Crucial for public trust-sensitive content.
