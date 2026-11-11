# VitaLoom — Sleep Tracking (UI baseline)

> **Design status:** selected visual direction / approved concept by product owner (2026-11-11). This repository change publishes **behavior and asset integration guidance**. The six approved screenshot PNG binaries and nine originally generated transparent PNG assets are still **PENDING_BINARY_IMPORT** (see [SCREEN_IMPORT.md](SCREEN_IMPORT.md)); the SVG icon fallbacks in this PR are separate **PROPOSED** assets and must not be represented as those exact PNGs.
>
> **Implementation:** not evidence of a running React Native screen or implemented API.

## Source of truth

- [Sleep module scope](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/00-module.md), [F1 Journal rules](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f1-sleep-journal/rules.md), [F2 Goal/Insights rules](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f2-sleep-goals-insights/rules.md)
- [F2 insight catalog A/B/C](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f2-sleep-goals-insights/insight-catalog-v2.md), [AI-content guardrails](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f2-sleep-goals-insights/ai-content-guidelines.md)
- [Global behavior standard](../BEHAVIOR_STANDARD.md), [Global asset mapping standard](../ASSET_MAPPING_STANDARD.md)
- [Shared app navigation drawer](../shared/health-metrics-sidebar/README.md)

## Baseline screen registry

| Stable ID | Selected screen / PNG filename | Owner and scope | File |
| --- | --- | --- | --- |
| SLT-SCR-001 | `01-sleep-home.png` | Journal + Goal + one featured insight | Pending binary import |
| SLT-SCR-002A | `02a-sleep-entry-time-range.png` | SLT-UC-004: start/end with date + hour/minute selectors | Pending binary import |
| SLT-SCR-002B | `02b-sleep-entry-duration-only.png` | SLT-UC-004: duration + end date | Pending binary import |
| SLT-SCR-003 | `03-sleep-insights.png` | SLT-UC-009: A/B/C discovery | Pending binary import |
| SLT-SCR-004 | `04-ai-insight-detail.png` | SLT-UC-009: evidence + optional AI explanation | Pending binary import |
| SLT-SCR-005 | `05-ai-weekly-sleep-story.png` | HIR-UC-002: weekly report section, Sleep F2 metrics | Pending binary import |

Also planned: `00-sleep-design-overview.png` (contact overview), optional; not a standalone interactive screen.

### Important visual decisions

- VitaLoom *Soft Wellness*: cream/mint light surfaces, teal CTAs, lilac AI content, organic moon/cloud/pillow accents, rounded cards, readable compact charts.
- **Same form shell and action order** for 002A/002B; only method-specific inputs differ.
- **Time-range input:** separate **Date**, **Hour (00–23)**, **Minute wheel** controls for both Start and End. The minute wheel represents `00/15/30/45`; wheel transition past 45 wraps to 00 and carries to hour/date, rather than storing minute 60.
- **Duration-only input:** End Date plus duration **Hours wheel / Minutes wheel**; proposed wheel range 0–100h is a visual affordance, **NOT** a valid storage range. Business validity is 1–1440 minutes per session. Values above 24h, or 24h with nonzero minute, must be invalid/disabled.
- The reference screenshots contain **example data**, not API responses and not clinical evaluations.

## Handoff artifacts

- [BEHAVIOR.md](BEHAVIOR.md) — navigation, actions, validation, failure handling, eligibility, acceptance checks.
- [SCREEN_STATES.md](SCREEN_STATES.md) — state matrix for loading/empty/errors/AI.
- [ASSET_MAPPING.md](ASSET_MAPPING.md) — per-screen composition & actual proposed SVG fallback inventory.
- [FE_HANDOFF.md](FE_HANDOFF.md) — UI data dependencies, API-contract boundaries, Expo implementation notes.
- [SCREEN_IMPORT.md](SCREEN_IMPORT.md) — exact PNG destinations and integrity verification before marking image links live.
- [Screen manifest](screen-manifest.json), [small asset catalog](../assets/sleep-tracking/README.md).

## Ownership / deferred screens

- **Sleep Journal / record detail/edit/delete**: SLT-UC-005/006/007 — screens not yet included in this 6-screen visual baseline.
- **Sleep Goal Management**: SLT-UC-008 — destination to be designed. Suggested 8h goal is never auto-saved.
- **Weekly Report** belongs to **HIR-UC-002**, not a newly invented Sleep UC. Sleep supplies metrics, insight/evidence and data-state eligibility.
- **Post-MVP** reminders, wearables, sleep stages, sleep coaching, free-form chat and offline journal queue are excluded.

Approval of the selected screenshot appearance does not by itself approve every illustrative numeric value, a new API contract, an SVG fallback, or an unreviewed navigation/detail screen.
