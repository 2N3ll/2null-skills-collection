# Testing Discord applications

## Testing layers

### Unit tests
Test business rules without Discord:
- Permission policy decisions.
- Ticket state transitions.
- Moderation validation.
- Reward calculations and idempotency.
- Input parsing and custom ID parsing.
- Error classification and retry decisions.

### Integration tests
Test adapters and persistence:
- Database repositories and migrations.
- Transactions and concurrent updates.
- Queue retry and dead-letter behaviour.
- Discord REST wrapper error handling.
- OAuth2 callback and session validation.

### Discord test-guild tests
Use a dedicated test application and guild to verify:
- Command registration and visibility.
- Actual component rendering.
- Modal submission.
- Role hierarchy and channel overwrites.
- Missing permissions.
- Behaviour on desktop and mobile clients.

Never use a production guild as the default integration test environment.

## Mocking guidance

Mock Discord at boundaries so business logic stays testable. Do not mock every internal function or build tests that only assert implementation details. A small number of real test-guild checks are important because mocks cannot verify client rendering, current API constraints, or actual permission behaviour.

## Reliability scenarios

Test:
- Two staff members claiming the same ticket at once.
- The same button clicked repeatedly.
- An interaction arriving after the workflow expires.
- A role or channel deleted while a workflow is active.
- A process restart during a queued action.
- Discord returning a rate limit or transient server error.
- A database transaction failing halfway through.
- A user losing permissions between opening a panel and clicking its button.

## Release gates

Before deployment, run the project's existing lint, typecheck, unit, integration, and build commands. Do not invent scripts; inspect package.json or the project's task runner. Record skipped checks and why they could not run.
