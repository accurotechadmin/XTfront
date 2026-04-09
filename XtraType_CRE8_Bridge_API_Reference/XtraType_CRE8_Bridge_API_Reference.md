# XtraType on CRE8 — Bridge API Reference

Below is the backend bridge I would treat as the **reference contract** between CRE8 and the XtraType frontend.

Two important framing notes first.

First, the XtraType docs define the **frontend grammar and required behaviors**, but they do **not** define backend protocols. So what follows is a proposed backend contract derived from:
- the XtraType frontend pack
- the CRE8 authority model
- the gap between a simple post/comment API and the richer XtraType object graph

The frontend will **never talk directly to raw CRE8 “Post” semantics** except through an XtraType adapter/facade layer. XtraType is too semantically rich to survive as “just more post payloads” without a stable domain contract.

## 1. Core architectural stance

Treat the system as three planes.

### A. Authority plane (CRE8-native)
This is where CRE8 remains the source of truth for:
- Owners
- Primary Author Keys
- Secondary Author Keys
- Use Keys
- Keychains
- Audience Groups
- sessions
- minting and delegation lineage
- granular permissions

### B. XtraType domain plane
This is the new structured domain layer for:
- targets
- entries
- sources
- evidence packets
- relationships
- collections
- lenses
- workflows
- trust
- provenance
- templates
- vocabularies
- domain packs
- public presentations
- overlays

### C. Projection/presentation plane
This supports frontend-specific read models:
- map views
- timeline views
- graph views
- queue views
- compare views
- dossier views
- overlay feeds
- public pages
- embeddable cards
- live collaboration/event streams

That separation is important because CRE8’s existing post/comment model is useful as a transport/event substrate, but XtraType needs a **typed record graph**.

## 2. CRE8-to-XtraType conceptual mapping

This is the minimum clean crosswalk.

### CRE8 principal objects
- **Owner** → executive/tenant root for a realm
- **Primary Author Key** → delegated admin-author principal inside that Owner’s realm
- **Secondary Author Key** → limited author/reviewer/operator principal
- **Use Key** → viewer/commenter/subscriber principal
- **Keychain** → aggregate authority context
- **Audience Group** → named audience/subscription bucket

### XtraType domain objects
- **Target** → what a record is about
- **Entry** → the record itself
- **Source** → external/internal source artifact
- **Evidence Packet / Chain** → grouped support structure
- **Relationship** → typed connection between objects
- **Collection** → active working surface, not just folder
- **Lens** → saved perspective/filter/view preset
- **Workflow/Trust/Provenance state** → explicit governance layers
- **Publication / Overlay** → public/shared projection objects

### Compatibility rule
A legacy CRE8 `Post` should not be your canonical XtraType domain object.
Instead, one of these should happen:

- either `Post` becomes a low-level persistence envelope for typed XtraType objects, or
- CRE8 remains the auth/session/key layer while XtraType gets its own normalized domain tables/services

I would choose the second option unless CRE8 is already event-sourced and extremely flexible.

## 3. Global API design rules

I would make all XtraType endpoints follow these rules.

### Common envelope
Every domain response should look roughly like:

```json
{
  "id": "xt_...",
  "object_kind": "target|entry|relationship|collection|source|publication|...",
  "object_type": "digital_resource|annotation|assertion|review_queue|...",
  "schema_version": "1.0",
  "realm_id": "realm_...",
  "created_at": "2026-04-09T18:00:00Z",
  "updated_at": "2026-04-09T18:00:00Z",
  "created_by": {
    "actor_id": "act_...",
    "key_id": "key_..."
  },
  "revision": 7,
  "permissions": {
    "can_view": true,
    "can_edit": true,
    "can_comment": true,
    "can_review": false,
    "can_publish": false
  },
  "data": {}
}
```

### Common request metadata
Every mutation endpoint should accept:

```json
{
  "client_mutation_id": "uuid-or-ulid",
  "idempotency_key": "optional-string",
  "if_revision": 6
}
```

Use this for:
- deduping retries
- optimistic concurrency
- offline sync recovery
- autosave reliability

### Common scalar types
- `id`: string, ideally ULID
- `timestamp`: ISO 8601 UTC string
- `enum`: string
- `json`: object
- `string[]`
- `boolean`
- `integer`
- `number`
- `bbox`: `{ "min_lat": number, "min_lng": number, "max_lat": number, "max_lng": number }`
- `interval`: `{ "start": timestamp, "end": timestamp|null }`

## 4. Authority plane endpoints

These are the CRE8-backed endpoints XtraType needs.

### 4.1 Owner and session endpoints

#### `POST /v1/owners`
Create Owner account.

Request:
```json
{
  "username": "string",
  "password": "string",
  "email": "string",
  "payment_token": "string",
  "display_name": "string"
}
```

Response:
```json
{
  "owner_id": "own_...",
  "realm_id": "realm_...",
  "status": "active|pending|suspended"
}
```

#### `POST /v1/sessions/owner`
Owner login.

Request:
```json
{
  "username_or_email": "string",
  "password": "string"
}
```

#### `POST /v1/sessions/key`
Key-based session start for non-registered users.

Request:
```json
{
  "key_token": "string",
  "display_profile": {
    "display_name": "string",
    "avatar_url": "string|null"
  }
}
```

Important: this is mandatory because XtraType explicitly needs key-bearer usage without forced registration.

#### `POST /v1/sessions/keychain`
Start session using aggregated authority.

Request:
```json
{
  "key_tokens": ["string", "string"]
}
```

#### `POST /v1/sessions/refresh`
Refresh token/session.

#### `DELETE /v1/sessions/current`
Logout.

#### `GET /v1/me`
Return:
- resolved actor identity
- current realm
- effective roles
- effective permissions
- key/keychain lineage
- default domain pack
- default capture settings

### 4.2 Key minting and management

#### `POST /v1/keys`
Mint a new key.

Request:
```json
{
  "key_type": "primary_author|secondary_author|use",
  "label": "string",
  "description": "string",
  "grants": [
    "entries:create",
    "entries:edit_own",
    "comments:create",
    "collections:view",
    "review:submit"
  ],
  "constraints": {
    "expires_at": "timestamp|null",
    "max_uses": 100,
    "domain_pack_allowlist": ["research_notebook", "fact_check"],
    "entry_type_allowlist": ["annotation", "citation", "assertion"],
    "collection_scope_ids": ["col_..."],
    "audience_scope_ids": ["aud_..."],
    "publish_allowed": false,
    "review_allowed": true
  }
}
```

Important rules:
- Owner can mint first Primary Author Key
- Primary Author Key can mint:
  - Primary Author Keys
  - Secondary Author Keys
  - Use Keys
- Secondary Author Key can mint:
  - Use Keys only
- Use Key cannot mint anything

Every key record should store:
- `minted_by_owner_id`
- `minted_by_key_id`
- `delegation_depth`
- `authority_chain[]`

#### `GET /v1/keys`
Filterable by:
- type
- status
- minted_by
- audience scope
- expiry

#### `GET /v1/keys/{key_id}`

#### `PATCH /v1/keys/{key_id}`
Allow:
- label updates
- permission tightening
- expiry changes
- audience/collection scope updates

Do not allow silent privilege escalation unless the caller is authorized and the mutation is auditable.

#### `POST /v1/keys/{key_id}/revoke`
Request:
```json
{
  "reason": "string"
}
```

#### `POST /v1/keys/{key_id}/rotate`
For compromised key replacement.

### 4.3 Keychains

#### `POST /v1/keychains`
Create a named aggregate authority object.

Request:
```json
{
  "label": "string",
  "key_ids": ["key_1", "key_2"]
}
```

#### `GET /v1/keychains`
#### `GET /v1/keychains/{id}`
#### `PATCH /v1/keychains/{id}`
#### `POST /v1/keychains/{id}/keys`
Attach key to keychain.
#### `DELETE /v1/keychains/{id}/keys/{key_id}`

Response should always include:
- effective grants
- conflicting grants
- narrowed scopes
- provenance of each authority fragment

### 4.4 Audience Groups

#### `POST /v1/audience-groups`
Create named audience group.

Request:
```json
{
  "name": "string",
  "description": "string",
  "join_mode": "open|invite|request|key_only",
  "default_notifications": true
}
```

#### `GET /v1/audience-groups`
#### `GET /v1/audience-groups/{id}`
#### `PATCH /v1/audience-groups/{id}`

#### `POST /v1/audience-groups/{id}/members`
Add members by actor, key, email, or invite token.

Request:
```json
{
  "actors": ["act_..."],
  "keys": ["key_..."],
  "emails": ["a@example.com"],
  "role": "member|manager|viewer"
}
```

#### `DELETE /v1/audience-groups/{id}/members/{member_id}`

#### `POST /v1/audience-groups/{id}/subscribe`
For key-bearing users with no account.

#### `POST /v1/audience-groups/{id}/unsubscribe`

## 5. Bootstrap and capability endpoints

The XtraType frontend will need a strong boot endpoint.

### `GET /v1/bootstrap`
Return everything needed to render initial UI without 20 round-trips.

Include:
- current actor/session
- effective permissions
- available domain packs
- available target types
- available entry types
- intent catalog
- workflow states
- visibility states
- trust vocab
- templates summary
- vocabulary summary
- feature flags
- frontend capability flags
- upload configuration
- realtime endpoints
- overlay support flags

### `GET /v1/capabilities`
Useful for frontend gating.

Response:
```json
{
  "can_create_targets": true,
  "can_create_entries": ["annotation", "citation", "assertion"],
  "can_comment": true,
  "can_publish": false,
  "can_review": true,
  "can_manage_templates": false,
  "can_manage_vocabularies": false,
  "can_use_overlay": true,
  "can_use_map_view": true
}
```

## 6. Core XtraType object schemas

These are the essential domain types.

### 6.1 Target

```json
{
  "id": "tgt_...",
  "target_type": "digital_resource|spatial|temporal|named_entity|abstract_logical|object_memory|composite",
  "label": "string",
  "summary": "string|null",
  "addresses": [],
  "aliases": [],
  "metadata": {},
  "domain_pack": "string|null",
  "provenance": {},
  "visibility": {},
  "trust": {},
  "relationships": []
}
```

#### Target address variants
A target may have one or more address objects.

##### URL/digital
```json
{
  "kind": "url",
  "url": "https://example.com",
  "canonical_url": "https://example.com",
  "title": "Page title",
  "selector": {
    "quote": "string|null",
    "text_position": { "start": 10, "end": 30 },
    "dom_selector": "string|null"
  }
}
```

##### spatial
```json
{
  "kind": "geo",
  "lat": 40.0,
  "lng": -90.0,
  "radius_m": 20
}
```

##### temporal
```json
{
  "kind": "interval",
  "start": "timestamp",
  "end": "timestamp|null"
}
```

##### entity
```json
{
  "kind": "entity_ref",
  "entity_type": "person|organization|device|species|concept",
  "external_ids": {
    "wikidata": "Q..."
  }
}
```

##### object-memory
```json
{
  "kind": "object_ref",
  "object_class": "vehicle|artifact|tool|asset",
  "serial_number": "string|null",
  "tag_code": "string|null"
}
```

##### composite
```json
{
  "kind": "composite",
  "parts": [
    { "ref": "tgt_123" },
    { "kind": "quote_anchor", "quote": "..." },
    { "kind": "interval", "start": "...", "end": "..." }
  ]
}
```

Composite targets need to be first-class, not hacks.

### 6.2 Entry

```json
{
  "id": "ent_...",
  "entry_type": "annotation|citation|evidence|classification|conversation|workflow|collection_curation|media|assertion",
  "intent": "informational|evaluative|evidentiary|conversational|organizational|operational|observational|referential|corrective|personal_mnemonic",
  "target_ids": ["tgt_..."],
  "title": "string|null",
  "body": {
    "blocks": []
  },
  "modalities": ["textual", "media", "structured"],
  "source_ids": ["src_..."],
  "relationship_ids": ["rel_..."],
  "collection_ids": ["col_..."],
  "workflow": {},
  "visibility": {},
  "trust": {},
  "provenance": {},
  "authorship": {},
  "context": {},
  "comment_count": 0
}
```

#### Entry block variants
Blocks should be typed.

```json
{ "block_type": "paragraph", "text": "..." }
{ "block_type": "quote", "text": "...", "source_ref": "src_..." }
{ "block_type": "citation", "citation_style": "url|manual|doi", "source_ref": "src_..." }
{ "block_type": "claim", "text": "...", "confidence": "low|medium|high" }
{ "block_type": "checklist", "items": [{ "label": "...", "checked": true }] }
{ "block_type": "media_ref", "media_id": "med_..." }
{ "block_type": "location", "lat": 0, "lng": 0 }
{ "block_type": "timeline_event", "start": "...", "end": "..." }
{ "block_type": "structured_fields", "fields": { "temperature": 32.1 } }
{ "block_type": "ai_suggestion", "status": "suggested|accepted|rejected", "why": "..." }
```

### 6.3 Source

```json
{
  "id": "src_...",
  "source_type": "url|document|image|audio|video|manual_note|sensor_trace|imported_record",
  "label": "string",
  "locator": {},
  "excerpt": "string|null",
  "metadata": {},
  "provenance": {},
  "integrity": {}
}
```

### 6.4 Relationship

```json
{
  "id": "rel_...",
  "relationship_family": "entry_target|entry_entry|target_target|source_claim|collection_membership|supersession_revision",
  "relationship_type": "supports|contradicts|replies_to|amends|duplicates|contains|belongs_to|about|derived_from|supersedes",
  "subject_ref": {
    "kind": "entry|target|source|collection",
    "id": "..."
  },
  "object_ref": {
    "kind": "entry|target|source|collection",
    "id": "..."
  },
  "note": "string|null",
  "weight": 1.0,
  "confidence": "low|medium|high|null",
  "provenance": {}
}
```

### 6.5 Collection

```json
{
  "id": "col_...",
  "collection_type": "notebook|case_file|dossier|review_queue|map_layer|timeline_set|board|gallery|route_trail|domain_library|public_layer|object_fleet|live_room",
  "name": "string",
  "description": "string|null",
  "domain_pack": "string|null",
  "ordering_mode": "manual|chronological|spatial|priority|graph|custom",
  "visibility": {},
  "workflow": {},
  "view_defaults": {},
  "member_counts": {
    "targets": 0,
    "entries": 0
  }
}
```

### 6.6 Lens

```json
{
  "id": "lens_...",
  "name": "string",
  "scope_ref": {
    "kind": "collection|realm|target",
    "id": "..."
  },
  "filters": {},
  "sort": {},
  "view_type": "list|card|board|timeline|map|graph|queue|compare|gallery|dossier",
  "presentation": {}
}
```

## 7. Target endpoints

### `POST /v1/targets`
Create target.

Request:
```json
{
  "target_type": "digital_resource",
  "label": "Article about ...",
  "addresses": [
    {
      "kind": "url",
      "url": "https://example.com/article",
      "selector": {
        "quote": "quoted text"
      }
    }
  ],
  "context": {
    "capture_surface": "browser_extension"
  },
  "provenance": {
    "creation_mode": "captured"
  }
}
```

### `POST /v1/targets/resolve`
Resolve-or-create stable target by address.

This is one of the most important endpoints in XtraType.

Request:
```json
{
  "target_type": "composite",
  "addresses": [
    { "kind": "url", "url": "https://example.com" },
    { "kind": "quote_anchor", "quote": "..." }
  ],
  "dedupe_mode": "strict|fuzzy|upsert"
}
```

Response:
```json
{
  "target_id": "tgt_...",
  "status": "matched|created|merged"
}
```

### `POST /v1/targets/bulk-resolve`
Needed for overlays, import, graph hydration, dossier assembly.

### `GET /v1/targets`
Filters:
- `target_type`
- `address_kind`
- `label`
- `collection_id`
- `bbox`
- `time_range`
- `updated_after`
- `visibility`
- `domain_pack`

### `GET /v1/targets/{id}`
### `PATCH /v1/targets/{id}`
### `GET /v1/targets/{id}/entries`
### `GET /v1/targets/{id}/relationships`
### `GET /v1/targets/{id}/activity`
### `POST /v1/targets/{id}/merge`
### `POST /v1/targets/{id}/alias`
### `POST /v1/targets/{id}/supersede`

## 8. Entry endpoints

### `POST /v1/entries`
Create entry.

Request:
```json
{
  "entry_type": "assertion",
  "intent": "evidentiary",
  "target_ids": ["tgt_..."],
  "title": "Claim about ...",
  "body": {
    "blocks": [
      { "block_type": "claim", "text": "..." },
      { "block_type": "paragraph", "text": "..." }
    ]
  },
  "modalities": ["textual", "structured"],
  "context": {
    "capture_surface": "manual_drafting",
    "domain_pack": "fact_check"
  },
  "workflow": {
    "draft_state": "draft"
  },
  "visibility": {
    "audience": "private"
  },
  "trust": {
    "confidence": "medium"
  },
  "provenance": {
    "creation_mode": "asserted"
  }
}
```

### `GET /v1/entries`
Filters:
- `entry_type`
- `intent`
- `target_id`
- `collection_id`
- `workflow_state`
- `publication_state`
- `review_state`
- `moderation_state`
- `confidence`
- `verification`
- `visibility`
- `author`
- `domain_pack`

### `GET /v1/entries/{id}`
### `PATCH /v1/entries/{id}`
### `DELETE /v1/entries/{id}`
Prefer soft delete or archive.

### `POST /v1/entries/{id}/clone`
### `POST /v1/entries/{id}/convert`
For escalation from lightweight note into assertion/evidence/workflow record.

Request:
```json
{
  "new_entry_type": "assertion",
  "preserve_history": true
}
```

### `GET /v1/entries/{id}/history`
Revision history is essential for trust-sensitive flows.

### `POST /v1/entries/{id}/autosave`
Optional convenience endpoint if you do not want full PATCH frequency.

### `POST /v1/entries/{id}/submit-for-review`
### `POST /v1/entries/{id}/publish`
### `POST /v1/entries/{id}/archive`
These can be wrappers around governance endpoints if you want ergonomic calls.

## 9. Comment/conversation endpoints

Even if CRE8 has native Comments, XtraType should treat comments as a specialized conversational entry.

### `POST /v1/comments`
Request:
```json
{
  "parent_ref": {
    "kind": "entry|target|collection|publication",
    "id": "..."
  },
  "thread_root_id": "com_...|null",
  "body": {
    "blocks": [
      { "block_type": "paragraph", "text": "..." }
    ]
  },
  "visibility": {
    "audience": "workspace"
  }
}
```

### `GET /v1/comments`
### `GET /v1/comments/{id}`
### `PATCH /v1/comments/{id}`
### `DELETE /v1/comments/{id}`

Compatibility note:
- raw CRE8 comment rows can still exist
- but the frontend should receive unified conversational-entry shapes

## 10. Capture endpoints

Because XtraType has multiple capture surfaces, I would add normalized capture entrypoints.

### `POST /v1/captures/browser`
Request:
```json
{
  "url": "https://example.com",
  "page_title": "string",
  "selection": {
    "quote": "string",
    "dom_selector": "string|null",
    "text_position": { "start": 0, "end": 10 }
  },
  "media_ids": [],
  "intent_hint": "referential|evidentiary|null",
  "collection_id": "col_...|null"
}
```

Response should return:
- created/resolved target
- draft entry
- suggestions
- provenance
- inferred domain pack

### `POST /v1/captures/mobile`
Include geo/location, photo/audio attachments, device context.

### `POST /v1/captures/import`
For import/share flows.

### `POST /v1/captures/voice`
For voice-first.

### `POST /v1/captures/object-scan`
For object-memory mode.

### `POST /v1/captures/ar`
For spatial placement.

These can all normalize into target + draft entry creation.

## 11. Source and evidence endpoints

### `POST /v1/sources`
Create source record.

### `GET /v1/sources`
### `GET /v1/sources/{id}`
### `PATCH /v1/sources/{id}`

### `POST /v1/evidence-packets`
Request:
```json
{
  "label": "Packet for claim X",
  "source_ids": ["src_1", "src_2"],
  "entry_ids": ["ent_1"],
  "ordering": [
    { "ref": "src_1", "position": 1 },
    { "ref": "src_2", "position": 2 }
  ],
  "summary": "string"
}
```

### `GET /v1/evidence-packets/{id}`
### `PATCH /v1/evidence-packets/{id}`

### `POST /v1/evidence-chains`
For linked support chains or correction chains.

### `POST /v1/assertions/{entry_id}/support`
Convenience wrapper around source-to-claim relationship.

Request:
```json
{
  "source_id": "src_...",
  "relationship_type": "supports|contradicts|attributes|derives_from",
  "note": "string"
}
```

## 12. Relationship endpoints

### `POST /v1/relationships`
Generic relationship creation.

### `GET /v1/relationships`
Filters:
- family
- type
- subject_ref
- object_ref
- collection_id
- target_id
- entry_id

### `GET /v1/relationships/{id}`
### `PATCH /v1/relationships/{id}`
### `DELETE /v1/relationships/{id}`

### `POST /v1/relationships/bulk`
Critical for import, merge, overlay hydration, and dossier assembly.

Request:
```json
{
  "operations": [
    {
      "op": "create",
      "relationship_family": "source_claim",
      "relationship_type": "supports",
      "subject_ref": { "kind": "source", "id": "src_1" },
      "object_ref": { "kind": "entry", "id": "ent_claim" }
    }
  ]
}
```

## 13. Collection endpoints

### `POST /v1/collections`
### `GET /v1/collections`
### `GET /v1/collections/{id}`
### `PATCH /v1/collections/{id}`
### `DELETE /v1/collections/{id}`

### `POST /v1/collections/{id}/members`
Add items.

Request:
```json
{
  "members": [
    { "kind": "entry", "id": "ent_..." },
    { "kind": "target", "id": "tgt_..." }
  ],
  "membership_type": "contains|references|queues|highlights|supports_packet",
  "ordering_position": 10
}
```

### `DELETE /v1/collections/{id}/members/{member_ref}`
### `PATCH /v1/collections/{id}/ordering`
### `GET /v1/collections/{id}/activity`
### `GET /v1/collections/{id}/view-data`
Useful projection endpoint for view hydration.

### Collection types to support
At minimum:
- notebook
- case_file
- dossier
- review_queue
- map_layer
- timeline_set
- board
- gallery
- route_trail
- domain_library
- public_layer
- object_fleet
- live_room

## 14. Lens and view endpoints

### `POST /v1/lenses`
### `GET /v1/lenses`
### `GET /v1/lenses/{id}`
### `PATCH /v1/lenses/{id}`
### `DELETE /v1/lenses/{id}`

Lens payload:
```json
{
  "name": "Needs review",
  "scope_ref": { "kind": "collection", "id": "col_..." },
  "filters": {
    "review_state": ["needs_review"],
    "entry_type": ["assertion", "evidence"]
  },
  "sort": {
    "field": "updated_at",
    "direction": "desc"
  },
  "view_type": "queue"
}
```

### `POST /v1/views/query`
This should be a projection endpoint that returns data already shaped for a chosen view.

Request:
```json
{
  "scope_ref": { "kind": "collection", "id": "col_..." },
  "view_type": "map|timeline|graph|queue|compare|dossier|list|board|gallery",
  "filters": {},
  "sort": {},
  "pagination": {
    "cursor": null,
    "limit": 50
  }
}
```

The backend should shape responses differently by view type.

## 15. Workflow, review, moderation, resolution, publication

Do not collapse these into one field.

### 15.1 Workflow state shape

```json
{
  "draft_state": "draft_saved|draft_enriched|ready_for_review",
  "review_state": "none|pending|in_review|reviewed",
  "moderation_state": "none|flagged|restricted|moderated",
  "resolution_state": "open|resolved|superseded",
  "publication_state": "private|staged|published|embedded|archived",
  "assignment": {
    "assignee_actor_id": "act_...|null",
    "assignee_group_id": "aud_...|null",
    "queue_id": "col_...|null"
  }
}
```

### 15.2 Governance action endpoints

#### `POST /v1/governance/review-actions`
```json
{
  "object_ref": { "kind": "entry", "id": "ent_..." },
  "action": "submit|start_review|approve|request_changes",
  "note": "string",
  "assignee_actor_id": "act_...|null"
}
```

#### `POST /v1/governance/moderation-actions`
```json
{
  "object_ref": { "kind": "entry|publication|overlay", "id": "..." },
  "action": "flag|restrict|restore|remove",
  "reason_code": "policy|abuse|privacy|safety",
  "note": "string"
}
```

#### `POST /v1/governance/resolution-actions`
```json
{
  "object_ref": { "kind": "entry|claim|issue", "id": "..." },
  "action": "resolve|reopen|supersede",
  "replacement_ref": { "kind": "entry", "id": "..." }
}
```

#### `POST /v1/governance/publication-actions`
```json
{
  "object_ref": { "kind": "entry|collection", "id": "..." },
  "action": "stage|publish|embed|archive",
  "audience": "public|link_shared|group",
  "slug": "string|null"
}
```

#### `POST /v1/governance/routing-actions`
```json
{
  "object_ref": { "kind": "entry", "id": "..." },
  "action": "assign|move_queue|unassign",
  "queue_id": "col_...",
  "assignee_actor_id": "act_..."
}
```

## 16. Visibility and sharing endpoints

Keep visibility, audience, and publication separate.

### `PATCH /v1/objects/{kind}/{id}/visibility`
Request:
```json
{
  "visibility_class": "private|workspace|restricted_group|review_only|link_shared|public|layer_specific",
  "audience_group_ids": ["aud_..."],
  "inheritance_mode": "local|inherited|overridden"
}
```

### `GET /v1/objects/{kind}/{id}/permissions/effective`
Must tell frontend:
- what is allowed
- why it is allowed or blocked
- which key/keychain/grant produced that result

### `POST /v1/shares`
Create share link or scoped access token.

## 17. Provenance and trust endpoints

These can be embedded in objects, but standalone endpoints help inspectors and bulk operations.

### `GET /v1/provenance/{object_kind}/{id}`
Return:
- creation provenance
- technical capture metadata
- integrity metadata
- suggestion provenance
- transformation provenance

### `PATCH /v1/trust/{object_kind}/{id}`
Request:
```json
{
  "confidence": "low|medium|high",
  "verification": "unverified|under_review|verified|rejected",
  "dispute": "none|contested|disputed",
  "quality": "rough|usable|polished",
  "sensitivity": "normal|sensitive|restricted"
}
```

Important: these should be permission-gated.

## 18. Template, vocabulary, schema, domain-pack endpoints

The frontend pack makes controlled growth a core feature, so these are not optional long-term.

### `GET /v1/domain-packs`
### `GET /v1/domain-packs/{id}`

Response should include:
- label
- default views
- preferred entry types
- preferred target types
- template defaults
- vocabulary bindings
- automation preferences
- UI emphasis rules

### `POST /v1/templates`
### `GET /v1/templates`
### `GET /v1/templates/{id}`
### `PATCH /v1/templates/{id}`
### `DELETE /v1/templates/{id}`

Template payload:
```json
{
  "name": "Field observation quick capture",
  "scope": "user|workspace|domain_pack|system",
  "entry_type": "evidence",
  "target_type": "spatial",
  "default_blocks": [],
  "required_fields": ["location"],
  "suggested_visibility": "workspace"
}
```

### `POST /v1/vocabularies`
### `GET /v1/vocabularies`
### `PATCH /v1/vocabularies/{id}`

### `POST /v1/schema-proposals`
Needed for “growth without chaos.”

Request:
```json
{
  "proposal_type": "new_field|new_label|new_template|new_branch|promote_local_to_shared",
  "scope": "workspace|domain_pack|system",
  "payload": {},
  "justification": "string"
}
```

### `POST /v1/schema-proposals/{id}/review`
### `POST /v1/schema-proposals/{id}/promote`

## 19. Suggestion and automation endpoints

Because suggestions must be explainable, I would keep them explicit.

### `POST /v1/suggestions`
Generic suggestion engine.

Request:
```json
{
  "context": {
    "capture_surface": "browser_extension",
    "domain_pack": "fact_check"
  },
  "draft_entry": {},
  "target_candidates": [],
  "requested_kinds": [
    "intent",
    "target",
    "support",
    "template",
    "taxonomy",
    "privacy",
    "workflow"
  ]
}
```

Response:
```json
{
  "suggestions": [
    {
      "kind": "intent",
      "value": "evidentiary",
      "confidence": 0.82,
      "why": "Selected quote and current pack resemble evidence capture.",
      "provenance": {
        "inputs": ["selection.quote", "domain_pack"]
      }
    }
  ]
}
```

### `POST /v1/suggestions/{id}/accept`
### `POST /v1/suggestions/{id}/reject`

Nothing high-stakes should happen silently.

## 20. Search, graph, and projection endpoints

The frontend needs more than CRUD.

### `POST /v1/search`
Structured search over XtraType objects.

Request:
```json
{
  "query": "string",
  "object_kinds": ["target", "entry", "collection", "source"],
  "filters": {
    "entry_type": ["assertion"],
    "visibility": ["workspace"],
    "domain_pack": ["research_notebook"]
  },
  "cursor": null,
  "limit": 25
}
```

### `POST /v1/graph/query`
Needed for graph view, support chains, and compare contexts.

### `POST /v1/map/query`
Needed for map layers, spatial targets, clustering.

### `POST /v1/timeline/query`
Needed for temporal targets, revision history, event layers.

### `POST /v1/compare/query`
Return two-or-more object comparison payload.

### `POST /v1/dossier/query`
Return packet-ordered presentation model.

### `POST /v1/queue/query`
Optimized for review/moderation/workflow.

## 21. Upload and media endpoints

### `POST /v1/uploads/initiate`
Request:
```json
{
  "filename": "photo.jpg",
  "mime_type": "image/jpeg",
  "byte_size": 123456
}
```

Response:
```json
{
  "upload_id": "upl_...",
  "upload_url": "signed-url",
  "media_id": "med_..."
}
```

### `POST /v1/uploads/complete`
### `GET /v1/media/{id}`
### `PATCH /v1/media/{id}`
### `POST /v1/media/{id}/attach`

Optional but useful:
- `POST /v1/media/{id}/transcribe`
- `POST /v1/media/{id}/extract-metadata`
- `POST /v1/media/{id}/generate-derivatives`

## 22. Activity, audit, realtime, presence

These are important for live evidence rooms, collaboration, moderation, and trust.

### `GET /v1/activity`
Global or scoped activity feed.

### `GET /v1/objects/{kind}/{id}/activity`
Per-object history.

### `GET /v1/audit-log`
Admin/steward-only.

### `POST /v1/live-rooms`
### `GET /v1/live-rooms/{id}`
### `POST /v1/live-rooms/{id}/join`
### `POST /v1/live-rooms/{id}/leave`

### `WS /v1/realtime`
Events:
- entry.updated
- comment.created
- relationship.created
- review.assigned
- moderation.changed
- publication.changed
- overlay.updated
- presence.updated
- audience.subscription_changed

## 23. Public presentation and overlay endpoints

These are mandatory if XtraType is going to support public record pages and ghost layers.

### Internal publication objects

#### `POST /v1/publications`
```json
{
  "source_ref": { "kind": "entry|collection", "id": "..." },
  "presentation_type": "record|collection|overlay|embed|map|timeline|history",
  "slug": "string",
  "audience": "public|link_shared|group",
  "theme": {},
  "trust_display": {
    "show_provenance": true,
    "show_revision_history": true,
    "show_verification": true
  }
}
```

#### `GET /v1/publications/{id}`
#### `PATCH /v1/publications/{id}`
#### `POST /v1/publications/{id}/unpublish`

### Overlay endpoints

#### `POST /v1/overlays`
Create overlay collection or overlay presentation.

#### `GET /v1/overlays/query`
Request can include:
- URL
- quote anchor
- bbox
- route segment
- object ID
- density preferences
- trust filters
- audience scope

#### `PATCH /v1/overlays/{id}`

### Public JSON endpoints
- `GET /public/records/{slug}`
- `GET /public/collections/{slug}`
- `GET /public/overlays/{slug}`
- `GET /public/maps/{slug}`
- `GET /public/timelines/{slug}`
- `GET /public/history/{slug}`
- `GET /public/embed/{slug}`

## 24. Frontend-specific convenience endpoints

These are not conceptually pure, but they will make the frontend much easier to build.

### `POST /v1/composer/init`
Given a surface and partial context, return a hydrated draft shell.

```json
{
  "capture_surface": "browser_extension|mobile|manual|import|voice|scan|ar",
  "domain_pack": "string|null",
  "target_seed": {},
  "collection_id": "col_...|null"
}
```

Response:
- draft entry shell
- target candidates
- allowed entry types
- suggested intent
- visible drawers
- required fields
- effective permissions

### `POST /v1/composer/validate`
Validate draft without saving.

### `POST /v1/composer/commit`
Commit draft to entry.

### `POST /v1/batch/read`
Hydrate a mixed set of objects in one round-trip.

### `POST /v1/batch/permissions`
Resolve permissions for many objects.

## 25. Minimum normalized database entities

These are the tables or aggregates I would expect even if some parts are JSONB-backed.

Authority plane:
- owners
- realms
- keys
- key_grants
- key_constraints
- keychains
- keychain_keys
- sessions
- audience_groups
- audience_memberships
- actors
- actor_profiles

XtraType domain plane:
- targets
- target_addresses
- entries
- entry_blocks
- sources
- evidence_packets
- evidence_packet_members
- relationships
- collections
- collection_members
- lenses
- publications
- overlays
- templates
- vocabularies
- vocabulary_terms
- schema_proposals

Governance plane:
- workflow_states
- trust_states
- visibility_states
- provenance_records
- review_actions
- moderation_actions
- publication_actions
- routing_actions
- audit_log

Support plane:
- media_assets
- activity_events
- notification_subscriptions
- realtime_presence
- derived_projections

## 26. Permission model you should explicitly encode

Do not keep permissions as vague booleans only. Use explicit grant strings plus scopes.

Examples:
- `targets:create`
- `targets:edit`
- `targets:merge`
- `entries:create`
- `entries:create:annotation`
- `entries:create:assertion`
- `entries:edit_own`
- `entries:edit_any`
- `comments:create`
- `comments:moderate`
- `sources:create`
- `evidence:attach`
- `relationships:create`
- `collections:create`
- `collections:curate`
- `lenses:create`
- `review:submit`
- `review:decide`
- `moderation:act`
- `publish:stage`
- `publish:go_live`
- `templates:create`
- `templates:promote`
- `vocabularies:manage`
- `keys:mint:primary_author`
- `keys:mint:secondary_author`
- `keys:mint:use`
- `keys:revoke`
- `audiences:manage`

Scope dimensions:
- realm-wide
- domain-pack-scoped
- collection-scoped
- audience-scoped
- entry-type-scoped
- target-type-scoped
- own-only
- inherited
- overridden

## 27. Extremely important separation rules

These matter a lot for XtraType.

### Keep these separate in storage and API
- target identity vs entry identity
- visibility vs publication state
- review vs moderation vs resolution
- confidence vs verification vs dispute vs quality
- authorship vs display identity
- source vs evidence relationship
- collection membership vs target relationship
- raw capture vs transformed/generated content
- suggestion vs committed user action

If these collapse early, the frontend will become confusing very fast.

## 28. Suggested compatibility strategy with CRE8 Post/Comment

This is the safest bridge plan.

### Phase 1 compatibility
Keep legacy CRE8 endpoints alive internally, but do not expose them as the frontend contract.

Instead:
- XtraType mutations hit the new facade
- facade uses CRE8 auth/key/session services
- facade persists XtraType objects in new tables
- facade can optionally emit CRE8-style post events for audit/activity compatibility

### Legacy mapping
- CRE8 `Post` → internal event/envelope, not primary product object
- CRE8 `Comment` → conversational entry or review note
- CRE8 `Use Key` → read/comment session
- CRE8 `Audience Group` → audience + notification/subscription primitive

## 29. Backend behaviors the frontend will depend on

These are easy to underestimate.

You will need:
- stable target deduping and resolution
- partial draft save
- optimistic concurrency
- revision history
- mixed-object hydration
- effective permission explanation
- rich filtering and projections
- event stream / realtime updates
- public projection generation
- overlay address resolution
- explainable suggestions
- auditable workflow changes
- reversible moderation/publication actions
- actorless keyed sessions
- upgrade path from key-only user to full account if desired

## 30. If you want the shortest “must-build first” endpoint set

If you want the first truly useful bridge, build these first:

- `POST /v1/sessions/key`
- `GET /v1/bootstrap`
- `POST /v1/targets/resolve`
- `POST /v1/entries`
- `PATCH /v1/entries/{id}`
- `POST /v1/comments`
- `POST /v1/relationships`
- `POST /v1/collections`
- `POST /v1/collections/{id}/members`
- `POST /v1/views/query`
- `POST /v1/uploads/initiate`
- `POST /v1/governance/review-actions`
- `POST /v1/governance/publication-actions`
- `GET /v1/objects/{kind}/{id}/permissions/effective`
- `GET /v1/objects/{kind}/{id}/activity`
- `POST /v1/suggestions`
- `GET /v1/overlays/query`

That gives you a serious XtraType bridge without waiting for every frontier feature.

## 31. Bottom line

The bridging infrastructure should be designed around this principle:

**CRE8 supplies authority, delegation, access aggregation, and audience primitives; XtraType supplies a typed contextual-record graph with explicit provenance, trust, workflow, collection, and publication semantics.**

So the backend should not merely add “post types.” It should expose:
- a stable authority model
- a stable target model
- a stable entry model
- a stable relationship model
- a stable governance model
- projection endpoints for the major frontend surfaces

That is the clean line between a simple API server and a fully expanded XtraType frontend.
