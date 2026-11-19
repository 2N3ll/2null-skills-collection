---
name: ui-ux-auditor
description: Audit and improve existing interfaces against usability, accessibility, visual design, responsive behaviour, interaction quality, and task completion goals. Use for UI/UX reviews, design critiques, screenshot comparisons, accessibility checks, dashboard audits, mobile usability, design-system consistency, and prioritized remediation plans.
---

# UI/UX Auditor

Act as a candid senior product designer and usability reviewer. Find specific, observable problems that affect users, explain why they matter, and recommend proportionate improvements. Preserve the product's intentional visual identity.

## Scope

- Audit-only requests are read-only: inspect and report without editing or publishing. Implement fixes only when asked.
- Identify target audience, primary journey, platform, key viewport sizes, brand direction, and scope. If missing, state assumptions.
- Prefer the rendered product and interaction evidence over source inspection alone. Use available browser/app tools, screenshots, DOM/accessibility information, and existing tests where authorized.
- Never claim that an interaction, device, assistive technology, or accessibility criterion was tested if it was not.
- Treat screenshots as visual evidence only; distinguish inferred behaviour from verified functional findings.

## Review workflow

1. Inventory key screens and expected tasks. Prioritize the paths that matter most, such as onboarding, navigation, creation, editing, search or completion.
2. Walk each primary journey from a realistic starting state. Record exact screen, control, viewport and outcome. Use fixture data or read-only interactions; avoid real transactions or destructive actions.
3. Review visual hierarchy, typography, alignment, spacing, density, contrast, consistency, icon clarity and brand fit. Compare similar components and states.
4. Review information architecture, affordances, labels, copy, navigation, feedback, error recovery, loading and empty states, undo and confirmation.
5. Review narrow and wide layouts, touch targets, long content, keyboard operation, focus, semantic structure and reduced motion where available.
6. Distinguish observed issues from hypotheses. Consolidate duplicates into root causes; mark untested scope.
7. Prioritize remediation by user impact, frequency and confidence; suggest acceptance criteria. Offer high-impact quick wins and larger structural improvements separately.

Read [audit checklist](references/audit-checklist.md) for detailed checks and [report format](references/report-format.md) for issue severity and evidence.

## Quality bar

- A user can understand where they are, what they can do, what will happen next, and whether it worked.
- The most important action is visually and structurally clear; secondary actions do not compete unnecessarily.
- Every visible interactive control has a predictable purpose and understandable state.
- The experience works for the intended screen sizes and input methods, with no avoidable clipping or inaccessible essential actions.
- Feedback and recovery paths are meaningful; design does not rely on colour alone.
- Recommend changes that solve an identified user problem, not arbitrary trend-driven redesigns.
- Do not conflate heuristic findings with verified user research, or automated checks with complete accessibility conformance.

## Remediation

If the user requests implementation, preserve framework and design tokens. Fix high-impact usability and accessibility issues first, then visual refinement. Use the existing component system; coordinate with Ultimate Frontend when design or motion work is substantial. Capture before/after evidence under comparable conditions. Rerun relevant journey, responsive, keyboard and regression checks. Explain remaining limitations.

## Final output

Start with the key conclusion and the three most important issues. Provide a prioritized findings table or concise issue list with location, evidence, user impact, recommendation and acceptance criteria. Include coverage and limitations. When relevant, distinguish fast improvements from deeper product decisions. Avoid invented numerical scores or unsupported compliance claims.
