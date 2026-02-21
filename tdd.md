# TDD — Technical Design Document (HOW)

**Audience:** Engineer & Tech Lead

Tujuan: menjelaskan *bagaimana sistem dibangun*.

---

## 1. System Overview

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

## 2. Service Boundaries & Data Ownership

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

## 3. Data & API Design

* Domain model / ERD
* API contract (main endpoints)
* Event design (jika event-driven)
* System use case / data orchestration

---

## 4. Non-Functional Requirements (NFR)

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

## 5. Tech Stack

Contoh:

* Backend: Spring Boot
* DB: PostgreSQL
* Cache: Redis
* Infra: Docker + Cloud

---

## 6. Decision Log / Architecture Decision Record (ADR)

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

## 7. Technical Risks & Mitigation

Contoh:

```
Risk: Redis down
Impact: API latency meningkat
Likelihood: Medium
Mitigation: fallback ke DB + alerting
```

---

## 8. Cost Awareness

Cost considerations:

* Cloud cost awareness
* Scaling cost impact
* Third-party pricing risk

Contoh:

```
Redis cluster increases infra cost but reduces DB load.
```
