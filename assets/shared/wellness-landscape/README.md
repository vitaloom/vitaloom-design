# Soft Wellness — Shared layered landscape

Reusable, **transparent PNG components**, composed at runtime beneath onboarding hero artwork. Files were generated separately from the original approved mockups; **none are screenshot crops**. This is a proposed composition pending visual QA in Expo.

## Individual assets

| Layer / role | PNG | Intrinsic px | zIndex |
| --- | --- | --- | --- |
| Back hills | [mint-back-hills.png](mint-back-hills.png) | 1360×662 | 10 |
| Middle waves | [mint-middle-waves.png](mint-middle-waves.png) | 1560×370 | 20 |
| Front mound | [mint-front-mound.png](mint-front-mound.png) | 1560×303 | 30 |
| Left sprout | [mint-leaf-sprout.png](mint-leaf-sprout.png) | 850×847 | 40 |
| Lower-left leaves | [mint-leaves-left.png](mint-leaves-left.png) | 850×647 | 50 |
| Lower-right leaves | [mint-leaves-right.png](mint-leaves-right.png) | 850×851 | 60 |

The machine-readable layout is [composition.json](composition.json). All six PNGs have an alpha channel; no backdrop or main hero is embedded.

## Layout contract

- Reference coordinate **stage = 390 × 570 design points**, *not* the physical screen size. Scale uniformly and center the stage within the available illustrated region; do not hardcode full-screen height to 570.
- The parent view owns the warm cream-to-mint background; do not bake that gradient into the assets.
- Draw in ascending `zIndex`. Image source keys must resolve from a **static require map**; React Native/Metro cannot statically bundle assets from arbitrary variable paths in `require(path)`.
- Each PNG is an independent absolutely positioned `Image` or `expo-image`, at its declared frame (x, y, width, height) multiplied by the stage scale. Keep `contain` and preserve the native aspect ratio.
- Render the per-screen hero **above the complete landscape**, then the native white bottom panel, text, pager and CTA. Set decorative layers `pointerEvents="none"` and `accessible={false}`.
- The same composition is reused by screens `ONB-SCR-001` through `ONB-SCR-004`. Do not stack the old screen-specific `*-landscape.svg` or the optional `mint-leaf-cluster.svg` on top: this scene already has foliage.

### Expo / React Native implementation sketch

```tsx
// Example only. Copy assets into the frontend feature/shared asset folder first.
const sceneAssets = {
  'back-hills': require('./mint-back-hills.png'),
  'middle-waves': require('./mint-middle-waves.png'),
  'front-mound': require('./mint-front-mound.png'),
  'left-sprout': require('./mint-leaf-sprout.png'),
  'left-leaves': require('./mint-leaves-left.png'),
  'right-leaves': require('./mint-leaves-right.png'),
} as const;

// Scale = min(availableStageWidth / 390, availableStageHeight / 570).
// Center the scaled reference stage, so optional content-safe margins remain.
const scale = Math.min(availableStageWidth / 390, availableStageHeight / 570);
const offsetX = (availableStageWidth - 390 * scale) / 2;
const offsetY = (availableStageHeight - 570 * scale) / 2;

// For each entry in composition.layers, in zIndex order:
<Image
  source={sceneAssets[layer.id as keyof typeof sceneAssets]}
  resizeMode="contain"
  accessible={false}
  style={{
    position: 'absolute',
    left: offsetX + layer.frame.x * scale,
    top: offsetY + layer.frame.y * scale,
    width: layer.frame.width * scale,
    height: layer.frame.height * scale,
  }}
/>
```

For this example, render inside a parent with `position: 'relative'`, `pointerEvents="none"` and dimensions `availableStageWidth` × `availableStageHeight`. The `<Image />` snippet is illustrative; wire actual data and parent layout in your feature code. If a container clips at its edges, confirm that the intended negative-x margins remain acceptable on narrow devices.

## Review criteria

- [ ] PNGs render with real transparency and crisp edge antialiasing.
- [ ] Hills and waves look visually connected when the native background is applied.
- [ ] All 4 onboarding stages retain space for the corresponding hero and lower content panel.
- [ ] No duplicate leaves or legacy SVG landscape are visible.
- [ ] Check compact / tall device aspect ratios, Android / iOS, text accessibility, and hero clipping.
- [ ] Never treat static health numbers within hero artwork as actual user data.

See [onboarding asset mapping](../../../onboarding/ASSET_MAPPING.md), [manifest](../../onboarding/asset-manifest.json), [global policy](../../../ASSET_MAPPING_STANDARD.md).
