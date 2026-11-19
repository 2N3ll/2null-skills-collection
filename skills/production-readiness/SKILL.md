---
name: production-readiness
description: Assess whether an application is ready to release or deploy by coordinating code quality, defensive security, UI/UX, backend reliability, testing, configuration, deployment, observability and recovery checks. Use for pre-release audits, launch checklists, go/no-go assessments, release blockers, staging validation and production handoff.
---

# Production Readiness

Act as a release reviewer. Produce an evidence-led go/no-go recommendation for a specific version, environment and release scope. A working build alone does not establish readiness.

## Operating rules

- Start read-only. A readiness review does not authorize deployment, publishing, production changes, credential rotation, migrations or destructive actions.
- Inspect source, existing checks, configuration templates, release documentation and available authorized test evidence. Do not expose secrets or probe live systems.
- Treat missing evidence as unverified, not passed. Distinguish observations, requirements, assumptions and recommendations.
- Scale the gate to the product's risk, complexity and release scope; do not require unnecessary infrastructure.
- Use defensive security source review and policy regression checks, not exploit development, offensive automation or attack reproduction.

## 1. Define the release

Identify target version/commit, product features, expected users, deployment environment, changed components, critical workflows, data sensitivity, external integrations, migrations and rollback needs. Record what is and is not in scope.

## 2. Coordinate specialist reviews

Use the following skills if installed and relevant. If unavailable, perform the equivalent scoped review using the checklist; do not claim a skill ran unless it did. Avoid duplicate checks and consolidate findings. Use read-only specialist workflows.

| Review | Skill |
|---|---|
| Interface implementation and motion | ultimate-frontend |
| Backend contracts and reliability | ultimate-backend |
| Discord bot behaviour and configuration | discord-platform-engineer |
| Usability and accessibility | ui-ux-auditor |
| Defensive security and route policy | security-auditor |
| Correctness and maintainability | code-quality-auditor |
| Test coverage and verification | ultimate-testing |
| Root cause of blocking failures | bug-investigator |

Read [Release gates](references/release-gates.md) for the criteria and [Release report](references/release-report.md) for decision rules.

## 3. Collect evidence

Verify available lint, typecheck, build, test and migration-check outputs in authorized isolated environments. Inspect actual user workflows when possible with synthetic data. Review configuration requirements, runtime compatibility, deployment steps, monitoring, backup and rollback plans. Record exact versions, commands, results and limitations.

Review the release-risk checklist even if specialist skills are unavailable. Mark each gate pass, fail, not applicable or unverified. Do not turn unverified mandatory checks into passes.

## 4. Decide and plan

Assign severity, ownership and evidence to each blocker and risk. Prioritize critical user workflow failures, known high-impact security or data-integrity defects, failed required checks, and unsafe release or recovery procedures.

Recommend NO-GO, CONDITIONAL GO or GO based on the evidence and risk acceptance criteria. A recommendation is not authorization to release. If a mandatory critical gate fails or is unverified, recommend NO-GO until resolved.

Provide a sequenced action plan, acceptance criteria, and post-release monitoring/rollback triggers. Make no production changes unless separately authorized.
