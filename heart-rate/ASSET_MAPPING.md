# Heart Rate — screen to independent art mapping

**Scope:** HRT-SCR-001 and HRT-SCR-001-D. Approved overall visual direction, new independent art vectors `PROPOSED` pending visual review.  
**Authority:** [Heart Rate screens](README.md), [UI behavior](BEHAVIOR.md), [asset mapping standard](../ASSET_MAPPING_STANDARD.md), [machine manifest](../assets/heart-rate/asset-manifest.json).

## Layer mapping

| Layer / z-index | Asset | Native / size | Position and rendering |
| --- | --- | --- | --- |
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

## Visual QA

- [ ] Heart illustration full-size visible, halo/gloss and pink scenery visible.
- [ ] Hero still reads as a wellness banner at 393dp viewport and in both themes.
- [ ] HR status and values accurate; the art itself conveys no medical interpretation.
- [ ] Chart min/max whiskers remain tied to observed buckets and detached from imagery.
