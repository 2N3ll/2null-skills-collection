# Reporting and refactoring

## Finding classification

| Priority | Meaning |
|---|---|
| Critical | Confirmed severe correctness failure or data integrity risk |
| High | Significant functional defect or reliability problem |
| Medium | Likely bug, meaningful maintainability burden or repeated waste |
| Low | Safe cleanup or localized readability improvement |
| Informational | Optional convention, tooling or architecture suggestion |

Use confidence labels confirmed, likely and needs verification. For unused code also specify whether removal is safe locally, needs confirmation or should be retained.

## Finding format

- ID; priority; category; confidence.
- File and line or precise symbol.
- Observed evidence and diagnostic identifier if available.
- Consequence and rationale.
- Suggested change; intended behavior preserved; verification.
- Effort (small, medium, large) and dependencies on other changes.

Example: CQ-012, Low, unused local, confirmed. A constant initialized with a pure literal is neither referenced nor exported. Recommend removing its declaration, then rerun lint/typecheck. Do not generalize this conclusion to effectful initialization or exported symbols.

## Report structure

1. Summary and unique finding counts.
2. Scope, tools actually run, exit statuses and limitations.
3. Prioritized correctness issues.
4. Unused code inventory: symbol, location, category and removal confidence.
5. Refactor suggestions: existing problem, recommended alternative, benefit, risk and effort.
6. Quick wins, next iteration, and larger changes needing approval.

Do not invent a quality percentage. If a score is explicitly requested, disclose its rubric, coverage and assumptions.

## Refactoring plan
- Establish baseline tests and observable behavior first.
- Prefer removing confirmed unused locals and redundant pure expressions before structural edits.
- Separate mechanical cleanup, bug fixes and behavior-preserving refactors into reviewable batches.
- Preserve side effects, evaluation order, async/error behavior, API contracts, naming conventions and framework lifecycle semantics.
- Add focused regression checks where behavior is insufficiently protected.
- Avoid speculative abstractions or rewriting working modules just to meet arbitrary size limits.
- Compare checks against baseline; disclose remaining issues and any behavior changes.
