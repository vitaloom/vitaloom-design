# Onboarding — transparent illustration assets

Status: transparent PNG hero illustrations for ONB-SCR-002/003/004 **selected by the user for replacement**, alongside existing SVG landscapes and a welcome SVG candidate. The approved full-screen WebP mockups remain unchanged in [the onboarding screen catalog](../../onboarding/README.md). See [screen-to-asset mapping](../../onboarding/ASSET_MAPPING.md) for roles and layout.

The new 1122 × 1402 hero illustrations are transparent RGBA PNGs generated independently, not crops or masks extracted from screenshot pixels. Remaining SVG layers have transparent root backgrounds.

| Screen ID | Approved screen reference | Hero | Decorative landscape |
| --- | --- | --- | --- |
| `ONB-SCR-001` | [01-welcome.webp](../../onboarding/01-welcome.webp) | [welcome-hero.svg](welcome-hero.svg) | [welcome-landscape.svg](welcome-landscape.svg) |
| `ONB-SCR-002` | [02-track-what-matters.webp](../../onboarding/02-track-what-matters.webp) | [track-hero.png](track-hero.png) | [track-landscape.svg](track-landscape.svg) |
| `ONB-SCR-003` | [03-build-healthy-habits.webp](../../onboarding/03-build-healthy-habits.webp) | [habits-hero.png](habits-hero.png) | [habits-landscape.svg](habits-landscape.svg) |
| `ONB-SCR-004` | [04-see-your-progress.webp](../../onboarding/04-see-your-progress.webp) | [progress-hero.png](progress-hero.png) | [progress-landscape.svg](progress-landscape.svg) |

Shared decoration: [mint-leaf-cluster.svg](../shared/mint-leaf-cluster.svg). Machine-readable mapping: [asset-manifest.json](asset-manifest.json).

## Composition

Use a native cream-to-mint gradient, draw the SVG landscape and overlay the PNG hero (or welcome SVG) using **independent responsive sizing**; the SVG 390 × 570 viewBox is not the PNG canvas. Render the rounded lower panel, title, description, pagination and CTA as native interactive UI. Do not bake controls or system chrome into illustrations.

## Integration and accessibility

Render `.png` heroes with React Native `Image` or `expo-image` using `contain` and without discarding alpha. Render existing `.svg` scenery through the app's SVG pipeline. Mark ornaments inaccessible to screen readers. The illustrated health metrics and chart labels are **static decoration**, not authenticated or live data.

## Fidelity and authority

The original WebP screens remain the approved full-screen references. The user selected the new PNG art for screens 002–004 on 10 November 2026; the welcome SVG still awaits visual acceptance. This does not assert pixel-perfect equivalence or completed frontend QA. Screen interactions are specified by [onboarding/BEHAVIOR.md](../../onboarding/BEHAVIOR.md). Read the [assets policy](../README.md).
