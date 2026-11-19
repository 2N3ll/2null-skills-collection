# Defensive security review checklist

Review code and configuration, record evidence and recommend established protective controls.

- Identity: supported session and identity-provider integrations, token lifecycle/validation, secure cookies, password storage, revocation, account recovery and MFA where appropriate.
- Authorization: server-side role/capability policies, ownership and tenant separation, least privilege, safe defaults, restricted administrative actions, privacy-conscious responses.
- Input and output: schema validation, parameterized database operations, context-appropriate encoding, safe rendering, trusted outbound destination policy, constrained file handling and request sizes.
- Data: encryption where required, sensitive field filtering, retention/deletion policy, backups, protected credentials, no secret values in logs, frontend bundles or public configuration.
- Integrations: signature verification, replay prevention through supported provider mechanisms, idempotent processing, timeout and concurrency limits.
- Browser protections: appropriate cookie attributes, CSRF controls, narrow CORS, content security policy and relevant security headers. Verify framework requirements and legitimate cross-origin needs.
- Dependencies: review lockfiles, maintained versions and authoritative advisory databases. Confirm applicability from dependency and configuration evidence. Recommend compatible security updates and verify tests.
- Infrastructure: separate development and production settings, least-privilege service credentials, secure transport, minimal exposed diagnostics, protected storage, safe error responses.
- Operations: rate and resource limits appropriate to workload, privacy-conscious audit logs for privileged operations, incident response and recovery planning.
- Business invariants: review transaction boundaries, authoritative calculations, lifecycle validation, duplicate-sensitive actions and concurrency protections through code and normal-path synthetic fixtures.

Never include attack payloads, exploit development, bypass procedures or credential values in findings.
