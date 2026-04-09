# XtraType Frontend Foundation and Product Grammar

> The canonical grammar the XtraType frontend must preserve across every surface and mode.

| Document status | Finalized and authoritative frontend specification |
| --- | --- |
| System | XtraType |
| Scope | Frontend product architecture, interface behavior, interaction rules, view systems, templates, and governance UX |
| Backend boundary | All authorization, persistence, and server-side operations are assumed to be handled behind a single API-key-backed service boundary; this document set does not define backend architecture |
| Canonical stance | Capture-first entry points + adaptive composer shell + progressive disclosure + target-centric workbench + domain-pack extensibility |


## 1. Core frontend contract

The XtraType frontend exists to make a structured meaning system usable. It does not flatten the model into a generic note app, and it does not expose raw ontology language in a way that burdens the user. Its job is translation: preserve the real semantic distinctions while presenting them as clear, humane interfaces.

The frontend contract is built on five layers:

| Layer | Meaning in XtraType | Frontend responsibility |
| --- | --- | --- |
| Target | The thing being addressed. | Make the target visible, stable, switchable, inspectable, and navigable. |
| Entry | The thing being authored. | Provide a universal authoring shell that supports many entry classes without semantic confusion. |
| Intent | Why the entry exists. | Drive the surface, field defaults, validation cues, and workflow options. |
| Context | The situation of capture and use. | Adapt the UI by surface, domain, environment, and privacy posture. |
| Governance | Workflow, trust, privacy, moderation, publication, and auditability. | Expose rigor explicitly without turning all authoring into governance work. |

## 2. Object families as frontend primitives

The centralized inventory defines object families that should map directly into interface primitives.

| Object family | Frontend expression |
| --- | --- |
| Target family | Target chips, target cards, target headers, target breadcrumbs, target graphs, target inspectors |
| Entry family | Entry cards, entry detail views, entry editors, entry threads, entry comparison surfaces |
| Relationship family | Link badges, relation lines, graph views, relation panels, support/contradiction inspectors |
| Source family | Source cards, source libraries, evidence trays, citation forms, support chains |
| Context record family | Capture badges, environmental detail rows, provenance drawers, origin chips |
| Identity and authorship family | Author chips, identity modes, pseudonym states, role-aware attribution display |
| Workflow and moderation family | Status rails, queue chips, reviewer strips, moderation actions, audit feeds |
| Permissions and audience family | Visibility pills, audience selectors, scope indicators, access explanations |
| Taxonomy and schema family | Type selectors, vocabulary fields, template pickers, domain-pack managers |
| Provenance and trust family | Confidence badges, verification markers, dispute labels, integrity inspectors |

## 3. Target grammar

The frontend must support the following target classes as first-class concepts:

| Target class | Typical examples | Core frontend needs |
| --- | --- | --- |
| Digital resource target | URL, file, message, page, API record | canonical target card, address metadata, quote anchoring, snapshot context |
| Spatial / geographic target | point, area, route, geofence | map view, radius/path controls, place cards, movement-aware capture |
| Temporal target | timestamp, span, recurring window | timeline rendering, time chips, scrubbers, offset-aware relationships |
| Named entity target | person, org, product, topic, project | entity cards, aliases, identity resolution display, cross-target views |
| Abstract / logical target | claim, issue, policy, requirement, decision | structured claim cards, support/dispute surfaces, argument or workflow views |
| Composite target | URL + quote, place + event window, object + route + condition | layered target summaries, re-anchoring UI, composite breadcrumbs |

### Target rules

- Every entry must attach to a target, even if the target is newly created in the flow.
- Composite targets are valid first-class frontend targets, not temporary hacks.
- A target summary must be visible anywhere an entry is edited or reviewed.
- Target identity must remain stable when the user moves from capture to workbench.
- A target can accumulate many entry classes and many views without collapsing them into one mixed feed.

## 4. Entry grammar

The frontend must treat entry classes as genuinely different authoring forms that share one shell.

| Entry class | What it is for | Required frontend support |
| --- | --- | --- |
| Annotation entry | local commentary on a target | body-first editor, quote/selection context, lightweight save |
| Citation entry | source-aware attribution | source picker, bibliographic fields, quote blocks, relation semantics |
| Evidence entry | support artifact or proof record | evidence type selector, support relation, integrity/provenance display |
| Classification entry | labeling, categorization, filing | fast chips, controlled vocabularies, batch use in collections |
| Social / conversational entry | reply, question, response, discussion | thread context, reply affordances, conversational display |
| Workflow entry | action that moves work through a process | status controls, routing, queue visibility, assignment display |
| Collection / curation entry | grouping or ordering move | collection membership UI, ordering controls, view relevance |
| Media entry | image, audio, video, clip, mixed media | media blocks, preview, metadata, transcription or OCR surfaces |
| Assertion entry | claim or statement intended to stand on its own | claim-focused editor, support/dispute panels, confidence and verification display |

### Entry rules

- Users do not need to think in inventory terms, but the interface must.
- Entry classes may share blocks, but they must not become semantically indistinguishable.
- An entry can evolve from a lightweight quick capture into a more rigorous class or hybrid form.
- Entry detail views must display what kind of record the entry is in plain language.

## 5. Intent grammar

Intent is not decoration. It is the main UI switchboard.

| Intent category | User-facing translation |
| --- | --- |
| Informational | I am recording or explaining something |
| Evaluative | I am assessing or judging something |
| Evidentiary | I am supporting, citing, or documenting something |
| Conversational | I am replying, asking, or discussing |
| Organizational | I am filing, grouping, or saving something |
| Operational | I am moving something through work |
| Observational | I am reporting what I saw, measured, or encountered |
| Referential | I am linking, pointing, or anchoring |
| Corrective | I am correcting, disputing, or amending |
| Personal / mnemonic | I am saving this for myself |

### Intent rules

- Intent may be selected, suggested, or inferred.
- Intent should almost always be editable in one click.
- Intent drives which drawer opens by default and which fields become prominent.
- The same entry class may support several intents; the frontend should not hard-code one-to-one assumptions.

## 6. Content modalities

Entries may be made from one or several modalities at once.

| Modality | Frontend meaning |
| --- | --- |
| Textual | typed body text, notes, quote blocks, summaries |
| Media | images, video, audio, clips, screenshots |
| Structured | forms, measurements, taxonomic fields, matrices |
| External reference | links, imported records, bibliographic handles, external IDs |
| Generated / computed | OCR, transcripts, geocodes, AI-assisted drafts, extracted facts |

### Modality rules

- Mixed-modality entries are normal.
- Generated/computed content must never masquerade as user-authored content.
- The frontend must preserve modality provenance at the block level where possible.

## 7. Context grammar

The frontend must honor four context layers:

| Context class | Frontend role |
| --- | --- |
| Capture context | adapts the entry surface based on where the record began |
| Domain context | tunes terminology, templates, views, and affordances |
| Environmental context | exposes time, movement, device, and environmental facts |
| Privacy context | shapes visibility cues, warnings, and publication affordances |

## 8. Relationships

Relationships are first-class product structures.

| Relationship class | Frontend use |
| --- | --- |
| Entry-to-target | attachment and address semantics |
| Entry-to-entry | reply, amendment, contradiction, support, duplicate, supersession |
| Target-to-target | aliasing, containment, equivalence, part-of, related-to |
| Source-to-claim | support, contradiction, attribution, derivation, translation |

### Relationship rules

- Relationship meaning should be visible in human language.
- Graphs are not the only display; list, thread, chain, diff, and compare surfaces must also reveal relationships.
- The frontend must support relationship creation without forcing a graph editor.

## 9. Governance and trust grammar

The frontend must render governance layers as explicit, inspectable dimensions:

- draft state
- review state
- moderation state
- resolution state
- publication state
- visibility class
- permission scope and inheritance
- creation provenance
- technical capture metadata
- integrity metadata
- confidence class
- verification class
- dispute class
- quality class

### Governance rules

- Governance is additive to authoring.
- Governance states must be visible when they matter, collapsible when they do not.
- Important state transitions should always read as actions, not as passive decoration.
- Trust semantics must not be implied only by polish, completeness, or popularity.

## 10. Universal frontend invariants

The following invariants apply across the entire product:

1. A user can always see what the current record is about.
2. A user can always tell whether a field is captured, inferred, asserted, imported, or reviewed.
3. A user can always save a valid draft.
4. A user can always inspect support and provenance if they need to.
5. A reviewer can always understand the relation between target, entry, support, workflow, and trust.
6. A template can specialize the surface without breaking the core grammar.
7. Different domain packs may change the feel, but not the underlying semantics.
