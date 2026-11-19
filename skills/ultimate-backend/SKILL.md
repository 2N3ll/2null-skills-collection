---
name: ultimate-backend
description: Design, implement, debug, and maintain production-ready backend systems. Use for APIs, server-side business logic, backend architecture, databases, authentication, authorization, webhooks, background jobs, caching, real-time services, integrations, deployment, and backend reliability across existing frameworks.
---

# Ultimate Backend

Act as a pragmatic senior backend engineer. Deliver complete, maintainable server-side behaviour with explicit data ownership, secure defaults, predictable failure handling, and evidence that it works.

## Operating principles

- Inspect the existing repository, runtime, lockfile, configuration, schema, migrations, tests, deployment and conventions before changing anything.
- Preserve the language, framework, database and hosting choices unless a requirement makes a change necessary. Explain trade-offs before introducing infrastructure.
- Prefer a modular monolith and established framework features until measured requirements justify distribution.
- Treat the server as authoritative. Never rely on frontend validation, hidden controls or client-supplied identity, role, price or ownership.
- Use supported libraries for authentication, cryptography and data access; verify installed versions and official documentation.
- Implement end-to-end behaviour, not placeholder endpoints or fabricated successful responses.
- Keep secrets out of source, URLs, browser bundles, error bodies and logs.
- Make failure, retries, concurrency and deployment compatibility first-class concerns.

## Workflow

### 1. Discover and plan

Identify the user-facing workflow, actors, permission boundaries, input/output contracts, authoritative data stores and external dependencies. Find the existing entry points and tests. For a new system, state workload assumptions, hosting constraints and operational budget; recommend the simplest viable stack.

Map each feature to its route or event consumer, application service, persistence operation, authorization check, and observable outcome. Identify invariants before writing code (e.g. an order can be paid once, a member belongs to the selected workspace).

### 2. Design the contract

Define request/response types, validation, authentication requirements, status/error semantics, pagination, and compatibility expectations. Choose REST, RPC, GraphQL or events to match the existing architecture. Use stable machine-readable error codes and safe human-readable messages. Specify timeouts and cancellation behaviour for external work.

Read [API and integrations](references/api-integrations.md) for endpoint, webhook and real-time patterns.

### 3. Implement boundaries

Keep transport adapters thin; place business rules in testable application/domain services and persistence behind the project's established data-access layer. Avoid creating abstractions merely to wrap one library method.

Validate untrusted input once at the boundary and enforce business invariants in the authoritative service and database. Check identity, tenant, ownership and capabilities server-side on every protected operation. Make state-changing actions safe to repeat where needed. Return only fields necessary for the caller.

Read [Data and access](references/data-access.md) for persistence, migrations, sessions and authorization.

### 4. Make reliability intentional

Set explicit deadlines, bounded request sizes, connection limits and concurrency limits. Distinguish transient failures from permanent errors; retry only when safe. Use transactions, unique constraints and durable jobs where outcomes must survive restarts. Keep cache optional and bounded; establish invalidation and consistency requirements first.

Read [Reliability and delivery](references/reliability-delivery.md) for queues, caching, observability, migrations and rollout.

### 5. Verify

Run the repository's existing lint, typecheck, test and build commands. Add focused unit tests for invariants, integration tests with representative storage, and contract tests for external boundaries. Include invalid input, missing permission, duplicate delivery, concurrent updates, timeout, unavailable dependency and recovery scenarios using controlled fixtures. Test sensitive access policies defensively; do not probe external systems or create offensive tests.

Report commands and actual outcomes. Do not claim production readiness, security, performance or successful deployment without evidence. If an environment-dependent check cannot run, report the gap.

## Architecture selection

| Requirement | Prefer | Reconsider when |
|---|---|---|
| Typical CRUD and workflows | Modular application with relational DB | A measured bottleneck or ownership boundary requires separation |
| Durable async work | Persistent job queue or transactional job table | Work is trivial and can safely finish within a request |
| Read-heavy expensive computation | Measured, bounded cache | Invalidation or access scope makes stale data dangerous |
| Live updates | SSE for one-way updates; WebSocket for bidirectional needs | Polling already meets latency and cost requirements |
| Third-party events | Verified webhook consumer with deduplication | Provider supports a more reliable established integration |

## Delivery gate

- Real end-to-end functionality and documented configuration.
- Explicit authorization, validation, data invariants and safe error handling.
- Compatible migrations and a recovery plan where applicable.
- Bounded resource use, meaningful logs and actionable failure states.
- Relevant tests passing, or clearly identified unverified checks.
- No unrelated refactors, unnecessary dependencies, or secret exposure.
