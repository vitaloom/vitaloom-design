# Healthy Check — First-Launch Onboarding

**Visual status:** User-approved, four screens. **Behavior status:** See [BEHAVIOR.md](BEHAVIOR.md) for explicit interaction decisions and open questions.

This is the **introductory carousel before authentication**. It is not the Personal Health Profile setup offered after sign-up. The approved screens use the common visual structure: **hero image above + rounded white text and CTA section below**.

## Approved screens and illustration assets

The WebP mockups below are the **approved full-screen design references**. The SVG assets are newly drawn transparent illustration layers **awaiting visual review**, not pixel-identical exports or approved replacement imagery.

| Screen ID | Approved full-screen design | New hero layer (transparent) | New landscape layer (transparent) | Message |
| --- | --- | --- | --- | --- |
| `ONB-SCR-001` | ![Welcome](01-welcome.webp) | [welcome-hero.svg](../assets/onboarding/welcome-hero.svg) | [welcome-landscape.svg](../assets/onboarding/welcome-landscape.svg) | Track · Improve · Feel Better |
| `ONB-SCR-002` | ![What matters](02-track-what-matters.webp) | [track-hero.svg](../assets/onboarding/track-hero.svg) | [track-landscape.svg](../assets/onboarding/track-landscape.svg) | Track What Matters |
| `ONB-SCR-003` | ![Healthy habits](03-build-healthy-habits.webp) | [habits-hero.svg](../assets/onboarding/habits-hero.svg) | [habits-landscape.svg](../assets/onboarding/habits-landscape.svg) | Build Healthy Habits |
| `ONB-SCR-004` | ![Progress](04-see-your-progress.webp) | [progress-hero.svg](../assets/onboarding/progress-hero.svg) | [progress-landscape.svg](../assets/onboarding/progress-landscape.svg) | See Your Progress |

[View all four approved screens in one image](onboarding-approved-overview.webp).

**Implementation handoff:** [screen-to-asset mapping, layer order and QA](ASSET_MAPPING.md) (following the [global asset mapping standard](../ASSET_MAPPING_STANDARD.md)) · [asset catalog](../assets/onboarding/README.md) · [machine-readable manifest](../assets/onboarding/asset-manifest.json). A [shared mint leaf](../assets/shared/mint-leaf-cluster.svg) is optional decoration; avoid duplicating leaves already drawn in the hero/landscape SVGs.

## Design contract

- Consistent warm white/cream + mint background, decorative leaves, soft illustrations and deep teal action button.
- Same vertical hierarchy on all four screens: hero art, lower rounded white surface, title, supporting copy, pagination dots, bottom CTA.
- Image content illustrates benefits, not live or device-connected health data.
- UI copy and numerical health examples in the images are illustrative, not application state.

## Related flow

[Behavior and transition matrix](BEHAVIOR.md) → [Authentication entry](../authentication/README.md) → optional [Personal Health Profile](https://github.com/vitaloom/vitaloom-business-docs-and-tools/tree/main/docs/usecase_spec/personal-health-profile).

**Assets policy:** these WebP files are complete screen designs, **not** transparent component assets. Newly drawn hero/landscape SVGs are under [`../assets/onboarding/`](../assets/onboarding/), and reusable decoration belongs under [`../assets/shared/`](../assets/shared/). The asset mapping is an implementation reference, not approval of the replacement visual style.

**PNG originals:** preserved in the handoff archive generated alongside this upload; the GitHub copies are optimized WebP renders of the same approved images.
