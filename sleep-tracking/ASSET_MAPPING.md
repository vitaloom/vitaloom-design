# Sleep Tracking — Screen to Asset Mapping

> Follows [global mapping standard](../ASSET_MAPPING_STANDARD.md). **Original generated transparent PNG images and selected full-screen PNGs are pending repository binary import.** The committed SVGs under `assets/sleep-tracking/icons/` are independent authored **PROPOSED FALLBACKS**, not crops from the designs and not replacements approved by the user.

## 1. Separate visual layers

1. `background`: native mint/cream gradient and organic curves, drawn responsively in React Native; do **not** bake app text into the image.
2. `hero`: isolated moon/cloud/stars illustration PNG once imported; should stay behind headers and noninteractive.
3. `decoration`: optional star, pillow/cloud artwork; no text or button baked in.
4. `surface`: native rounded cards, shadows and chart containers.
5. `interactive-ui`: native text, inputs, wheel/date pickers, reactions, chart with real data, buttons and navigators.

Never display a full-screen screenshot as the implementation of a functional page. Asset roots are transparent; make them non-accessible where purely decorative.

## 2. Mapping per approved screen

| Screen | Selected full PNG file (pending import) | Planned original transparent artwork (pending) | Committed SVG fallback icons (PROPOSED) |
|---|---|---|---|
| `SLT-SCR-001` Home | `01-sleep-home.png` | `moon-cloud-stars.png`, `pillow-stars.png`, `star-smiling.png` | [trend-up.svg](../assets/sleep-tracking/icons/trend-up.svg), [bars.svg](../assets/sleep-tracking/icons/bars.svg) |
| `SLT-SCR-002A` Time Range | `02a-sleep-entry-time-range.png` | `moon-cloud-stars.png`, `sleep-cloud.png` | [feeling-comfortable.svg](../assets/sleep-tracking/icons/feeling-comfortable.svg), [feeling-normal.svg](../assets/sleep-tracking/icons/feeling-normal.svg), [feeling-tired.svg](../assets/sleep-tracking/icons/feeling-tired.svg) |
| `SLT-SCR-002B` Duration Only | `02b-sleep-entry-duration-only.png` | same sleep hero | same three reactions |
| `SLT-SCR-003` Insights | `03-sleep-insights.png` | `moon-cloud-stars.png` | [trend-up.svg](../assets/sleep-tracking/icons/trend-up.svg), [bars.svg](../assets/sleep-tracking/icons/bars.svg) |
| `SLT-SCR-004` Detail | `04-ai-insight-detail.png` | `pillow-stars.png` | reaction icons + [bars.svg](../assets/sleep-tracking/icons/bars.svg) |
| `SLT-SCR-005` Weekly | `05-ai-weekly-sleep-story.png` | `moon-cloud-stars.png`, `star-smiling.png` | [bars.svg](../assets/sleep-tracking/icons/bars.svg), [trend-up.svg](../assets/sleep-tracking/icons/trend-up.svg) |

Image filename references without hyperlinks are **intentional** until PNGs exist on branch. Do not silently mark them `APPROVED_FILE_PRESENT`.

## 3. Artwork filename/import mapping

Original standalone images generated for this design (do not screenshot-crop):

| Repo target after import | Independent role | Status |
|---|---|---|
| `assets/sleep-tracking/moon-cloud-stars.png` | header hero | PENDING_BINARY_IMPORT |
| `assets/sleep-tracking/sleep-cloud.png` | cloud character | PENDING_BINARY_IMPORT |
| `assets/sleep-tracking/pillow-stars.png` | insight decoration | PENDING_BINARY_IMPORT |
| `assets/sleep-tracking/star-smiling.png` | decoration | PENDING_BINARY_IMPORT |
| `assets/sleep-tracking/feeling-comfortable.png` | self-assessment illustration | PENDING_BINARY_IMPORT |
| `assets/sleep-tracking/feeling-normal.png` | self-assessment illustration | PENDING_BINARY_IMPORT |
| `assets/sleep-tracking/feeling-tired.png` | self-assessment illustration | PENDING_BINARY_IMPORT |
| `assets/sleep-tracking/trend-up.png` | trend decorative graphic | PENDING_BINARY_IMPORT |
| `assets/sleep-tracking/bars.png` | bar-graph decorative graphic | PENDING_BINARY_IMPORT |

See [art catalog](../assets/sleep-tracking/README.md) and [import instructions](SCREEN_IMPORT.md). Icons are visual affordances; actual chart values need native chart components. Do not reuse illustration PNG as a static chart in place of live data.

## 4. Responsive composition

- Reference screen artboard: 390 × 844 dp at 3× export (1170 × 2532). Rescale art to available width; use safe areas, scroll views and screen-reader order.
- Hero: align upper right, reserve left header text, constrain max bounding box so it does not cover button or input.
- Reactions: all three icon hit areas ≥44 pt; selected state uses border/background + accessible label.
- Never layer independent artwork over an actual picker, chart label, weekly date selector or save control.
- Accent palette follows shared VitaLoom Soft Wellness; keep minimum contrast for functional text.

## 5. Validation

- [ ] All planned PNG files exist before linking; ensure alpha/transparency and no screenshot-crop provenance.
- [ ] Relative SVG fallback links resolve.
- [ ] Do not duplicate binaries under both `sleep-tracking/` and `assets/sleep-tracking/`.
- [ ] Do not confuse `PROPOSED` SVGs with user-approved original generated PNG artwork.
- [ ] Manifest and mapping cover identical screen IDs and **real** existing asset paths.
- [ ] All controls and data charts are rendered natively.
