# Audit checklist

Select checks that fit the product; mark not applicable and untested separately.

## Visual and content
- Clear page purpose, primary action and meaningful headings.
- Consistent typography, alignment, spacing, tokens, surfaces and icon language.
- Legible size, line length, line height and foreground/background contrast.
- Distinct interactive, selected, disabled, loading, error and focus states.
- Specific labels and helpful copy; no unexplained jargon or misleading affordances.
- Preserve useful information density for professional tools; whitespace alone is not quality.

## Task completion
- Entry points are discoverable; navigation labels match content.
- Search/filter/sort controls provide meaningful feedback and reset options.
- Forms have persistent labels, appropriate input types, meaningful validation and preserved user input on failure.
- System status, progress, success and errors are understandable. Recovery steps are actionable.
- High-risk actions have suitable confirmation and undo/recovery when possible.
- Empty, first-run, offline, slow network and partial failure states guide the next step.

## Responsive and interaction
- Test available narrow, medium and wide viewport sizes; record actual dimensions.
- Inspect horizontal overflow, fixed/sticky overlays, content truncation, menu placement and long localized text.
- Check touch targets, pointer/hover independence, keyboard navigation and scroll behaviour.
- Verify dialogs and menus maintain predictable focus, closing and return-focus behaviour.
- Inspect zoom/reflow and text resizing where possible; prioritize essential content and controls.
- Motion conveys state without blocking progress; respect reduced-motion settings.

## Accessibility
Use the relevant version of WCAG and official W3C guidance (https://www.w3.org/WAI/standards-guidelines/wcag/). Verify exact success criterion and applicability before citing compliance.
- Semantic headings, landmarks, names, labels and control roles.
- Keyboard access, logical focus order, visible focus and no unintended traps.
- Measure contrast for actual rendered colours with appropriate text size and state; avoid relying on colour alone.
- Alternatives for meaningful imagery; accessible status and validation messages.
- Captions/transcripts for relevant media.
- Evaluate automated findings manually; report assistive technology checks only when actually performed.

## Performance perception
- Look for layout movement, delayed feedback, unresponsive interactions and excessive animation.
- Measure with available tools and state conditions. Distinguish laboratory measurements from actual user data.
- Recommend prioritized payload, rendering or interaction improvements based on evidence.
