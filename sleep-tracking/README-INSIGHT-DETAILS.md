# VitaLoom F2 — Insight Detail visual baselines (2026-11-15)

All nine individual 941 × 1672 PNGs are committed to `main` in `e0ceb5a`. **This README is an index**; the canonical design/behavior/data/asset handoff is [RECENT_INSIGHT_DESIGN.md](RECENT_INSIGHT_DESIGN.md).

| Code | Visual reference | Main visualization |
| --- | --- | --- |
| A01 | [13-insight-a01-recording-coverage.png](13-insight-a01-recording-coverage.png) | 7-day coverage calendar + count /7 |
| A02 | [14-insight-a02-goal-achievement.png](14-insight-a02-goal-achievement.png) | 7-day achieved/not-achieved/missing/not-applicable state cells + numerator/eligible denominator |
| A03 | [15-insight-a03-duration-trend.png](15-insight-a03-duration-trend.png) | two completed 7-day mean bars + signed minute delta |
| A04 | [16-insight-a04-bedtime-wake-variation.png](16-insight-a04-bedtime-wake-variation.png) | two min-max range tracks: bedtime and wake-up, relative-day timeline |
| A05 | [17-insight-a05-weekday-weekend-duration.png](17-insight-a05-weekday-weekend-duration.png) | two bars for weekday/weekend means, signed minute delta, per-group n |
| B01 | [18-insight-b01-feeling-distribution.png](18-insight-b01-feeling-distribution.png) | three-segment 100% distribution/donut, count/denominator, missing-feeling note |
| B02 | [19-insight-b02-duration-vs-feeling.png](19-insight-b02-duration-vs-feeling.png) | two comparable average-duration bars for Comfortable and Tired, signed minutes |
| B03 | [20-insight-b03-feeling-trend.png](20-insight-b03-feeling-trend.png) | two 100%-stacked distributions for completed windows, signed percentage-point changes |
| B04 | [21-insight-b04-tired-goal-exception.png](21-insight-b04-tired-goal-exception.png) | exception count + dated verified record cards with duration vs effective day-goal |

All examples are **mock values** that may be inconsistent across PNGs; do not hard-code them or infer clinical outcomes. Group C is DEFERRED. F2 rules, insight eligibility and window boundaries are defined in [Insight Catalog v2](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f2-sleep-goals-insights/insight-catalog-v2.md). Reuse committed assets via [ASSET_MAPPING.md](ASSET_MAPPING.md), not screenshot cropping. `04-recent-insight-detail.png` is a shared UI shell; the nine PNGs are variants of `SLT-SCR-004`, not separate routes.
