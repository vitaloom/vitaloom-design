# Onboarding — mapping for hero assets and shared composable landscape

**Scope:** `ONB-SCR-001` through `ONB-SCR-004`. Approved full-screen WebP mockups remain the visual references. Foreground PNG hero artwork for 002–004 was specifically selected; the welcome SVG hero remains a separate visual candidate. **The new shared landscape composition is proposed and needs Expo visual QA**.

Behavior/navigation authority: [BEHAVIOR.md](BEHAVIOR.md). Repository policy: [ASSET_MAPPING_STANDARD.md](../ASSET_MAPPING_STANDARD.md).

## Per-screen asset mapping

| Screen ID | Approved full-screen design | Foreground hero | Active landscape recipe | Legacy standalone landscape (fallback only) |
| --- | --- | --- | --- | --- |
| `ONB-SCR-001` | [01-welcome.webp](01-welcome.webp) | [welcome-hero.svg](../assets/onboarding/welcome-hero.svg) | [Shared composition](../assets/shared/wellness-landscape/composition.json) | [welcome-landscape.svg](../assets/onboarding/welcome-landscape.svg) |
| `ONB-SCR-002` | [02-track-what-matters.webp](02-track-what-matters.webp) | [track-hero.png](../assets/onboarding/track-hero.png) | [Shared composition](../assets/shared/wellness-landscape/composition.json) | [track-landscape.svg](../assets/onboarding/track-landscape.svg) |
| `ONB-SCR-003` | [03-build-healthy-habits.webp](03-build-healthy-habits.webp) | [habits-hero.png](../assets/onboarding/habits-hero.png) | [Shared composition](../assets/shared/wellness-landscape/composition.json) | [habits-landscape.svg](../assets/onboarding/habits-landscape.svg) |
| `ONB-SCR-004` | [04-see-your-progress.webp](04-see-your-progress.webp) | [progress-hero.png](../assets/onboarding/progress-hero.png) | [Shared composition](../assets/shared/wellness-landscape/composition.json) | [progress-landscape.svg](../assets/onboarding/progress-landscape.svg) |

All 4 screens now use the same *active* landscape composition; **never render the old landscape SVG and new layered scene together**. The old SVG files remain in source control solely as temporary compatibility references for frontend code that has not migrated. Their paths are still present as the legacy `landscape` field in the manifest; prefer `activeLandscape=shared-composition` and `landscapeComposition` instead.

## Shared PNG layers and ordering

Render components from [shared wellness landscape catalog](../assets/shared/wellness-landscape/README.md) according to [composition.json](../assets/shared/wellness-landscape/composition.json):

| Order | Layer | File | Role |
| --- | --- | --- | --- |
| 10 | Back hills | [mint-back-hills.png](../assets/shared/wellness-landscape/mint-back-hills.png) | Rounded mint hills |
| 20 | Middle waves | [mint-middle-waves.png](../assets/shared/wellness-landscape/mint-middle-waves.png) | Soft overlapping ribbons |
| 30 | Front mound | [mint-front-mound.png](../assets/shared/wellness-landscape/mint-front-mound.png) | Foreground foot |
| 40 | Left sprout | [mint-leaf-sprout.png](../assets/shared/wellness-landscape/mint-leaf-sprout.png) | Upright accent |
| 50 | Bottom-left leaves | [mint-leaves-left.png](../assets/shared/wellness-landscape/mint-leaves-left.png) | Side decoration |
| 60 | Bottom-right leaves | [mint-leaves-right.png](../assets/shared/wellness-landscape/mint-leaves-right.png) | Side decoration |

All assets are individually generated transparent PNGs, not slices from screenshots. Do not reuse the old `mint-leaf-cluster.svg` simultaneously, as the composite already contains foliage.

## Composition and responsive contract (Expo/React Native)

Layer sequence from back to front:

1. Native background cream `#FFFCF9` to mint `#E6F9F3` gradient (not part of PNGs).
2. Shared **six image layers**, drawn as individual absolutely positioned images using each `frame` and `zIndex` from the JSON recipe.
3. Separate foreground **hero** image for the current screen; image fitting and sizing independent from landscape.
4. Native lower white rounded panel and interactive title, subtitle, pagination and CTA.

Coordinates are from a **390 × 570 reference scene**, not a fixed device resolution. Calculate a uniform scale using the actual available illustration-stage width/height, center it and preserve every image's original aspect ratio. Some waves use negative x to extend softly off-stage; verify intended clipping on compact phones. Never render a full-screen WebP mockup as UI.

Only copy static asset paths through `require()` so Metro can package them. `Image` / `expo-image` uses `contain` for PNGs. Mark the six decorative components inaccessible to assistive tech and non-interactive. User-facing text/actions must remain native.

## Machine-readable authority and review status

- [Feature asset-manifest.json](../assets/onboarding/asset-manifest.json) records the active shared recipe by Screen ID plus the legacy SVG fallback field.
- [Composition recipe JSON](../assets/shared/wellness-landscape/composition.json) owns shared layer IDs, PNG filenames, positions, intrinsic stage and `zIndex`; do not maintain conflicting layout constants elsewhere.
- `ONB-SCR-001`: welcome hero is pending visual acceptance; 002–004: new PNG heroes selected by user. The **combined landscape** is a new proposal, not automatically approved by the selected hero artwork.
- Validate all 4 screens on narrow and tall devices, confirm no duplicate leaves, check cropping around CTA/panel, and confirm illustrated measurements are not live user data.
