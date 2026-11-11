# Statistics Overview B — visual assets and composition

**Approved visual baseline:** raster crops of the original **Wellness Analytics B** phones:
- [Light](approved-b-week-light.webp)
- [Dark](approved-b-week-dark.webp)

Both images are faithful **crops of the approved artwork**, reduced in pixel resolution for repo preview. No image-generation or SVG reconstruction step was applied to change their content. If the crop and a low-fidelity legacy SVG conflict, the **crop wins**. These crops must **not** be used as flat screens in the running app.

## Reuse existing feature artwork

| Card | Asset recommendation | Why |
| --- | --- | --- |
| HR | [Dimensional pulse heart](../assets/heart-rate/heart-pulse-hero.svg) or an existing matching polished heart icon | Matches glossy coral heart identity; **not** the prior hand-drawn tiny heart path |
| Steps | [Sneaker illustration](../assets/steps/steps-sneakers-hero.svg) or existing app sneaker illustration | Preserve mint-and-white dimensional shoes from approved screen |
| Water | Existing frontend water-bottle illustration from the Water feature, or suitable existing shared water asset | Preserve translucent blue bottle style; no flat square bottle rebuild |
| Sleep | [Moon/cloud illustration](../assets/sleep-tracking/moon-cloud-stars.png) or selected sleep UI artwork | Dimensional purple pillow/moon/stars, not simple crescent built from paths |
| Calendar / menu / chevron / bottom nav | Existing app shared icon library / AppShell | Same glyph, alignment and stroke style as app; not duplicated inline vector sketches |
| Mini charts | **Native components** based on real API series | HR connected dot line; Steps mint bars; Water blue bars; Sleep violet duration bars; do **not** use sample chart pixels as measurements |

## Layout / layering

- Parent canvas uses the app's soft neutral/mint wellness palette in light mode and deep navy/charcoal dark mode.
- Use top header from **shared AppShell** (sidebar closed by default), below it feature title/description and right-side small green/pink accent bars. Keep it subtle, not a big Home hero.
- Place the global period control above **all** metric cards. The current active pill in B is **rose/coral**, not mint/teal.
- Pastel backgrounds belong on the four individual cards. Each card contains: icon left, label/context center-left, value toward lower-left, compact chart at lower-right, and navigational chevron upper-right.
- Match nuanced surface highlights, shadows, illustrations and spacing of the *actual B raster*. Never draw a replacement illustration using generic SVG circles/triangles.
- No KPI comparison/range badge/footer insight, giant vertical chart, or detailed information in this approved compact view.

## QA checklist

- [ ] Compare FE **directly against** the approved B Light/Dark crops at equivalent viewport aspect, not against any SVG in `legacy/`.
- [ ] Illustration matches actual asset vocabulary: 3D heart / mint shoes / blue bottle / lavender sleep art.
- [ ] Card content and mini chart remain separate native, accessible elements, not flattened images.
- [ ] No forced fit-all-cards: natural vertical scroll, accessible text and responsive layouts.
- [ ] Correct Day/Week chart semantics use backend data; no future dots/bars, no fabricated values or progress.
- [ ] No redesigned detail pages, new backend contracts or unsolicited visual changes.
