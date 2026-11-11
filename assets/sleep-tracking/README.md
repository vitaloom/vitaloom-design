# Sleep Tracking — visual assets (transparent PNG + optional SVG)

All nine **original generated PNG assets** are committed here, plus two additional independently uploaded PNGs in commit `7dd2fa9`. They were independently created as standalone artworks (not cropped/masked from the screen designs). The nine original assets are 1254 × 1254 RGBA sources with transparent canvas; verify alpha/dimensions of the two newer files at FE import.

| Preview / download | Role |
|---|---|
| [moon-cloud-stars.png](moon-cloud-stars.png) | Main hero: smiling crescent moon in cloud with stars |
| [sleep-cloud.png](sleep-cloud.png) | Sleepy cloud standalone |
| [pillow-stars.png](pillow-stars.png) | Lilac pillow with two stars |
| [star-smiling.png](star-smiling.png) | Smiling golden star |
| [feeling-comfortable.png](feeling-comfortable.png) | Comfortable reaction |
| [feeling-normal.png](feeling-normal.png) | Normal reaction |
| [feeling-tired.png](feeling-tired.png) | Tired reaction |
| [trend-up.png](trend-up.png) | Rising decorative trend chart |
| [bars.png](bars.png) | Rising decorative bar chart |

### Added assets — commit 7dd2fa9

| File | Role | Color policy |
|---|---|---|
| [star-pillow-cloud.png](star-pillow-cloud.png) | Combined moon/cloud/pillow/star hero on Journal, Edit, Detail and Insights states | Overlay on **green wellness** UI |
| [bed.png](bed.png) | Small purple bed illustration for sleep cards / goal | **Minor purple accent only**, not screen dominant |

> Screens 7–12 are **structure-only** references because their purple-dominant palette is incorrect. See [mandatory wellness-green correction](../../sleep-tracking/ADDITIONAL_SCREENS_20261111.md).

**Usage:** see [screen-to-asset mapping](../../sleep-tracking/ASSET_MAPPING.md), [behavior](../../sleep-tracking/BEHAVIOR.md), [asset manifest](asset-manifest.json).

### Independently authored SVG fallbacks (PROPOSED only)

[moon](icons/moon.svg) · [cloud](icons/cloud.svg) · [pillow](icons/pillow.svg) · [star](icons/star.svg) · [comfortable](icons/feeling-comfortable.svg) · [normal](icons/feeling-normal.svg) · [tired](icons/feeling-tired.svg) · [trend](icons/trend-up.svg) · [bars](icons/bars.svg).

SVGs are simpler editable icon alternatives and **not the approved glossy PNG illustrations**. Native icon libraries may be preferable for basic calendar, back arrow, clock and menu glyphs. Do not render PNG trend artwork as if it were computed live health data.
