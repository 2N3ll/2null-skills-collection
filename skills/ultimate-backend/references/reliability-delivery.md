# Reliability and delivery

## Jobs and consistency
- Separate request latency from long-running work. Persist important work before acknowledging acceptance.
- Assume at-least-once delivery; use stable operation keys and atomic state transitions. Acknowledge jobs only after durable outcomes.
- Bound workers, retries and job age; surface terminal failures for authorized operators to inspect and deliberately retry. Do not silently discard important work.
- Consider a transactional outbox when publishing an event must correspond to a database transaction. Reconcile external actions using stable provider identifiers.

## Caching
- Measure before caching. Define ownership, key namespace, TTL, maximum size, freshness target and invalidation on writes.
- Avoid sharing identity-specific data between users or tenants. Never use a cache as the only source for durable state.
- Plan cold-cache traffic and avoid unbounded refresh activity. Test stale and unavailable-cache behaviour.

## Operations
- Validate environment at startup with safe, actionable messages. Provide an example configuration with placeholders only.
- Expose appropriate liveness/readiness signals with minimal sensitive detail. Handle termination by draining requests and closing clients within a deadline.
- Emit structured logs, request IDs and meaningful metrics (latency, error rate, saturation, dependency health, queue age). Keep sensitive data out of telemetry; avoid unbounded metric label cardinality.
- Establish service objectives from actual requirements. Measure representative load in an authorized test environment; report hardware, data and concurrency, not unsupported throughput claims.
- Pin dependencies using the project's lockfile, review supported versions and maintain update procedures.

## Rollout and verification
- Use isolated development/test configuration and synthetic data. Validate tests, static checks, build and migrations before release.
- Deploy with health checks and compatibility between application versions; define rollback triggers and owner.
- Document backup restoration, rollback or forward repair, dependency outages and job recovery. Verify recovery procedures periodically.
- Never deploy, modify live infrastructure, rotate credentials or perform destructive migration unless requested and authorized.
