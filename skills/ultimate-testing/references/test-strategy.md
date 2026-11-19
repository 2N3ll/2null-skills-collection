# Test strategy

| Layer | Best use |
|---|---|
| Unit | Pure functions, business invariants, state transitions and policy decisions |
| Component | Rendering, interaction, feedback and accessibility behaviour |
| Integration | Real persistence, transactions, adapters and framework routing |
| Contract | Request/response schemas and supported third-party interfaces |
| End-to-end | A few critical journeys through realistic isolated systems |

Choose based on failure impact and which boundary can reveal the defect.

## Case design

- Enumerate equivalence classes, boundary values, valid/invalid ordinary data and relevant state transitions.
- Use table-driven tests for related scenarios; avoid excessive parametrization that obscures intent.
- Test asynchronous success, timeout, cancellation, bounded retries and graceful dependency failures with controlled stubs.
- For stateful work, test idempotency, atomic updates and concurrent legitimate operations with synthetic records.
- For UI, prefer user-facing roles, labels and stable selectors. Test navigation, form validation, loading/empty states and keyboard access where relevant.
- For API integration, verify documented contracts, persistent effects and intended decisions with authorized synthetic identities.
- Prefer representative real databases or local adapters for persistence correctness; avoid mock-only claims about transactions.

## Fixtures and mocks

Keep fixtures minimal, valid and independently reset. Mock external dependencies at their boundary, not the code under test. Use fixed clocks, controlled randomness and temporary resources. Clean up after tests; avoid real payments, notifications, production credentials or network calls.

## Existing tooling

Prefer the project's runner: for example Vitest/Jest, Playwright, React Testing Library, pytest, Go testing, cargo test, JUnit or xUnit where already appropriate. Verify version-specific commands with installed documentation.
