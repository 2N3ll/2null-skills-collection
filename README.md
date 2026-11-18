# 2null Skills Collection

A collection of reusable skills for AI coding agents.

## Available skills

### [Ultimate Frontend](./skills/ultimate-frontend/SKILL.md)

A unified frontend design and engineering skill combining:
- **Frontend Design** — art direction, layout, typography, visual hierarchy, responsive design, and design systems.
- **GSAP** — timelines, interaction animation, and ScrollTrigger-driven experiences.
- **Lenis** — smooth scrolling and coordinated scroll behaviour.
- **React Bits** — expressive React components and visual effects.

The skill is framework-aware: React Bits is used only in React projects (or React islands), while the design and appropriate motion guidance can be applied to other frontend stacks.

## Install

Using the Skills CLI:

```bash
npx skills add 2N3ll/2null-skills-collection --skill ultimate-frontend
```

For details about the Skills ecosystem and supported agents, see https://skills.sh/.

## Structure

```text
skills/
└── ultimate-frontend/
    ├── SKILL.md
    └── references/
        ├── accessibility-performance.md
        ├── design-system.md
        ├── gsap-and-scrolltrigger.md
        ├── lenis-integration.md
        └── react-bits.md
```

## Principles

- Design quality before effects.
- Use only the libraries a project actually needs.
- Inspect existing code before changing its architecture.
- Prioritise accessibility, responsive behaviour, and performance.
- Verify current library documentation rather than relying on stale snippets.
