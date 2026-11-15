# VitaLoom — Sleep Tracking design & handoff (F1/F2)

> **Updated 2026-11-15 from GitHub commit `e0ceb5a`.** The new Recent Sleep designs and 9 Insight Details are available as **visual mockups**, not proof of shipped Expo screens or backend APIs. Canonical business rules always override illustrative dates/counts/copy in PNGs.

## Canonical business references

- [Sleep module overview](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/00-module.md)
- [F1 Sleep Journal rules](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f1-sleep-journal/rules.md)
- [F2 Goal/Recent Report/Insights rules](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f2-sleep-goals-insights/rules.md), [UC-009](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f2-sleep-goals-insights/SLT-UC-009_kham-pha-sleep-insights.md)
- [Insight catalog A01–A05, B01–B04](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f2-sleep-goals-insights/insight-catalog-v2.md), [OW-01–61](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f2-sleep-goals-insights/observation-window-decisions-2026-11-14.md)
- [Global behavior standard](../BEHAVIOR_STANDARD.md) and [global asset mapping standard](../ASSET_MAPPING_STANDARD.md)

## Current active visual references

| Stable screen ID | Current visual baseline | Purpose |
| --- | --- | --- |
| `SLT-SCR-001` | [01-sleep-home-recent.png](01-sleep-home-recent.png) | Sleep Home: latest verified MAIN, Goal, Journal, Recent Report entry; <=1 featured insight |
| `SLT-SCR-002A` / `002B` | [Time range](02a-sleep-entry-time-range.png) / [Duration only](02b-sleep-entry-duration-only.png) | F1 recording forms, one shared draft; Main-only |
| `SLT-SCR-003` | [03-all-sleep-insights-recent.png](03-all-sleep-insights-recent.png) | Group A/B READY + Locked only; C deferred |
| `SLT-SCR-004` | [04-recent-insight-detail.png](04-recent-insight-detail.png) | Reusable Insight Detail shell + [9 specific chart variants](README-INSIGHT-DETAILS.md) |
| `SLT-SCR-006` | [Journal](7_sleep_journal.png) | F1 Journal reference; **structure-only**, purple palette rejected |
| `SLT-SCR-007` | [Record detail](8_sleep_record_detail.png) | F1 persisted record details; structure-only |
| `SLT-SCR-008` | [Edit](9_sleep_record_detail_edit.png) | F1 edit, current-week/latest-only; structure-only |
| `SLT-SCR-009` | [Goal](10_sleep_goal_setup.png) | SLT-UC-008; structure-only; 8h suggestion not autosaved |
| `SLT-SCR-010` | [02-recent-sleep-report.png](02-recent-sleep-report.png) | **Current rolling 7-day Recent Sleep Report and optional AI Recent Story** |

- `SLT-SCR-004` has nine **visual variants**, A01–A05 and B01–B04, in [Insight Detail design spec](RECENT_INSIGHT_DESIGN.md); they are *not* 9 new routes.
- `SLT-SCR-003/NO_DATA` and `/INSUFFICIENT_DATA` keep [11](11_sleep_insight_empty.png) / [12](12_sleep_not_enough_data_insight.png) as **structure-only historical state references** requiring green palette and correct data semantics.
- `01-sleep-home.png`, `03-sleep-insights.png`, `04-ai-insight-detail.png`, `05-ai-weekly-sleep-story.png`, `6_weekly_report_screen.png`, and [old overview](00-sleep-design-overview.png) are preserved for provenance only; **not active FE baselines**. `SLT-SCR-005` remains a retired fixed-week screen ID. Do not delete/rename old binaries merely to update the registry.

## Current UX contract

- Recent Report uses **[D−6,D]**, `D` = today in Asia/Ho_Chi_Minh; coverage days/7, average over *recorded MAIN days*. No week switch, past Report archive, fixed-week Sleep report or HIR Sleep Weekly Story.
- AI Recent Story lives in Report and loads **separately after verified metrics/insights**, when consent ON and >=1 READY insight other than A01; max 2 selected observations. OFF hides entire Story section.
- A03/B03 compare **two completed seven-day windows**, not the report's [D−6,D]. Locked is status-only. Group C deferred/hidden.
- Sleep Journal still has **calendar-week create/backfill** and **latest-only edit/delete**. Reporting window is not a CRUD window.
- No clinical sleep scoring, sleep-stage estimates, causality or quality grading from duration.

## Design language & asset reuse

Soft Wellness green/mint primary (`#F6FAF7`, `#D7EFE3`, `#51B89A`, `#244C43`), purple `#A993DC` only as a sparse accent. New report/details use short native text, one primary visualization per screen, contextual sample/period, progressive disclosure. Screens 7–12 remain **structure-only** because of purple-dominant artwork.

**First reuse** the existing standalone small assets in [assets/sleep-tracking](../assets/sleep-tracking/README.md). Full per-screen/per-insight mapping: [ASSET_MAPPING.md](ASSET_MAPPING.md) and [asset manifest](../assets/sleep-tracking/asset-manifest.json). Use native/vector icons for calendar/clock/target controls not already available; do not crop assets from screenshots. Never use decorative `bars.png`/`trend-up.png` in place of dynamic charts.

## Handoff documents

- [BEHAVIOR.md](BEHAVIOR.md) — navigation, actions, CRUD states and F2 interactions.
- [RECENT_INSIGHT_DESIGN.md](RECENT_INSIGHT_DESIGN.md) — canonical **nine-detail-variant design and evidence mapping**.
- [FE_HANDOFF.md](FE_HANDOFF.md) — Expo component boundaries and API dependency checklist.
- [SCREEN_STATES.md](SCREEN_STATES.md) — report and detail progressive-loading/non-READY states.
- [ASSET_MAPPING.md](ASSET_MAPPING.md) — existing PNGs vs native data charts, mappings.
- [screen-manifest.json](screen-manifest.json) — machine-readable active and legacy registry.
- [SCREEN_IMPORT.md](SCREEN_IMPORT.md) — uploaded visual provenance.
- [ADDITIONAL_SCREENS_20261111.md](ADDITIONAL_SCREENS_20261111.md) — color correction and legacy structural notes.

**Release gate:** screenshot references are not an API contract, business-rule approval of simulated metrics, or proof FE implementation has been visually accepted.
