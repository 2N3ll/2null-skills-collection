# Reporting findings

## Severity
| Level | Meaning |
|---|---|
| Critical | Primary journey blocked, essential control inaccessible, or serious irreversible mistake likely |
| High | Major friction or repeated failures in important tasks |
| Medium | Recoverable confusion, inconsistent behaviour, or meaningful visual/usability issue |
| Low | Minor polish or limited-context friction |

Base priority on impact, frequency, reach and confidence, not subjective visual preference. Label confidence as confirmed, inferred or needs verification.

## Finding template
- ID and short title.
- Severity and confidence.
- Screen/route, viewport or platform, and affected journey.
- Evidence: what was actually observed; include screenshot annotation or component reference where available.
- User impact: consequence for a specific user task.
- Recommendation: concrete, proportionate change.
- Acceptance criteria: observable expected outcome.

Example: **High · Confirmed — Save action covered at narrow viewport.** On the settings screen at 390px width, the sticky toolbar overlaps Save. Users cannot complete edits without rotating or zooming. Move the toolbar into the responsive layout and reserve adequate content space. Accept when Save remains visible and reachable at the tested widths with keyboard and touch.

## Summary
State goal, scope, tested routes and viewports, methods, limitations, top priorities, then findings. Separate verified failures from potential risks. Group related defects under a shared root cause; identify quick fixes versus design-system or architecture changes. Avoid numerical grades unless the rubric, coverage and measurement methodology are explicit.
