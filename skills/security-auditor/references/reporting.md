# Reporting and verification

## Severity rubric

| Severity | Description |
|---|---|
| Critical | Strong code evidence of a missing protective control with potentially catastrophic business or data impact |
| High | Significant authorization, identity, sensitive-data or integrity weakness |
| Medium | Meaningful security risk with limited impact or important prerequisites |
| Low | Narrow risk or incremental hardening |
| Informational | Best-practice improvement without a demonstrated defect |

Use confidence labels confirmed from code, likely, or needs verification. Do not provide exploitability scores without sufficient evidence.

## Report structure

1. Executive summary and highest-priority remediation.
2. Scope, inspected components and limitations.
3. Route protection matrix: route/action, intended audience, observed protection, required change and status.
4. Findings: ID, severity/confidence, file/symbol, missing protective control, business impact, remediation and defensive acceptance criteria.
5. Prioritized release checklist and remaining verification.
6. If fixes were authorized, summarize changed files and actual check results.

## Verification

Use static analysis, existing repository tests and isolated unit/integration fixtures that assert correct policy decisions, safe configuration and intended legitimate functionality. Use ordinary test inputs, no attack strings or vulnerability reproduction. Do not test against third-party or production targets. Report unverified deployment behaviour explicitly.
