# Statistics — UI behavior contract

**Screen family:** `STA-SCR-001`; four variants and visual status are registered in [README.md](README.md). This document follows [BEHAVIOR_STANDARD.md](../BEHAVIOR_STANDARD.md). **Visual correction is CONFIRMED by user:** in `statistic_day_light.png` and `statistic_day_dark.png`, the order shown in the artwork is wrong; the correct order in ALL variants is **Nhịp tim → Bước chân → Lượng nước → Giấc ngủ**. Do not change the binaries; correct composition in FE.

## Screen registry

| ID | Entry / source image | Exit |
| --- | --- | --- |
| `STA-SCR-001-W-L` | Statistic tab, Week Light · [image](statistic_week_light.png) | Existing HR / Steps / Water / Sleep detail |
| `STA-SCR-001-W-D` | Statistic tab, Week Dark · [image](statistic_week_dark.png) | Same destinations |
| `STA-SCR-001-D-L` | Day Light · [image](statistic_day_light.png) (**order defect**) | Same destinations |
| `STA-SCR-001-D-D` | Day Dark · [image](statistic_day_dark.png) (**order defect**) | Same destinations |

**CONFIRMED visual structure:** upper banner with text left/illustration right; one Day/Week switch; four metric sections; Day Sleep uses reaction + text while Week Sleep uses a chart. **Existing UI contract retained:** default to Week on first entry and preserve scope when returning within a session. No new route name, endpoint, metric calculation or business policy is declared here.

## Navigation and user actions

| Action | Source / trigger | Immediate feedback and success outcome | Failure / alternate | Status |
| --- | --- | --- | --- | --- |
| `STA-ACT-001` | Enter Statistics tab | Load four metrics for default Week or retained session selection | Independent skeleton/error/empty per metric | Retained UI contract |
| `STA-ACT-002` | Tap `Ngày` or `Tuần` | Highlight selected segment and refresh **all four** metric sections for common scope | Keep selection consistent, render only failed sections with retry | Retained UI contract |
| `STA-ACT-003` | Previous / next date or week | Change the selected **local** day or Mon–Sun week; all metrics/date labels update together | Disable future/invalid ranges; avoid fabricating future values | Retained UI contract |
| `STA-ACT-004` | Tap Heart Rate section | Whole section is accessible press target → existing Heart Rate detail | If destination unavailable, surface navigation feedback; do not silently redirect | Retained UI contract |
| `STA-ACT-005` | Tap Steps section | Open existing Steps detail | Same | Retained UI contract |
| `STA-ACT-006` | Tap Water section | Open existing Water detail | Same | Retained UI contract |
| `STA-ACT-007` | Tap Sleep section | Open existing Sleep detail | Same | Retained UI contract |
| `STA-ACT-008` | Return from detail | Retain selected mode/date and scroll position where supported | Fallback to same mode/date if scroll restoration unavailable | Retained UI contract |
| `STA-ACT-009` | Pull to refresh / retry failed section | Refresh selected-scope data without clearing other successful sections | Localized error and retry; do not show stale data as freshly confirmed | Retained UI contract |
| `STA-ACT-010` | Menu / drawer | Use existing AppShell drawer, initially closed | Back/backdrop dismiss via shared behavior | Shared AppShell |

No per-card Day/Week control or interactive miniature-chart tooltip. Tapping inside a preview routes to the corresponding detail unless an explicit retry button receives the action. Detail pages own their own expanded charts, filtering and tooltips.

## Required card semantics

| Fixed position | Metric | Week | Day |
| --- | --- | --- | --- |
| 1 | **Heart Rate / Nhịp tim** | Available mean BPM for selected week; preview line for observed buckets | Day mean BPM from accepted measurements; preview observed points | 
| 2 | **Steps / Bước chân** | Recorded weekly total and daily distribution | Recorded day total and supported hourly distribution |
| 3 | **Water / Lượng nước** | Weekly daily mean **when supported and correctly computed**; weekly preview | Selected-day recorded intake and day-specific indicator |
| 4 | **Sleep / Giấc ngủ** | Mean recorded duration if supported; compact week graph | Recorded sleep duration/context plus **feeling reaction and short text** instead of week graph |

- Day Sleep reaction must come from **recorded feeling data** (e.g. comfortable/normal/tired), not from hours slept, a color heuristic, or a model guess. A sample label such as “Thoải mái sau khi thức dậy” is display copy **only if that feeling is recorded**. If missing, show “Chưa ghi nhận cảm giác” (proposed microcopy) with no fake emoji sentiment.
- Charts in uploaded images and isolated `pink_graph.png` / `green_graph.png` are **visual guides**, not a valid data series. Data-bearing trends should be drawn at runtime from supported source values; decorative glow assets may be reused independently.
- Gaps/null mean unavailable, not zero. Do not connect Heart Rate samples across missing buckets; do not draw future buckets as observations. No fabricated sleep duration, live ECG, goal percentage, or AI health conclusion.
- Chart previews fit their section; scrolling is page-level, never horizontal inside a mini-chart. Keep visual metric order constant even if one metric fails to load.

## State model and recovery

| State | All sections | Additional Day Sleep behavior |
| --- | --- | --- |
| `READY` | Show accepted records for selected local scope | Show the **recorded** feeling plus descriptive text when present |
| `LOADING` | Skeleton within the respective metric section, unaffected cards remain usable | No premature reaction/label |
| `EMPTY` | “Chưa có dữ liệu trong kỳ” and no invented chart/value | No recorded feeling → neutral unavailable message |
| `ERROR` | Distinguishable error UI and explicit Retry where relevant | Never replace error with neutral sentiment or false no-data |
| `PARTIAL` | Current day/week in progress, incomplete buckets not extrapolated | Feeling only when user entered it; absence remains absence |
| `DARK` | Same sequence, semantic labels and behavior; use theme tokens and sufficient contrast | Feeling icon/text remain readable |

These are UI state labels, **not** assertions about backend enum names. For API availability, aggregation and timezone rules, actual Business/BE specifications override mockup text.

## Accessibility / responsiveness

- Provide readable labels and **44pt or larger** touch targets for segmented options, date arrows and metric navigation.
- Expose selected scope and dates to screen readers, with units and status for each metric. Accessible names include the destination (e.g. “Xem chi tiết giấc ngủ”).
- Treat decorative banner artwork/glows as non-accessible. Reaction icon must have accessible feeling text if meaningful.
- Content adapts to 320/390/430dp, safe areas, large text and Light/Dark, without clipping the banner or hiding the final Sleep section.
- Back/navigation never resets selected day/week unnecessarily. Reuse shared AppShell and bottom navigation once.

## Acceptance criteria

- [ ] All four [screen variants](README.md) are implemented; the two Day screenshots' **wrong visual ordering is NOT replicated**.
- [ ] For both themes and modes, rendered order is **HR → Steps → Water → Sleep** (including loading, empty and error states).
- [ ] Banner artwork is on right, text on left; global Day/Week selection controls all sections.
- [ ] Day Sleep has reaction + short text rather than Week graph; no guessed feeling when absent.
- [ ] Week Sleep has chart preview generated from valid data; all sections route to existing detail screens.
- [ ] Missing and failed data never masquerade as recorded zero; date navigation cannot select future scope.
- [ ] Native controls and data-bound charts used, not flattened screenshots or static illustrative graphs.
- [ ] Both themes, responsive widths and accessible navigation validated on device.

## Visual asset mapping / change log

See [ASSET_MAPPING.md](ASSET_MAPPING.md), [asset catalog](../assets/statistic/README.md) and [manifest](component-manifest.json).

**2026-11-12:** Migrated to four actual PNG references uploaded in commits `2fbcbfc` / `f152c19`. Recorded user-confirmed Day order defect and Day Sleep reaction distinction. Superseded documentation claiming Day has no independent visual and Week relies on now-removed raster crops. Existing UI scope/navigation and data integrity constraints retained, not redefined as new backend requirements.
