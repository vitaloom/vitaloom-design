# VitaLoom — FE UI Enhancement Handoff (Steps & Heart Rate)

**Target branch (design source):** `design/steps-heart-rate-analytics-refresh-20261111`  
**Goal:** Bring the existing, API-connected mobile screens into the **user-approved visual direction** for Steps and Heart Rate. This is **not** a business-logic or API rewrite.  
**Priority:** Hero art/layer fidelity → chart viewport + tooltip fidelity → insight visuals/icons → light/dark responsive QA.  
**Out of scope by request:** DevTools/console errors and warnings, favicon/DOM warnings, unrelated lint/refactors, new Backend endpoints and domain changes.

## 0. Read these before editing code

1. [Steps design](steps/README.md), [Steps layer composition](steps/ASSET_MAPPING.md), [Steps asset inventory](assets/steps/README.md).
2. [Heart Rate design](heart-rate/README.md), [HR layer composition](heart-rate/ASSET_MAPPING.md), [Heart illustration assets](assets/heart-rate/README.md).
3. [Shared analytics icon kit](assets/shared/analytics-icons/README.md) and [chart interaction rules](shared/analytics-components/CHART_INTERACTIONS.md).
4. [Existing AppShell + sidebar](shared/health-metrics-sidebar/README.md).
5. [Steps canonical API/model links](steps/REFERENCES.md), [HR canonical API/model links](heart-rate/REFERENCES.md). **Read actual Backend docs/code**; design files do not redefine data or DTOs.

**IMPORTANT:** `final-light.svg` and `final-dark.svg` are *editable screen-level vector reconstructions*, not an exact export of the original approved generated raster images. The independently authored hero assets in this branch are **new redraws** that follow the approved illustration direction. Compare mobile screenshots against the user-approved concepts and request final visual acceptance where needed; do not claim pixel-perfect parity from the existence of SVG alone.

## HR visual completeness addendum — must apply (Min / Avg / Max and warm canvas)

**The previous asset handoff lacked distinct KPI art and the soft blush page backdrop.** These assets now exist and are required for a visually faithful HR enhancement.

| UI element | Light asset | Dark asset | Placement |
| --- | --- | --- | --- |
| Min tile (Thấp nhất) | `assets/heart-rate/icons/hr-min-light.svg` | `assets/heart-rate/icons/hr-min-dark.svg` | Integrated colored badge, 30–40dp; tile label/value remain native |
| Average tile (Trung bình) | `assets/heart-rate/icons/hr-avg-light.svg` | `assets/heart-rate/icons/hr-avg-dark.svg` | Coral pulse badge |
| Max tile (Cao nhất) | `assets/heart-rate/icons/hr-max-light.svg` | `assets/heart-rate/icons/hr-max-dark.svg` | Rose ascending-arrow badge |
| Analytics title icon | `assets/heart-rate/icons/hr-analytics-light.svg` | `assets/heart-rate/icons/hr-analytics-dark.svg` | Header icon before “Phân tích nhịp tim” |
| Optional background aura | `assets/heart-rate/hr-screen-ambient-light.svg` | `assets/heart-rate/hr-screen-ambient-dark.svg` | Behind feature scroll content only; native theme gradient beneath |

**Page background requirement:** HR Light base `#FFF9FA → #FFF3F6`, dark `#211F29 → #1A242B` as visual references, adapted through existing app theme. Do **not** color the whole AppShell or the Steps page rose. Read [HR background tokens](assets/heart-rate/BACKGROUND_TOKENS.md), [HR icon guide](assets/heart-rate/icons/README.md), and the updated [asset manifest](assets/heart-rate/asset-manifest.json). The icons already have integrated tinted circles; avoid a second circle. Treat them as `PROPOSED` artwork redraws awaiting review, not pixel-identical extractions.

**UI acceptance expansion:** HR Min/Avg/Max must have visible matching theme icons; gentle blush visible around content; existing hero and chart data structure kept intact. No backend work and **no DevTools fixes** as requested.

## 1. Current UI gaps to correct

| Area | Present issue seen in screen review | Expected |
| --- | --- | --- |
| HR hero | Flat blush card, text-only, heart graphic/scene absent | Large glossy coral heart on the right, blush waves/leaves below, real native latest BPM on the left |
| Steps hero | Steps total isolated from illustration and scenery | Two mint-white sneakers, mint scenery, big step total, day badge and accepted-record count |
| Chart sizing | Daily series wider than viewport with mandatory horizontal scrolling | **Day mode fully fits available card width** (e.g. 393dp device), 24-hour steps / 96×15-min HR coordinate frame; responsive sparse plot |
| Tooltip | Selected bucket causes an extra panel under the chart (layout shift) | **Floating anchored overlay** inside chart, near selected bar/dot, clamped to card edges; no reflow |
| Y-axis / min-max | Numeric grid sparse or min-max hard to read | Visible axis units/ticks; HR subtle vertical min-max whiskers and connected avg dot segments |
| Visual hierarchy | Missing icons, hero accents, consistent KPI tiles | Exact named visual assets, icon scale, selected tab pill, pleasant spacing and softened insight tiles |
| Theme | Basic colors but limited feature-specific art | Proper light/dark contrast for art/cards, chart grid, tooltip and selected state |

## 2. Composition recipe — React Native + Web

Implement real interactive UI, **not an image of the entire screen**. The app currently has `react-native-svg` and `expo-linear-gradient`; check its existing vector asset-loading pipeline before adding dependencies. An explicit equivalent React Native SVG component is acceptable if SVG file imports are not configured.

- **Container:** App background; one shared header/sidebar and bottom navigation; content vertically scrolls, fixed-width max container where app already specifies one.
- **Title:** Same left-aligned hierarchy for Steps/HR: eyebrow (12–13sp), primary title (28–32sp), descriptive subtitle (12–14sp); leave good whitespace.
- **Hero card:** width of content, radius ~22–26dp, reference height **150–176dp**, padding ~16–20dp, `overflow: hidden`, slight native gradient and low shadow. Maintain 16dp side gutter for 393dp iPhone-size viewport.
- **Hero layers in order:** themed background → transparent scenery (bottom, full width) → hero illustration on right (`contain`, approx 150–180dp) → native date/value/timestamp text on left. Illustration and scenery `pointerEvents="none"`, accessibility hidden. Text must remain clear on smaller widths; shrink art before text.
- **Icons:** use named SVG files under `assets/shared/analytics-icons/`; render 18–24dp inside chips/tiles. Preserve feature accents (Steps mint, HR coral). For equivalent existing icon pack mapping, preserve visual shape and spacing.
- **Analytics card:** radius ~22–26dp; single segmented control Day / Week / Custom (active pill); readable day selection as applicable; chart with axis labels; 3 insight tiles with icons; a short context note. Avoid nested large plain-green summary cards that suppress the hero/graph hierarchy.
- **Theme:** React Native theme variables are authoritative. Separate themed surfaces from art assets; don't simply invert PNG/SVG colors. Verify dark on device/web.

### Supplied independent assets — exact paths

| Purpose | Path |
| --- | --- |
| Steps hero sneakers | `assets/steps/steps-sneakers-hero.svg` |
| Steps mint wave scene | `assets/steps/steps-hero-scenery.svg` |
| HR glossy coral heart | `assets/heart-rate/heart-pulse-hero.svg` |
| HR pink wave scene | `assets/heart-rate/heart-hero-scenery.svg` |
| Named analytics icons | `assets/shared/analytics-icons/*.svg` |
| Screen-to-asset map | `steps/ASSET_MAPPING.md`, `heart-rate/ASSET_MAPPING.md` |
| Machine-readable mapping | `assets/steps/asset-manifest.json`, `assets/heart-rate/asset-manifest.json` |

The hero SVGs have transparent backgrounds and contain **no user-specific measurements**. **Do not** replace these with the complete full-screen reference SVG as a static screenshot.

## 3. Steps chart: fit 24h without scroll

- **Daily** renders 24 **hourly** buckets from backend over an X-axis labelled 00, 06, 12, 18, 24. Chart width equals parent chart viewport minus Y-axis label gutter (~34–42dp) and a small right pad; `width: '100%'` / measured `onLayout`. **No `Math.max(520,...)` minimum and no horizontal `ScrollView` for Daily.**
- Render positive event-bearing buckets as rounded vertical bars with a subtle green gradient/solid fallback, 4–9dp (adapt). Missing buckets **do not create tiny colored marks**, a zero-activity claim, or bars in the future.
- Add Y-axis ticks 0 .. useful rounded max, 3–5 horizontal gridlines, unit “Bước”, foreground highlighted peak bucket with optional crown icon.
- Anchor tooltip to selected bar (bucket local hour and steps + accepted event count), positioned absolutely, clamped to left/right/top of chart. Tapping outside, pressing Back/Escape or switching scope clears it.
- Below chart: peak hour & steps, number of event-bearing hourly buckets, accepted record count, plus short truthful context. Do not label a count of buckets as “time continuously tracked.”
- Week/Custom are available **only per current canonical contracts**. Fit readable aggregated visual where semantics can be validated; for dense ranges choose an appropriate summarized overview + drilldown rather than accidentally forcing a huge horizontally scrolling graph.

## 4. Heart Rate chart: connected avg line + translucent ranges

- **Daily:** backend 15-minute buckets, positioned on a shared **00–24h fixed plot area**. 96 bucket slots fit within the card width without forced horizontal scrolling. Use responsive SVG coordinates, not one fixed pixel width per bucket. For dense data, resolve touch to nearest observed bucket rather than making every 3px marker a separate 44dp button.
- **Average:** visible coral line with small dots at actual populated buckets; **connect only adjacent nonempty buckets**. Null intervals split the path; do not interpolate through missing observations. Visible dot radius ~3–4dp; selected ~5–6dp.
- **Min/max:** a translucent pink vertical whisker for each populated bucket from its real min to real max; the mean dot sits within it. Use same Y scale for extrema and line, with readable BPM ticks. If data is sparse, leave the chart sparse.
- **Tooltip:** overlay on selected dot, show local interval, `Min / Avg / Max`, sample count. Use actual backend bucket values. **Do not insert another card below the chart.** Tooltip follows theme, clamps inside chart bounds, does not reflow.
- **KPI row:** low / daily average / high where supported. Correct date/range scope; do not take a simple unweighted mean of per-bucket averages when samples differ. Use backend summary average/status for the selected day.
- **Hero:** latest recorded reading stays independent of selected date. Do not display Live, ECG telemetry, clinical risk labels or inferred device connection.
- **Other periods:** show time/date ticks appropriate to backend resolution, not 96 equally spaced daily labels everywhere. Keep gap awareness and no future data.

## 5. Suggested FE touchpoints (verify current branch file locations)

- `src/features/heart-rate/screens/heart-rate-screen.tsx`
- `src/features/statistics/components/heart-rate-chart.tsx`
- `src/features/steps/screens/steps-screen.tsx`
- `src/features/steps/components/steps-chart.tsx`
- Shared shell: `src/components/ui/health-metrics-sidebar.tsx`, bottom tab component.
- Existing theme, typography, API hooks and localization should be **reused**. Do not duplicate heart/steps data models in FE design components.

## 6. Acceptance criteria and screenshots

At minimum capture **Steps and Heart Rate in Light and Dark** at **393 × 852**, plus a narrow ~320dp case and one sparse-data state. Compare to current design screenshots and the approved conceptual compositions.

- [ ] Both hero cards have prominent feature illustrations + wave scenes (not flat text-only rectangles).
- [ ] Icons actually present in chart title, badge, KPIs and notes; correct spacing with responsive type.
- [ ] Dedicated **Min / Avg / Max** colored icon assets selected by active light/dark theme, no text-emoji substitutes.
- [ ] Light-mode HR page softly warm blush (not mint or vivid red); dark mode muted mauve-charcoal; other metrics and AppShell unchanged.
- [ ] No horizontal swipe for **daily** chart on 393dp viewport; vertical scrolling of page is okay.
- [ ] Dot/bar tap produces a **positioned overlay tooltip**, no card insertion or layout shift.
- [ ] HR mean line only connects neighboring observed buckets; translucent min-max markers correspond to observed data.
- [ ] Y axes/ticks readable; future buckets blank; values and context accurately match canonical API data.
- [ ] Empty/loading/error and light/dark behavior remain correct; original business logic and scope remain intact.
- [ ] No new backend feature is invented; identify unsupported periods/insights separately.
- [ ] Diff contains only Steps/HR UI, shared presentation utilities/assets and related docs. **DevTools warnings/errors explicitly excluded from this task.**

## Agent output expected

Return a **concise implementation report**: changed FE files/components, screenshots (light/dark at 393dp), before/after on the four visual gaps, which actual SVG assets were imported, Daily chart width/tooltip approach, and remaining purely UI differences. **Do not open or merge PR into `main` automatically**; user will decide once visual parity is verified.
