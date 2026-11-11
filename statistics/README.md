# Statistics Overview — Wellness Analytics B (approved visual direction)

**Status: APPROVED VISUAL BASELINE FOR WEEK OVERVIEW.** The **user-approved high-fidelity Wellness Analytics B** from the original four-screen design board is the **sole visual source of truth**. This folder now includes *unaltered-composition crops* of the two B phone screens as raster previews. They are scaled-down preview exports of the user's selected board, **not manually redrawn SVGs**. The original board image supplied during design review takes precedence if a tiny preview lacks fine detail.  

**Do not implement any of the older `overview-*.svg` drawings as current design.** Those were primitive approximations and have been moved under [legacy](legacy/README.md) specifically to prevent an agent copying their inferior illustrations.

## Current approved visual references (mode = Week)

| Screen | Reference | Purpose |
| --- | --- | --- |
| `STA-SCR-001-W-L` | ![Approved B — Week Light](approved-b-week-light.webp) | Light mode, original B card artwork and proportions |
| `STA-SCR-001-W-D` | ![Approved B — Week Dark](approved-b-week-dark.webp) | Dark mode, original B colors and rendering |

[Open Week Light](approved-b-week-light.webp) · [Open Week Dark](approved-b-week-dark.webp).

These are **reduced-resolution raster crops** directly from the approved board, included to preserve visual fidelity and avoid another redraw. They should **not** be used as actual UI images. Real UI must be responsive React Native components with real data and independent chart rendering. Use the original board presented in the review conversation for the highest-clarity comparison. Do not interpret its example metric values as API fixtures.

### Day mode

**Behavior approved, separate visual artwork NOT independently approved:** The global period control supports Day as well as Week. Use the exact same card shell, iconography, spacing, palette and visual language as the approved Week B mockup. Adjust the displayed metric context, period text and charts according to [BEHAVIOR.md](BEHAVIOR.md). **Do not revive the hand-drawn SVG day version as a new visual baseline.** If a separate Day screenshot is needed later, it requires its own design review.

## Scope and layout

- **Statistics is a multi-metric trend explorer**, not Home 2.0.
- One vertically scrollable page with **four metric preview cards**, in order: Heart Rate → Steps → Water → Sleep.
- Shared header/navigation shell. Native `Thống kê` heading, subtle wave and compact green decorative bars at upper right. Separate global `Ngày / Tuần` segmented selector and period navigation.
- Week is the **default** first-visit scope. User taps whole card to open existing metric detail screen.
- Each card: expressive original **metric artwork** on left, title + short context, large value + unit, **small chart preview** at lower-right, chevron at upper-right. No tooltip on preview cards.
- HR coral/blush, Steps mint, Water sky blue, Sleep lavender. Light page mostly cream-white and mint; dark page deep navy/charcoal with softened metric-color panels.
- Cards may extend below screen and require vertical scrolling. **Do not compress them just to show all four in one viewport.**
- Only compact B: no comparison with previous periods, no Min/Avg/Max sub-cards, no long insight ribbons, no `Tối giản / Chi tiết` toggle, no quick-add, and no new metric-detail redesign.

## Responsive reference

A cropped screenshot from a design presentation is not a precise DP scale. For a 393dp viewport, start with ~16dp outer gutters, ~16dp internal card padding, ~18–22dp radius, ~10–14dp card gap, and a ~110–145dp natural card height depending on text scaling/locale. Treat these as **implementation guidelines**, not a reason to change the approved screenshot's proportions. Mini charts should fit their designated right-side space with no horizontal scrolling.

**Important:** The SVGs in [legacy](legacy/) are not authoritative for proportions, font, illustration or icons. The original B screenshot is authoritative for those properties. Other modules' legacy backgrounds or redesign experiments must not override it.

## Related specifications

- [Behavior: day/week/navigation, independently handled states](BEHAVIOR.md)
- [Asset reuse and screenshot fidelity](ASSET_MAPPING.md)
- [Manifest — current screen authority and deprecated references](component-manifest.json)
- [Shared health metrics drawer](../shared/health-metrics-sidebar/README.md)

**API/model ownership:** This is a visual specification, not a duplicate API schema or database model. Read current canonical backend docs and existing frontend repositories when implementing.
