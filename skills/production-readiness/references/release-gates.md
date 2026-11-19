# Release gates

| Gate | Evidence to seek |
|---|---|
| Build/runtime | Pinned dependencies, supported runtime, successful applicable build/type/lint checks |
| Core functionality | Representative isolated tests and smoke checks for critical journeys |
| UI/UX | Essential controls, responsive layouts, accessibility, loading and failure feedback |
| Defensive security | Static review of route policy, authorization, configuration, secrets handling and applicable advisories |
| Data integrity | Constraints, transactions, migrations, representative test data and verified recovery strategy |
| Backend reliability | Timeouts, safe retries, bounded resources, failure states and idempotency where needed |
| Performance | Relevant measured budgets or explicitly documented limitations |
| Configuration | Validated required environment settings, placeholders, environment separation and supported infrastructure |
| Deployment | Documented process, compatibility, health checks, rollout and rollback plan |
| Observability | Appropriate logs, redaction, actionable metrics and ownership |
| Recovery | Backup/restore and rollback or forward-repair plan proportional to risk |
| Documentation | Accurate setup, release notes, operational handoff and known limitations |

For Discord applications, verify configured intents, least-privilege permissions, interaction lifecycle, registration strategy, and controlled test-guild evidence where available. For desktop applications, include supported OS/runtime compatibility, packaging and update process. Mark inapplicable gates with rationale.

## Evidence levels

- Observed: actual relevant result from authorized inspection or a safe check.
- Documented: a credible current artifact or procedure exists, not independently verified.
- Unverified: no adequate evidence for the release.
- Not applicable: explain why the gate does not apply.

Do not treat documentation alone as proof of real deployment or recovery behaviour.
