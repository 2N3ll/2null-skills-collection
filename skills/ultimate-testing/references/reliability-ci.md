# Reliability and CI

## Diagnose unstable tests

- Re-run the specific test with controlled seed, environment and logs; distinguish reproducible deterministic failure from intermittent behaviour.
- Look for shared fixtures, order dependence, timer races, asynchronous work not awaited, environment-specific paths, network dependence and inconsistent data cleanup.
- Replace arbitrary sleeps with condition-based waits and finite timeouts. Use controlled clocks and deterministic fixtures where appropriate.
- Fix the underlying cause rather than masking failures with unlimited retries. If quarantine is authorized, document ownership, expiry and failure tracking.

## CI design

- Use the repository lockfile and supported runtime. Separate fast checks from slower suites.
- Provide test configuration with placeholders and dedicated test credentials supplied by the CI secret store.
- Avoid production systems; use isolated services and databases.
- Preserve actionable diagnostics, test reports and safe artifacts. Redact secrets and personal information.
- Gate merges on meaningful checks. Use coverage to identify untested important branches, not as proof that behaviour is correct.
- Do not claim a CI configuration works until the relevant run or equivalent local checks are observed.

## Delivery report

Include exact commands, exit statuses, tests added/changed and behaviours exercised. List baseline failures and environment blockers separately from regressions introduced by the work. Name remaining high-risk coverage gaps.
