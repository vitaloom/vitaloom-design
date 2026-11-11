# Heart Rate — analytics interaction contract

**Status:** PROPOSED UX, pending integrated FE/BE validation. **Screen:** [HRT-SCR-001](README.md). [References](REFERENCES.md), [shared shell](../shared/health-metrics-sidebar/README.md), [shared chart UX](../shared/analytics-components/CHART_INTERACTIONS.md).

| ID | UI control | Behavior | Status |
| --- | --- | --- | --- |
| HRT-ACT-001 | Period control | Day / Week / Custom selects corresponding backend Statistics range, updates chart/time units, retains prior selection while loading. | PROPOSED |
| HRT-ACT-002 | Calendar | Day/week/month navigation must follow canonical ranges. Future dates disabled. | PROPOSED |
| HRT-ACT-003 | Dot selection | Tap/keyboard focus shows tooltip for that bucket: local time/range, min, average, max, sample count where present. | PROPOSED |
| HRT-ACT-004 | Tooltip dismissal | Tap outside, Escape/Back, period change or invalidated selection closes tooltip. | PROPOSED |
| HRT-ACT-005 | Retry/refresh | Retry specific failed request while preserving period/date and latest if independently loaded. | PROPOSED |
| HRT-ACT-006 | Shared drawer | Use existing shared AppShell drawer; closed by default. | CONFIRMED shared spec |

## Line chart truthfulness

- **Average** is a coral line with visible connected dots. **Min/max** is a subtle translucent vertical range centered on each observed bucket; tooltip numbers belong to that same bucket.
- Connect average dots **only across adjacent, nonempty buckets**. Never bridge a missing bucket with a smooth curve or line. Do not render future buckets as recorded. Gaps, not zeros, indicate missing samples.
- The graph is of aggregated observations, **not a heart monitor/ECG**, and does not imply a continuous sensor feed.
- Y-axis explicitly labels BPM. Scale includes all nonempty bucket min/max values and enough padding so extrema are not clipped or exaggerated.
- For Daily, render 15-minute buckets, with time-label spacing appropriate to screen width. Week/Custom use their canonical bucket resolutions, not hardcoded 15-minute intervals.
- Tap, keyboard and screen-reader details: anchor tooltip without covering key values; allow focus on data points, state date/time and range, meet readable contrast; reduced-motion and scroll support.
- KPI Min/Max must refer to the **same selected period and underlying available buckets**. When summary Average is a separate backend result, preserve its canonical status/date scope; do not pretend it is the arithmetic mean of plotted dots.
- **Latest Recorded** hero is always account-wide latest accepted observation; changing calendar scopes only the dated analytics and daily average, not the hero. Never relabel Latest as Live or Current.
- For historical dates, display backend completeness/unverified status. Today is provisional. Never infer data completeness or health normality from BPM or elapsed time.

## Missing/error states

| State | Required UX |
| --- | --- |
| Loading | Skeleton charts/KPIs for pending data; keep static text and active selection; latest may render independently. |
| No latest / no chart | Each region is independently empty. Never use 0 BPM. |
| Partial day | Current-day summary marked provisional and clearly scoped. |
| Historical unverified | Show caution sourced from backend status; do not manufacture verification. |
| Error | Explicit fetch error with retry; no fallback that implies valid empty data. |
| Missing bucket | No dot, min/max mark or connecting line across gap. |
| Dark theme | Same statuses, same data and tooltip semantics; adequate range/line contrast. |

## Chart acceptance checks

- [ ] Selected dots and transparent min/max bars match the same data bucket.
- [ ] Chart has usable axes, grid, legible tooltips and no misleading interpolation across data gaps.
- [ ] Current-day future positions blank; chart not mistaken for continuous live telemetry.
- [ ] Latest hero stays unchanged when selected date changes; no received/snapshot time substituted for occurredAt.
- [ ] Mean and min/max display are consistent with source/period and data status.
- [ ] Loading/empty/error/historical-unverified are distinguishable and accessible.
- [ ] No duplicated AppShell/sidebar and no invented API or clinical assessment.
