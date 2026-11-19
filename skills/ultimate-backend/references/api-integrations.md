# API and integrations

## Contracts
- Follow existing API naming and versioning. Document method, path, identity/capabilities, input constraints, response shape and errors; maintain backward compatibility or plan migration.
- Validate types, lengths, ranges and content types; reject unsupported fields when appropriate. Map validation, authentication, authorization, absence, conflict and availability failures to the protocol's established semantics.
- Bound list results, filter and sort fields; prefer stable cursor pagination for changing large datasets. Never expose internal exception dumps or sensitive model fields.
- Allocate request/correlation IDs; carry them through service and dependency logs.

## External services
- Configure endpoint and credentials server-side. Use documented SDKs where appropriate.
- Apply timeouts and cancellation; bound retries with exponential backoff and jitter only for retryable, replay-safe calls. Respect provider retry hints.
- Validate outbound destinations against an explicit trust policy; constrain redirects, download size and file handling. Treat integration output as untrusted data.
- Handle provider downtime with explicit degraded status; never silently invent success.

## Webhooks
- Verify provider signatures against the original request body using the supported SDK, including timestamp policy if supported.
- Persist the provider event ID with a uniqueness constraint before processing duplicate-sensitive work; acknowledge promptly when durable intake succeeds.
- Decouple expensive work where necessary. Handle out-of-order events through state transitions and authoritative provider reconciliation.
- Record delivery and processing status without storing unnecessary secrets or sensitive payloads.

## Real-time
- Authenticate connections and authorize every subscription and state-changing message.
- Scope channels by authorized resource; handle permission changes and reconnects.
- Bound message sizes, connection counts and backlog; support graceful shutdown.
- Design snapshot plus incremental updates and explicit resync on missing events. Do not assume exactly-once delivery.

## Contract example
For an authenticated workspace task update, resolve workspace membership from the current session; validate allowed fields; apply the permitted state transition atomically; return the persisted public task representation. Use a version check if concurrent edits must not overwrite one another.
