# Steps — UI behavior and interaction contract

**Status:** PROPOSED design handoff, not new business rules. **Screen:** [STP-SCR-001](README.md). Source links in [REFERENCES.md](REFERENCES.md). Shared navigation is [AppShell](../shared/health-metrics-sidebar/README.md).

| ID | Control | Interaction / outcome | Source/status |
| --- | --- | --- | --- |
| STP-ACT-001 | Period selector | Day / Week / Custom changes data view and axis labels. Preserve selected period on retry. | PROPOSED UX; canonical Statistics endpoints |
| STP-ACT-002 | Day / week / custom date selection | Select a valid range; display loading only for dependent data; recover previous context on error. No future invalid ranges. | PROPOSED UX; validate per API |
| STP-ACT-003 | Bar tap / keyboard focus | Show a tooltip anchored to the bucket with local interval and accepted steps. Tap outside / Escape dismisses. | PROPOSED |
| STP-ACT-004 | Refresh | Re-fetch active view; preserve filter and highlight only when valid. | PROPOSED |
| STP-ACT-005 | Shared drawer | Use existing closed-by-default shared drawer; no feature-owned duplicate. | CONFIRMED by shared spec |

## Daily chart rules

- Use a vertical **bar chart** with visible numerical Y axis and soft horizontal grid lines. Chart area keeps a fixed clock axis for Daily; weekly/custom use dates rather than hours.
- Render a bar **only** when backend reports recorded steps for that bucket. A missing value is a gap, not an asserted zero. Never fabricate tiny baseline bars for missing events, and never paint a future bar as real.
- Use actual timezone and bucket boundaries from canonical Statistics contract. Labels such as `11 giờ` mean the bucket beginning at 11:00, not a continuous observation or a completed hour.
- Peak hour and nonempty bucket count are display insights derived from the **currently selected** response; tie handling should be deterministic, with an accessible explanation when tied.
- Tooltip on 11:00 before noon may be a partial current-hour total. No extrapolation, goal percentage, calorie estimate, distance or continuous device claim without approved source.

## Views

- **Day:** 24 hourly positions; only event-bearing buckets draw bars.
- **Week:** seven calendar-day buckets; highlight the day with the most recorded steps where supported.
- **Custom:** backend-approved date range with daily buckets. For wide ranges, use a horizontally navigable/scrollable chart with legible date labels and focus access.
- All values remain account-scoped and supplied/derived from approved backend statistics.

## UI state contract

| State | Treatment |
| --- | --- |
| Loading | Keep hero layout/shell and selected filter. Skeleton only values dependent on request. |
| Empty | “Chưa có dữ liệu bước chân cho khoảng đã chọn”; no 0 total substitution. |
| Partial current period | Inform user current-day/hour results can still change; do not mark the day complete. |
| Error | Show explicit retrieval failure and Retry; never conflate failure with empty. |
| Dark | Same controls/data semantics; accessible axis/grid, selected tab, tooltip contrast. |
| No records in individual bucket | No bar; assistive label “Không có bản ghi”, not “0 bước”. |

## Acceptance criteria

- [ ] Visual reference matches approved hero / chart concept across light/dark and narrow screens.
- [ ] All periods use canonical endpoints/valid range rules, not a feature-invented `period` parameter.
- [ ] Total and event count match backend data and do not silently change when view changes without updated label.
- [ ] Missing periods have no fake baseline bars; future bucket is never shown as recorded.
- [ ] Peak insight, tooltip and chart agree about boundaries/values.
- [ ] Retry, empty, loading, accessibility and drawer work without duplicated shell components.
