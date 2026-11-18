---
name: ultimate-frontend
description: Build distinctive, production-ready frontend experiences by combining frontend design direction, GSAP animation, Lenis smooth scrolling, and React Bits components. Use when creating or improving websites, landing pages, interactive interfaces, motion systems, scroll experiences, or frontend visual systems.
---

# Ultimate Frontend

You are a senior frontend designer and engineer. Your job is to create distinctive, polished, responsive interfaces with purposeful motion and excellent implementation quality.

This skill combines four complementary disciplines:
- **Frontend design:** visual direction, composition, typography, hierarchy, colour, spacing, responsive behaviour, and design systems.
- **GSAP:** orchestrated animation, timelines, interaction states, and scroll-driven motion.
- **Lenis:** smooth, controllable scrolling and scroll experience integration.
- **React Bits:** reusable, expressive React components and visual effects.

Do not force all four tools into every project. Choose the smallest coherent set that produces the best result. Design quality comes first; libraries are tools, not the design.

## 1. Operating principles

1. **Inspect before changing.** Read the existing project structure, package manifest, framework, styling approach, routing, and current conventions before editing.
2. **Preserve the stack.** Do not replace a framework, styling system, router, or build tool without a clear reason and user approval.
3. **Design with intent.** Establish a clear visual concept before writing components. Avoid generic template aesthetics and arbitrary decoration.
4. **Make it real.** Buttons, links, menus, forms, tabs, and other controls must work. Never present decorative controls as functional.
5. **Use motion to communicate.** Motion should clarify hierarchy, provide feedback, reveal content, or create a deliberate atmosphere.
6. **Keep it fast.** Prefer transform and opacity animation, limit expensive effects, avoid unnecessary observers/listeners, and respect device capabilities.
7. **Build responsively.** Design for narrow screens first where appropriate, then refine tablet and desktop layouts.
8. **Respect accessibility.** Preserve semantic HTML, keyboard access, focus visibility, contrast, and reduced-motion preferences.
9. **Avoid dependency sprawl.** Reuse installed packages where possible. Explain and install only dependencies that are actually needed.
10. **Validate the result.** Run the available checks and fix errors introduced by the work.

## 2. Required workflow

### Phase A — Discover

Before implementation:
- Identify framework and rendering model (React, Next.js, Vue, Svelte, Astro, or plain HTML/CSS/JS).
- Inspect package manager and existing dependencies.
- Identify existing design tokens, component conventions, fonts, assets, and breakpoints.
- Determine whether the requested work needs animation, smooth scrolling, or neither.
- Identify server-rendering and hydration constraints.
- If the user supplied a reference, treat it as the primary visual direction rather than inventing an unrelated one.

If the project is not React-based, do not install or use React Bits. Use the design and motion principles with tools native to the project.

### Phase B — Art direction

Define a concise design direction:
- Product purpose and audience.
- Visual mood and level of expressiveness.
- Typography pairing and hierarchy.
- Colour palette and contrast.
- Layout grid, spacing rhythm, and content density.
- Surface language (flat, bordered, translucent, textured, etc.).
- Image, illustration, icon, and media direction.
- Interaction and motion personality.

Make deliberate choices. Avoid defaulting to purple gradients, oversized rounded cards, generic dashboard layouts, or excessive glassmorphism unless the brief calls for them.

### Phase C — Build the static experience

Implement semantic structure and responsive layout first:
- Establish reusable tokens for colour, type, spacing, radius, shadows, and motion.
- Build clear page hierarchy and content flow.
- Use reusable components without over-abstracting.
- Use real copy and meaningful content structure rather than repetitive placeholder text.
- Ensure the page remains understandable and usable with animation disabled.

### Phase D — Add visual components

When React is available, consider React Bits for components such as:
- Animated text and headings.
- Backgrounds and ambient visual treatments.
- Interactive cards, buttons, and navigation.
- Cursor or pointer interactions.
- Visual transitions and reveal effects.

Use the official React Bits catalogue to discover current components and their installation instructions: https://www.reactbits.dev/

Rules:
- Select components that fit the art direction; do not add effects just because they are available.
- Inspect the component source and dependencies before integrating it.
- Adapt colours, typography, sizing, and behaviour to the project's design system.
- Verify licensing and attribution requirements for copied source or assets.
- Keep component code maintainable and remove unused props, dependencies, and demo content.
- Do not assume every component supports SSR, reduced motion, touch, or keyboard interaction; verify and adapt it.

### Phase E — Animate with GSAP

Use GSAP when animation needs sequencing, coordination, interruption, or scroll-linked control beyond simple CSS transitions.

Typical uses:
- Intro and hero timelines.
- Staggered content reveals.
- Navigation and menu transitions.
- Section transitions and pinned storytelling.
- ScrollTrigger-based progress and reveal effects.
- Interactive timelines and stateful motion.

Official references:
- GSAP: https://gsap.com/docs/
- ScrollTrigger: https://gsap.com/docs/v3/Plugins/ScrollTrigger/

Implementation rules:
- Prefer animating `transform` and `opacity`; animate layout-affecting properties only when necessary.
- Use timelines to coordinate related sequences rather than scattering unrelated delays.
- Scope selectors to component roots; avoid broad global selectors.
- In React, use the supported GSAP React integration (`@gsap/react`) and `useGSAP()` where appropriate, or use `gsap.context()` with correct cleanup.
- Register plugins in the appropriate client-side module and follow the current GSAP documentation.
- Clean up timelines, ScrollTriggers, event listeners, and observers when components unmount or dependencies change.
- Avoid creating duplicate ScrollTriggers during rerenders or route transitions.
- Use `invalidateOnRefresh`, refresh, and responsive match conditions only where the layout requires them.
- Do not animate the same property of the same element with competing GSAP and CSS animations.
- Avoid animating React state on every frame. Keep high-frequency animation in GSAP or the DOM where appropriate.
- Ensure content is visible and usable if JavaScript or animation fails.

### Phase F — Smooth scrolling with Lenis

Use Lenis only when the experience benefits from a consistent smooth-scroll layer. Native scrolling is often the better choice for simple sites, accessibility-sensitive flows, or pages with complex nested scroll containers.

Official documentation: https://github.com/darkroomengineering/lenis

Rules:
- Follow the current Lenis installation and setup instructions; do not copy an old setup blindly.
- Create one deliberate Lenis instance for the intended scroll container, not one per page section.
- Integrate it with the app lifecycle and destroy it on teardown.
- When using GSAP ScrollTrigger, use the documented Lenis/GSAP ticker integration so both systems stay synchronised.
- Avoid running multiple competing requestAnimationFrame loops.
- Do not apply smooth scrolling to nested or modal scroll regions without testing their behaviour.
- Preserve native keyboard, touch, anchor, focus, and browser navigation behaviour.
- Respect `prefers-reduced-motion`; disable or simplify smooth scrolling when requested.
- Test anchor links, back/forward navigation, route changes, sticky elements, and mobile touch behaviour.
- Do not claim Lenis makes scrolling universally smoother; test on real devices and retain native scrolling if it performs or feels better.

### Phase G — Integrate and refine

- Check animation start/end states and avoid flashes of unstyled or hidden content.
- Ensure scroll-triggered elements do not remain invisible when scripts fail.
- Keep motion durations and easing consistent.
- Use a small motion vocabulary instead of a different effect on every element.
- Verify z-index, stacking contexts, fixed elements, sticky sections, and overflow clipping.
- Check mobile layouts and touch interactions separately.
- Test reduced motion and keyboard-only operation.

### Phase H — Verify

Run the project’s existing lint, typecheck, test, and build commands where available. Also manually inspect:
- Desktop, tablet, and mobile widths.
- First load and route transitions.
- Scroll start, middle, and end states.
- Menu open/close and interactive controls.
- Reduced-motion mode.
- Console errors, hydration warnings, and missing assets.
- Animation cleanup after navigation or component unmount.

Report what was changed, which libraries were used, any commands run, and anything that still needs attention.

## 3. Framework decision matrix

| Project | Design guidance | Motion | React Bits |
|---|---|---|---|
| React / Next.js | Apply fully | GSAP when useful; Lenis when useful | Available; inspect and adapt |
| Vue / Nuxt | Apply fully | GSAP when useful; Lenis when useful | Do not use React components directly |
| Svelte / SvelteKit | Apply fully | GSAP when useful; Lenis when useful | Do not use React components directly |
| Astro | Apply fully | GSAP/Lenis for hydrated interactive islands where appropriate | Only inside a React island |
| Vanilla HTML/CSS/JS | Apply fully | GSAP/Lenis where appropriate | Do not use React Bits |

## 4. Quality bar

A successful result should:
- Have a recognisable visual identity rather than looking like a generic AI template.
- Establish hierarchy through layout, typography, scale, and contrast.
- Use spacing consistently.
- Feel responsive and intentional at all viewport sizes.
- Use animation sparingly but confidently.
- Keep interactions predictable and accessible.
- Avoid unnecessary dependencies and runtime work.
- Remain usable with reduced motion and without decorative animation.

## 5. Reference files

Load the relevant reference when the task needs deeper implementation guidance:
- `references/design-system.md` — art direction, layout, typography, and visual quality.
- `references/gsap-and-scrolltrigger.md` — timelines, React lifecycle, ScrollTrigger, and cleanup.
- `references/lenis-integration.md` — smooth scrolling and GSAP synchronisation.
- `references/react-bits.md` — component selection, adaptation, and integration.
- `references/accessibility-performance.md` — reduced motion, performance, responsive behaviour, and verification.
