# 35ni Skills Collection

A collection of reusable skills for AI coding agents.

## Available skills

### [Ultimate Frontend](./skills/ultimate-frontend/SKILL.md)

A unified frontend design and engineering skill combining:
- **Frontend Design** — art direction, layout, typography, visual hierarchy, responsive design, and design systems.
- **GSAP** — timelines, interaction animation, and ScrollTrigger-driven experiences.
- **Lenis** — smooth scrolling and coordinated scroll behaviour.
- **React Bits** — expressive React components and visual effects.

The skill is framework-aware: React Bits is used only in React projects (or React islands), while the design and appropriate motion guidance can be applied to other frontend stacks.

### [Discord Platform Engineer](./skills/discord-platform-engineer/SKILL.md)

A production-focused Discord engineering skill covering:
- **Commands & interactions** — slash commands, context menus, autocomplete, buttons, select menus, and modals.
- **Components V2** — modern message layouts, component architecture, and rendering validation.
- **Security & permissions** — OAuth2, Gateway intents, least privilege, role hierarchy, and server-side authorization.
- **Production operations** — persistence, rate limits, queues, deployment, monitoring, and scaling.
- **Testing** — unit, integration, concurrency, and test-guild validation.

### [Ultimate Backend](./skills/ultimate-backend/SKILL.md)

A framework-aware backend engineering skill covering API contracts, business logic, databases, migrations, authentication, authorization, webhooks, background jobs, caching, real-time integrations, reliability, and deployment.

### [UI/UX Auditor](./skills/ui-ux-auditor/SKILL.md)

An evidence-driven interface review skill covering visual hierarchy, usability, responsive layouts, accessibility, interaction states, task completion, and prioritized improvements with acceptance criteria.

### [Security Auditor](./skills/security-auditor/SKILL.md)

A defensive application security review skill covering missing route protection, authentication, authorization, tenant isolation, insecure configuration, dependencies, secrets, and prioritized vulnerability remediation with defensive regression checks.

### [Code Quality Auditor](./skills/code-quality-auditor/SKILL.md)

A DeepScan-inspired static analysis skill covering correctness bugs, unused declarations and dependencies, dead code, duplication, complexity, and behavior-preserving refactoring recommendations across languages.

### [Ultimate Testing](./skills/ultimate-testing/SKILL.md)

A framework-aware testing skill covering unit, integration, contract, component and end-to-end tests, regression prevention, deterministic fixtures, flaky-test diagnosis and CI verification.

### [Bug Investigator](./skills/bug-investigator/SKILL.md)

An evidence-driven debugging skill covering root-cause analysis, log interpretation, hypothesis testing, minimal durable fixes and regression verification.

### [Production Readiness](./skills/production-readiness/SKILL.md)

A release-review skill coordinating the collection's specialist skills to assess functionality, security, code quality, usability, reliability, deployment and recovery through evidence-based go/no-go gates.

## Install

Using the Skills CLI:

```bash
npx skills add 35ni/35ni-skills --skill ultimate-frontend
npx skills add 35ni/35ni-skills --skill discord-platform-engineer
npx skills add 35ni/35ni-skills --skill ultimate-backend
npx skills add 35ni/35ni-skills --skill ui-ux-auditor
npx skills add 35ni/35ni-skills --skill security-auditor
npx skills add 35ni/35ni-skills --skill code-quality-auditor
npx skills add 35ni/35ni-skills --skill ultimate-testing
npx skills add 35ni/35ni-skills --skill bug-investigator
npx skills add 35ni/35ni-skills --skill production-readiness
```

For details about the Skills ecosystem and supported agents, see https://skills.sh/.

## Structure

```text
skills/
├── ultimate-frontend/
│   ├── SKILL.md
│   └── references/
├── discord-platform-engineer/
│   └── SKILL.md
├── ultimate-backend/
│   ├── SKILL.md
│   └── references/
├── ui-ux-auditor/
│   ├── SKILL.md
│   └── references/
├── security-auditor/
│   ├── SKILL.md
│   └── references/
├── code-quality-auditor/
│   ├── SKILL.md
│   └── references/
├── ultimate-testing/
│   ├── SKILL.md
│   └── references/
├── bug-investigator/
│   ├── SKILL.md
│   └── references/
└── production-readiness/
    ├── SKILL.md
    └── references/
```

## Principles

- Design quality before effects.
- Use only the libraries a project actually needs.
- Inspect existing code before changing its architecture.
- Prioritise accessibility, responsive behaviour, and performance.
- Verify current library documentation rather than relying on stale snippets.
