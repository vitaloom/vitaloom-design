# Statistics — Screen-to-Asset Mapping

**Current screen source:** the four `statistics/statistic_*.png` files. **Standalone visual asset source:** `assets/statistic/` (singular); see [catalog](../assets/statistic/README.md). In accordance with [global mapping standard](../ASSET_MAPPING_STANDARD.md), full-screen screenshots remain references only; native components render functional UI.

> **Known visual defect / REQUIRED FE correction:** `statistic_day_light.png` and `statistic_day_dark.png` have an incorrect metric section order. Apply **Heart Rate → Steps → Water → Sleep** using the `statistic_week_*` order, with Sleep always last. Keep the screenshot files unchanged. The Day Sleep section should show a recorded feeling reaction and small text instead of the Week Sleep graph.

## 1. Full-screen mapping

| Stable ID | Full-screen reference / status | Feature-owned asset mapping | Per-variant note |
| --- | --- | --- | --- |
| `STA-SCR-001-W-L` | [Week Light](statistic_week_light.png) · `CURRENT_USER_UPLOADED_REFERENCE` | [heart](../assets/statistic/heart.png), [shoe](../assets/statistic/shoe.png), [bottle](../assets/statistic/blue_bottle.png), [sleep](../assets/statistic/sleeping_star_pillow.png); [pink trend](../assets/statistic/pink_graph.png), [pink glow](../assets/statistic/pink_smooth.png), [green trend](../assets/statistic/green_graph.png), [green glow](../assets/statistic/green_smooth.png) | Week Sleep uses a trend; order is canonical |
| `STA-SCR-001-W-D` | [Week Dark](statistic_week_dark.png) · `CURRENT_USER_UPLOADED_REFERENCE` | Same standalone art; theme-adapt the native surfaces and labels | Week Sleep uses a trend; order is canonical |
| `STA-SCR-001-D-L` | [Day Light](statistic_day_light.png) · `REFERENCE_WITH_KNOWN_ORDER_DEFECT` | Same illustration and decorative layer set; optional external [comfortable reaction](../assets/sleep-tracking/feeling-comfortable.png) **only for corresponding recorded feeling** | **FE overrides screenshot's wrong ordering**; replace Sleep graph with reaction + text |
| `STA-SCR-001-D-D` | [Day Dark](statistic_day_dark.png) · `REFERENCE_WITH_KNOWN_ORDER_DEFECT` | Same; text, controls and surfaces theme-adapt | **FE overrides screenshot's wrong ordering**; replace Sleep graph with reaction + text |

The Day feeling icon is a **reuse candidate** from the existing Sleep Tracking asset set, not a new Statistic-specific asset, and is **PENDING_FE_VISUAL_VERIFICATION**. A matching recorded `normal` / `tired` state may reuse the corresponding existing Sleep Tracking reaction if validated. Never display `feeling-comfortable.png` by default when the recorded feeling is missing. **No separately exported Day Sleep reaction exists under `assets/statistic/` in these commits.**

## 2. Asset roles, ownership and provenance

| Exact asset path (relative to repo root) | Suggested role / mapping | Ownership | Status |
| --- | --- | --- | --- |
| [`assets/statistic/heart.png`](../assets/statistic/heart.png) | HR metric illustration | Statistic | User-uploaded PNG / available |
| [`assets/statistic/shoe.png`](../assets/statistic/shoe.png) | Steps metric illustration | Statistic | User-uploaded PNG / available |
| [`assets/statistic/blue_bottle.png`](../assets/statistic/blue_bottle.png) | Water metric illustration | Statistic | User-uploaded PNG / available |
| [`assets/statistic/sleeping_star_pillow.png`](../assets/statistic/sleeping_star_pillow.png) | Sleep metric illustration | Statistic | User-uploaded PNG / available |
| [`assets/statistic/pink_graph.png`](../assets/statistic/pink_graph.png) | Pink/coral chart-like **visual reference/decorative overlay** (candidate for HR) | Statistic | User-uploaded PNG / available |
| [`assets/statistic/pink_smooth.png`](../assets/statistic/pink_smooth.png) | Pink soft glow behind illustration/graph | Statistic | User-uploaded PNG / available |
| [`assets/statistic/green_graph.png`](../assets/statistic/green_graph.png) | Green chart-like **visual reference/decorative overlay** (candidate for Steps) | Statistic | User-uploaded PNG / available |
| [`assets/statistic/green_smooth.png`](../assets/statistic/green_smooth.png) | Green soft glow behind illustration/graph | Statistic | User-uploaded PNG / available |

**Provenance:** source files uploaded in the user-supplied commits, not crops created by this documentation task. **Alpha/transparency:** intended independent assets; validate actual alpha bounds and background in the Expo import pipeline rather than asserting an uninspected property. Exact associations/placement of the two color-coded chart assets must be visually checked against each screenshot; their filenames alone do not prove backend chart semantics.

## 3. Composition (back to front)

1. **Background:** actual native Light/Dark wellness surface; not the full-screen PNG.
2. **Soft ambient color:** optionally layer `pink_smooth.png` or `green_smooth.png` behind its matching visual where the reference uses it; `contain`, respect natural aspect ratio, avoid readability overlap.
3. **Metric illustration / decorative preview:** independently render heart/shoe/bottle/sleep artwork, and only appropriate `*_graph.png` visual accents. Header/banner artwork sits on the **right**, with live heading and copy on the **left**.
4. **Native card surfaces:** four sections in fixed HR → Steps → Water → Sleep order; soft metric accents; responsive layouts.
5. **Functional content above art:** real metric values, labels, scope control, navigation, chart paths/bars, and Day Sleep's conditional feeling/text. This layer must remain dynamic and accessible.

**Data visualizations:** Never use a frozen PNG graph to impersonate actual recorded metrics. Reimplement any data-bearing line/bars with a chart component using valid data; isolated PNG graph artwork can serve only as decorative reference/overlay where it does not misrepresent a reading. Do not flatten screen into an image.

## 4. FE handoff checks

- [ ] Four current screenshots resolve and old cropped Week/legacy SVG links have been removed from active docs.
- [ ] All eight listed standalone assets resolve at **`assets/statistic/`**, without relocating binary files during this documentation-only change.
- [ ] The Day screenshot ordering defect is explicitly corrected in **both Day themes**; Week order is used across all variants.
- [ ] Day Sleep feeling is data-backed; missing feeling has neutral fallback; Week Sleep still has trend.
- [ ] Banner uses text-left/illustration-right; graphs/glows are positioned behind live text/controls with no clipping.
- [ ] React Native chart/data UI is native; transparent PNG bounds and visual fidelity are reviewed at runtime.
- [ ] Mapping is consistent with [component manifest](component-manifest.json) and [asset manifest](../assets/statistic/asset-manifest.json); no unsupported backend contract inferred from art.
