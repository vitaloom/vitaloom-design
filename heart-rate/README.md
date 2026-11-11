# Heart Rate — analytics refresh

**Status:** PROPOSED implementation handoff / visual review. Replaces **MVP UI layout** as current design direction; not an API or business-rules revision.

## Active screen references

| ID | Visual | Purpose |
| --- | --- | --- |
| `HRT-SCR-001` | [Heart Rate — Light](final-light.svg) | Latest-recorded hero; date-aware average; connected-dot chart with subtle min/max ranges |
| `HRT-SCR-001-D` | [Heart Rate — Dark](final-dark.svg) | Same semantics and hierarchy in dark theme |

These editable SVGs are **full-screen visual references**, not code or account data. Example figures are illustrative and chosen to support the pictured chart. The user-approved prior raster mockup is the target visual language; review fidelity before production sign-off.

## Independent hero artwork

- [Glossy heart](../assets/heart-rate/heart-pulse-hero.svg) and [blush hero scenery](../assets/heart-rate/heart-hero-scenery.svg) are reusable transparent vectors.
- [HR asset mapping / layer order](ASSET_MAPPING.md) · [shared icon kit](../assets/shared/analytics-icons/README.md) · [visual enhancement handoff](../UI_ENHANCEMENT_HANDOFF.md).
- Independent assets are redrawn and still PROPOSED pending visual review; do not mislabel them as exact screenshots.

## Preserve

- Steps-like left-aligned heading structure: eyebrow, “Nhịp tim”, supporting subtitle.
- Prominent blush/coral **latest recorded** hero and its actual measured-at timestamp.
- Main chart: coral **connected average dots**, thin translucent vertical min–max whiskers, numerical Y-axis, horizontal grid, and restrained tooltip.
- Light/dark palettes; maintain native shared navigation/one drawer, never embed a second drawer.
- No real-time, ECG waveform, device-connected status or clinical classification is asserted by the illustration.

## Enrich

- Day / Week / Custom period selection with calendar navigation.
- Daily summary with status derived from backend.
- Min/average/max tiles only where derived values are accurate for the selected range; sample count and nonempty-bucket caption.
- Distinct loading/empty/error/historical-unverified states (defined behaviorally; old SVG states retained only in [legacy](legacy/README.md)).

## Authorities

- [Heart Rate behavior](BEHAVIOR.md) — interaction and chart behavior.
- [Canonical references & UI dependencies](REFERENCES.md) — links to active backend and approved business docs; **no schema copies**.
- [Shared analytics component specification](../shared/analytics-components/README.md).
- [Legacy MVP visual spec & states](legacy/README.md) — historical only, not to implement as current layout.

**For implementation:** re-read the Backend API contract, Statistics read model and BRs at current `main`. If a design KPI cannot be derived correctly, mark as blocked / omit it rather than inventing data.
