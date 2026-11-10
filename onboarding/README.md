# Healthy Check — First-Launch Onboarding

**Visual status:** User-approved, four screens. **Behavior status:** See [BEHAVIOR.md](BEHAVIOR.md) for explicit interaction decisions and open questions.

This is the **introductory carousel before authentication**. It is not the Personal Health Profile setup offered after sign-up. The approved screens use the common visual structure: **hero image above + rounded white text and CTA section below**.

## Approved screens and illustration assets

The WebP mockups below are the **approved full-screen design references**. The user selected the three newly generated transparent PNG hero assets for ONB-SCR-002/003/004 as replacements. All four pages now map to a single **shared six-piece transparent PNG landscape** rendered from a scene recipe; individual legacy SVG landscapes remain as migration fallbacks. The welcome hero still awaits visual review.

| Screen ID | Approved full-screen design | Hero layer (transparent PNG for 002–004) | Active layered landscape (shared PNG) | Message |
| --- | --- | --- | --- | --- |
| `ONB-SCR-001` | ![Welcome](01-welcome.webp) | [welcome-hero.svg](../assets/onboarding/welcome-hero.svg) | [Shared scene](../assets/shared/wellness-landscape/composition.json) | Track · Improve · Feel Better |
| `ONB-SCR-002` | ![What matters](02-track-what-matters.webp) | [track-hero.png](../assets/onboarding/track-hero.png) | [Shared scene](../assets/shared/wellness-landscape/composition.json) | Track What Matters |
| `ONB-SCR-003` | ![Healthy habits](03-build-healthy-habits.webp) | [habits-hero.png](../assets/onboarding/habits-hero.png) | [Shared scene](../assets/shared/wellness-landscape/composition.json) | Build Healthy Habits |
| `ONB-SCR-004` | ![Progress](04-see-your-progress.webp) | [progress-hero.png](../assets/onboarding/progress-hero.png) | [Shared scene](../assets/shared/wellness-landscape/composition.json) | See Your Progress |

[View all four approved screens in one image](onboarding-approved-overview.webp).

**Implementation handoff:** [screen-to-asset mapping, layer order and QA](ASSET_MAPPING.md) (following the [global asset mapping standard](../ASSET_MAPPING_STANDARD.md)) · [asset catalog](../assets/onboarding/README.md) · [machine-readable manifest](../assets/onboarding/asset-manifest.json). The [shared composition](../assets/shared/wellness-landscape/README.md) is assembled from six separate PNGs: back hills, middle waves, front mound and three leaf clusters. Do not combine it with the deprecated screen-specific SVG landscapes or optional duplicate leaves.

## Design contract

- Consistent warm white/cream + mint background, decorative leaves, soft illustrations and deep teal action button.
- Same vertical hierarchy on all four screens: hero art, lower rounded white surface, title, supporting copy, pagination dots, bottom CTA.
- Image content illustrates benefits, not live or device-connected health data.
- UI copy and numerical health examples in the images are illustrative, not application state.

## Related flow

[Behavior and transition matrix](BEHAVIOR.md) → [Authentication entry](../authentication/README.md) → optional [Personal Health Profile](https://github.com/vitaloom/vitaloom-business-docs-and-tools/tree/main/docs/usecase_spec/personal-health-profile).

**Assets policy:** these WebP files are complete screen designs, **not** transparent component assets. The selected PNG hero assets and legacy fallback SVGs are under [`../assets/onboarding/`](../assets/onboarding/); reusable decoration is under [`../assets/shared/`](../assets/shared/). Implement native UI for all actions and text outside illustrations.

**PNG hero files:** `track-hero.png`, `habits-hero.png` and `progress-hero.png` are committed as independent transparent PNG art, not as full-screen WebP mockups.

**Visual review:** The shared landscape recipe is a new compositional proposal; its layout and overlap with each hero must be checked in the app on representative device sizes. The original approved full-screen designs remain unchanged.
