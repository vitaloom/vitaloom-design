# Sleep Tracking — Independent artwork inventory

**Source:** Nine PNG artwork files manually uploaded to `assets/sleep-tracking/` on `main`, 2026-11-11. All names/paths are retained. Standalone assets are not complete screens or live data visualizations.

[Owning module screen catalog](../../sleep-tracking/README.md) · [Per-screen asset mapping](../../sleep-tracking/ASSET_MAPPING.md) · [Interaction behavior](../../sleep-tracking/BEHAVIOR.md) · [Machine manifest](asset-manifest.json) · [Global policy](../../ASSET_MAPPING_STANDARD.md).

| Asset | Intended semantic role | Important boundary |
| --- | --- | --- |
| [`start_cloud.png`](./start_cloud.png) | Trăng lưỡi liềm và các ngôi sao trên mây; visual hero/cue | Decorative until verified for a particular screenshot |
| [`cloud.png`](./cloud.png) | Mây đang ngủ; decorative/support | Decorative until verified for a particular screenshot |
| [`pillow_star.png`](./pillow_star.png) | Gối tím và sao; entry/decorative | Decorative until verified for a particular screenshot |
| [`smilling_star.png`](./smilling_star.png) | Ngôi sao mỉm cười; positive insight/decorative | Decorative until verified for a particular screenshot |
| [`bar_chart.png`](./bar_chart.png) | Cụm cột xanh; decoration ONLY, không thay chart thật | Static decorative art only; never use as real metric graph |
| [`arrow_bar_chart.png`](./arrow_bar_chart.png) | Cột xanh và mũi tên; decoration ONLY, không thay chart thật | Static decorative art only; never use as real metric graph |
| [`good_emo.png`](./good_emo.png) | Dễ chịu (self-report) | Optional self-reported feeling; native selection/text required |
| [`nornal_emo.png`](./nornal_emo.png) | Bình thường (self-report); tên file gốc giữ nguyên | Optional self-reported feeling; native selection/text required |
| [`tired_emo.png`](./tired_emo.png) | Mệt mỏi (self-report) | Optional self-reported feeling; native selection/text required |

## Implementation notes

- **Feeling options:** `good_emo.png` → Dễ chịu; `nornal_emo.png` → Bình thường; `tired_emo.png` → Mệt mỏi. No selected default is implied. Selection is optional and stored *per sleep session*, not per day; obey F1 BR-F1.17.
- **Decorative chart icons:** `bar_chart.png`, `arrow_bar_chart.png` are fixed illustrations. Weekly metrics, comparisons, percentages and evidence must use real backend data/native chart rendering; images must not convey fabricated account data.
- **Decorative sleep motif:** `start_cloud.png` (moon-and-cloud visual), `cloud.png`, `pillow_star.png`, `smilling_star.png`. Use `resizeMode: contain`-equivalent and respect transparency and text contrast.
- **Naming legacy:** `nornal_emo.png`, `smilling_star.png`, `start_cloud.png` are preserved to avoid broken links; clean FE variable names may wrap those paths.
- **Provenance:** user-provided project artwork. No new redraw, screenshot crop, licensed stock attribution or claim of production acceptance is implied by this documentation.
- **Placement:** see [per-screen mapping](../../sleep-tracking/ASSET_MAPPING.md); currently `PROPOSED / VISUAL_QA_REQUIRED`, not pixel-confirmed.

For Expo bundling, place copies under the Sleep feature asset area and use statically analyzable `require` paths; make interactive controls native and provide accessible text labels.
