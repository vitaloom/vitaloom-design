# Analytics icons — visual source files

These are **independent original SVG icons**, each with a 24×24 viewBox. The SVG source uses `currentColor` so native FE components can apply semantic colors with `react-native-svg` (or corresponding existing icon adapters). For image loaders that do not inherit `currentColor`, replace it via a component-level tint or an explicit parsed SVG color; do not treat black default as the intended feature color.

| Purpose | Asset |
| --- | --- |
| Analytics title | [chart-bars.svg](chart-bars.svg) |
| Time and record coverage | [clock.svg](clock.svg) |
| Steps increments | [record-stack.svg](record-stack.svg) |
| Peak hour | [crown-peak.svg](crown-peak.svg) |
| HR latest / mean | [heart-pulse.svg](heart-pulse.svg) |
| Low range | [trend-low.svg](trend-low.svg) |
| High range | [trend-high.svg](trend-high.svg) |
| Data caveat | [info-circle.svg](info-circle.svg) |
| Day navigation | [calendar.svg](calendar.svg) |
| Step marker | [footsteps.svg](footsteps.svg) |

**No external image fetch, font asset, or icon-service dependency is required.** All icons are editable vectors. Preserve 44dp accessible hit targets for interactive controls; the visible icon can remain ~18–24dp. If the app already uses equivalent icons from an installed library, using those native icons is acceptable when the resulting visuals match the reference.

Other assets: [Steps](../../steps/README.md), [Heart Rate](../../heart-rate/README.md), [UI handoff](../../../UI_ENHANCEMENT_HANDOFF.md).
