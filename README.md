# 📘 Software Project Preparation Master Guide

Dokumen ini merangkum 4 dokumen inti sebelum & selama pengembangan aplikasi:

1. PRD — WHAT & WHY
2. TDD — HOW
3. Execution Plan — WHEN & WHO
4. Runbook — OPERATE & MAINTAIN

---

# 1️⃣ PRD — Product Requirement Document (WHAT & WHY)

**Audience:** Business stakeholder, product, designer, engineer (non-technical friendly)

Tujuan: menjelaskan *masalah, value, user, dan scope produk*.

---

## A. Problem & Value

* Background masalah
* Problem statement
* Value proposition
* Success metrics (OKR/KPI)

Contoh metric:

* Daily active users (DAU) / MAU
* Conversion rate
* Revenue impact
* Time saved

---

## B. User

* Target user
* Pain points user

---

## C. Features & Scope

### Core features

* Feature list
* User flow (UI journey)
* Business use cases (system behavior)

### Scope definition

* MVP scope
* Out of scope

---

## D. Product Risks

Untuk awareness stakeholder:

* Requirement belum stabil
* Integrasi belum pasti

Gunakan format:

```
Risk:
Impact:
Potential:
Mitigation:
```

---

## E. Constraints

Untuk awaraness engineer:

* Budget terbatas
* Target release

---

# 2️⃣ TDD — Technical Design Document (HOW)

**Audience:** Engineer & Tech Lead

Tujuan: menjelaskan *bagaimana sistem dibangun*.

---

## A. System Overview (HLD)

### Application context

* Web / mobile / internal / public
* Expected traffic:

  * Low <1k/day
  * Medium 10k–100k/day
  * High millions

### Architecture design

* Monolith / modular monolith / microservices
* High level design

---

## B. Service Boundaries & Data Ownership

### Golden rule

> Only ONE service can WRITE its data.

Service lain:

* Read via API / event
* Tidak boleh akses DB langsung

### Example (E-commerce)

| Service | Responsibility  | Owned Data          |
| ------- | --------------- | ------------------- |
| User    | Auth, profile   | users, addresses    |
| Product | Catalog, stock  | products, inventory |
| Order   | Order lifecycle | orders, order_items |
| Payment | Transactions    | payments            |

Order menyimpan snapshot:

* product_name_snapshot
* price_snapshot

Agar history tidak berubah.

---

## C. Data & API Design

* Domain model / ERD
* API contract (main endpoints)
* Event design (jika event-driven)
* System use case / data orchestration

---

## D. Non-Functional Requirements (NFR)

### Performance

* Target response time (ex: <300ms)

### Scalability

* Hardware scaling
* Caching strategy
* Concurrency
* Locking
* Queue
* Database strategy
* Storage scaling

### Security

* Auth strategy (JWT/OAuth)
* Rate limiting
* Data protection

### Reliability

* Error handling
* Testing strategy
* Retry strategy
* Idempotency
* Circuit breaker
* Timeout strategy

### Observability

* Logging: structured & centralized
* Metrics: CPU, DB, error rate
* Monitoring
* Alerting

### Maintainability

* Modular architecture
* Coding standards
* Naming & readability
* Good error definition
* Configuration over code
* Migration backward compatibility

---

## E. Tech Stack

Contoh:

* Backend: Spring Boot
* DB: PostgreSQL
* Cache: Redis
* Infra: Docker + Cloud

---

## F. Decision Log / Architecture Decision Record (ADR)

Format:

```
Decision:
Context:
Options considered:
Chosen option:
Trade-offs:
Date:
```

---

## G. Technical Risks & Mitigation

Contoh:

```
Risk: Redis down
Impact: API latency meningkat
Likelihood: Medium
Mitigation: fallback ke DB + alerting
```

---

## H. Cost Awareness

Cost considerations:

* Cloud cost awareness
* Scaling cost impact
* Third-party pricing risk

Contoh:

```
Redis cluster increases infra cost but reduces DB load.
```

# 3️⃣ Execution Plan — Delivery (WHEN & WHO)

**Audience:** Tech Lead, PM, team

Tujuan: memastikan delivery realistis.

---

## A. Milestone & Timeline

Contoh:

* Phase 1 — Core backend
* Phase 2 — Payment integration
* Phase 3 — Production readiness

---

## B. Sprint Breakdown

* Sprint goals
* Deliverables per sprint
* Definition of Done (DoD):
    * Code reviewed
    * Tests passing
    * Deployed to staging
    * Monitoring added
    * Documentation updated

---

## C. Dependency & Responsibility

* External dependencies
* Team ownership

---

## D. Communication & Rituals

* Sprint planning
* Daily standup
* Sprint review/demo
* Sprint retro

---

## E. Delivery Risks & Mitigation

Contoh:

* Resource terbatas
* tigh timeline
* Dependency tim lain

Mitigation:

* Buffer sprint
* Prioritas MVP
* Milestone review

---

# 4️⃣ Runbook — Operate & Maintain

**Audience:** Engineer & DevOps

Tujuan: menjaga sistem tetap hidup di production.

---

## A. Deployment Procedure

* CI/CD pipeline
* Environment:

  * Local
  * Staging
  * Production

---

## B. Monitoring & Alerting

* Logs
* Metrics
* Alerts (email/slack)

---

## C. Incident Handling

* Escalation path

---

## D. Rollback Procedure

* Revert deployment strategy

---

## E. Backup & Recovery

* Backup frequency
* Disaster recovery plan

---
