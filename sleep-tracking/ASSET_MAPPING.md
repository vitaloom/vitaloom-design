# Sleep Tracking — Screen to Asset Mapping

> Scope: all selected Sleep UI mockups and independently generated transparent PNG assets. Follows [ASSET_MAPPING_STANDARD](../ASSET_MAPPING_STANDARD.md) and [BEHAVIOR.md](BEHAVIOR.md).
>
> **Visual baseline:** screen compositions were selected by the user; the 9 standalone PNG artworks were generated independently and **not cropped from the UI screenshots**. SVG outlines under `icons/` are independently authored, PROPOSED editable alternatives, not visually approved substitutes for the glossy PNGs.

## 1. Composition layers and ownership

1. `background`: native mint/cream gradient and organic wave shapes (native view, no screenshot backgrounds).
2. `hero`: floating moon/clouds/stars image anchored upper-right, placed behind title text and controls.
3. `decoration`: cloud / pillow / smiling star images only where needed (never overlay readable UI).
4. `surface`: native rounded cards, soft shadows, separator/divider and chart frame.
5. `interactive-ui`: actual texts, charts, date/time wheel pickers, input validation, buttons and navigation, never baked into an asset.

- **Shared UI:** AppShell / Health Metrics Drawer owned outside this feature. No duplicate drawer.
- **Source formats:** PNG for independent glossy 3D illustrations (alpha channel); optional SVG outlines for editable UI fallbacks.
- **Reference screens:** 941 × 1672 px screenshots (single portrait screen, no device frame); overview collage 1199 × 1312 px.
- **Original PNG artwork:** 1254 × 1254 px RGBA with transparent outer canvas; illustration object may not fill the entire square.

## 2. Screen-to-image/asset mapping

| Screen ID | Approved screen reference | Primary PNG assets & roles |
|---|---|---|
| `SLT-SCR-001` | [01 Sleep Home](01-sleep-home.png) | [moon hero](../assets/sleep-tracking/moon-cloud-stars.png), [pillow](../assets/sleep-tracking/pillow-stars.png), [trend graphic](../assets/sleep-tracking/trend-up.png) |
| `SLT-SCR-002A` | [02a Start & End](02a-sleep-entry-time-range.png) | [moon hero](../assets/sleep-tracking/moon-cloud-stars.png); [Comfortable](../assets/sleep-tracking/feeling-comfortable.png), [Normal](../assets/sleep-tracking/feeling-normal.png), [Tired](../assets/sleep-tracking/feeling-tired.png) |
| `SLT-SCR-002B` | [02b Duration Only](02b-sleep-entry-duration-only.png) | Same hero + reaction set as 02a; `Date/Hour/Minute` are native interactive pickers |
| `SLT-SCR-003` | [03 Sleep Insights](03-sleep-insights.png) | [moon hero](../assets/sleep-tracking/moon-cloud-stars.png), [trend graphic](../assets/sleep-tracking/trend-up.png), [bars](../assets/sleep-tracking/bars.png) |
| `SLT-SCR-004` | [04 AI Insight Detail](04-ai-insight-detail.png) | [pillow](../assets/sleep-tracking/pillow-stars.png), [reaction graphics](../assets/sleep-tracking/feeling-comfortable.png), [bars](../assets/sleep-tracking/bars.png) |
| `SLT-SCR-005` | [05 Weekly Sleep Report](05-ai-weekly-sleep-story.png) | [moon hero](../assets/sleep-tracking/moon-cloud-stars.png), [trend graphic](../assets/sleep-tracking/trend-up.png), [reaction graphics](../assets/sleep-tracking/feeling-tired.png) |

[See selected overview](00-sleep-design-overview.png).

## 3. Transparent PNG inventory (all actual files)

| Filename | Role | Ownership | Visual status |
|---|---|---|---|
| [moon-cloud-stars.png](../assets/sleep-tracking/moon-cloud-stars.png) | Main floating moon/cloud hero | Sleep feature | Generated original / AVAILABLE |
| [sleep-cloud.png](../assets/sleep-tracking/sleep-cloud.png) | Independent cute cloud | Sleep feature | Generated original / AVAILABLE |
| [pillow-stars.png](../assets/sleep-tracking/pillow-stars.png) | Purple pillow decorative asset | Sleep feature | Generated original / AVAILABLE |
| [star-smiling.png](../assets/sleep-tracking/star-smiling.png) | Single smiling star decoration | Sleep feature | Generated original / AVAILABLE |
| [feeling-comfortable.png](../assets/sleep-tracking/feeling-comfortable.png) | Comfortable illustration | Sleep feature | Generated original / AVAILABLE |
| [feeling-normal.png](../assets/sleep-tracking/feeling-normal.png) | Normal illustration | Sleep feature | Generated original / AVAILABLE |
| [feeling-tired.png](../assets/sleep-tracking/feeling-tired.png) | Tired illustration | Sleep feature | Generated original / AVAILABLE |
| [trend-up.png](../assets/sleep-tracking/trend-up.png) | Decorative upward trend | Sleep feature | Generated original / AVAILABLE |
| [bars.png](../assets/sleep-tracking/bars.png) | Decorative rising bars | Sleep feature | Generated original / AVAILABLE |

**Important:** Decorative graph PNGs cannot replace data-bound charts in functional screens. Real bars, labels and evidence must be generated from verified analytics. Self-assessment control state is native, not encoded in a preselected PNG.

## 4. Responsive placement and app handoff

- Use safe-area insets, screen readers, semantic text, scroll and responsive spacing; 390 × ~690 dp screenshot proportions are illustrative, not a global fixed height.
- Moon/cloud assets align top-right and must never occlude form fields. Cards and heading use native text for translations/dynamic contents.
- Use `contain` with alpha PNGs; remove invisible outer padding only through layout/canvas cropping *of the independent artwork if explicitly approved*, never by screenshot-cropping.
- Reaction icons are decoration inside min 44pt native hit targets. Selected state must include border, accessible selected label, and readable contrast.
- Per-screen event and state logic lives exclusively in [BEHAVIOR.md](BEHAVIOR.md).
- Fingerprint original files via [import record](SCREEN_IMPORT.md); machine mappings in [screen-manifest.json](screen-manifest.json) and [asset-manifest.json](../assets/sleep-tracking/asset-manifest.json).

## 5. Acceptance checks

- [x] Six approved single-screen PNGs and the selected overview are present in `sleep-tracking/`.
- [x] Nine individual PNG assets exist in `assets/sleep-tracking/` and have alpha transparency.
- [x] Assets are independently generated, not cropped from main screen screenshots.
- [x] Mapping references actual relative paths and is consistent with manifests.
- [ ] UI states beyond happy path (empty/error/loading/AI stale) receive separate visual acceptance.
- [ ] Expo UI uses native functional controls and matches selected visual references after device QA.
