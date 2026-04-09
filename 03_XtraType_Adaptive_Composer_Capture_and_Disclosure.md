# XtraType Adaptive Composer, Capture, and Disclosure

> The universal authoring system for every XtraType record, from the lightest capture to the most governed review flow.

| Document status | Finalized and authoritative frontend specification |
| --- | --- |
| System | XtraType |
| Scope | Frontend product architecture, interface behavior, interaction rules, view systems, templates, and governance UX |
| Backend boundary | All authorization, persistence, and server-side operations are assumed to be handled behind a single API-key-backed service boundary; this document set does not define backend architecture |
| Canonical stance | Capture-first entry points + adaptive composer shell + progressive disclosure + target-centric workbench + domain-pack extensibility |


## 1. Composer operating model

The composer is the single universal authoring shell for XtraType. It must accept inputs from every capture surface and every domain pack while keeping the meaning of the record coherent.

The composer is built around four decision axes:

| Axis | User-facing question |
| --- | --- |
| Target axis | What is this about? |
| Intent axis | What are you doing here? |
| Support / evidence axis | What supports or illustrates this? |
| Workflow / privacy axis | Who is this for, and what process posture applies? |

These axes should govern what appears first, what stays collapsed, what is required, and what suggestions the frontend offers.

## 2. Composer anatomy

### Always-visible regions
- **Target bar**: canonical target chip, summary, re-anchor control, target-switch control
- **Intent rail**: primary intent chips, recommended intent, recent intent shortcuts
- **Primary body pane**: text, blocks, media, structured fields, or assertion builder
- **Save/status strip**: current draft state, unsaved changes, current visibility posture, current workflow posture

### Expandable regions
- **Support drawer**: sources, evidence artifacts, quotes, citations, media proof, imported records
- **Relationship drawer**: replies, support links, contradictions, amendments, duplicate/supersession links, target relations
- **Workflow and privacy drawer**: audience, review path, moderation posture, publication controls
- **Metadata and provenance drawer**: capture facts, inferred data, import details, integrity markers
- **Template and taxonomy drawer**: current type, vocabulary fields, custom shape, save-as-template, propose-type actions

## 3. Progressive disclosure model

The composer must reveal rigor in layers rather than all at once.

| Tier | Name | What it contains |
| --- | --- | --- |
| Tier 1 | Quick capture | target confirmation, likely intent, minimal body or artifact, immediate save |
| Tier 2 | Structured enrichment | support blocks, structured fields, relations, classification, metadata cleanup |
| Tier 3 | Governance and trust | visibility, review routing, publication posture, verification/dispute/quality signals |
| Tier 4 | Reuse and system growth | save template, propose vocabulary, branch type, domain-pack shaping |
| Tier 5 | Expert and steward tools | compare, supersede, audit, version, bulk edit, schema review |

### Disclosure rules

- Every record can stop at Tier 1 and still be valid.
- The product may suggest moving upward, but never trap the user there.
- Domain packs may open at higher tiers when rigor is intrinsic to the work.
- Reviewer, moderator, and steward modes may begin with Tier 3 or above already expanded.

## 4. Capture-specific behavior

### Browser capture flow
Default inputs:
- selected text
- current URL
- page title
- page snapshot metadata
- screenshot option
- reading time or timestamp

Recommended quick intents:
- cite
- comment
- save for later
- flag
- classify
- quote
- correct

### Mobile capture flow
Default inputs:
- location or place target
- time and timezone
- movement state
- photo, audio, or video
- nearby object or scanned target
- route segment if applicable

Recommended quick intents:
- observe
- document
- inspect
- note issue
- attach evidence
- create place/event record
- record memory

### Manual drafting flow
Default inputs:
- target search or target creation
- collection context
- template choice
- domain pack
- related existing record suggestions

Recommended quick intents:
- assert
- cite
- build source packet
- classify
- start review item
- create public-ready note
- create case record

### Import/share flow
Default inputs:
- file or link
- clipboard contents
- shared content
- source detection
- metadata extraction

Recommended quick intents:
- save source
- create evidence item
- create citation
- create media entry
- open in full composer
- attach to existing target

### Voice-first flow
Default inputs:
- transcript draft
- timestamps
- route/place association
- confidence markers
- segmented suggestion cards

Recommended quick intents:
- record observation
- journal memory
- log route event
- capture interview note
- draft claim to refine later

### Object scan flow
Default inputs:
- scanned code or detected object
- object target resolution
- location/time
- media proof
- current condition summary

Recommended quick intents:
- note condition
- log maintenance
- flag issue
- verify presence
- attach photo evidence

### AR flow
Default inputs:
- visible place/object target
- spatial anchor
- filtered overlay layer
- local camera scene
- time and position

Recommended quick intents:
- add spatial note
- check existing layer
- attach observation
- compare present vs prior state

## 5. Entry block system

The composer should assemble entries from reusable blocks. Core blocks include:

- body text
- quote block
- citation block
- source card block
- evidence artifact block
- media block
- measurement block
- checklist or rubric block
- label/classification block
- claim block
- correction/amendment block
- relation block
- timeline block
- location block
- witness/account block
- transcript block
- AI suggestion block
- provenance summary block
- audit note block

### Block rules

- Blocks may be added manually or suggested contextually.
- Block provenance must remain visible for machine-generated blocks.
- Templates and domain packs may reorder or preseed blocks.
- A block should be removable without invalidating unrelated parts of the record.

## 6. Suggestion system

Suggestions are a product feature, not a black box.

The frontend may suggest:
- likely intent
- likely target match
- likely evidence type
- likely source relation
- likely privacy posture
- likely workflow routing
- likely template
- likely vocabulary term
- likely public title/summary
- likely duplicate or related record
- likely support or contradiction source
- likely collection placement

### Suggestion disclosure rules

- Every suggestion must be labeled as a suggestion.
- Confidence language must be plain and human-readable.
- The user must be able to accept, reject, or edit the suggestion.
- Important suggestions should explain why they appeared.
- Suggestions must never silently perform publish, verify, moderate, or share actions.

## 7. Save model

The frontend should support several save moments:

| Save state | Meaning |
| --- | --- |
| Draft saved | a valid but incomplete record exists |
| Draft enriched | structure and support have been added |
| Ready for review | the record meets review prerequisites |
| Reviewed / verified / disputed / resolved | governance states applied |
| Published / shared | public or semi-public presentation state |

The save strip should always show the current state without forcing governance decisions too early.

## 8. Conversion and escalation rules

The frontend must support upward and sideways evolution of records:

- note → citation
- note → assertion
- screenshot → evidence entry
- quick observation → governed field report
- saved source → citation or support block
- classification-only save → full record later
- personal mnemonic → public article-like record later
- draft correction → superseding correction chain
- local custom shape → reusable template
- template → workspace/domain proposal

## 9. Settings model

Granular control is part of the product.

Settings should exist at:
- global user level
- domain-pack level
- workspace level
- capture-context level
- template level
- specific suggestion-type level

Users should be able to decide:
- what gets auto-filled
- what gets suggested
- what gets remembered
- what is shown by default
- when the composer opens in minimal vs expanded mode
- whether overlays or ghost layers are enabled
- what trust/provenance details are visible by default

## 10. Non-negotiable composer behaviors

- The composer must never feel like a giant universal form.
- The composer must never obscure what was captured versus what was generated.
- The composer must never require a full taxonomy choice just to save a record.
- The composer must never hide state-changing automation.
- The composer must always make the current target and current record type legible.
