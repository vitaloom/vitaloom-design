# Steps — approved-direction screen to independent art mapping

**Scope:** STP-SCR-001 and STP-SCR-001-D; artwork added 2026-11-11 on the Steps/Heart Rate refresh branch.  
**Visual status:** Approved **overall direction** from screen review; independent vector redraws are `PROPOSED` until visual side-by-side review.  
**Source of truth:** [Steps screens](README.md), [UI behavior](BEHAVIOR.md), [global asset mapping](../ASSET_MAPPING_STANDARD.md), [manifest](../assets/steps/asset-manifest.json).

## Current source assets

| Role / z-order | Exact asset | Artboard | Composition |
| --- | --- | --- | --- |
| background, 0 | Native themed mint/neutral hero gradient | card native surface | Full bounds; do not bake functional text into image |
| scenery, 1 | [Mint waves and leaves](../assets/steps/steps-hero-scenery.svg) | 430 × 180 transparent SVG | Absolute, bottom 0, width 100%; preserve aspect, clipped to rounded hero |
| hero, 2 | [Two sneakers](../assets/steps/steps-sneakers-hero.svg) | 440 × 320 transparent SVG | Absolute right ~0–8dp, upper center; contain, reference width ~160–180dp on a 393dp viewport |
| interactive UI, 3 | Native date, total steps, count, labels | Actual FE values | Left aligned, above scenery; avoid overlap on narrow widths |
| icons | [Analytics SVG icon kit](../assets/shared/analytics-icons/README.md) | 24 × 24 | Named semantic icons in title/summary/tooltips; adapt tint to app theme |

Reference full screens: [Light](final-light.svg) · [Dark](final-dark.svg). These are **full-screen designs**, never installed as a screen background.

## Composition details

- Reference viewport: **393 × 852 CSS/device-independent units**. Responsive content area uses ~16dp horizontal padding. Hero radius 22–26dp, height ~150–176dp (adapt to text scaling).
- Hero illustration must occupy the **right third** without occluding the large value. If text wraps, shrink art (not text) or stack appropriately. Clip illustration+scenery at hero radius.
- Keep illustrated scene decoration independent from live labels, buttons and chart. Artwork has `pointerEvents="none"`; decorative screen-reader content is hidden.
- The image backgrounds are **transparent**. Preserve the original gradient using native FE theme colors and/or `expo-linear-gradient`. Do not replace hero with a blank solid white card.
- Use the same geometry in dark theme; only surface, elevation, tint/opacity and text contrast adjust. No fake steps or device status in artwork.

## Data and boundary

- Chart, numeric Y axis, tooltip, tabs, KPI tiles are **native interactive UI**, never part of imported art.
- The original approved generated screen is a visual target; the new editable sneaker vectors are independently redrawn assets and may need further art polish after comparison.
- Follow [Steps canonical references](REFERENCES.md); screenshot figures are placeholders only.

## Acceptance checks

- [ ] Every mapped asset path exists on this branch; reusable assets have clear roles and transparent root.
- [ ] Hero text remains selectable/accessible and is not embedded in scenery or sneaker image.
- [ ] Shoe illustration, lower mint waves, date badge and record count are visually present.
- [ ] No illustration obscures text at 320/393/430 widths or large text scale.
- [ ] Light and dark show identical content and chart behavior.
