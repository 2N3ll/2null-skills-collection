# Discord bot production operations

Primary references:
- https://discord.com/developers/docs/topics/rate-limits
- https://discord.com/developers/docs/events/gateway
- https://discordjs.guide/

## Startup and configuration

Validate configuration at process startup:
- Bot token and application/client identifiers.
- Database connection and migration state.
- Environment name and allowed guild IDs for development-only actions.
- Required intents and feature flags.
- External API credentials and callback URLs.

Fail fast with a clear error when required configuration is missing. Never print secret values.

## Graceful shutdown

On termination:
- Stop accepting new background work.
- Mark readiness as unavailable.
- Finish or safely cancel in-flight jobs.
- Persist critical state.
- Close database and queue connections.
- Destroy the Discord client cleanly.

Avoid creating multiple clients or registering duplicate listeners during reloads.

## Rate limits and retries

Discord REST responses include rate-limit information. Prefer the library's REST manager for normal Discord requests. If implementing raw REST calls:
- Respect route and global limits.
- Use server-provided retry timing.
- Retry only operations that are safe to repeat.
- Use bounded exponential backoff with jitter for transient failures.
- Do not blindly retry validation, permission, or not-found errors.

Do not hardcode a global request-per-second number as a universal safe limit.

## Background jobs

Use a queue only when tasks are slow, bursty, scheduled, or need durability. Bound queue length and concurrency. Persist jobs whose loss would harm users. Make jobs idempotent and track attempts, next run, completion, and terminal failure.

## Logging and monitoring

Prefer structured logs with:
- Timestamp, severity, environment.
- Event/command name and correlation ID.
- Guild/channel identifiers only when needed.
- Duration and outcome.
- Error class and safe diagnostic context.

Do not log tokens, webhook URLs, interaction tokens, full private messages, or unnecessary personal data.

Monitor:
- Gateway connection and reconnect state.
- Interaction acknowledgement failures.
- REST error rates and rate-limit waits.
- Command and component handler failures.
- Queue depth and oldest job age.
- Database connectivity and query latency.
- Memory, CPU, and process restarts.

## Sharding and scaling

Do not shard by default. Start with a single process if the workload and Discord's current requirements allow it. Introduce sharding when guild scale, Gateway session constraints, or operational needs justify it.

When scaling:
- Separate Gateway ownership from web/API workers where useful.
- Share durable state through a database.
- Use distributed coordination for jobs that must run once.
- Avoid assuming process-local caches are shared.
- Plan shard restarts and identify concurrency limits using current Gateway documentation.

## Deployment checklist

- Separate test and production Discord applications.
- Store secrets in the host's secret manager.
- Apply database migrations as a controlled release step.
- Register application commands deliberately.
- Configure intents and bot permissions.
- Set process restart and graceful shutdown behaviour.
- Add health checks and actionable alerts.
- Test backup and restore procedures.
- Pin dependencies and review security advisories.
- Document rollback and token-rotation procedures.
