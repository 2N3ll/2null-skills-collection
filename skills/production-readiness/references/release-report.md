# Release report

## Decision rules

- **NO-GO:** required critical checks fail or are unverified; major unresolved correctness, security, data-integrity or recovery risks remain.
- **CONDITIONAL GO:** critical gates are satisfied; residual limited risks or operational prerequisites require explicit acceptance or completion before the release proceeds.
- **GO:** applicable mandatory gates are satisfied, release scope is defined, no known unacceptable blockers remain, and residual limitations are documented. This is a recommendation, not approval or a guarantee.

## Report template

1. Decision, scope/version, target environment and date.
2. Critical blockers, ranked by impact and evidence.
3. Gate matrix: category, status, evidence, owner or next action.
4. Findings and residual risks: severity, affected area, remediation, acceptance criteria.
5. Checks actually run and outputs summarized; existing failures and missing tools distinguished.
6. Sequenced pre-release actions and required sign-offs.
7. Proposed rollout, health signals, rollback triggers and recovery owner.
8. Explicit unverified areas and scope limits.

Avoid invented numeric readiness scores. If requested, explain any rubric and mandatory blockers. Report unknowns instead of hiding them behind a percentage. Never deploy or modify live infrastructure on the basis of a readiness assessment alone.
