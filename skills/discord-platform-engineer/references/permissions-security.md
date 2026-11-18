# Discord permissions and application security

Primary references:
- https://discord.com/developers/docs/topics/permissions
- https://discord.com/developers/docs/topics/oauth2
- https://discord.com/developers/docs/events/gateway

## Understand the permission layers

These mechanisms are related but not interchangeable:

1. OAuth2 scopes determine what an authorization or installation grants.
2. Bot permission bitfields determine what the bot can do in a guild or channel.
3. Gateway intents determine which event categories the application receives.
4. Command default permissions and command permissions affect command availability.
5. Application authorization determines whether this particular user may perform this particular action.

Always enforce sensitive operations in application code, even if Discord hides the command or the UI disables a button.

## Least privilege

Create a permission matrix per feature. For each action, identify:
- User permission or application role required.
- Bot permission required.
- Role hierarchy constraints.
- Channel-specific overwrites.
- Required Gateway intents.
- Required OAuth2 scopes.

Do not ask users to grant Administrator when a narrow set of permissions is sufficient. Explain why each privileged intent is needed and enable it in the Developer Portal only when necessary.

## Role hierarchy

Before managing roles, members, timeouts, or bans:
- Check the bot's effective permissions in the target channel/guild.
- Check role hierarchy and whether the target is manageable.
- Handle owners, administrators, and higher-ranked roles safely.
- Re-check state immediately before the API operation.
- Provide a useful failure message when Discord rejects the action.

## OAuth2 and dashboards

- Keep client secrets, bot tokens, and refresh tokens on the server.
- Validate OAuth2 state to protect the authorization callback against CSRF.
- Use PKCE when applicable to the chosen OAuth2 flow.
- Request only the scopes required.
- Validate callback errors and state before creating a session.
- Use secure, HTTP-only, appropriately SameSite cookies.
- Protect state-changing dashboard routes against CSRF.
- Check guild membership and permissions server-side for each privileged request.
- Never trust a guild ID, role ID, or permission value supplied by the browser.

## Secrets and data

- Keep secrets out of source control, frontend bundles, logs, screenshots, and error reports.
- Use secret managers or environment variables and rotate exposed credentials.
- Redact interaction tokens and webhook URLs.
- Collect only the user data the feature needs.
- Define retention and deletion behaviour for transcripts, logs, and support records.
- Restrict access to staff notes and exported data.

## Mentions and untrusted input

- Explicitly control allowed mentions when sending user-generated content.
- Escape or constrain Markdown and formatting.
- Validate attachment sizes and types.
- Avoid fetching arbitrary user-supplied URLs from privileged servers.
- Use request timeouts and destination allowlists for external fetches.
- Use parameterised SQL and safe serialization.
- Never execute user-provided code or shell commands.
