# XtraType Taxonomy, Automation, Trust, and Governance UX

> The user-facing rules for system growth, suggestion behavior, provenance, privacy, workflow, and trust.

| Document status | Finalized and authoritative frontend specification |
| --- | --- |
| System | XtraType |
| Scope | Frontend product architecture, interface behavior, interaction rules, view systems, templates, and governance UX |
| Backend boundary | All authorization, persistence, and server-side operations are assumed to be handled behind a single API-key-backed service boundary; this document set does not define backend architecture |
| Canonical stance | Capture-first entry points + adaptive composer shell + progressive disclosure + target-centric workbench + domain-pack extensibility |


## 1. Controlled growth is a core frontend feature

XtraType is designed to expand continuously. The frontend must therefore provide sanctioned paths for users to propose new shapes, fields, branches, vocabularies, templates, and domain-specific variations without collapsing into inconsistency.

### Growth ladder

| Level | Meaning | Frontend support |
| --- | --- | --- |
| Local custom shape | one-off structure on one record | add field, add block, local rename, temporary grouping |
| Personal reusable template | user-specific repeatable structure | save template, edit template, set defaults |
| Workspace/domain proposal | shared structure request | proposal form, rationale, preview, steward queue |
| Promoted shared concept | stable shared concept | versioned template, vocabulary publication, dependency display |

## 2. Taxonomy interfaces

The frontend must include the following taxonomy-oriented surfaces:

- type selector
- subtype or domain-type selector
- vocabulary field chips
- schema preview
- template picker
- template fork/clone dialog
- proposal-to-shared dialog
- dependency and impact preview
- stewardship queue
- deprecated/consolidated concept banner

### Taxonomy rules

- User-facing labels must remain plain language even if internal concepts are formal.
- The interface must help the user decide whether they are creating a local variation or a new shared concept.
- Templates and vocabularies should expose “why this exists” and “where this applies.”
- The frontend should warn against near-duplicate concepts before a user proposes a new one.

## 3. Template behavior

Templates are the main way the frontend becomes domain-comfortable without becoming incoherent.

Templates may define:
- default entry class
- default intent
- visible blocks
- hidden or advanced blocks
- required and optional fields
- default views
- preferred collections
- recommended relationships
- suggested sources/evidence types
- review requirements
- default privacy posture
- naming and display conventions

### Template actions

The frontend must support:
- create from blank
- create from existing record
- fork template
- compare templates
- install template
- favorite or pin template
- save current record as personal template
- propose current pattern as shared template

## 4. Suggestion and automation model

Suggestions are part of the frontend experience, not invisible magic.

### Suggestion categories

- target match suggestions
- intent suggestions
- source or evidence suggestions
- relationship suggestions
- vocabulary suggestions
- template suggestions
- privacy or audience suggestions
- workflow routing suggestions
- duplicate or supersession suggestions
- public-title or summary suggestions
- resurfacing suggestions (“you have similar records”)
- view suggestions (“map view may fit this collection”)

### Automation boundaries

The frontend may automatically:
- prefill capture metadata
- prepopulate obvious fields from the capture surface
- suggest likely types, intents, or relations
- remember user layout preferences
- restore recent targets or collections
- stage computed blocks as reviewable suggestions

The frontend may **not** silently:
- publish
- verify
- dispute
- resolve
- supersede
- escalate
- share publicly
- change audience scope
- install shared templates
- change trust status

## 5. Provenance presentation

The frontend must visually distinguish at least five origin states:

| State | Meaning |
| --- | --- |
| Captured | collected directly from the environment or interface |
| Asserted | written or selected intentionally by the user |
| Imported | brought in from an external item or record |
| Inferred / computed | produced by a system process |
| Reviewed / verified | affirmed or modified through explicit workflow |

These states should appear at block level where appropriate and at record level always.

### Provenance surfaces

- provenance drawer
- capture summary chips
- integrity detail rows
- original snapshot preview
- generated-content markers
- diff view for changed computed suggestions
- activity log and record history

## 6. Trust semantics

Trust in XtraType must be inspectable and multidimensional.

### Trust dimensions

| Dimension | Frontend expression |
| --- | --- |
| Confidence | confidence chip, confidence slider, or plain-language confidence text |
| Verification | verified / unverified / partially verified markers |
| Dispute | disputed, challenged, unresolved, superseded ribbons |
| Quality | complete, incomplete, low-quality, needs-source, duplicate, stale indicators |

### Trust rules

- Confidence is not the same as verification.
- A polished record may still be unverified.
- A published record may still be disputed.
- A private record may still carry high confidence.
- Trust states must be available in public reading where relevant, not only internal review.

## 7. Workflow UX

Workflow is a visible process layer. The frontend must support:
- drafting
- review routing
- moderation handling
- verification
- dispute
- resolution
- publication
- supersession
- archival

### Workflow surfaces

- queue view
- board view
- action strip
- review notes panel
- decision history timeline
- compare-before-action desk
- activity feed
- resolution summary card

## 8. Privacy and audience UX

Even with backend enforcement out of scope, the frontend must present privacy clearly.

Possible audience states:
- private to me
- shared with current workspace
- restricted team or group
- review-only
- link-shared
- public
- layer-specific visibility (personal overlay, team overlay, public overlay)

The audience state should always be visible in the composer and in detail views where it matters.

## 9. Roles and stewardship as UI

Although backend authorization is abstracted away, the frontend still needs role-aware affordances:

- contributor
- reviewer
- moderator
- verifier
- workspace steward
- domain curator
- system steward

Role-aware UI may change:
- visible actions
- approval affordances
- proposal routing
- queue visibility
- public publication controls
- template promotion rights
- verification controls

## 10. Settings surfaces

Settings should exist at multiple levels:

| Level | Typical settings |
| --- | --- |
| User | layout density, default pack, suggestion sensitivity, overlay defaults |
| Workspace | audience defaults, review requirements, visible packs, approved templates |
| Domain pack | default terms, default views, required fields, pack-specific suggestions |
| Capture context | auto-open drawers, auto-prefill behavior, save mode, overlay prompts |
| Template | block order, required fields, recommended relations, default trust posture |
| Public layer | what badges, provenance details, and filters appear to readers |

## 11. Auditability and reversibility

The frontend must support:
- change history
- visible supersession
- withdrawn or corrected record banners
- version comparison
- restored prior version preview where available
- activity feed by target, collection, and user
- explicit “why was this suggested?” and “why was this changed?” surfaces

## 12. Growth without chaos

To prevent taxonomy sprawl and UI chaos, the frontend must always ask, explicitly or implicitly:
- Is this a one-off field or a reusable concept?
- Is this a local term or a shared vocabulary item?
- Is this a template or a deeper semantic type?
- Is this a domain-pack specialization or only a stylistic preference?
- Does this proposal create new workflow or trust implications?

Those questions should be embedded into the proposal and template interfaces, not left to unwritten convention.
