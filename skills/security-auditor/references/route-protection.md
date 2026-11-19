# Route and access-control review

Build a protection inventory from the application's declared routing and server-side handlers. Determine intended access from product requirements, policies and existing tests; flag ambiguity instead of guessing.

| Route class | Expected protection |
|---|---|
| Public landing/help/health | Deliberately public, minimal data, bounded resources |
| Account dashboard | Valid session and relevant account membership |
| Tenant resources | Valid identity and server-enforced tenant/resource scope |
| Admin and staff | Explicit server-side role or capability policy |
| Webhook | Provider-supported authenticity verification |
| Internal job/service | Appropriately scoped service identity |
| Real-time subscription | Verified identity and authorization for subscribed resource |
| Login/callback/reset | Intended public entry point with appropriate state and lifecycle controls |

## Review method
- Inspect route registration and the framework's middleware/handler composition. Confirm intended policy is actually attached to each protected action.
- Inspect server actions and underlying business services as well as page rendering. A redirect or hidden element is user experience, not authorization.
- Verify access decisions use authenticated server-side identity and authoritative membership records.
- Check ownership scope in the data layer; sensitive reads, writes, deletes, imports and exports require appropriate policy.
- Review authorization after permission changes, session expiry and membership removal. Do not trust stale client state.
- Identify routes without clear intended audiences. Ask for clarification or recommend a conservative default while preserving legitimate public access.
- Document safe denial semantics appropriate to the application: sign-in, access denied, or neutral not-found behaviour without sensitive details.
- Review policies in source and isolated policy unit tests. Do not attempt bypasses or interact with external systems.

## Remediation acceptance
Use a shared, well-tested policy where appropriate. Test synthetic identity fixtures for anonymous, ordinary member, permitted owner, administrator and non-member decisions. Verify intended public flows remain usable, and that protected operations return only authorized data. Keep identity and policy checks server-side even when frontend navigation also enforces them.
