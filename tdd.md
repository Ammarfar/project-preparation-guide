# TDD — Technical Design Document (HOW)

**Audience:** Engineer & Tech Lead

Tujuan: menjelaskan *bagaimana sistem dibangun*.

---

## 1. System Overview

### Application context

* Web / mobile / internal / public
* Expected traffic

### Architecture design

* Runtime System: Monolith / modular monolith / microservices
* Application Structure: Layered (N-tier) / module-based / clean
* High level diagram

---

## 2. Data Model

* Entities
* Relationships
* Constraints [Optional if any]
* Design Decisions [Optional if any]

---

## 3. API Design

* System use case / data orchestration (each API)
* API contract (URL, request, response)
* Event design (Key, request, response)

---

## 4. Non-Functional Requirements (NFR)

### Reliability

* Failure & error handling
* Timeout strategy
* Testing strategy
* Retry strategy
* Idempotency
* Circuit breaker

### Security

* Auth strategy (JWT/OAuth)
* Rate limiting
* Data protection

### Scalability

* Hardware scaling
* Caching strategy
* Concurrency
* Locking
* Queue
* Database strategy
* Storage scaling

### Performance

* Target response time (ex: <300ms)

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
