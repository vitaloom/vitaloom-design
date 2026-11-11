# Heart Rate — screen to independent art mapping

**Scope:** HRT-SCR-001 and HRT-SCR-001-D. Approved overall visual direction, new independent art vectors `PROPOSED` pending visual review.  
**Authority:** [Heart Rate screens](README.md), [UI behavior](BEHAVIOR.md), [asset mapping standard](../ASSET_MAPPING_STANDARD.md), [machine manifest](../assets/heart-rate/asset-manifest.json).

## Additional page background and KPI art

| UI role | Light | Dark | Placement |
| --- | --- | --- | --- |
| Feature-page native base gradient | `#FFF9FA` → `#FFF3F6` | `#211F29` → `#1A242B` | HR page only; behind scroll content; never global AppShell |
| Optional ambient backdrop | [Blush glow — light](../assets/heart-rate/hr-screen-ambient-light.svg) | [Blush glow — dark](../assets/heart-rate/hr-screen-ambient-dark.svg) | `absoluteFill` behind HR content, pointer-events none, hidden from a11y |
| Min KPI icon | [hr-min-light.svg](../assets/heart-rate/icons/hr-min-light.svg) | [hr-min-dark.svg](../assets/heart-rate/icons/hr-min-dark.svg) | Native Minimum tile, render 30–40dp |
| Avg KPI icon | [hr-avg-light.svg](../assets/heart-rate/icons/hr-avg-light.svg) | [hr-avg-dark.svg](../assets/heart-rate/icons/hr-avg-dark.svg) | Native Average tile, render 30–40dp |
| Max KPI icon | [hr-max-light.svg](../assets/heart-rate/icons/hr-max-light.svg) | [hr-max-dark.svg](../assets/heart-rate/icons/hr-max-dark.svg) | Native Maximum tile, render 30–40dp |
| Analytics heading icon | [hr-analytics-light.svg](../assets/heart-rate/icons/hr-analytics-light.svg) | [hr-analytics-dark.svg](../assets/heart-rate/icons/hr-analytics-dark.svg) | Before native `Phân tích nhịp tim` label; ~28–32dp |

Assets include their own circular badge backgrounds: **do not double-wrap in another pastel circle**. See [background theme guidance](../assets/heart-rate/BACKGROUND_TOKENS.md) and [HR icon catalog](../assets/heart-rate/icons/README.md). Numbers, labels and BPM units stay native accessible text sourced from canonical BE.

## Layer mapping

| Layer / z-index | Asset | Native / size | Position and rendering |
| --- | --- | --- | --- |
| -2 — page background | Native warm blush/charcoal feature-only gradient | full-screen container | Under all HR feature content; AppShell unaffected |
| -1 — page ambient | [Light](../assets/heart-rate/hr-screen-ambient-light.svg) / [Dark](../assets/heart-rate/hr-screen-ambient-dark.svg) | Transparent SVG | Optional ambient overlay behind scroll content; no pointer events |
| 0 — hero surface | Native light blush gradient or dark rose surface | rounded card, themed | Fill rounded rectangle ~150–176dp high, ~22–26dp radius |
| 1 — scenery | [Blush waves and botanical accents](../assets/heart-rate/heart-hero-scenery.svg) | Transparent 430×180 SVG | Anchor bottom, 100% width; clip within hero |
| 2 — glossy heart | [Coral dimensional pulse illustration](../assets/heart-rate/heart-pulse-hero.svg) | Transparent 320×300 SVG | Contain on right, approx 150–175dp wide on 393dp viewport |
| 3 — native text | Latest, BPM, actual occurred-at instant | Real API-driven text | Left aligned, above scene; never contained inside the SVG |
| Icons | [Analytics SVG kit](../assets/shared/analytics-icons/README.md) | 24×24 vectors | Heart, chart bars, trend low/high, info, calendar, clock |

Reference screens: [Light](final-light.svg) · [Dark](final-dark.svg). Full-screen references **must not** be used as flat interactive screen assets.

## Precise behavior for rendering

- Keep the approved Steps-like **left-aligned** screen title area, and the dramatic **coral/pink heart hero** instead of a plain rectangular flat-colored card.
- Render 3D-style heart PNG-like aesthetic using the **included authored vector**, rather than substituting a tiny emoji/icon or independently recreating the heart shape in each screen.
- The white zig-zag on the heart is **decorative artwork** and does **not** mean ECG, Live or continuous monitoring. No invented medical claims.
- In narrow layouts, value and timestamp remain readable; responsive art shrinks/relocates before hiding text. Dynamic theme colors must not reduce legibility.
- Hero art, scenery and labels are separate layers with fixed z-order; no pointer interception or image-only functional text.

## Feature / API boundary

Do not bake chart dots, tooltip, low/avg/high or sample count into images. Those remain native UI based on the actual [canonical HR Backend contract](REFERENCES.md). No API schema or database model is copied into this design folder.

## Additional icon QA

- [ ] All 3 KPI tiles use the **dedicated matching theme variant** (`hr-min-*`, `hr-avg-*`, `hr-max-*`).
- [ ] HR analytics title uses the `hr-analytics-*` icon, not a text emoji.
- [ ] The ambient blush remains subtle on page margins; the white/elevated cards remain high contrast.
- [ ] Do not tint Steps/Water pages with HR blush or overpaint shared shell/footer.

## Visual QA

- [ ] Heart illustration full-size visible, halo/gloss and pink scenery visible.
- [ ] Hero still reads as a wellness banner at 393dp viewport and in both themes.
- [ ] HR status and values accurate; the art itself conveys no medical interpretation.
- [ ] Chart min/max whiskers remain tied to observed buckets and detached from imagery.
