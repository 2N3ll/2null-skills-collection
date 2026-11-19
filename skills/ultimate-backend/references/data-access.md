# Data and access

## Persistence
- Model entities, lifecycle, ownership and invariants before choosing schema. Use explicit primary keys, foreign keys, uniqueness and check constraints where supported.
- Use parameterized operations and transactions. Choose isolation/locking according to the invariant; use an atomic conditional update or uniqueness constraint when concurrent requests might otherwise violate it.
- Index from measured access patterns and inspect query plans on representative non-production data. Avoid unbounded queries, accidental N+1 access and returning entire rows indiscriminately.
- Use UTC instants for events and explicit timezone semantics for calendar schedules. Store monetary amounts in exact types with explicit currency.
- Define deletion, retention, backup and recovery requirements; never run destructive changes against live data without explicit authorization.

## Schema changes
- Write versioned migrations with compatibility across running versions. For risky changes, expand schema, deploy compatible reads/writes, backfill in bounded batches, verify, then contract in a separately approved step.
- Rehearse migration and restore on a representative disposable database. Monitor locks, runtime and resource usage. Preserve a rollback or forward-repair strategy.

## Identity and access
- Prefer established session or identity-provider integrations. Distinguish authentication (who) from authorization (what).
- Use secure cookie settings and appropriate CSRF protections for cookie-authenticated mutations. Enforce HTTPS and narrowly scoped CORS policy.
- Validate token issuer, audience, expiry and signature using supported libraries where tokens are used. Plan expiration, revocation and rotation.
- Use established password hashing and reset flows; never store passwords in plaintext or invent cryptography.
- Resolve roles and membership on the server; maintain tenant/resource scope in data-access queries and service policies. Default deny when identity or policy is uncertain.
- Use least-privilege database and service credentials. Limit fields and redact sensitive output. Log relevant administrative changes without credentials.
- Add defensive regression tests proving actors can access their own permitted fixtures, but cannot access disallowed fixture resources or perform unauthorized operations. Use synthetic accounts and controlled environments.
