# Static analysis checklist

## Correctness and behavior
- Unreachable branches, contradictory conditions, always-true/false checks, fallthrough, missing returns and assignments overwritten before use.
- Null/undefined handling, invalid assumptions about object shapes, unsafe narrowing and casts, incorrect equality or precedence.
- Ignored promises/results, missing awaits, inconsistent error propagation, parallel operations with ordering requirements.
- Incorrect loop boundaries, stale derived values, incorrect lifecycle cleanup, duplicate listeners/timers, resource leaks and unintended mutation.
- Framework-specific problems such as unstable list keys or effect dependencies; verify framework semantics.
- Inconsistent error paths, state transitions or return contracts. Prefer small focused regression tests for ordinary expected behavior.
- Meaningless expressions and suspicious copy/paste mistakes; verify intent before declaring defects.

## Unused or redundant code
Distinguish local declarations from exports and entry points. Track reachability through imports, symbol references and configured entry points, not text-search counts alone.
- Unused constants, variables, arguments, assignments, types, imports and expressions.
- Unused functions, classes, methods, exports, files, styles and assets.
- Redundant wrappers, identical conditions, unnecessary intermediate variables, dead feature branches and obsolete configuration.
- Dependencies lacking apparent usage; inspect scripts, configuration, plugin loading, build and deployment first.

Before deletion:
- Check reflection, dependency injection, decorators, dynamic import, automatic route discovery, generated callers, framework lifecycle hooks, CLI entry points, plugin contracts and public consumers.
- Check whether an initializer or import has side effects. An unused binding does not mean its expression is disposable.
- Preserve type-only exports, intentionally unused interface arguments, test fixtures and package public APIs as appropriate.
- Classify candidates as safe local cleanup, needs confirmation, or intentional/retain. Never mass-delete based solely on heuristic output.

## Maintainability
- Duplicate logic with the same business rule (not merely similar-looking syntax).
- Complex conditions, deeply nested control flow, large functions and modules with mixed responsibilities.
- Repeated literals with shared domain meaning, unclear names, mutable global state, overbroad types, duplicated configuration.
- Excessive dependencies, unnecessary abstraction or indirection, obsolete APIs and inconsistent conventions.
- Inefficient repeated work with measurable or plausible cost; separate performance hypotheses from measured bottlenecks.
- Test gaps around important invariants and error handling. Do not treat coverage percentage alone as evidence of test quality.
