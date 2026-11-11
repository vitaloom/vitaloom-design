# Sleep Tracking — Baseline screen-to-asset mapping

**Status:** `BASELINE_UPLOADED` for actual full-screen images and `PROPOSED / VISUAL_QA_REQUIRED` for the **per-screen use** of individual assets. This adopts [ASSET_MAPPING_STANDARD.md](../ASSET_MAPPING_STANDARD.md). All nine PNGs were manually uploaded to `main`; **do not claim** an isolated PNG was created/redrawn by this documentation PR.

[Screen registry](README.md) · [Behavior](BEHAVIOR.md) · [Asset inventory](../assets/sleep-tracking/README.md) · [Machine manifest](../assets/sleep-tracking/asset-manifest.json).

## 1. Screen references and candidate compositions

**Why candidate?** The repository file inventory and individual PNG artwork have been inspected, but exact placement/layering inside the six large baseline PNGs still requires visual cross-check. The groups below express useful **role-based suggestions** consistent with asset semantics, not a confirmed pixel-perfect reverse engineering. When screenshots disagree, **follow the screenshot and update both Markdown + JSON**; never force an unrelated illustration into the screen.

| Screen ID | Actual baseline | Candidate independent assets with roles | Status |
| --- | --- | --- | --- |
| `SLT-SCR-001` | [1_sleep_tracking_main_screen.png](./1_sleep_tracking_main_screen.png) | [start_cloud.png](../assets/sleep-tracking/start_cloud.png), [cloud.png](../assets/sleep-tracking/cloud.png), [pillow_star.png](../assets/sleep-tracking/pillow_star.png) | `PROPOSED / VISUAL_QA_REQUIRED` |
| `SLT-SCR-002` | [2_record_start_end_time_sleep.png](./2_record_start_end_time_sleep.png) | [pillow_star.png](../assets/sleep-tracking/pillow_star.png), [good_emo.png](../assets/sleep-tracking/good_emo.png), [nornal_emo.png](../assets/sleep-tracking/nornal_emo.png), [tired_emo.png](../assets/sleep-tracking/tired_emo.png) | `PROPOSED / VISUAL_QA_REQUIRED` |
| `SLT-SCR-003` | [3_record_duration_sleep.png](./3_record_duration_sleep.png) | [pillow_star.png](../assets/sleep-tracking/pillow_star.png), [good_emo.png](../assets/sleep-tracking/good_emo.png), [nornal_emo.png](../assets/sleep-tracking/nornal_emo.png), [tired_emo.png](../assets/sleep-tracking/tired_emo.png) | `PROPOSED / VISUAL_QA_REQUIRED` |
| `SLT-SCR-004` | [4_sleep_insights_screen.png](./4_sleep_insights_screen.png) | [bar_chart.png](../assets/sleep-tracking/bar_chart.png), [arrow_bar_chart.png](../assets/sleep-tracking/arrow_bar_chart.png), [smilling_star.png](../assets/sleep-tracking/smilling_star.png) | `PROPOSED / VISUAL_QA_REQUIRED` |
| `SLT-SCR-005` | [5_insight-detail-screeen.png](./5_insight-detail-screeen.png) | [smilling_star.png](../assets/sleep-tracking/smilling_star.png), [bar_chart.png](../assets/sleep-tracking/bar_chart.png) | `PROPOSED / VISUAL_QA_REQUIRED` |
| `SLT-SCR-006` | [6_weekly_report_screen.png](./6_weekly_report_screen.png) | [arrow_bar_chart.png](../assets/sleep-tracking/arrow_bar_chart.png), [bar_chart.png](../assets/sleep-tracking/bar_chart.png), [start_cloud.png](../assets/sleep-tracking/start_cloud.png) | `PROPOSED / VISUAL_QA_REQUIRED` |

**No separate baseline for:** Journal/Detail/Edit/Delete, Goal and validation/empty/error/AI consent overlays. Do not create pseudo-filenames or assign a fake mockup.

## 2. Asset role and ownership ledger

| Exact uploaded file (do not rename) | Visual description | Implementation role | Owner / status |
| --- | --- | --- | --- |
| [`start_cloud.png`](../assets/sleep-tracking/start_cloud.png) | Trăng lưỡi liềm và các ngôi sao trên mây; visual hero/cue | Illustration | `assets/sleep-tracking/` · Uploaded; usage review pending |
| [`cloud.png`](../assets/sleep-tracking/cloud.png) | Mây đang ngủ; decorative/support | Illustration | `assets/sleep-tracking/` · Uploaded; usage review pending |
| [`pillow_star.png`](../assets/sleep-tracking/pillow_star.png) | Gối tím và sao; entry/decorative | Illustration | `assets/sleep-tracking/` · Uploaded; usage review pending |
| [`smilling_star.png`](../assets/sleep-tracking/smilling_star.png) | Ngôi sao mỉm cười; positive insight/decorative | Illustration | `assets/sleep-tracking/` · Uploaded; usage review pending |
| [`bar_chart.png`](../assets/sleep-tracking/bar_chart.png) | Cụm cột xanh; decoration ONLY, không thay chart thật | Data motif | `assets/sleep-tracking/` · Uploaded; usage review pending |
| [`arrow_bar_chart.png`](../assets/sleep-tracking/arrow_bar_chart.png) | Cột xanh và mũi tên; decoration ONLY, không thay chart thật | Data motif | `assets/sleep-tracking/` · Uploaded; usage review pending |
| [`good_emo.png`](../assets/sleep-tracking/good_emo.png) | Dễ chịu (self-report) | Feeling option | `assets/sleep-tracking/` · Uploaded; usage review pending |
| [`nornal_emo.png`](../assets/sleep-tracking/nornal_emo.png) | Bình thường (self-report); tên file gốc giữ nguyên | Feeling option | `assets/sleep-tracking/` · Uploaded; usage review pending |
| [`tired_emo.png`](../assets/sleep-tracking/tired_emo.png) | Mệt mỏi (self-report) | Feeling option | `assets/sleep-tracking/` · Uploaded; usage review pending |

The uploaded filenames **`nornal_emo.png`**, **`smilling_star.png`**, **`start_cloud.png`** and **`5_insight-detail-screeen.png`** contain pre-existing spelling inconsistencies. They remain unchanged for link safety. Frontend may map clean semantic aliases to exact original file paths, but must not silently rename/move upstream assets.

## 3. Composition recipe (role-based; precise placement pending visual QA)

1. **Background** is an Expo native screen surface/gradient responsive to safe area; no independent full-screen background is currently inventoried for Sleep.
2. **Illustrative layer** may use `start_cloud`, `cloud`, `pillow_star` or `smilling_star` where a matching reference screenshot truly shows it. Preserve source aspect ratio with `contain`; avoid distortion/cropping faces and adding text to the image.
3. **Feeling illustration layer:** `good_emo`, `nornal_emo`, `tired_emo` are **visual representatives** of three valid user-selected self-assessments. Pair with native text and active/checked semantics; none should silently select a default feeling.
4. **Analytics accent layer:** `bar_chart` and `arrow_bar_chart` are static decorative illustrations, **not numerical charts**. Genuine sleep duration, progress, weekly trends, bars, axes, denominators and insight evidence must be built from authenticated data with accessible native visualization.
5. **Native interactive layer (always top):** title/body copy, Journal cards, tab/chips, entry fields, date/time and timezone pickers, buttons, bottom sheets, goal controls, AI consent, errors and navigation. **Never render a baseline screenshot as the app's interactive surface.**

**Layer priority:** native background → isolated decorative PNGs (if visually verified) → functional cards/plots → text and controls → modals/validation/feedback. Size/anchor/z-index vary by screenshot and viewport; do not assume a fixed artboard or copy screenshot pixels.

**Transparency/provenance:** nine files are user-supplied project PNG artwork and preview as isolated illustrations. Preserve transparent backgrounds where present. Do not reconstruct assets by cropping screenshots; preserve author-provided artwork and validate usage rights before public release.

## 4. Visual verification and frontend handoff

- [x] Six existing baseline image links and nine asset links use actual uploaded filenames.
- [x] Distinguish reusable illustrations from full-page mockups and from runtime metric charts.
- [x] Exact paths available in machine manifest; `PROPOSED` placement cannot be mistaken for approved.
- [ ] Compare every candidate screen-asset link to the large full-screen image; delete unsupported placement claims; mark verified pairs `APPROVED` in both files.
- [ ] Check transparency and exports on device, screen sizes, accessibility contrast and native graphics.
- [ ] FE copies assets **by actual file name** into `src/features/sleep/assets/` (or its established asset organization) and records any alias; do not hotlink production UI to GitHub.
- [ ] FE keeps API/AI policy, HIR report ownership and journal/goal behavior separate from visual decoration.

For functional semantics, see [BEHAVIOR.md](BEHAVIOR.md), not this asset ledger. For canonical domain rules, follow [Sleep module spec](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/00-module.md).
