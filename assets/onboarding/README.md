# Onboarding — original transparent illustration assets

Status: newly illustrated vector assets for visual review. The four approved full-screen WebP mockups remain unchanged in [the onboarding screen catalog](../../onboarding/README.md). Use the [screen-to-asset mapping](../../onboarding/ASSET_MAPPING.md) for authoritative link pairs and layout instructions.

All images below are original SVG drawings with transparent root backgrounds. They are not crops, masks, or extracted screenshot pixels.

| Screen ID | Approved screen reference | Hero | Decorative landscape |
| --- | --- | --- | --- |
| `ONB-SCR-001` | [01-welcome.webp](../../onboarding/01-welcome.webp) | [welcome-hero.svg](welcome-hero.svg) | [welcome-landscape.svg](welcome-landscape.svg) |
| `ONB-SCR-002` | [02-track-what-matters.webp](../../onboarding/02-track-what-matters.webp) | [track-hero.svg](track-hero.svg) | [track-landscape.svg](track-landscape.svg) |
| `ONB-SCR-003` | [03-build-healthy-habits.webp](../../onboarding/03-build-healthy-habits.webp) | [habits-hero.svg](habits-hero.svg) | [habits-landscape.svg](habits-landscape.svg) |
| `ONB-SCR-004` | [04-see-your-progress.webp](../../onboarding/04-see-your-progress.webp) | [progress-hero.svg](progress-hero.svg) | [progress-landscape.svg](progress-landscape.svg) |

Shared decoration: [mint-leaf-cluster.svg](../shared/mint-leaf-cluster.svg). Machine-readable mapping: [asset-manifest.json](asset-manifest.json).

## Composition

Use a native cream-to-mint gradient, overlay the page landscape then hero on a common 390 x 570 reference coordinate plane, and finally render the white rounded lower panel, title, description, pagination and CTA using native interactive UI. Do not bake screen controls, status bars or phone frames into illustrations. Keep landscape and hero aspect ratios synchronized.

## Integration and accessibility

SVG sources can be rendered in Expo using react-native-svg and react-native-svg-transformer or exported to PNGs with alpha. Mark ornamental landscapes and leaves inaccessible to screen readers. Treat the textual values inside tracking/progress illustrations as decorative demonstration, not actual account state.

## Fidelity and authority

The original WebP screens remain the approved visual references. This new vector artwork is not intended as a pixel-perfect copy of the previous photorealistic assets. Visual approval of this redraw is required before replacing the existing screen imagery. Screen interactions are specified by [onboarding/BEHAVIOR.md](../../onboarding/BEHAVIOR.md). Read the [assets policy](../README.md).
