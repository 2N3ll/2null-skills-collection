# Investigation playbook

| Symptom | First diagnostic focus |
|---|---|
| Build or type failure | First meaningful compiler error, dependency versions, config and generated inputs |
| Crash or unhandled exception | Stack trace, first application frame, input shape and lifecycle |
| Incorrect output | Data flow, authoritative state, assumptions and transformation boundaries |
| Intermittent failure | Ordering, concurrent state, stale data, environment and time dependence |
| Feature stopped working | Recent scoped changes, configuration differences, contract changes and baseline |
| Slow or stuck operation | Timing breakdown, waiting dependencies, queues, cancellation and resource limits |
| Integration failure | Documented contract, timeout, safe configuration and provider status |

## Evidence discipline

Use an evidence ledger with observation, source, implication and uncertainty. Do not treat correlation or last-modified code as proof. Preserve baseline logs and compare like-for-like conditions. Inspect existing tests before adding instrumentation. If temporary instrumentation is authorized, use scoped structured logs, redact sensitive data and remove it after diagnosis.

## Minimal correction

Prefer fixing the earliest incorrect assumption or invariant, rather than suppressing downstream symptoms. Do not catch-and-ignore errors, disable validations, turn off protective controls, restart indefinitely, or add unbounded retries. Preserve API behaviour and error semantics unless the user explicitly wants a change.

For a non-security bug, capture a focused regression around the ordinary user workflow. For security defects, use static evidence and tests of intended defensive policy, not exploit reproduction. Test neighbouring behaviour and any migration or operational implications.
