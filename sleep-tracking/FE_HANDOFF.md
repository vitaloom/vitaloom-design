# Sleep Tracking — Expo FE implementation handoff (design-level)

**MANDATORY COLOR OVERRIDE:** New screen PNGs 7–12 use the WRONG purple-dominant palette. Implement their structure and content in green/mint wellness UI with cream neutral surfaces and green primary CTA; purple is decorative bed/pillow/icon accent only. See [2026-11-11 correction](ADDITIONAL_SCREENS_20261111.md).

**Not an API contract.** This is a screen-to-data dependency checklist for FE/BE agreement. Canonical business rules and the backend's published API contract take precedence.

## Component boundaries

```text
AppShell (shared header, drawer, global tabs)
└─ Sleep feature navigator
   ├─ SleepHomeScreen                  SLT-SCR-001
   ├─ RecordSleepScreen                SLT-SCR-002A/B (one shared draft)
   │  ├─ SleepTypeSegment
   │  ├─ InputMethodSegment
   │  ├─ TimeRangePicker                date + hour wheel + minute wheel + timezone
   │  ├─ DurationPicker                 end date + hour/minute wheels
   │  ├─ OptionalFeelingPicker
   │  └─ SaveRecordAction
   ├─ SleepJournalScreen               SLT-SCR-006
   │  └─ SleepRecordDetailScreen        SLT-SCR-007
   │     └─ SleepRecordEditScreen       SLT-SCR-008 (reuse record form)
   ├─ SleepGoalScreen                  SLT-SCR-009
   ├─ SleepInsightsScreen              SLT-SCR-003 (also NO_DATA/INSUFFICIENT_DATA)
   ├─ SleepInsightDetailScreen         SLT-SCR-004
   └─ HIRWeeklyReportScreen            SLT-SCR-005 (HIR-owned)
```

## Data dependencies to define with BE

| UI surface | Server-derived data needed | Nonnegotiable semantics |
|---|---|---|
| Journal | confirmed sessions grouped by statistical day, method, feeling | duration-only never has inferred clock times |
| Record detail/edit/delete | persisted record, revision, stored timezone and write outcome | existing timed timezone immutable; conflict/reconciliation, no false success |
| Goal management | active/historic goal, duration constraints, confirmation | 8h suggested only; removing goal preserves history |
| Insights empty/insufficient | verified no-data vs category-specific insufficient evidence | images 11/12 are states of 003, not routes |
| Latest sleep | confirmed session ID, type, duration, statistical day, optional feeling, and time semantics | no invented timestamps for duration-only |
| Sleep Goal | current goal + historical effective goal + day status/progress | no auto 8h goal; no percent without verified data |
| Time Range form | resolved timezone; submit start/end instants; validation errors | DST/overlaps checked server-side; preserve one reference zone |
| Duration Only | total integer minutes; user-chosen end date | 1–1440, no implied clock times |
| Save | request identity, acknowledged/unknown status | idempotency and version control per backend tech design |
| Insights list | insight code/category, period, status, coverage, sample, summary, evidence version | only READY insights displayed as evidence-backed |
| Insight detail | deterministic evidence, source record refs, limitations, AI eligibility/consent, validated explanation | AI cannot override numbers; stale text hidden |
| Weekly Report | completed week status, day-level dataStatus, daily durations, weekly metrics, eligible insights and optional AI story | date missing != 0h; owner HIR-UC-002 |

Do not invent endpoint paths, response field names, token storage, retry API, or time zone serialization; request them from backend contract. The F2 insight catalog's JSON example is **logic illustration, not approved wire schema**.

## FE-specific recommendations (PROPOSED)

- Navigation IDs must map to current Expo navigation implementation, not assumed route strings.
- Use a single screen plus method-specific form sections for 002A/B. Preserve raw user edits while switching tabs, but do not send hidden incompatible fields.
- Create accessible wheel pickers and date pickers; support DST disambiguation or fallback to duration-only if instants cannot be resolved.
- Extract date/time normalization in pure tested helpers; keep server as authority on overlap/date validation.
- Store one optional feeling per session; charts use actual computed aggregates, not exported decorative assets.
- Use reusable skeleton/empty/error/unknown-result components and a refresh-on-confirmation data strategy.
- AI consent state and versioning must be server-provided/validated; no client-generated medical inference.

## New assets and corrected visual acceptance

- Structural screenshot references: [Journal 7](7_sleep_journal.png), [Detail 8](8_sleep_record_detail.png), [Edit 9](9_sleep_record_detail_edit.png), [Goal 10](10_sleep_goal_setup.png), [No Data 11](11_sleep_insight_empty.png), [Insufficient 12](12_sleep_not_enough_data_insight.png).
- Standalone assets: [combined hero](../assets/sleep-tracking/star-pillow-cloud.png) and [small purple bed](../assets/sleep-tracking/bed.png).
- Do not sample purple screen gradients/buttons/cards from screenshots 7–12: use existing wellness-green design tokens and shared shell components.
- Reject screenshot sample values contradicting F1: time-range record statistical day is local end date in stored timezone; duration-only clock times must not be invented.
- Verify corrected green FE screens visually; design image existence alone is not UI implementation proof.

## Suggested contract acceptance scenarios

1. Time-range example 2026-11-10 23:15 → 2026-11-11 06:45 in a stable zone = 450 min; future/unresolvable/overlapping invalid.
2. Duration-only 07:30 + selected end date creates 450-minute estimated record, without start/end timestamps.
3. 00:00 invalid; 24:00 valid; 24:15 and 25:00 invalid even if wheel visually allows 0–100h.
4. Loading ≠ empty; unknown save result ≠ success; deleted source records invalidate linked AI copy.
5. C01 is not displayed without eligible B02; detailed evidence/sample is consistent with its card.
6. Current/incomplete week shows numeric/template report but no AI Weekly Story.
7. AI consent-off/network-failure does not block deterministic insights/weekly metrics.

## Missing before FE integration

- Journal/Detail/Edit/Goal and two Insights state **structure-only** references now exist; green-theme correction and visual review required. Consent, further error/confirmation and unconfigured-state visual designs remain open.
- API contract with exact request/response/error schema, idempotency rules and evidence version semantics.
- Cross-module HIR-UC-002 presentation alignment and privacy/security review.
- App-specific font/spacing token review. Screenshot/PNG asset import is now complete; see [asset mapping](ASSET_MAPPING.md).

Release readiness requires Expo device QA against approved visual and validated BR/UC, not just this handoff.
