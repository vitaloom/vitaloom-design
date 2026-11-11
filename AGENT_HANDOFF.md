# Agent handoff — Steps + Heart Rate analytics refresh

**Branch:** `design/steps-heart-rate-analytics-refresh-20261111`  
**Delivery mode:** Investigation and FE/BE implementation on feature branches; **do not create a PR or merge to `main` on the user's behalf**. This branch is the current UI reference; its new SVG screen drawings are editable visual reconstructions of the agreed light-mode concepts, while dark is proposed. Confirm fidelity before final acceptance.

## Start here

1. [Steps design](steps/README.md) · [behavior](steps/BEHAVIOR.md) · [canonical links](steps/REFERENCES.md).
2. [Heart Rate design](heart-rate/README.md) · [behavior](heart-rate/BEHAVIOR.md) · [canonical links](heart-rate/REFERENCES.md).
3. [Shared chart patterns](shared/analytics-components/README.md) · [chart interactions](shared/analytics-components/CHART_INTERACTIONS.md) · [theme](shared/analytics-components/THEME_TOKENS.md).
4. [Shared AppShell / drawer](shared/health-metrics-sidebar/README.md).

## Required backend compatibility investigation

Before writing endpoint clients, read current canonical contracts AND actual backend/controller/service/repository implementations in `vitaloom-backend`. Check both availability and correctness against the designs:

| Concern | Validate using canonical docs and actual code |
| --- | --- |
| Steps daily / weekly / custom | Authentication, dates/zone, bucket resolution/count, missing-bucket semantics, totals/event counts, expected validation errors |
| Steps peak / record insights | Which insights can be derived from documented data without new backend fields; correct current-hour semantics |
| HR summary | Latest is account-wide and measured-at; daily avg date-scoped and status-aware; independent null states |
| HR daily / weekly / custom time series | Bucket times, observed mean/min/max/sample-count, gaps, current-day partial data |
| HR min/max and average cards | Same selected period, consistent weighting and rounding; identify any unsupported exact aggregate |
| Error/empty/partial | Server distinguishes no data from errors; frontend must not fabricate success |
| Access boundaries | Per-user authenticated reads; no accidental use of unisolated older dashboard paths |
| Light/dark | Use existing app theme tokens and responsive chart implementation, not hardcoded screenshot raster as UI |

## Agent deliverable: evidence-based compatibility matrix

For **each visual KPI/control** document:
- Screen ID and UI element
- Required behavior/value
- Backend route and exact source file/contract link (or explicit `not available`)
- Status: `SUPPORTED`, `FRONTEND_DERIVABLE`, `BACKEND_GAP`, or `OPEN`
- Proposed FE component and fallback/decision needed

Do not replicate DTOs, model definitions or backend formulas into this design repo. A compatibility matrix of references and findings is okay. Do not treat the visual's sample numbers as fixtures or API guarantees.

## Implementation constraints

- Preserve the approved visual direction: Steps mint hero and bar chart; HR coral hero plus adjacent-bucket connected-average line and translucent per-bucket min/max range.
- Render **null as missing**, not zero. Never connect HR dots across empty buckets; never paint recorded activity after current time. Axes, tooltip, status, accessibility, and dates must match real data.
- Shared shell and drawer stay single-instance; use existing FE app structure and real theme.
- Keep full-screen images as *design reference*, functional cards/charts as native UI. Do not import the SVG screenshot as the interactive page.
- Never change canonical BE/BR contracts because a design graphic happens to display a value. Escalate gaps first.
- Run relevant tests and provide screenshots of both modes/states for visual review.

**Exit condition:** User reviews backend compatibility findings and the implemented visual; user opens PR to main only when satisfied.
