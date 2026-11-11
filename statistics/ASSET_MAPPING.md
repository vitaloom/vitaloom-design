# Statistics Overview — visual asset and composition mapping

The Statistics Overview is **presentation only**. Import reusable illustrations from existing design/frontend repositories rather than copying or reauthoring them. Full-screen [Week](overview-week-light.svg) and [Day](overview-day-light.svg) mockups are visual references, **not flattened UI components**.

| Card | Preferred existing asset | Native sizing / use |
| --- | --- | --- |
| Heart Rate | [Glossy coral heart SVG](../assets/heart-rate/heart-pulse-hero.svg) or [HR pulse icon](../assets/shared/analytics-icons/heart-pulse.svg) | About 36–50dp, clipped/contained within card left icon slot, no ECG/live claim |
| Steps | [Mint sneaker SVG](../assets/steps/steps-sneakers-hero.svg) or [footsteps icon](../assets/shared/analytics-icons/footsteps.svg) | About 40–50dp; reuse art without adding a second hero |
| Water | Existing frontend bottle artwork (`vitaloom-frontend/assets/images/bottle.png`) or native droplets icon | Blue accent, about 36–50dp. Water design repo currently has no standalone approved bottle PNG |
| Sleep | [Moon-cloud-stars PNG](../assets/sleep-tracking/moon-cloud-stars.png), [Moon SVG fallback](../assets/sleep-tracking/icons/moon.svg) | About 40–50dp, only muted lilac inside card; do not recolor the page purple |
| Header / calendar / chevron | Existing app icon components | Shared UI, no cloned icon file required |
| Mini chart | **Native SVG/views derived from real metric data** | Never embed pre-rendered chart pictures from screenshot |
| Tab and bottom nav | Existing app design tokens + shared navigation | Single owner, keep existing app shell |

## Screen composition

1. Header, VitaLoom brand, shared drawer toggle → app-owned.
2. Statistics eyebrow/title/subtitle → native feature screen content.
3. Segmented mode + centered period navigation → shared local state.
4. Four pastel cards (HR / Steps / Water / Sleep), each native card: illustration left, title, context, value, **right-side mini chart**, chevron.
5. Existing shared bottom tabs, active Statistics route.

No additional 3D artwork or red-background layer is required for this simple Statistics baseline. The **pastel color is local to each metric card**; keep the canvas mint/neutral with a very subtle decorative heading wave only.

To avoid screenshot-implementation drift: compare frontend renders against the four [screen references](README.md), but treat example dates/values as illustrative. Do not use a large HR/Shoes hero banner inside a 110–125dp overview card.
