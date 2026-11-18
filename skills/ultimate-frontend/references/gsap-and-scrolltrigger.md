# GSAP and ScrollTrigger implementation

Official documentation is authoritative and may change:
- https://gsap.com/docs/
- https://gsap.com/docs/v3/Plugins/ScrollTrigger/
- https://gsap.com/resources/React/

## When to use GSAP

Choose GSAP for coordinated timelines, complex sequences, scroll-driven scenes, precise control, and interactions that need to be paused, reversed, or synchronised. Prefer CSS transitions/keyframes for simple hover and state transitions.

## React lifecycle

- Prefer the official `@gsap/react` integration and `useGSAP()` when it fits the project.
- Scope animations to a component container.
- Use context-safe patterns for animations created by delayed callbacks or event handlers.
- Clean up timelines and ScrollTriggers on unmount.
- Avoid global selectors and duplicate animation setup.
- Do not mutate React-managed DOM structure behind React's back.

Example pattern (adapt to the installed GSAP version and project conventions):

```jsx
import { useRef } from "react";
import gsap from "gsap";
import { useGSAP } from "@gsap/react";

gsap.registerPlugin(useGSAP);

function Hero() {
  const root = useRef(null);

  useGSAP(() => {
    gsap.from("[data-hero-item]", {
      y: 24,
      opacity: 0,
      duration: 0.7,
      stagger: 0.12,
      ease: "power3.out",
    });
  }, { scope: root });

  return (
    <section ref={root}>
      <h1 data-hero-item>Make something memorable.</h1>
      <p data-hero-item>Supporting copy goes here.</p>
    </section>
  );
}
```

Check the current official React guide for the correct package setup, plugin registration, and cleanup semantics.

## Timeline design

- Use one timeline for a related sequence.
- Prefer relative positions and labels over many arbitrary delays.
- Keep durations purposeful and consistent.
- Avoid animating too many elements at once.
- Make the first meaningful content visible promptly.
- Use `fromTo()` when explicit start and end states prevent state ambiguity.
- Avoid animating layout properties when transforms can achieve the same result.

## ScrollTrigger

- Use ScrollTrigger for scroll-linked reveals, progress indicators, pinned scenes, and scrubbed sequences.
- Use meaningful trigger elements and start/end positions.
- Avoid pinning large portions of a page without a strong narrative reason.
- Test refreshes, responsive layout changes, image loading, font loading, and route transitions.
- Kill or revert triggers when their owning component is removed.
- Do not create a ScrollTrigger for every tiny decorative element.
- Ensure hidden/revealed content remains accessible and does not disappear permanently if JavaScript fails.

## Property ownership

Never let GSAP and CSS independently animate the same property on the same element at the same time. Define which system owns each animated property. Keep hover/focus transitions in CSS where practical and reserve GSAP for orchestrated motion.

## Performance

- Prefer transforms and opacity.
- Avoid large blur filters, huge animated shadows, and continuous layout recalculation.
- Avoid animating hundreds of DOM nodes individually.
- Use batching or a small number of parent-level effects where appropriate.
- Do not run animations when elements are offscreen unless needed.
- Respect reduced-motion preferences and provide a non-animated state.
