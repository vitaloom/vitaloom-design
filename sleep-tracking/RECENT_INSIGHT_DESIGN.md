# VitaLoom — Recent Sleep Insight Detail Visual Specification (MVP)

> **Status:** visual baseline committed to `main` in `e0ceb5a`; this file defines design handoff, **not** evidence of FE/API implementation or user approval of sample data. Canonical policy: [F2 rules](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f2-sleep-goals-insights/rules.md), [Insight Catalog v2](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f2-sleep-goals-insights/insight-catalog-v2.md), [SLT-UC-009](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f2-sleep-goals-insights/SLT-UC-009_kham-pha-sleep-insights.md), [AI guidelines](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f2-sleep-goals-insights/ai-content-guidelines.md).

## Scope and navigation

- Active: A01–A05 (Sleep Pattern), B01–B04 (Sleep Feeling); Group C (C01–C04) **DEFERRED** and hidden, including Locked lists.
- Stable destination `SLT-SCR-004` is **one parameterized Insight Detail route/component** (`insightCode`). PNGs 13–21 are **nine visual variants**, not nine routes; `04-recent-insight-detail.png` is a shared shell reference.
- Entry: READY cards from `03-all-sleep-insights-recent.png`, Home featured insight, Recent Report highlights or Story observations. Re-evaluate insight status/evidence on entry; never display stale claims.
- Header: back + short title + compact group label; summary KPI; one visualization matched to the insight; visible period and sample `n`; collapsed **Dữ liệu & cách tính / Giới hạn**; optional **Giải thích bằng AI** when eligible. Long calculations and sources are progressive disclosure, not dense default text.
- All displayed numbers and feelings come from verified API evidence. **The screenshots contain independently simulated data, which may disagree with one another or fail eligibility; never use mockup values as business rules, fixtures or hard-coded API examples.**

## Nine variants — exact presentation intent

| Code | PNG | What the user should understand | Primary native visual | Evidence and eligibility |
| --- | --- | --- | --- | --- |
| A01 | [Coverage](13-insight-a01-recording-coverage.png) | Number of days with a recorded MAIN | 7-day status calendar + `recorded/7` ring | >=3 MAIN, verified current [D−6,D] |
| A02 | [Goal](14-insight-a02-goal-achievement.png) | Days meeting their *effective daily* Goal | categorical 7-day cells + `achieved/eligible`; distinct missing/no-goal | >=3 days each with MAIN + verified effective Goal |
| A03 | [Duration trend](15-insight-a03-duration-trend.png) | Signed difference of two average sleep durations | two mean-duration bars + minute delta, show both ranges and `n` | two completed 7-day windows, >=3 MAIN each |
| A04 | [Sleep/wake variation](16-insight-a04-bedtime-wake-variation.png) | The two **ranges** of observed bedtime and wake time | two independent min–max time tracks, using relative day for bedtime | >=3 MAIN RANGE from user's selected timezone; DST policy |
| A05 | [Weekday/weekend](17-insight-a05-weekday-weekend-duration.png) | Mean MAIN duration on weekdays vs weekends | two bars + signed minute difference + samples per group | >=3 weekday MAIN, >=2 weekend MAIN |
| B01 | [Feeling distribution](18-insight-b01-feeling-distribution.png) | Share/count of Comfortable, Normal, Tired | 3-category donut/100% distribution and exact count labels | >=3 MAIN with recorded feeling; missing feelings excluded from denominator |
| B02 | [Duration vs feeling](19-insight-b02-duration-vs-feeling.png) | Descriptive difference of duration means by feeling | two comparable mean bars for Comfortable/Tired + signed delta | >=3 Comfortable and >=3 Tired MAIN |
| B03 | [Feeling trend](20-insight-b03-feeling-trend.png) | Changes in feeling shares across two completed windows | two 100%-stacked distributions + **percentage-point** deltas | >=3 MAIN with feeling in each completed 7-day window |
| B04 | [Tired despite goal](21-insight-b04-tired-goal-exception.png) | Count and dates of Tired records with duration >= effective Goal | exception count, small record cards comparing duration/Goal | >=3 MAIN with feeling, >=1 eligible exception; Goal history verified |

### Time-window rules

- Let `D` be today in `Asia/Ho_Chi_Minh`. For A01/A02/A04/A05/B01/B02/B04 use rolling **[D−6,D]** including today.
- For **A03 and B03 only**, compare `[D−7,D−1]` with `[D−14,D−8]`. Both are completed windows. Do **not** label them "this week / last week" as calendar weeks or include today.
- Missing verified MAIN is **"Chưa ghi nhận"**, never 0 hours or "failed goal". Unverified history must not yield aggregates, READY insight or AI output.
- A04 records require actual RANGE timestamps, selected reference timezone and DST eligibility; duration-only never synthesizes time. **Do not** relabel range as bedtime consistency score or classify as "regular/irregular".
- B01/B03 feeling shares use **recorded feelings only**, never treat no feeling as Tired. B02 describes difference only, with no inferred cause. B04 does not infer that sufficient duration should guarantee good recovery.
- If an illustrative PNG depicts percentages, sample counts or a "quality/health improvement" interpretation not backed by policy, **replace it with API facts and non-clinical neutral copy**.

## Asset-first component composition

**Reuse the committed small transparent artwork before adding new artwork.** Existing assets live in [`assets/sleep-tracking/`](../assets/sleep-tracking/README.md); complete mapping in [ASSET_MAPPING.md](ASSET_MAPPING.md) and machine manifests.

| Variant | Existing standalone assets (decorative only) | Native / data-bound components |
| --- | --- | --- |
| A01 | `moon-cloud-stars.png`, `sleep-cloud.png` | Lunar/cloud accent, calendar cells native |
| A02 | `pillow-stars.png`, `bed.png` | Pillow/bed decoration, Goal states native |
| A03 | `trend-up.png`, `bars.png` | Trend/bar artwork decorative only, real comparison bars native |
| A04 | `moon-cloud-stars.png`, `sleep-cloud.png` | Moon/cloud accent, two time tracks native |
| A05 | `moon-cloud-stars.png`, `bars.png` | Moon/bar accent, two mean bars native |
| B01 | `feeling-comfortable.png`, `feeling-normal.png`, `feeling-tired.png` | Reuse all three feeling reaction PNGs |
| B02 | `feeling-comfortable.png`, `feeling-tired.png`, `bars.png` | Reuse Comfortable/Tired PNGs; render averages natively |
| B03 | `feeling-comfortable.png`, `feeling-normal.png`, `feeling-tired.png`, `trend-up.png` | Reuse 3 feeling PNGs; comparison charts native |
| B04 | `feeling-tired.png`, `bed.png`, `pillow-stars.png` | Reuse tired face/bed/pillow; exceptions list native |

- `trend-up.png` and `bars.png` are **static decorations**, not valid recorded data charts. Calendar, target, timer, check, info, lock and arrow icons may use the app's native/vector icon set; no need to create or crop PNG icons from screenshots.
- Use `feeling-comfortable.png`, `feeling-normal.png`, `feeling-tired.png` in B-series, scaled with `contain` and accessible labels. If the full screen mockup depicts a different emotional icon, the standalone PNG inventory and semantic feeling mapping win.
- Design tokens: wellness background `#F6FAF7`, mint `#D7EFE3`, green primary `#51B89A`, text `#244C43`, lilac `#A993DC` used only sparingly (~10%). Rounded neutral cards, concise Vietnamese copy, independent section spacing.
- Never embed exported full-screen PNGs as live RN views. Backgrounds/cards, data charts, labels and controls must stay responsive and accessible.

## Interaction and states

- READY: current validated evidence, formula/sample/period, sources and optional AI explanation. `NO_DATA`, `INSUFFICIENT_DATA`, `UNVERIFIED_DATA`: show correct state, **hide unsupported chart/claim/AI**; locked list item shows only status, not unlock progress or unmet numeric conditions.
- Explanation is **explicit click-to-generate** only for READY with consent ON, then inline three sections **Quan sát / Dữ liệu & phép tính / Giới hạn** (<=150 Vietnamese words); evidence remains available without AI. AI failure/cooldown can show clearly labeled deterministic explanation if evidence is current.
- If consent OFF, AI Explanation request must be blocked; non-AI evidence remains. Story is separate (Report focus) and should not auto-generate here.
- When insightCode from an AI Story becomes non-READY, keep detail destination but show current non-READY state and discard stale explanation.
- No medical causes, stages, REM, sleep score, action plan or diagnosis.

## Integration acceptance checklist

- [ ] Screen `SLT-SCR-004` renders all 9 variants by code with correct charts and existing asset references.
- [ ] Eligibility, date windows, sample and ratio denominators are sourced from verified backend evidence, not screenshot numbers.
- [ ] A03/B03 comparisons use **completed 7+7 windows**, not the Report's rolling current 7-day bars.
- [ ] A04 uses two time **ranges**, not duration trend or subjective regularity scoring.
- [ ] B01/B03 ratios use recorded feelings; B02/B04 remain descriptive and non-medical.
- [ ] All cards support READY, Locked/non-READY and staleness with correct AI consent behavior.
- [ ] Source records are permission-checked; charts/icons are interactive/native where appropriate; PNGs only provide illustration.
- [ ] Do a separate Expo device visual review; committed mockups do not constitute implementation proof.
