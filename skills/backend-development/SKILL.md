---
name: backend-development
version: v1.0
description: >
  Design, build, and review production-grade backend systems and APIs.
  Use this skill when the user asks to create REST or GraphQL APIs, design
  database schemas, write server-side business logic, set up authentication,
  build microservices, configure CI/CD pipelines, or solve any server-side
  engineering challenge. Supports Node.js, Python, Go, and Java stacks.
tags: [api, rest, graphql, database, python, nodejs, go, microservices, auth, sql]
category: Developer
author: Marketplace
license: MIT
---

# Backend Development Skill

This skill guides the design and implementation of robust, scalable, and maintainable
backend systems. It produces clean, idiomatic server-side code with careful attention
to architecture, security, and operational concerns.

The user provides a backend requirement: an API to build, a schema to design, a service
to architect, or a bug to fix. They may specify a language, framework, or leave the
choice open.

---

## 1. Architecture Thinking — Do This First

Before writing code, understand the full context:

| Question | What to resolve |
|---|---|
| **Scope** | Single endpoint? Full service? Monolith or microservice? |
| **Stack** | Preferred language / framework, or choose the best fit |
| **Data** | What entities exist? What are the relationships and cardinalities? |
| **Scale** | Expected load, latency SLOs, and storage growth rate |
| **Security** | Auth model (JWT, OAuth2, API key), data sensitivity, compliance needs |
| **Ops** | Deployment target (Docker, Lambda, bare metal), logging, monitoring |

> **CRITICAL:** Design for today's requirements but structure for tomorrow's growth.
> Avoid over-engineering, but never ignore obvious scaling pressure points.

---

## 2. Language & Framework Selection

Choose based on the user's preference or the best fit for the task:

| Use case | Recommended stack |
|---|---|
| REST / GraphQL API | Node.js + Fastify, Python + FastAPI, Go + Gin |
| Data-heavy pipelines | Python + SQLAlchemy / Pandas |
| High-throughput services | Go, Rust |
| Enterprise / JVM shops | Java + Spring Boot, Kotlin + Ktor |
| Serverless functions | Node.js or Python on AWS Lambda / Cloudflare Workers |
| Real-time (WebSockets) | Node.js + Socket.io, Go |

---

## 3. Implementation Standards

All backend code must be:

- ✅ **Idiomatic** — follows language/framework conventions and community style guides
- ✅ **Secure by default** — input validation, parameterised queries, no secrets in code
- ✅ **Error-handled** — every failure path has an explicit, meaningful response
- ✅ **Tested** — unit tests for business logic, integration tests for endpoints
- ✅ **Documented** — inline comments on non-obvious logic; OpenAPI spec for APIs
- ✅ **Observable** — structured logging and key metrics instrumented from day one

---

## 4. API Design Guidelines

### REST
- Use **nouns for resources**, HTTP verbs for actions: `GET /users`, `POST /orders`
- Return **consistent response envelopes**: `{ data, error, meta }`
- Use **HTTP status codes correctly**: 200/201/204/400/401/403/404/409/422/500
- Version APIs from the start: `/api/v1/…`
- Paginate all list endpoints: `?page=1&limit=20` or cursor-based

### GraphQL
- Define a **strongly-typed schema** before resolvers
- Use **DataLoader** to batch and cache DB calls — avoid N+1 queries
- Separate **queries** (read) from **mutations** (write) clearly
- Implement **depth limiting** and **query complexity analysis** to prevent abuse

---

## 5. Database Guidelines

### Schema Design
- Normalise to 3NF by default; denormalise deliberately with documented justification
- Every table needs: `id` (UUID or serial), `created_at`, `updated_at`
- Use **foreign key constraints** and **indexes on every join column** and filter column
- Write **migrations**, not manual ALTER TABLE statements

### Query Safety
- **Always use parameterised queries** — never string-interpolate user input into SQL
- Use **transactions** for multi-step writes that must be atomic
- Add **`EXPLAIN ANALYSE`** for any query running on large tables before shipping

### Technology Selection
| Need | Choice |
|---|---|
| Relational, transactional | PostgreSQL (default) |
| Simple key-value / cache | Redis |
| Document store | MongoDB (only if schema is genuinely variable) |
| Full-text search | Postgres `tsvector` or Elasticsearch |
| Time-series | TimescaleDB or InfluxDB |

---

## 6. Security Checklist

- [ ] **Authentication**: tokens are short-lived; refresh tokens stored securely (httpOnly cookie or encrypted DB)
- [ ] **Authorisation**: every route checks permissions — never trust client-supplied roles
- [ ] **Input validation**: validate and sanitise all incoming data at the boundary
- [ ] **Rate limiting**: applied to auth endpoints at minimum; global limits on all public routes
- [ ] **Secrets management**: environment variables only — never hardcoded; use a secrets manager in prod
- [ ] **CORS**: explicitly configured — never `*` in production
- [ ] **Dependency audit**: run `npm audit` / `pip-audit` / `govulncheck` before shipping
- [ ] **SQL injection**: parameterised queries everywhere
- [ ] **HTTPS only**: enforce TLS; redirect HTTP → HTTPS

---

## 7. Code Structure

### Node.js / TypeScript (recommended layout)
```
src/
  routes/          # Express/Fastify route definitions
  controllers/     # Request handling, input validation
  services/        # Business logic (pure functions where possible)
  repositories/    # Data access layer (DB queries)
  middleware/      # Auth, logging, error handling
  models/          # Type definitions / ORM models
  utils/           # Shared helpers
  config/          # Environment config loader
tests/
  unit/
  integration/
```

### Python / FastAPI (recommended layout)
```
app/
  routers/         # APIRouter definitions per domain
  schemas/         # Pydantic request/response models
  services/        # Business logic
  repositories/    # SQLAlchemy queries
  models/          # ORM models
  dependencies/    # FastAPI Depends() providers (auth, DB session)
  core/            # Config, security helpers
tests/
```

---

## 8. Testing Standards

| Layer | Tool (Node) | Tool (Python) | Coverage target |
|---|---|---|---|
| Unit | Jest / Vitest | pytest | 80 %+ on services |
| Integration | Supertest | httpx + pytest | All API routes |
| DB | testcontainers | pytest + SQLite/testcontainers | All queries |
| Load | k6 | Locust | P99 < SLO |

- Tests live next to the code **or** in a top-level `tests/` directory — be consistent
- Use **fixtures and factories**, not production data
- Every bug fix ships with a **regression test**

---

## 9. CI/CD Pipeline (Recommended)

```yaml
# Minimal GitHub Actions pipeline
steps:
  - Lint (ESLint / Ruff / golangci-lint)
  - Type-check (tsc --noEmit / mypy)
  - Unit tests
  - Integration tests (spin up DB via Docker service)
  - Security audit (npm audit / pip-audit)
  - Build Docker image
  - Push to registry (on main branch only)
  - Deploy to staging → smoke test → promote to prod
```

---

## 10. Output Format

- Provide **complete, runnable code** — no `// TODO: implement this` stubs
- Include a **`README.md`** snippet with setup steps when creating a new service
- Include an **OpenAPI / Swagger snippet** for any new API endpoints
- Add a **`docker-compose.yml`** when the service needs a database or cache
- Highlight any **assumptions made** and **trade-offs chosen** in a brief comment block at the top

---

## 11. Example Trigger Phrases

Use this skill when the user says things like:

- *"Build a REST API for…"*
- *"Design the database schema for…"*
- *"Create an authentication system with…"*
- *"Write a microservice that…"*
- *"How should I structure my backend for…"*
- *"Fix this SQL query / API endpoint / server error"*
- *"Add rate limiting / caching / auth to my API"*

---

## 12. Quality Checklist (self-review before output)

- [ ] Is every user-supplied input validated before use?
- [ ] Are all DB queries parameterised?
- [ ] Is the error handling consistent and informative?
- [ ] Are secrets loaded from environment variables?
- [ ] Is there at least one test per service function?
- [ ] Would a mid-level engineer understand this code without asking questions?
- [ ] Is the code ready to run as-is, or does it require undocumented setup?
