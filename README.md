# EV_PnC_Consent_registry

Core consent service (modular monolith): catalogue, notices, grants, receipts, safeguards, rights, tenancy; also runs revocation propagation workers as a separate deployable.

Part of the **EV Owners Roaming Consent** project: a central, neutral consent registry and decision point for EV owners' roaming data (which hub may receive which data, for which purpose, under which KVKK safeguard). Repo family plan: `repo-plan/consent/README.md` in the project files.

## Scope

- Modules: catalogue, notices, grants, receipts, safeguards, rights, tenancy, propagation
- Signed receipts (JWS) with keys from the HSM/KMS
- Outbox pattern to Kafka for grant events
- Separate deployables from one repo: registry-api, propagation-worker

## Requirements

RC-CAT-*, RC-GRANT-*, RC-REC-*, RC-REV-*, RC-RIGHTS-*, RC-LEGAL-*, RC-TEN-* (see `EV_PnC_Consent_docs`, specs from `roaming-consent/spec.md`)

## Tech stack

Kotlin, Spring Boot 3, PostgreSQL, Kafka

## Infrastructure (BOM)

PostgreSQL HA, Kafka, HSM/KMS, K8s

## Scaling

Stateless API pods scale horizontally; PostgreSQL partitioned by tenant when a second tenant arrives; propagation workers scale on Kafka lag

## Ownership

Backend team A · Visibility: public · Wave 1: now (Phase 0–1, Nov 2026 – Feb 2027)

## Status

Scaffold only. Not production ready.

## License

Apache-2.0 (proposed)
