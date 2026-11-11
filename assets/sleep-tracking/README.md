# Sleep Tracking — standalone artwork

This feature-owned directory contains independent artwork and icon fallback assets for the Sleep module. See [Screen-to-Asset Mapping](../../sleep-tracking/ASSET_MAPPING.md), [global asset standard](../../ASSET_MAPPING_STANDARD.md), and [PNG import list](../../sleep-tracking/SCREEN_IMPORT.md).

### Committed editable SVG icons (PROPOSED, transparent root canvas)

| Asset | Role | Status |
|---|---|---|
| [moon.svg](icons/moon.svg) | outline moon / sleep motif | PROPOSED fallback |
| [cloud.svg](icons/cloud.svg) | outline cloud / sleep motif | PROPOSED fallback |
| [pillow.svg](icons/pillow.svg) | outline pillow decoration | PROPOSED fallback |
| [star.svg](icons/star.svg) | outline star decoration | PROPOSED fallback |
| [feeling-comfortable.svg](icons/feeling-comfortable.svg) | positive reaction state | PROPOSED fallback |
| [feeling-normal.svg](icons/feeling-normal.svg) | neutral reaction state | PROPOSED fallback |
| [feeling-tired.svg](icons/feeling-tired.svg) | tired reaction state | PROPOSED fallback |
| [trend-up.svg](icons/trend-up.svg) | trend card icon | PROPOSED fallback |
| [bars.svg](icons/bars.svg) | chart card icon | PROPOSED fallback |

These vector icons were independently authored; **they are not cropped from the selected screenshots, and are not the previously generated glossy illustration PNGs**. Use them only if product design accepts the simplified icon style; keep real controls/chart values in React Native.

### Original generated PNG illustration targets

`moon-cloud-stars.png`, `sleep-cloud.png`, `pillow-stars.png`, `star-smiling.png`, `feeling-comfortable.png`, `feeling-normal.png`, `feeling-tired.png`, `trend-up.png`, `bars.png` — all **PENDING_BINARY_IMPORT** from the conversation-created original assets. Do not invent public links to them until upload succeeds.

SVGs have transparent root canvases and are suitable as project editable sources; no font or image screenshot is embedded.
