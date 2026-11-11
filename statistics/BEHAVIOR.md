# Statistics Overview B — UI-only behavior contract

**Screen:** `STA-SCR-001` in [README](README.md). **Status:** approved simple-B interaction direction. **Visual authority is the raster-cropped original Wellness Analytics B**, not any SVG in [legacy](legacy/README.md). Day mode follows the same card style but has no separately approved Day visual.

| ID | User action / state | Observable behavior |
| --- | --- | --- |
| STA-ACT-001 | Enter Statistics | Default to **Tuần** for first visit. Preserve mode/date when returning from a metric detail during same session. |
| STA-ACT-002 | Switch Ngày / Tuần | Update **all four cards** for the same selected calendar scope; selection and visual active state stay in sync. No per-card independent selector. |
| STA-ACT-003 | Select previous/next scope | Change selected local day or Monday–Sunday week; prevent invalid/future selections; keep the label and all cards consistent. |
| STA-ACT-004 | Tap anywhere on a card (including chart preview) | Navigate to the matching **existing** detail route (HR /steps /water /sleep). Entire card is one accessible press target. |
| STA-ACT-005 | Back from detail | Keep original selected mode/date and scroll position when possible; do not force reset to today. |
| STA-ACT-006 | Pull-to-refresh | Refresh eligible card data in the selected scope without clearing selection/other successful cards. |
| STA-ACT-007 | Open drawer | Reuse shared, closed-by-default AppShell drawer. Card content never mounts its own drawer. |

## Card responsibilities

| Card | Primary value (week / day) | Chart preview | Context |
| --- | --- | --- | --- |
| Heart Rate | Available mean BPM for selected period / date | Coral line with small dots; **connect adjacent observed buckets only**, gaps where no data | “Trung bình trong tuần/ngày” (never imply Live ECG) |
| Steps | Total recorded steps for week / day | Seven daily bars for week; sparse hourly distribution for day | “Tổng số bước” and correct recorded-data semantics |
| Water | Weekly daily mean **if available** / day total | Seven daily intake bars for week; compact day-progress/amount visual for day | Context must match metric computed; goal percentage **not implied by default** |
| Sleep | Mean recorded duration per night/day **if available** / day recorded duration | Weekly 7-day bars; concise duration/timeline in Day mode if supported | Do not invent bed/wake timestamps or complete nights |

**No fake live data.** The demo figures in screen art are **not** implementation test fixtures. Agents should use existing source-of-truth Backend + Business docs and frontend repositories instead of copying schema/formulas into this design repo.

## Mini-chart behavior

- Preview charts are intentionally **non-interactive within the card**: no dot tooltip, dragging, min/max whisker popup, horizontal scrolling, or chart-specific long press. **Tap routes to detail.**
- Time labels may be omitted on mini previews to preserve space; display only a compact meaningful trend visualization and concise numeric context.
- For Day, show events/measurements within the selected day only; do not fabricate filled future buckets.
- Missing/empty buckets remain gaps or empty positions. A zero measurement and missing measurement are not interchangeable; avoid 0 BPM, 0 sleep hours or 0 steps as fallback for missing data.
- If period averages are unavailable or cannot be calculated correctly from the authorized data, show truthful “Chưa có số liệu” or relevant fallback, never a mock summary.
- Mobile chart **fits the card width**. No horizontal scroll within overview card. Detail screen owns full axes/tooltips/drilldowns.

## Independent UI states

- `LOADING`: each card shows compact shimmer/skeleton matching card shape; other cards remain usable.
- `EMPTY`: same card shell, icon, title, “Chưa có dữ liệu trong kỳ”, no rendered fake chart/value.
- `ERROR`: same card shell and clear error affordance; retry interaction may exist within card but must not swallow card navigation accidentally. Prefer one explicit retry control only where necessary.
- `PARTIAL`: selected current day/week still accumulating data, small textual status where needed; do not imply complete week.
- `HISTORICAL_UNVERIFIED`: if backend distinguishes this, show neutrally; do not invent verification.
- `DARK`: same content and interaction semantics, theme-aware legibility, no SVG chart screenshot substitution.
- Future day/week navigation disabled. Do not draw future bars as recorded.

## Acceptance criteria

- [ ] Approved **simple B** layout (not the enriched comparison/insight/toggle explorations).
- [ ] 4 vertical pastel metric cards, complete header and period controls, light/dark.
- [ ] Global selection updates each card independently; date/week displayed consistently in local timezone.
- [ ] Mini charts are in cards, no sideways scroll, no tooltips; tap the whole card routes to detail.
- [ ] No duplicates of metric detail charts/hero screens or quick actions from Home.
- [ ] Independent empty/error/loading/partial behavior without mock/fake measurements.
- [ ] Shared AppShell and bottom navigation used once, accessible controls, fits 320/390/430dp.
