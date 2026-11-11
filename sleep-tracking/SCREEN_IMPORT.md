# Sleep Tracking — PNG import verification

**Status:** Original six selected screen PNGs, overview and nine original transparent assets are COMMITTED. Six supplemental screen PNGs and two new standalone assets were committed to `main` in `fba900f` and `7dd2fa9`. **The supplemental screenshots are structure-only due to their rejected purple-dominant UI palette; green wellness FE correction is mandatory.** Binary blobs were uploaded without resizing, downsampling or screen-cropping.

## Exact paths and content fingerprints

SHA-256 fingerprints from original source bytes before GitHub blob upload; bytes are source file sizes.

| Relative path | Bytes | SHA-256 |
|---|---:|---|
| [`sleep-tracking/00-sleep-design-overview.png`](../sleep-tracking/00-sleep-design-overview.png) | 2418823 | `36f66a4453056fa0ab6272820bcf558592c83e728c20fe7085ad00d13cde4146` |
| [`sleep-tracking/01-sleep-home.png`](../sleep-tracking/01-sleep-home.png) | 1579657 | `d1bb2dbd29f28648b54d6154c2e96b9d02577faf90780bae0468253573045d02` |
| [`sleep-tracking/02a-sleep-entry-time-range.png`](../sleep-tracking/02a-sleep-entry-time-range.png) | 1576170 | `0e3d30b5023a5f82d90038dee930dbbde32bf54fe263991e06b425f109a9860b` |
| [`sleep-tracking/02b-sleep-entry-duration-only.png`](../sleep-tracking/02b-sleep-entry-duration-only.png) | 1263026 | `794695f7d9bf78675bbaca98f153c188d19ec334c195be7ed676f3a2d1dcc401` |
| [`sleep-tracking/03-sleep-insights.png`](../sleep-tracking/03-sleep-insights.png) | 1714261 | `40e461bede0e9ad60ea7728fa83c4de3e8943af94c8b3da67809c39f9971baf7` |
| [`sleep-tracking/04-ai-insight-detail.png`](../sleep-tracking/04-ai-insight-detail.png) | 1728853 | `df184af6d261ad74153584b83ff3b28f106bc0c3fed67fdb6d70084c2e7dada5` |
| [`sleep-tracking/05-ai-weekly-sleep-story.png`](../sleep-tracking/05-ai-weekly-sleep-story.png) | 1660266 | `6635ed9a5916c6b03426b1fa462fccba0ddc91f52271c127c71f6c300f33d2a6` |
| [`assets/sleep-tracking/moon-cloud-stars.png`](../assets/sleep-tracking/moon-cloud-stars.png) | 672728 | `6cc8a875ea46421b3af4d72dab9ae43f9b2b83c62f8d67ea5fca3a234843b1ac` |
| [`assets/sleep-tracking/sleep-cloud.png`](../assets/sleep-tracking/sleep-cloud.png) | 536931 | `029dc01bd206b9bc2d63c1b5daba672814867e3258ed39c309479e1fc8c4b5e7` |
| [`assets/sleep-tracking/pillow-stars.png`](../assets/sleep-tracking/pillow-stars.png) | 449375 | `1d5b5155d04f721c98730db543747b2d77ea15b471e6027d79a033b1d490e56c` |
| [`assets/sleep-tracking/star-smiling.png`](../assets/sleep-tracking/star-smiling.png) | 541925 | `72fa1f8f8d9bdf239af14af86f76bb3b78ddeeaf74acdd6d87668fc34f17222f` |
| [`assets/sleep-tracking/feeling-comfortable.png`](../assets/sleep-tracking/feeling-comfortable.png) | 561359 | `975d2d2b6f030c4a54145a1acd918e556ea752a84dbe333376ba0be96b8d447b` |
| [`assets/sleep-tracking/feeling-normal.png`](../assets/sleep-tracking/feeling-normal.png) | 466683 | `f163f05417a97e6749bbeb9bb1fa990ad0659e66cbf76eca83b8d3e80d2db3d9` |
| [`assets/sleep-tracking/feeling-tired.png`](../assets/sleep-tracking/feeling-tired.png) | 549542 | `e4174efc67841dd112417770a9ea2e1491badc815f02b9c72e20741ea1f85be1` |
| [`assets/sleep-tracking/trend-up.png`](../assets/sleep-tracking/trend-up.png) | 259966 | `e9e15b6e7119656ac1af73c3fe4ce6b533ebe249f0eb3251994d0d717b7e5a1f` |
| [`assets/sleep-tracking/bars.png`](../assets/sleep-tracking/bars.png) | 211738 | `5f5f0ec7d848dc525a3f01b4728f77e52f6d299c65af1c3653b4efe32d4819db` |

## File format

- `sleep-tracking/00-sleep-design-overview.png`: 1199 × 1312 RGBA collage (visual overview only).
- Six single-screen mockups: 941 × 1672 RGB, one mobile screen each.
- Nine standalone assets: 1254 × 1254 RGBA, transparent corners.
- Each asset was generated independently in the conversation and is **not a direct crop from any approved design**.

## Design vs business correctness

The user selected the visuals; any illustrative time, date, percentage, average or AI sentence in a PNG is sample copy, **not authoritative business data**. [Behavior](BEHAVIOR.md), [F1 BR](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f1-sleep-journal/rules.md) and [F2 BR](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f2-sleep-goals-insights/rules.md) take precedence. Do not use a full screenshot as runtime UI.

## Review check

- [x] Actual PNG paths exist in GitHub tree.
- [x] Original bytes and dimensions preserved, matching this SHA-256 table.
- [x] PNG feature mockups stay with `sleep-tracking/` docs.
- [x] Small standalone PNGs live under `assets/sleep-tracking/`.
- [x] The independent asset names match `ASSET_MAPPING.md` and machine manifest.
- [ ] FE device QA and alternate-state screenshot approvals remain future work.

## Supplemental uploads — 2026-11-11

| File | GitHub tree size (bytes) | Git blob SHA | Source commit | Visual usage |
|---|---:|---|---|---|
| [7_sleep_journal.png](7_sleep_journal.png) | 1579015 | `0348a3ceacb56fe8ea4bef9cefa3b196e05d6734` | `fba900f` | Structure only; change purple to green |
| [8_sleep_record_detail.png](8_sleep_record_detail.png) | 1587541 | `7fb589a7509c74b2717a37020841dd8f70d0e918` | `fba900f` | Structure only; change purple to green |
| [9_sleep_record_detail_edit.png](9_sleep_record_detail_edit.png) | 1532376 | `4ef9340e1144ad4e23e8b62096a63f5b69e4a540` | `fba900f` | Structure only; change purple to green |
| [10_sleep_goal_setup.png](10_sleep_goal_setup.png) | 1551066 | `3c91b15d4e3d80bcaff8ef71f831a678c0066033` | `fba900f` | Structure only; change purple to green |
| [11_sleep_insight_empty.png](11_sleep_insight_empty.png) | 1526932 | `5bc2ff148eaa6a2736ffbc8c9284809942bd6f0d` | `fba900f` | 003 NO_DATA state; change purple to green |
| [12_sleep_not_enough_data_insight.png](12_sleep_not_enough_data_insight.png) | 1414049 | `b5cf2a8fbf6e4e774bb104cfec658e53eee3d564` | `fba900f` | 003 INSUFFICIENT_DATA state; change purple to green |
| [bed.png](../assets/sleep-tracking/bed.png) | 823175 | `162e1faaba01505bceb46c1b1bda9be48c5586eb` | `7dd2fa9` | Small purple accent only |
| [star-pillow-cloud.png](../assets/sleep-tracking/star-pillow-cloud.png) | 1080527 | `978b0438ef3f8523c97e7528f8b1d5b4673ba0a8` | `7dd2fa9` | Independent hero for green-themed UI |

The new values above are **Git blob SHA identifiers, not SHA-256 content hashes**; the SHA-256 table higher in this file applies only to the original upload set. New PNG format/alpha and pixel dimensions were not independently decoded by this documentation update; verify in FE import QA.

**Do not modify source PNGs or infer purple color tokens**. Their color is a known design error. See [mandatory green wellness override](ADDITIONAL_SCREENS_20261111.md). Corrected FE visual acceptance is still pending.
