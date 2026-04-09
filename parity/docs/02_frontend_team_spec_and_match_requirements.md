# Frontend Team Requirements: What Had to be Specified and Matched Exactly

## Purpose
This document captures what frontend had to specify so backend and integration layers could produce deterministic, auditable parity.

---

## 1) Frontend had to specify a stable contract posture

### 1.1 Declare FIG/BFF as the integration boundary
- Frontend had to avoid direct dependency on raw backend internals.
- The boundary was formalized as: frontend contract -> FIG/BFF translation -> backend canonical routes.

### 1.2 Require deterministic envelopes and diagnostics
Frontend required strict consistency for:
- success/failure envelope shape behavior,
- canonical error code/detail-code mapping,
- request correlation propagation to diagnostics surfaces.

### 1.3 Maintain backend-authoritative policy semantics
Frontend specified that policy outcomes are rendered, not inferred.
This prevented split-brain authorization logic in clients.

---

## 2) Frontend had to provide concrete parity scaffolding

### 2.1 ICD operational shape
Frontend had to seed and maintain ICD rows with sufficient detail to execute and audit, including:
- endpoint mapping FE -> FIG -> core route
- schema references
- policy gate references
- negative path definitions
- parity test IDs
- artifact links and sensitivity tagging

### 2.2 Pilot row completion
Frontend had to provide concrete row stubs and then complete rows for:
- Auth
- Feed
- Keychain

### 2.3 Dashboard model
Frontend had to define parity dashboard sections that backend could validate against:
- schema parity
- error parity
- policy parity
- telemetry parity
- drift status

---

## 3) Frontend had to match backend governance exactly

### 3.1 Accept merge-blocking parity CI
- No "soft" drift handling for contract classes.

### 3.2 Accept lockstep payload rules
- No orphan frontend contract changes.
- Contract-affecting updates required corresponding test and traceability updates.

### 3.3 Adopt checkpoint evidence discipline
- P0–P5 evidence packet expectation applied jointly.

---

## 4) Frontend artifact responsibilities proven in cycle

Frontend generated and committed (Day-2 packet):
- day index artifact
- gate rerun report
- keychain mapping resolution evidence
- dashboard refresh artifact
- updated ICD pilot rows with policy and artifact linkage fields

This closed traceability demands and enabled checkpoint progression.

---

## 5) Core frontend lesson
For complex integration, frontend must ship not only UX and adapters, but also **operational contract artifacts** that make backend review deterministic and low-friction.
