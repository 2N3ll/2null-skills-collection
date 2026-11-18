# Lenis smooth scrolling

Official documentation: https://github.com/darkroomengineering/lenis

Always check the current documentation and installed package version before implementing. Lenis setup APIs and recommended integrations can evolve.

## Decide whether Lenis is appropriate

Use it when the design benefits from a consistent smooth-scroll feel and the page uses a conventional scrolling surface. Keep native scrolling when it is simpler, more accessible, or more reliable.

Be cautious with:
- Nested scroll containers.
- Dialogs and drawers with internal scrolling.
- Complex sticky and fixed layouts.
- Full-page routing transitions.
- Mobile touch behaviour.
- Browser-native scroll restoration and anchor navigation.

## Lifecycle

- Create one instance for the intended scroll surface.
- Keep the instance in an appropriate application-level owner.
- Destroy it when that owner unmounts.
- Do not create one instance per component or section.
- Avoid multiple animation-frame loops.
- Preserve native links, keyboard scrolling, focus movement, and browser history.

## GSAP ScrollTrigger integration

When GSAP ScrollTrigger is present, use the current Lenis-recommended integration. The common integration pattern is to notify ScrollTrigger when Lenis scrolls and drive Lenis from GSAP's ticker, but verify the exact current API and ticker time units in the official documentation before copying code.

Do not run both an independent Lenis RAF loop and a GSAP ticker loop for the same instance.

After major layout changes, ensure the scroll system and ScrollTrigger measurements are refreshed at an appropriate time. Avoid excessive refresh calls.

## Reduced motion

Read the user's reduced-motion preference. When reduced motion is requested, disable or simplify smooth scrolling and scroll-linked effects. Do not make essential navigation depend on smooth scrolling.

## Test checklist

- Mouse wheel and trackpad.
- Touch scrolling on mobile.
- Keyboard scrolling and Page Up/Page Down.
- Anchor links.
- Focus moving to offscreen content.
- Browser back/forward and scroll restoration.
- Dialog and nested-container scrolling.
- Sticky and fixed elements.
- Reduced-motion mode.
- Route changes and teardown.
