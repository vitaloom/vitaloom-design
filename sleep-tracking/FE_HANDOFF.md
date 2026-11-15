# Sleep Tracking — Expo FE handoff (design-level, updated 2026-11-15)

> **Not an API contract and not evidence of implementation.** Business [F1 rules](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f1-sleep-journal/rules.md) and [F2 rules](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f2-sleep-goals-insights/rules.md) override mockup data. Read [RECENT_INSIGHT_DESIGN.md](RECENT_INSIGHT_DESIGN.md), [BEHAVIOR.md](BEHAVIOR.md), [ASSET_MAPPING.md](ASSET_MAPPING.md).

## Component / navigator structure

```text
Shared AppShell & navigation
└─ Sleep feature
   ├─ SleepHomeScreen                SLT-SCR-001  (01-sleep-home-recent.png)
   ├─ RecordSleepScreen              SLT-SCR-002A/B (one draft, Main-only)
   │  ├─ TimeRangePicker / DurationPicker
   │  └─ OptionalFeelingPicker
   ├─ SleepJournalScreen             SLT-SCR-006
   │  └─ RecordDetailScreen          SLT-SCR-007
   │     └─ RecordEditScreen         SLT-SCR-008
   ├─ SleepGoalScreen                SLT-SCR-009
   ├─ RecentSleepReportScreen        SLT-SCR-010  (02-recent-sleep-report.png)
   │  ├─ VerifiedSummary + 7DayCoverageChart
   │  ├─ HighlightInsightCards (max 3 READY)
   │  └─ AIRecentStoryCard (conditional, independent HTTP/loading)
   ├─ AllSleepInsightsScreen         SLT-SCR-003  (03-all-sleep-insights-recent.png)
   └─ SleepInsightDetailScreen       SLT-SCR-004  (insightCode parameter)
      ├─ VerifiedEvidenceHeader + Sample/Period
      ├─ InsightSpecificChart        (A01–A05, B01–B04)
      ├─ EvidenceAndLimitations      (collapsible)
      └─ AIExplanationInline         (explicit click + consent)
```

**Never implement a weekly selector, `HIRWeeklyReportScreen` for Sleep, `SLT-SCR-005` as active, 9 separate Detail routes, or C-group navigation.** HIR weekly is Steps/Water only. The old 01/03/04/05 PNGs remain provenance, not current code baselines.

## Server-derived data checklist (logical, NOT endpoint schema)

| Surface | Needed from backend | FE invariant |
| --- | --- | --- |
| Home/latest | confirmed MAIN ID/day/duration/method/optional feeling, Goal/progress | never infer clock time from duration-only, no 0 for missing |
| Journal/Create/Edit/Delete | server-confirmed records, reference timezone, edit/delete eligibility and outcomes | F1 current-calendar-week create/backfill; edit/delete latest-only |
| Goal | active goal + historic effective goal | 8h suggestion is not active; validate 60–1440 minutes, 15-min step |
| Recent Report | current `[D−6,D]`, verification state, coverage calendar, days with MAIN, mean/denominator, up to 3 READY highlights | `D` today in Asia/Ho_Chi_Minh; no historical picker |
| All Insights | A/B code/title/status/priority/evidence fingerprint, READY vs Locked | backend-sorted READY; Locked last with status only; C hidden |
| Insight Detail | code, period, baseline period where relevant, sample/denominator, measurement, limitations, source references, fingerprint/status | render **code-specific chart**; never use screenshot's illustrative figures |
| A03/B03 | two **completed** seven-day windows + means or feeling ratios per period | excludes today even if Report includes today |
| A04 | eligible MAIN RANGE samples, reference timezone, min/max relative-day times, DST status | no fabricated timestamps/regularity labels |
| B01/B02/B03/B04 | actual opted-in feeling per MAIN; effective goal history for B04 | missing feeling != tired; descriptive only, correct denominators |
| AI Story | consent, eligibility, independent response + evidence freshness | only on Report open/focus, cache/fallback as server directed; hide Story area when consent OFF |
| AI Explanation | consent + latest READY detail evidence; explicit request outcome | never auto-generate on detail open; show 3 parts inline; stale text hidden |

AI Story max 120 Vietnamese words, <=2 selected READY observations (>=1 outside A01); Explanation max 150 words. API, Redis TTL/cooldown/timeout/validation/retry/single-flight are Backend responsibilities. FE must not create speculative client-side caches, sleep scores, medical labels, polling or background AI jobs.

## Component-specific chart mapping

- `A01`: 7-day coverage calendar + count /7; >=3 MAIN, verified recent 7 days.
- `A02`: 7-day achieved/not-achieved/missing/not-applicable state cells + numerator/eligible denominator; >=3 MAIN days with effective historical Goal; verified Journal+Goal history.
- `A03`: two completed 7-day mean bars + signed minute delta; >=3 MAIN per completed window, both verified; current day excluded.
- `A04`: two min-max range tracks: bedtime and wake-up, relative-day timeline; >=3 eligible MAIN RANGE in selected same timezone; DST exclusions.
- `A05`: two bars for weekday/weekend means, signed minute delta, per-group n; >=3 weekday MAIN and >=2 weekend MAIN in recent window.
- `B01`: three-segment 100% distribution/donut, count/denominator, missing-feeling note; >=3 MAIN with feeling in recent window.
- `B02`: two comparable average-duration bars for Comfortable and Tired, signed minutes; >=3 Comfortable and >=3 Tired MAIN in recent window.
- `B03`: two 100%-stacked distributions for completed windows, signed percentage-point changes; >=3 MAIN with feeling in each completed 7-day window.
- `B04`: exception count + dated verified record cards with duration vs effective day-goal; >=3 MAIN with feeling, >=1 Tired with duration >= effective Goal, verified goal history.

Treat all PNG example values independently illustrative; even an attractive generated statement may contradict conditions. Derive every number and annotation from the verified wire contract, show `n` and period; time, absence, Goal and feeling semantics are mandatory.

## Existing asset reuse (first choice)

Assets are in [`../assets/sleep-tracking/`](../assets/sleep-tracking/README.md), mapped per code in [RECENT_INSIGHT_DESIGN.md](RECENT_INSIGHT_DESIGN.md), [ASSET_MAPPING.md](ASSET_MAPPING.md), and machine-readable [asset manifest](../assets/sleep-tracking/asset-manifest.json).

- Reuse `moon-cloud-stars.png`, `sleep-cloud.png`, `pillow-stars.png`, `star-pillow-cloud.png`, `bed.png` for calm decorations, and `feeling-*.png` for actual three feeling categories.
- For A01 calendar, A02 Goal, A04 time range, use existing native/vector icon components. `bars.png` and `trend-up.png` are decorative and **never substitute data-driven graphs**.
- No screen screenshot cropping or new generated assets unless explicitly reviewed. Use native React Native layouts, charts, type, progress, safe areas and hit areas.
- Screens 7–12 remain **structure-only** due to invalid purple-dominant palette; mint/green is required in code, purple minor (~10%).

## Progressive loading and error handling

- On Report focus: server-verified metrics/evidence first; AI Story separate. Stale output never remains visible when data/policy/window/consent change. No polling; next focus can recheck.
- `NO_DATA`: guided Journal action; not a 0h chart. `INSUFFICIENT_DATA`: verified metrics if valid, no unsupported insight. `UNVERIFIED_DATA`: show only verified *individual* facts, no aggregate/Story.
- On a non-READY insight Detail: show status only, no fake evidence/chart/AI. Locked list item exposes status only, not missing requirements/progress.
- F1 write outcomes and form validation stay server-authoritative. Do not optimistically assert success or lose drafts on uncertain responses.

## FE acceptance gate

- [ ] No fixed-week Sleep report, weekly navigation, Group C or nine separately routed detail screens.
- [ ] All 9 chart variants use correct window, sample, Goal and feeling facts.
- [ ] Existing small assets imported once into shared mapping, not duplicated or cropped from PNG screenshots.
- [ ] Native charts accessible, screen-reader labels for actual measurements, no misleading green health verdicts.
- [ ] READY/non-READY/stale/consent/loading/fallback states visually tested in Expo on supported screen sizes.
- [ ] Backend contract reconciled before API integration; documented visual baselines are not acceptance of backend numbers.
