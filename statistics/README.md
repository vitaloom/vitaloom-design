# Statistics Overview — Wellness Analytics B (minimal / approved)

**Design status:** `APPROVED_DIRECTION` (user selected Wellness Analytics **B – simple**).  
**Scope:** **Statistics Overview only**. Do not redesign Steps, Heart Rate, Water or Sleep detail screens.  
**Visual source:** this folder's light/dark, Day/Week SVG screen references. Artboards are `390 × 844`, SVGs are self-contained editable drawings. Their numbers/charts are **illustrative fixtures**, never actual user/API data. The accepted board image in the design conversation establishes the visual direction; these vectors are implementation-friendly reconstructions, not a pixel-identical export.

## Screen catalog

| ID | Reference | Purpose |
| --- | --- | --- |
| `STA-SCR-001-W-L` | [Week / Light](overview-week-light.svg) | **Default**, all four metric cards, weekly comparison period |
| `STA-SCR-001-W-D` | [Week / Dark](overview-week-dark.svg) | Same hierarchy with dark-themed pastel-on-charcoal |
| `STA-SCR-001-D-L` | [Day / Light](overview-day-light.svg) | Single selected date, same cards and layout |
| `STA-SCR-001-D-D` | [Day / Dark](overview-day-dark.svg) | Day mode in dark theme |

## Design goal

**Statistics = multi-metric trend explorer, not Home 2.0.**

- Use a **single vertical scrolling list of four metric cards**: Heart Rate, Steps, Water, Sleep.
- Global **Ngày / Tuần** switcher and previous/next period selector; default `Tuần`.
- Each card has **one main value + concise context + a small chart preview**. Use appropriate chart geometry for each metric.
- Full card is a navigation target to **existing** metric detail screen.
- No greeting, encouragement/marketing hero, reminder, quick add, add-record buttons, comparison badges, separate per-card time selectors, min/avg/max tile grid, custom-range control, or Tối giản/Chi tiết toggle in this **approved simple baseline**.
- Future enriched mode is a separate design decision; do not implement from historical exploration.

## Layout reference (390dp phone)

| Element | Suggested size / treatment |
| --- | --- |
| Shared app header / drawer | Reuse existing AppShell/sidebar; do not duplicate within feature |
| Heading | Small eyebrow + `Thống kê` at ~26–30sp + one-line subtitle |
| Global time switch | Full-content-width segmented pill: Day and Week; active style rose/coral |
| Date scope selector | Previous chevron, centered period label, next chevron; future scopes disabled |
| Card layout | Content width minus ~16–20dp side margins; corner radius ~18–20dp; gap ~8–12dp |
| Card height | Roughly **110–125dp**, with responsive growth for longer locale/text |
| Icon/illustration | ~36–50dp, left; distinct pastel tint per metric; visually similar to accepted B |
| Metric label & caption | Title ~14–16sp, supporting line ~10–12sp |
| Main value | ~21–25sp bold, proper unit; no overlap with chart |
| Mini chart | ~105–125dp wide × 42–60dp high, right-lower quadrant; **native interactive card preview**, not a static screenshot |
| Footer | Shared bottom navigation, active Statistics destination, no nested scroll |
| Dynamic type & 320dp | Value/text win space over decoration; allow card height to grow or stack chart below text when needed |

Color hierarchy: HR coral pink `#FFF0F4` / rose line, Steps mint `#E6FBF3` / green bars, Water pale blue `#E6F4FF` / blue bars, Sleep lilac `#F0E9FF` / purple bars **only inside its card**; overall app and header stay mint/neutral. Dark uses desaturated charcoal cards with corresponding colored chart accents, not fully saturated panels.

See [Behavior](BEHAVIOR.md), [Asset mapping](ASSET_MAPPING.md), [Component manifest](component-manifest.json). **No Backend contracts or data models are duplicated here.** Always use existing app services and canonical docs for real metric values.
