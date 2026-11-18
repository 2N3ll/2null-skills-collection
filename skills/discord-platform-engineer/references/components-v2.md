# Discord message components and Components V2

Primary references:
- https://discord.com/developers/docs/components/overview
- https://discord.com/developers/docs/resources/message
- https://discord.js.org/docs

## Start with the user experience

Choose the simplest supported message layout that makes the task understandable. Traditional embeds and action rows remain useful for many bots. Components V2 provides richer composition, but should not be used merely because it is newer.

## Before implementation

Check:
- The current Components V2 message flag and required payload shape.
- Whether the selected library version exposes the required builders and types.
- Component nesting and valid parent/child combinations.
- Current limits for components, rows, text, media, and files.
- Whether the message can be edited and which fields remain available.
- Whether the design requires legacy content/embeds or a V2-only layout.
- Client support and rendering differences.

Never copy an old code sample without checking it against the installed version and current Discord documentation.

## Layout guidance

Use components according to their semantic role:
- Containers to group related content.
- Text displays for readable copy and headings.
- Sections for structured content with accessories.
- Separators to establish visual grouping.
- Media galleries for related images.
- File and media components for supported attachments.
- Buttons and select menus for explicit actions.

Keep hierarchy clear. Do not overload a message with nested panels, decorative separators, or excessive controls. Use concise labels and group related actions.

## Interaction safety

A component's custom ID is a routing value, not an authorization token. Every interaction must verify:
- The user is allowed to interact with this message/workflow.
- The guild and channel match the expected context.
- The referenced record exists and is still active.
- The requested state transition is valid.
- The operation has not already been completed.

For destructive actions, use a confirmation step and make the final operation idempotent.

## Rendering and testing

Test messages in an actual Discord test guild:
- Desktop and mobile clients.
- Long and short content.
- Missing or inaccessible media.
- Disabled, expired, and stale controls.
- Permission-denied and already-completed states.
- Screen-reader and keyboard usability where applicable.

If V2 support is unavailable in the installed library, update the library deliberately or use a compatible simpler layout. Do not invent builder names, component types, or flags.
