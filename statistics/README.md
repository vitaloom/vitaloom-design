# Statistics — VitaLoom Health Overview

**Current source:** user-uploaded PNG screens at commits [2fbcbfc](https://github.com/vitaloom/vitaloom-design/commit/2fbcbfcd200895a6202fb88e62c2ff0d186be8d1) and [f152c19](https://github.com/vitaloom/vitaloom-design/commit/f152c19df06696bc150cf8878cfd0b02ea125d01) (2026-11-12 documentation sync). **Module folder: `statistics/`; asset folder: `assets/statistic/` (singular).** These are the current visual references; older `approved-b-week-*.webp` and `legacy/overview-*.svg` references were removed from main and are **not** implementable baselines.

> **MANDATORY VISUAL EXCEPTION — Day Light and Day Dark:** The uploaded `statistic_day_light.png` and `statistic_day_dark.png` show an incorrect metric section order. Do **not** reproduce that order in FE. Both Day screens must follow Week order: **Nhịp tim → Bước chân → Lượng nước → Giấc ngủ**. Keep the Sleep section last; retain its Day-specific feeling reaction and supporting text. The PNG files remain unchanged for traceability. This correction is explicitly user-directed, not an optional suggestion.

## Screen inventory

| Stable screen ID | Mode / theme | Current full-screen reference | Visual status |
| --- | --- | --- | --- |
| `STA-SCR-001-W-L` | Tuần · Light | [statistic_week_light.png](statistic_week_light.png) | `CURRENT_USER_UPLOADED_REFERENCE` |
| `STA-SCR-001-W-D` | Tuần · Dark | [statistic_week_dark.png](statistic_week_dark.png) | `CURRENT_USER_UPLOADED_REFERENCE` |
| `STA-SCR-001-D-L` | Ngày · Light | [statistic_day_light.png](statistic_day_light.png) | `REFERENCE_WITH_KNOWN_ORDER_DEFECT` |
| `STA-SCR-001-D-D` | Ngày · Dark | [statistic_day_dark.png](statistic_day_dark.png) | `REFERENCE_WITH_KNOWN_ORDER_DEFECT` |

The Day screenshots are **valid visual references for artwork, layout language and Day-specific Sleep presentation**, **not** for their incorrect section sequence. The Week screenshots establish the correct section order for every mode and theme. Screen IDs remain stable across this migration.

## Page structure (top to bottom)

1. **Statistics banner/header:** left-aligned heading and supporting copy, with decorative statistics artwork on the **right**. Copy and controls are native text/UI, not pixels extracted from the reference.
2. **Global period selector:** `Ngày` / `Tuần`. A date/week context and previous/next navigation follow the active selection as supported by the actual app.
3. **Four vertically stacked metric sections/cards (fixed order):**
   1. **Nhịp tim** (Heart Rate) — coral/pink family; headline value and small relevant trend presentation.
   2. **Bước chân** (Steps) — green/mint; value plus steps preview.
   3. **Lượng nước** (Water) — blue; value plus hydration preview.
   4. **Giấc ngủ** (Sleep) — lavender accent; **Week:** compact sleep trend. **Day:** one recorded feeling reaction with short explanation (e.g. “Thoải mái sau khi thức dậy”), **instead of** the Week-style graph.
4. **Shared app navigation** follows the real AppShell structure; do not duplicate bottom navigation or the health-metrics drawer inside this module.

The same four metric sections remain available in **both** Day/Week and Light/Dark. Maintain coherent spacing, soft wellness surfaces, rounded corners and legibility, while respecting the full-screen reference for individual section composition. Natural vertical scrolling is expected; never shrink content to force all cards above the fold.

## Behavior and information integrity

- **Week remains the first-visit default** from the previously documented interaction contract; returning from detail should preserve the selected period in the same session where feasible.
- All sections use the **same selected local date or week**; do not make separate period selectors for individual cards.
- Each metric section opens its **existing** dedicated feature screen; mini trend previews are not independent analytics drilldowns.
- Display factual data only. Example values/graph pixels in uploaded PNGs are illustrative, not backend records, fixtures, contract fields, or health judgments.
- Day Sleep's reaction/text is conditional on a **recorded user feeling**; do not infer that the user feels comfortable without a valid source. When unavailable, use an explicit no-feeling state.
- Light/Dark differ in palette/contrast, **not** information hierarchy or behavior.

## Handoff and files

- [Screen behavior, navigation, UI states and acceptance checks](BEHAVIOR.md)
- [Screen-to-asset mapping and layered composition](ASSET_MAPPING.md)
- [Current screen/component manifest](component-manifest.json)
- [Standalone artwork catalog](../assets/statistic/README.md) and [asset manifest](../assets/statistic/asset-manifest.json)
- [Global mapping standard](../ASSET_MAPPING_STANDARD.md) · [Behavior standard](../BEHAVIOR_STANDARD.md)
- [Shared AppShell/drawer](../shared/health-metrics-sidebar/README.md)

**FE implementation:** copy individual approved-reference assets into the feature's asset structure as needed, but implement text, values, controls, accessible cards and data-driven charts as React Native components. No backend schema/API change is implied by this document. Confirm data availability against canonical Business Docs and backend contracts before binding metrics.
