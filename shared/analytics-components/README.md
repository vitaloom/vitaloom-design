# Shared Analytics Presentation — Steps + Heart Rate

**Status:** PROPOSED shared UI guideline; frontend owns actual components. This folder is not an API/BFF schema and does not supersede the live app design system.

**New independent artwork:** [Steps illustration](../../assets/steps/README.md) · [HR illustration](../../assets/heart-rate/README.md) · [Analytics icon set](../../assets/shared/analytics-icons/README.md). **Current UI enhancement task:** [Implementation handoff](../../UI_ENHANCEMENT_HANDOFF.md).

## Suggested reusable frontend pieces

| Concept | Responsibility | Ownership |
| --- | --- | --- |
| `AnalyticsPeriodSwitcher` | Day / Week / Custom selection with stateful active treatment | Shared FE |
| `DateScopePicker` | Valid day/week/custom date selection (limits delegated to per-feature canonical API) | Shared FE |
| `ChartFrame` | Numeric Y-axis, units, horizontal grid, X-axis, focus, responsive/scroll layout | Shared FE |
| `ChartTooltip` | Data-point/bucket hover/tap/focus, smart placement and dismissal | Shared FE |
| `InsightTile` | Semantic stat label/value/unit and unavailable state | Shared FE |
| `MetricStateBoundary` | Loading/empty/error/retry separation for each independent section | Shared FE |
| `MetricHero` | Visually consistent rounded hero container with metric-specific art | Shared FE |
| `HealthMetricsDrawer` | **Already belongs to AppShell**, not duplicated here | [Existing shared spec](../health-metrics-sidebar/README.md) |

**Feature-owned:** StepsBarChart and HeartRateRangeLineChart (do **not** force both into the same series geometry). Both use shared ChartFrame and Tooltip where suitable.

## Palette direction

- Steps: mint/teal/emerald light hero and bar highlights.
- Heart Rate: blush/coral + dark text hero, coral mean dots/line, faint min/max whiskers.
- Dark: dark teal/charcoal canvas, uplifted card surfaces, mint + rose accents; preserve contrast, never invert chart blindly.
- Follow actual frontend theme tokens first. The [theme tokens](THEME_TOKENS.md) are visual **fallback references** only.

See [Chart interactions](CHART_INTERACTIONS.md), [Steps](../../steps/README.md), [Heart Rate](../../heart-rate/README.md).

## Boundaries

This repo defines observable UX, not React Native code, API schemas, backend response types, data pipeline, cache policy or persistence. Do not create a parallel list of backend DTOs here. Before implementation open each feature's REFERENCES.md and read the actual linked backend/BR sources.
