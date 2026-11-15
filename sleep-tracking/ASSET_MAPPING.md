# Sleep Tracking — Screen to Asset Mapping

> Scope: current Sleep UI mockups (Recent F2 + F1), legacy structural references and independently generated transparent PNG assets. Follows [ASSET_MAPPING_STANDARD](../ASSET_MAPPING_STANDARD.md) and [BEHAVIOR.md](BEHAVIOR.md).
>
> **Visual baseline:** screen compositions were selected by the user; the 9 standalone PNG artworks were generated independently and **not cropped from the UI screenshots**. SVG outlines under `icons/` are independently authored, PROPOSED editable alternatives, not visually approved substitutes for the glossy PNGs.

> **MANDATORY: Screens 7–12 are structure-only references; the dominant purple background/buttons/cards are WRONG. FE must render green/mint wellness dominant UI; purple is limited to small assets/icons.** See [corrective specification](ADDITIONAL_SCREENS_20261111.md).

## 1. Composition layers and ownership

1. `background`: native mint/cream gradient and organic wave shapes (native view, no screenshot backgrounds).
2. `hero`: floating moon/clouds/stars image anchored upper-right, placed behind title text and controls.
3. `decoration`: cloud / pillow / smiling star images only where needed (never overlay readable UI).
4. `surface`: native rounded cards, soft shadows, separator/divider and chart frame.
5. `interactive-ui`: actual texts, charts, date/time wheel pickers, input validation, buttons and navigation, never baked into an asset.

- **Shared UI:** AppShell / Health Metrics Drawer owned outside this feature. No duplicate drawer.
- **Source formats:** PNG for independent glossy 3D illustrations (alpha channel); optional SVG outlines for editable UI fallbacks.
- **Reference screens:** 941 × 1672 px screenshots (single portrait screen, no device frame); overview collage 1199 × 1312 px.
- **Original PNG artwork:** 1254 × 1254 px RGBA with transparent outer canvas; illustration object may not fill the entire square.

## 2. Screen-to-image/asset mapping

| Screen ID | Approved screen reference | Primary PNG assets & roles |
|---|---|---|
| `SLT-SCR-001` | [01 Recent Sleep Home](01-sleep-home-recent.png) | [moon hero](../assets/sleep-tracking/moon-cloud-stars.png), [pillow](../assets/sleep-tracking/pillow-stars.png), [trend graphic](../assets/sleep-tracking/trend-up.png) |
| `SLT-SCR-002A` | [02a Start & End](02a-sleep-entry-time-range.png) | [moon hero](../assets/sleep-tracking/moon-cloud-stars.png); [Comfortable](../assets/sleep-tracking/feeling-comfortable.png), [Normal](../assets/sleep-tracking/feeling-normal.png), [Tired](../assets/sleep-tracking/feeling-tired.png) |
| `SLT-SCR-002B` | [02b Duration Only](02b-sleep-entry-duration-only.png) | Same hero + reaction set as 02a; `Date/Hour/Minute` are native interactive pickers |
| `SLT-SCR-003` | [03 All A/B Insights](03-all-sleep-insights-recent.png) | [moon hero](../assets/sleep-tracking/moon-cloud-stars.png), [trend graphic](../assets/sleep-tracking/trend-up.png), [bars](../assets/sleep-tracking/bars.png) |
| `SLT-SCR-004` | [04 Recent Insight Detail shell](04-recent-insight-detail.png) | [pillow](../assets/sleep-tracking/pillow-stars.png), [reaction graphics](../assets/sleep-tracking/feeling-comfortable.png), [bars](../assets/sleep-tracking/bars.png) |
| `SLT-SCR-005` | [05 Old fixed-week design](05-ai-weekly-sleep-story.png) — **HISTORICAL ONLY** | [moon hero](../assets/sleep-tracking/moon-cloud-stars.png), [trend graphic](../assets/sleep-tracking/trend-up.png), [reaction graphics](../assets/sleep-tracking/feeling-tired.png) |

### Added screen/state-to-asset mapping (2026-11-11)

| Stable ID / state | Structural image (color rejected) | Independent asset role |
|---|---|---|
| `SLT-SCR-006` | [Journal](7_sleep_journal.png) | [star-pillow-cloud.png](../assets/sleep-tracking/star-pillow-cloud.png) hero; [bed.png](../assets/sleep-tracking/bed.png) small sleep card icon |
| `SLT-SCR-007` | [Record Detail](8_sleep_record_detail.png) | same hero and small bed accent; native detail table/actions |
| `SLT-SCR-008` | [Edit Record](9_sleep_record_detail_edit.png) | same hero; bed for sleep type, existing feeling illustrations; native form |
| `SLT-SCR-009` | [Goal](10_sleep_goal_setup.png) | small bed on goal card, optional hero; native selectors and buttons |
| `SLT-SCR-003 / NO_DATA` | [Insights empty](11_sleep_insight_empty.png) | combined hero; native tabs/CTA |
| `SLT-SCR-003 / INSUFFICIENT_DATA` | [Insights insufficient](12_sleep_not_enough_data_insight.png) | combined hero; native evidence/requirements/CTA |

**Composition:** green/mint native background → isolated transparent artwork with `contain` → cream/white surface cards → green/teal functional controls. Keep only limited purple accents (bed/pillow/icon). Do not use screenshots for functional UI or data charts; preserve screen IDs and separate Insights states.

[See selected overview](00-sleep-design-overview.png).


## 2A. Current Recent Report and A01–B04 small-asset reuse (2026-11-15)

**Current report:** `SLT-SCR-010` → [02-recent-sleep-report.png](02-recent-sleep-report.png); reuse `moon-cloud-stars.png`, `pillow-stars.png` or `sleep-cloud.png` as optional decoration; chart/coverage/Story layout must be native and data-bound. Home `SLT-SCR-001`, All Insights `SLT-SCR-003` and Detail `SLT-SCR-004` use their `*-recent.png` references. `SLT-SCR-005` and the former fixed-week assets are historical only.

**Asset-first mapping for nine variants of `SLT-SCR-004`:**

| Code | PNG variant | Reused standalone artwork | Chart implementation |
| --- | --- | --- | --- |
| A01 | [13-insight-a01-recording-coverage.png](13-insight-a01-recording-coverage.png) | [moon-cloud-stars.png](../assets/sleep-tracking/moon-cloud-stars.png), [sleep-cloud.png](../assets/sleep-tracking/sleep-cloud.png) | 7-day coverage calendar + count /7; **native/data-driven** |
| A02 | [14-insight-a02-goal-achievement.png](14-insight-a02-goal-achievement.png) | [pillow-stars.png](../assets/sleep-tracking/pillow-stars.png), [bed.png](../assets/sleep-tracking/bed.png) | 7-day achieved/not-achieved/missing/not-applicable state cells + numerator/eligible denominator; **native/data-driven** |
| A03 | [15-insight-a03-duration-trend.png](15-insight-a03-duration-trend.png) | [trend-up.png](../assets/sleep-tracking/trend-up.png), [bars.png](../assets/sleep-tracking/bars.png) | two completed 7-day mean bars + signed minute delta; **native/data-driven** |
| A04 | [16-insight-a04-bedtime-wake-variation.png](16-insight-a04-bedtime-wake-variation.png) | [moon-cloud-stars.png](../assets/sleep-tracking/moon-cloud-stars.png), [sleep-cloud.png](../assets/sleep-tracking/sleep-cloud.png) | two min-max range tracks: bedtime and wake-up, relative-day timeline; **native/data-driven** |
| A05 | [17-insight-a05-weekday-weekend-duration.png](17-insight-a05-weekday-weekend-duration.png) | [moon-cloud-stars.png](../assets/sleep-tracking/moon-cloud-stars.png), [bars.png](../assets/sleep-tracking/bars.png) | two bars for weekday/weekend means, signed minute delta, per-group n; **native/data-driven** |
| B01 | [18-insight-b01-feeling-distribution.png](18-insight-b01-feeling-distribution.png) | [feeling-comfortable.png](../assets/sleep-tracking/feeling-comfortable.png), [feeling-normal.png](../assets/sleep-tracking/feeling-normal.png), [feeling-tired.png](../assets/sleep-tracking/feeling-tired.png) | three-segment 100% distribution/donut, count/denominator, missing-feeling note; **native/data-driven** |
| B02 | [19-insight-b02-duration-vs-feeling.png](19-insight-b02-duration-vs-feeling.png) | [feeling-comfortable.png](../assets/sleep-tracking/feeling-comfortable.png), [feeling-tired.png](../assets/sleep-tracking/feeling-tired.png), [bars.png](../assets/sleep-tracking/bars.png) | two comparable average-duration bars for Comfortable and Tired, signed minutes; **native/data-driven** |
| B03 | [20-insight-b03-feeling-trend.png](20-insight-b03-feeling-trend.png) | [feeling-comfortable.png](../assets/sleep-tracking/feeling-comfortable.png), [feeling-normal.png](../assets/sleep-tracking/feeling-normal.png), [feeling-tired.png](../assets/sleep-tracking/feeling-tired.png), [trend-up.png](../assets/sleep-tracking/trend-up.png) | two 100%-stacked distributions for completed windows, signed percentage-point changes; **native/data-driven** |
| B04 | [21-insight-b04-tired-goal-exception.png](21-insight-b04-tired-goal-exception.png) | [feeling-tired.png](../assets/sleep-tracking/feeling-tired.png), [bed.png](../assets/sleep-tracking/bed.png), [pillow-stars.png](../assets/sleep-tracking/pillow-stars.png) | exception count + dated verified record cards with duration vs effective day-goal; **native/data-driven** |

- Reuse the exact assets in `../assets/sleep-tracking/` via shared import registry. `feeling-comfortable.png`, `feeling-normal.png`, `feeling-tired.png` have distinct semantics and must not be interchanged.
- Calendar/Goal/clock/check/info/lock/back icons are basic controls: reuse an existing icon library/native SVG, **not** a cropped icon from new screenshots. No need to create another PNG before FE builds these screens.
- `bars.png`/`trend-up.png` represent decorative illustrations, **never health data**. Computed bars/donuts/time tracks/coverage cells must use API evidence and accessible vector/native chart primitives.
- Use `contain` on standalone transparent PNGs without causing clipping; avoid oversize hero decoration on dense insight pages. Green/mint dominant with lilac <=~10%; one primary KPI/graph, collapsed evidence/limitations.
- [RECENT_INSIGHT_DESIGN.md](RECENT_INSIGHT_DESIGN.md) defines exactly what A01–B04 must measure and the evidence conditions. This mapping is **proposed artwork composition**, not confirmation that visuals have already been extracted and reused in React Native.

## 3. Transparent PNG inventory (all actual files)

| Filename | Role | Ownership | Visual status |
|---|---|---|---|
| [moon-cloud-stars.png](../assets/sleep-tracking/moon-cloud-stars.png) | Main floating moon/cloud hero | Sleep feature | Generated original / AVAILABLE |
| [sleep-cloud.png](../assets/sleep-tracking/sleep-cloud.png) | Independent cute cloud | Sleep feature | Generated original / AVAILABLE |
| [pillow-stars.png](../assets/sleep-tracking/pillow-stars.png) | Purple pillow decorative asset | Sleep feature | Generated original / AVAILABLE |
| [star-smiling.png](../assets/sleep-tracking/star-smiling.png) | Single smiling star decoration | Sleep feature | Generated original / AVAILABLE |
| [feeling-comfortable.png](../assets/sleep-tracking/feeling-comfortable.png) | Comfortable illustration | Sleep feature | Generated original / AVAILABLE |
| [feeling-normal.png](../assets/sleep-tracking/feeling-normal.png) | Normal illustration | Sleep feature | Generated original / AVAILABLE |
| [feeling-tired.png](../assets/sleep-tracking/feeling-tired.png) | Tired illustration | Sleep feature | Generated original / AVAILABLE |
| [trend-up.png](../assets/sleep-tracking/trend-up.png) | Decorative upward trend | Sleep feature | Generated original / AVAILABLE |
| [bars.png](../assets/sleep-tracking/bars.png) | Decorative rising bars | Sleep feature | Generated original / AVAILABLE |
| [star-pillow-cloud.png](../assets/sleep-tracking/star-pillow-cloud.png) | New standalone combined hero | Sleep feature | COMMITTED; green UI usage, pending FE visual QA |
| [bed.png](../assets/sleep-tracking/bed.png) | New small standalone purple bed | Sleep feature | COMMITTED; minor accent ONLY |

**Important:** Decorative graph PNGs cannot replace data-bound charts in functional screens. Real bars, labels and evidence must be generated from verified analytics. Self-assessment control state is native, not encoded in a preselected PNG.

## 4. Responsive placement and app handoff

- Use safe-area insets, screen readers, semantic text, scroll and responsive spacing; 390 × ~690 dp screenshot proportions are illustrative, not a global fixed height.
- Moon/cloud assets align top-right and must never occlude form fields. Cards and heading use native text for translations/dynamic contents.
- Use `contain` with alpha PNGs; remove invisible outer padding only through layout/canvas cropping *of the independent artwork if explicitly approved*, never by screenshot-cropping.
- Reaction icons are decoration inside min 44pt native hit targets. Selected state must include border, accessible selected label, and readable contrast.
- Per-screen event and state logic lives exclusively in [BEHAVIOR.md](BEHAVIOR.md).
- Fingerprint original files via [import record](SCREEN_IMPORT.md); machine mappings in [screen-manifest.json](screen-manifest.json) and [asset-manifest.json](../assets/sleep-tracking/asset-manifest.json).

## 5. Acceptance checks

- [x] Six approved single-screen PNGs and the selected overview are present in `sleep-tracking/`.
- [x] Nine individual PNG assets exist in `assets/sleep-tracking/` and have alpha transparency.
- [x] Assets are independently generated, not cropped from main screen screenshots.
- [x] Mapping references actual relative paths and is consistent with manifests.
- [x] Six supplemental reference files and two new standalone assets exist and are mapped; purple-dominant screen colors explicitly rejected.
- [ ] Corrected green FE layout and remaining alternate/error states receive separate visual acceptance.
- [ ] Expo UI uses native functional controls and matches selected visual references after device QA.
