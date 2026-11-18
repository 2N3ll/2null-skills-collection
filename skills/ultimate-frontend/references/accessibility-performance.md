# Accessibility, responsiveness, and performance

## Reduced motion

- Respect `prefers-reduced-motion: reduce`.
- Remove non-essential parallax, large movement, scrubbed scenes, and looping effects when reduced motion is enabled.
- Do not hide essential content until an animation runs.
- Provide immediate state changes and clear interaction feedback.
- If a library has a reduced-motion option, use it; otherwise implement a reliable alternative.

## Keyboard and semantics

- Use semantic elements: buttons for actions, anchors for navigation, and appropriate form controls.
- Ensure all interactions work without a pointer.
- Preserve visible focus indicators.
- Do not make hover the only way to reveal information.
- Ensure animated menus and dialogs manage focus correctly.
- Avoid keyboard traps and respect Escape behaviour where expected.
- Keep DOM reading order aligned with visual reading order.

## Responsive and touch behaviour

- Test narrow screens, touch, orientation changes, and dynamic viewport sizes.
- Do not rely on hover or cursor position for essential interactions.
- Reduce or replace expensive effects on low-power devices when appropriate.
- Avoid fixed-height sections that clip content at short viewport heights.
- Ensure pinned scroll scenes have a usable mobile alternative.

## Performance

- Prefer transform and opacity for animation.
- Avoid unnecessary React rerenders during high-frequency animation.
- Keep event listeners and observers scoped and clean them up.
- Avoid excessive simultaneous animations and large numbers of animated nodes.
- Use image dimensions, responsive image sources, and lazy loading appropriately.
- Avoid loading animation libraries on pages that do not use them.
- Consider dynamic imports for non-critical interactive sections.
- Avoid unnecessary layout thrashing and repeated measurements.
- Test on a real mobile device where possible.

## Validation

- Run lint, typecheck, tests, and production build where available.
- Check console and network errors.
- Verify no hydration mismatch or flash of hidden content.
- Inspect keyboard navigation and reduced-motion mode.
- Check layout at mobile, tablet, and desktop widths.
- Confirm animation and scroll instances clean up after route changes.
