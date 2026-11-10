# Onboarding illustration assets

**Current layout:** per-screen foreground hero + **shared layered PNG landscape**. Approved full-screen WebP mockups live in [the onboarding catalog](../../onboarding/README.md). Behavior and navigation remain in [BEHAVIOR.md](../../onboarding/BEHAVIOR.md).

| Screen ID | Hero asset | Active landscape | Previous SVG landscape (legacy only) |
| --- | --- | --- | --- |
| `ONB-SCR-001` | [welcome-hero.svg](welcome-hero.svg) | [Shared PNG scene](../shared/wellness-landscape/composition.json) | [welcome-landscape.svg](welcome-landscape.svg) |
| `ONB-SCR-002` | [track-hero.png](track-hero.png) | [Shared PNG scene](../shared/wellness-landscape/composition.json) | [track-landscape.svg](track-landscape.svg) |
| `ONB-SCR-003` | [habits-hero.png](habits-hero.png) | [Shared PNG scene](../shared/wellness-landscape/composition.json) | [habits-landscape.svg](habits-landscape.svg) |
| `ONB-SCR-004` | [progress-hero.png](progress-hero.png) | [Shared PNG scene](../shared/wellness-landscape/composition.json) | [progress-landscape.svg](progress-landscape.svg) |

The 1122 × 1402 hero PNGs for 002–004 were chosen for use by the user and were newly generated (not cropped from screen references). Welcome SVG remains a review candidate. The new shared landscape, built from [six individually transparent PNG components](../shared/wellness-landscape/README.md), still requires frontend composition QA.

## Handoff

Follow the [mapping document](../../onboarding/ASSET_MAPPING.md) and [JSON asset manifest](asset-manifest.json). Read [composition.json](../shared/wellness-landscape/composition.json) for the exact layering and scale coordinates. Draw the native gradient behind scenery, scenery before hero, and functional native content above both. **Do not mix new scene with legacy `*-landscape.svg`**; those SVGs are retained for migration compatibility only. Do not hardcode device size to the reference stage dimensions.

Decorative images must use `pointerEvents="none"` and be hidden from screen readers. Illustrated values are not live health metrics.
