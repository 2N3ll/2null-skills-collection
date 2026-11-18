# Commands and interaction design

Primary references:
- https://discord.com/developers/docs/interactions/overview
- https://discord.com/developers/docs/interactions/application-commands
- https://discordjs.guide/

## Command design

Use a command for a clear user goal, not for every internal operation. Prefer a small, discoverable command surface with subcommands and autocomplete where appropriate.

For each command, define:
- User-facing purpose and description.
- Required options and validation rules.
- Contexts where it can run (guild, bot DM, private context where supported).
- Default member permissions.
- Runtime authorization policy.
- Response visibility and expected duration.
- Audit and failure behaviour.

Keep command registration separate from runtime handlers. Use a deployment script or controlled registration process, and distinguish development guild commands from global production commands. Before using a bulk overwrite endpoint, confirm that the complete intended command list is available; the endpoint replaces the existing list for that scope.

## Interaction lifecycle

An interaction has a short acknowledgement window. Consult the current Discord documentation for the exact timing and response types.

A robust handler should:
1. Parse and validate the interaction.
2. Perform cheap authorization checks.
3. Acknowledge immediately with a reply, defer, or modal as appropriate.
4. Execute business logic with a timeout and clear error handling.
5. Edit the deferred original response or send a follow-up.
6. Record important outcomes without logging tokens or sensitive content.

Do not defer every interaction automatically: some interactions, such as opening a modal, require a specific initial response. Do not attempt multiple initial acknowledgements.

## Component routing

Use namespaced custom IDs, for example:
- `support:ticket:claim:<opaque-id>`
- `moderation:case:review:<opaque-id>`
- `settings:notifications:toggle:<opaque-id>`

Treat all custom ID content as untrusted. Parse strictly, validate the expected format, and load authoritative workflow state from storage. Verify that the actor is allowed to perform the requested transition.

Prefer a central router with feature-specific handlers over a giant conditional statement. Ensure handlers are registered once and are removed or scoped correctly during tests and hot reloads.

## Stateful workflows

Model a workflow as explicit states and allowed transitions. For example:

```text
OPEN -> CLAIMED -> CLOSED
  |         |
  +------> CLOSED
CLOSED -> OPEN (only if reopening is allowed)
```

Persist the current state, owner, timestamps, and relevant audit metadata. Use transactions or conditional updates so two staff members cannot claim or close the same ticket simultaneously.

## Autocomplete

Autocomplete is a suggestion mechanism, not validation. Limit and rank suggestions, avoid expensive per-keystroke work, and re-check the chosen option when the command is submitted.
