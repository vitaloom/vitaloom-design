# Onboarding — approved screen to transparent asset mapping

**Status:** approved **screen mockups** + newly drawn **SVG asset candidates awaiting visual acceptance**.
**Scope:** ONB-SCR-001 to ONB-SCR-004. This document applies the repository-wide [Asset Mapping Standard](../ASSET_MAPPING_STANDARD.md) to onboarding-specific art and layout; it does not prescribe universal layers, color tokens or fixed viewBox sizes. [BEHAVIOR.md](BEHAVIOR.md) remains the interaction authority.

## Source-of-truth relationship

- Full-screen designs in this `onboarding/` folder are the approved visual references and remain unchanged.
- Individual SVG files under [`../assets/onboarding/`](../assets/onboarding/) are newly drawn visual-only assets with transparent canvases. They are **not crops** from the mockups or pixel-perfect reproductions.
- The viewBox for each hero and landscape is `0 0 390 570`; this is a shared illustration coordinate system, **not a mandatory device-size or fixed safe-area height**.
- Machine-readable mapping: [`../assets/onboarding/asset-manifest.json`](../assets/onboarding/asset-manifest.json).

## Per-screen mapping

| Screen ID | Approved mockup | Foreground hero (new SVG) | Behind-hero landscape (new SVG) | Hero illustration meaning |
| --- | --- | --- | --- | --- |
| `ONB-SCR-001` | [01-welcome.webp](01-welcome.webp) | [welcome-hero.svg](../assets/onboarding/welcome-hero.svg) | [welcome-landscape.svg](../assets/onboarding/welcome-landscape.svg) | Woman holding a water bottle with decorative lettering |
| `ONB-SCR-002` | [02-track-what-matters.webp](02-track-what-matters.webp) | [track-hero.svg](../assets/onboarding/track-hero.svg) | [track-landscape.svg](../assets/onboarding/track-landscape.svg) | Tilted mobile-style health metric illustration |
| `ONB-SCR-003` | [03-build-healthy-habits.webp](03-build-healthy-habits.webp) | [habits-hero.svg](../assets/onboarding/habits-hero.svg) | [habits-landscape.svg](../assets/onboarding/habits-landscape.svg) | Habit calendar, target and wellness items |
| `ONB-SCR-004` | [04-see-your-progress.webp](04-see-your-progress.webp) | [progress-hero.svg](../assets/onboarding/progress-hero.svg) | [progress-landscape.svg](../assets/onboarding/progress-landscape.svg) | Weekly progress and achievement illustration |

### Optional shared decoration

[mint-leaf-cluster.svg](../assets/shared/mint-leaf-cluster.svg) is a reusable independent vector illustration. It is **optional**, not a fifth mandatory layer in every scene. Some hero and landscape SVGs already contain leaves; do not inadvertently stack duplicate clusters.

## Layer order in React Native / Expo

From back to front:

1. **App-owned background gradient:** warm cream `#FFFCF9` to soft mint `#E6F9F3`; gradient should be implemented in the layout, not baked into SVG root backgrounds.
2. **Landscape SVG:** decorative mountains, waves and foliage for the current screen (no touch handling).
3. **Hero SVG:** isolated subject/illustration for the current screen (no touch handling).
4. **Native rounded white content panel:** sits above/overlaps the illustration region and contains the current title, subtitle, pagination indicator and CTA.
5. **Native app UI:** system/safe-area accommodation, text, buttons and event handlers; never render these as an image.

Keep hero and landscape fitted to the **same parent illustration box and aspect ratio**. In Expo, render editable SVGs using `react-native-svg` and an appropriate SVG transform/build workflow, or export a transparent PNG at the required density. Avoid using a full-screen mockup WebP as the actual interactive screen.

### Composition sketch

```text
OnboardingScreen (native layout)
├── HeroStage (matching 390:570 illustration aspect ratio)
│   ├── Native cream/mint background gradient
│   ├── <LandscapeSvg />  // decorative; absolute fill
│   └── <HeroSvg />       // decorative; absolute fill
└── ContentPanel (native rounded surface; overlaps HeroStage)
    ├── Title and description
    ├── 4 pagination dots (current state)
    └── CTA (native pressable, navigation per BEHAVIOR.md)
```

## Visual review and acceptance

- [ ] `ONB-SCR-001`: welcome illustration matches desired photorealistic vs. vector direction; bottle and lettering are legible.
- [ ] `ONB-SCR-002`: each card/icon in the tracking illustration is recognizable at mobile scale.
- [ ] `ONB-SCR-003`: calendar, goal target, water, sleep and heart motifs read clearly.
- [ ] `ONB-SCR-004`: bars, progress arrow and trophy remain legible at typical device sizes.
- [ ] All four pairs have truly transparent root canvases and clean isolated boundaries.
- [ ] Landscape/hero alignment remains consistent with varying device widths; no forced cropping over the white panel.
- [ ] Text and buttons are native accessible components; no accidental noninteractive screenshot implementation.
- [ ] Ensure no UI treats the numbers illustrated inside hero assets as actual authenticated metrics.

**Important visual limitation:** the welcome mockup uses a realistic human figure, whereas the newly drawn SVG is a stylized vector. This mapping is correct by *screen role and asset filename*, but it does not prove an exact appearance match or signify final visual approval.

## Documentation traceability

- [Onboarding visual catalog](README.md) and [behavior contract](BEHAVIOR.md)
- [Editable assets](../assets/onboarding/README.md) and [JSON manifest](../assets/onboarding/asset-manifest.json)
- [Global asset mapping standard](../ASSET_MAPPING_STANDARD.md), [asset storage rules](../assets/README.md) and [screen behavior standard](../BEHAVIOR_STANDARD.md)
