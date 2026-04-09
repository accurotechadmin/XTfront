# XtraType Frontend Implementation Readiness Index

> The authoritative readiness index for turning the full XtraType frontend universe into concrete specifications and buildable interface systems.

| Document status | Finalized and authoritative frontend specification |
| --- | --- |
| System | XtraType |
| Scope | Frontend product architecture, interface behavior, interaction rules, view systems, templates, and governance UX |
| Backend boundary | All authorization, persistence, and server-side operations are assumed to be handled behind a single API-key-backed service boundary; this document set does not define backend architecture |
| Canonical stance | Capture-first entry points + adaptive composer shell + progressive disclosure + target-centric workbench + domain-pack extensibility |


## 1. Purpose

This document defines the frontend artifacts, component families, state boundaries, and API assumptions needed to move from product definition into build planning. It does not assign release versions. It identifies the pieces the frontend must eventually support.

## 2. Frontend application zones

The full application should be thought of as several coordinated zones:

| Zone | Purpose |
| --- | --- |
| Capture zone | quick surfaces for encounter-time entry |
| Composer zone | universal authoring shell |
| Workbench zone | exploration, comparison, organization, and review |
| Public zone | reading, shared layers, and overlays |
| Management zone | templates, vocabularies, packs, settings, saved lenses |
| Frontier zone | live room, object scan, voice, AR, ghost layer |

## 3. Screen inventory

Minimum screen families the frontend architecture should account for:

- home / dashboard
- target page
- collection page
- entry detail page
- source page
- composer full page
- quick composer modal / side sheet
- browser mini-capture
- mobile capture
- import staging surface
- review queue
- moderation board
- compare desk
- graph view
- map view
- timeline view
- gallery view
- live evidence room
- template catalog
- template detail/compare
- vocabulary management
- proposal queue
- settings
- public target page
- public collection page
- object scan sheet
- voice transcript cleanup
- AR overlay sheet
- ghost layer sidebar

## 4. Component inventory

Core component families:

### Identity and addressing
- target chip
- target card
- target header
- breadcrumb chain
- anchor preview
- alias/merge card

### Authoring
- intent chip rail
- block editor
- quote block
- citation block
- evidence block
- source card block
- claim block
- correction block
- media uploader/preview
- location block
- measurement block
- transcript block

### Governance and trust
- visibility pill
- workflow strip
- trust badge set
- provenance chip set
- activity log row
- audit timeline
- dispute ribbon
- superseded banner

### Organization and navigation
- collection card
- saved lens chip
- filter tray
- queue card
- board lane
- graph node card
- timeline card
- map pin sheet

### Growth and management
- template card
- template compare row
- vocabulary chip editor
- proposal drawer
- dependency list
- pack switcher

## 5. Frontend state model

Even with backend logic abstracted behind a single API key boundary, the frontend needs a clear state model.

### Required state categories
- current domain pack
- current target
- current collection
- current entry draft
- current view/lens
- suggestion state
- provenance display state
- trust/governance display state
- import staging state
- upload/attachment state
- live collaboration session state
- overlay visibility state
- scan or AR session state
- user and workspace preferences

### Draft model
Drafts should support:
- auto-save
- quick-save completion
- reopen in full composer
- conflict-safe reopening
- unsaved-change visibility
- conversion to richer forms
- preservation of rejected suggestions

## 6. API boundary assumptions

The frontend assumes a single API boundary that can support at least the following operations:

- authenticate session through API-key-backed application boundary
- fetch targets
- fetch entries
- fetch sources/evidence
- create/update drafts
- create/update relationships
- upload and attach media
- fetch/save templates and vocabularies
- fetch/save collections and saved lenses
- fetch activity and workflow states
- fetch public-facing or shared layers
- submit review/governance actions
- fetch overlay or AR/scan data where relevant

This document set deliberately does not define the backend protocols, auth architecture, or persistence strategy.

## 7. Readiness artifacts that should eventually exist

- target addressing specification
- entry block specification
- composer field-map specification
- view taxonomy specification
- collection semantics specification
- template and taxonomy proposal specification
- trust and provenance display specification
- workflow action specification
- overlay and public-layer specification
- live room specification
- object memory scan specification
- voice-first capture specification
- AR surface specification
- design system token and component specification

## 8. UX invariants to test in prototypes

The frontend is not ready until prototypes prove the following:

1. A user can save quickly from browser capture without confusion.
2. A user can save quickly from mobile capture without losing provenance clarity.
3. A user can convert a quick draft into a rich record without feeling punished.
4. A reviewer can understand support, workflow, and trust at a glance.
5. A domain pack can change the product’s feel without breaking the grammar.
6. A public-facing record can remain trustworthy and legible.
7. A taxonomy proposal can happen from the point of friction without causing chaos.
8. A collection can switch views without semantic drift.
9. A record can survive movement between private, team, and public layers visibly.
10. Frontier surfaces such as ghost layer, object scan, and voice capture can still resolve into the same core record grammar.

## 9. Final readiness principle

The frontend is ready when the architecture can support the full universe without pretending everything must ship at once. The goal is not a maximal first release. The goal is a durable, expandable frontend structure that can host every sanctioned XtraType expression cleanly over time.
