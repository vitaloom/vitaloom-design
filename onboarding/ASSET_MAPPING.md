# Onboarding — approved screen to transparent asset mapping

**Status:** user-approved full-screen mockups; **new transparent PNG hero assets adopted** for ONB-SCR-002/003/004 (10 November 2026). The welcome SVG remains a visual-review candidate.
**Scope:** ONB-SCR-001 to ONB-SCR-004. This document applies the repository-wide [Asset Mapping Standard](../ASSET_MAPPING_STANDARD.md) to onboarding-specific art and layout; it does not prescribe universal layers, color tokens or fixed viewBox sizes. [BEHAVIOR.md](BEHAVIOR.md) remains the interaction authority.

## Source-of-truth relationship

- Full-screen designs in this `onboarding/` folder are the approved visual references and remain unchanged.
- Individual artwork under [`../assets/onboarding/`](../assets/onboarding/) consists of transparent PNG hero illustrations for screens 002–004, one welcome SVG hero, and SVG landscapes. The new PNG illustrations are newly generated, **not cropped from the full-screen designs**.
- SVG landscapes and the welcome SVG hero use a `0 0 390 570` illustration coordinate system. The new raster PNG heroes are `1122 × 1402` pixels with alpha. **Do not assume their aspect ratio matches the SVG landscape viewBox.**
- Machine-readable mapping: [`../assets/onboarding/asset-manifest.json`](../assets/onboarding/asset-manifest.json).

## Per-screen mapping

| Screen ID | Approved mockup | Foreground hero (transparent PNG for 002–004) | Behind-hero landscape (new SVG) | Hero illustration meaning |
| --- | --- | --- | --- | --- |
| `ONB-SCR-001` | [01-welcome.webp](01-welcome.webp) | [welcome-hero.svg](../assets/onboarding/welcome-hero.svg) | [welcome-landscape.svg](../assets/onboarding/welcome-landscape.svg) | Woman holding a water bottle with decorative lettering |
| `ONB-SCR-002` | [02-track-what-matters.webp](02-track-what-matters.webp) | [track-hero.png](../assets/onboarding/track-hero.png) | [track-landscape.svg](../assets/onboarding/track-landscape.svg) | User-selected soft 3D illustration of tilted health cards on a mint device |
| `ONB-SCR-003` | [03-build-healthy-habits.webp](03-build-healthy-habits.webp) | [habits-hero.png](../assets/onboarding/habits-hero.png) | [habits-landscape.svg](../assets/onboarding/habits-landscape.svg) | User-selected soft 3D calendar with target, water bottle, sleep clock and heart |
| `ONB-SCR-004` | [04-see-your-progress.webp](04-see-your-progress.webp) | [progress-hero.png](../assets/onboarding/progress-hero.png) | [progress-landscape.svg](../assets/onboarding/progress-landscape.svg) | User-selected soft 3D weekly progress card and trophy callout |

### Optional shared decoration

[mint-leaf-cluster.svg](../assets/shared/mint-leaf-cluster.svg) is a reusable independent vector illustration. It is **optional**, not a fifth mandatory layer in every scene. Several hero PNGs and SVG landscapes already include leaves; avoid accidentally duplicating them with shared decoration.

## Layer order in React Native / Expo

From back to front:

1. **App-owned background gradient:** warm cream `#FFFCF9` to soft mint `#E6F9F3`; gradient should be implemented in the layout, not baked into SVG root backgrounds.
2. **Landscape SVG:** decorative mountains, waves and foliage for the current screen (no touch handling).
3. **Hero illustration:** `*.png` with transparency for screens 002–004, `welcome-hero.svg` for screen 001 (no touch handling).
4. **Native rounded white content panel:** sits above/overlaps the illustration region and contains the current title, subtitle, pagination indicator and CTA.
5. **Native app UI:** system/safe-area accommodation, text, buttons and event handlers; never render these as an image.

Keep hero and landscape under one responsive illustration stage, but **position and scale them independently**: render PNG heroes with React Native `Image`/`expo-image` using `contain`, and SVG landscapes using `react-native-svg` or the existing SVG pipeline. Preserve transparent alpha and avoid cropping the subject. Do not use a full-screen mockup WebP as interactive UI.

### Composition sketch

```text
OnboardingScreen (native layout)
├── HeroStage (matching 390:570 illustration aspect ratio)
│   ├── Native cream/mint background gradient
│   ├── <LandscapeSvg />     // decorative; absolute fill
│   └── <HeroIllustration /> // PNG for screens 002–004; SVG for 001
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
- [ ] New hero PNGs have transparent alpha and clean isolated outlines; remaining SVG layers have transparent roots.
- [ ] SVG landscape and PNG hero align on varying device widths despite different aspect ratios; no forced cropping over the white panel.
- [ ] Text and buttons are native accessible components; no accidental noninteractive screenshot implementation.
- [ ] Ensure no UI treats the numbers illustrated inside hero assets as actual authenticated metrics.

**Visual acceptance:** the user explicitly selected the new PNG illustrations for screens 002–004 as replacements. The welcome SVG remains a candidate because its stylized vector differs from the approved realistic full-screen reference. Actual device-size compositing still requires frontend QA.

## Documentation traceability

- [Onboarding visual catalog](README.md) and [behavior contract](BEHAVIOR.md)
- [Editable assets](../assets/onboarding/README.md) and [JSON manifest](../assets/onboarding/asset-manifest.json)
- [Global asset mapping standard](../ASSET_MAPPING_STANDARD.md), [asset storage rules](../assets/README.md) and [screen behavior standard](../BEHAVIOR_STANDARD.md)
