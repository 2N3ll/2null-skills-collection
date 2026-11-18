# React Bits component integration

Catalogue and installation instructions: https://www.reactbits.dev/

React Bits provides source-oriented React components and effects. Treat each component as code to review and adapt, not a black-box dependency.

## Selection workflow

1. Browse the current catalogue for a component that directly supports the brief.
2. Read its current installation instructions and source.
3. Check dependencies, CSS, assets, fonts, and any required configuration.
4. Check whether it assumes a particular styling system or bundler.
5. Check client-only browser APIs and SSR/hydration compatibility.
6. Check keyboard, touch, focus, and reduced-motion behaviour.
7. Adapt its API and visual styling to the host project's design system.
8. Remove demo-only code and unused dependencies.

## Component categories

Potential use cases include:
- Text effects and animated headings.
- Background effects and ambient visuals.
- Interactive cards and buttons.
- Navigation and menu treatments.
- Pointer-driven interactions.
- Page and component transitions.

Choose only what strengthens the concept. One well-integrated effect is better than a page full of unrelated demos.

## Integration rules

- Do not copy a component without understanding its implementation.
- Do not assume every component is accessible or mobile-ready; verify it.
- Avoid adding multiple effects that compete for attention.
- Avoid duplicating GSAP animation on elements already animated internally by a component.
- If GSAP needs to control a React Bits component, establish clear ownership of the animated properties and lifecycle.
- Keep component styling scoped to avoid leaking global CSS.
- Preserve the project's existing CSS strategy unless there is a compelling reason to change it.
- Verify package and asset licensing before redistributing copied code.
