# Sleep Tracking — UI state matrix

> **MANDATORY:** New illustrations of Journal/Goal/Insights states (images 7–12) are STRUCTURE-ONLY; their purple-dominant palette is WRONG. FE must use green/mint wellness as dominant UI, purple only small asset/icon accents. See [additional screens](ADDITIONAL_SCREENS_20261111.md).

| Area | Data-ready | Pending | Empty / insufficient | Error / stale | Required user feedback |
|---|---|---|---|---|---|
| Home/latest | Confirmed session and optional feeling | skeleton | `No recorded sleep yet` | network/auth failure, not an empty history | record action or retry |
| Home/goal | history-valid progress | load goal and day | no goal ⇒ don't show percent; optionally invite to set | unverified data ⇒ hide percentage | navigate Goal management |
| Home/featured | ≤1 eligible READY insight | load | none if ineligible | stale ⇒ hide claim | navigate Insights |
| Entry | valid local draft | `SAVING` | feeling is optional | invalid range/DST/future/overlap, offline, unknown result | inline error / retry or reconcile |
| Insights | eligible A/B/C cards | loading | `NO_DATA`: [11](11_sleep_insight_empty.png) on verified no-data; `INSUFFICIENT_DATA`: [12](12_sleep_not_enough_data_insight.png) when evidence below category-specific threshold | `UNVERIFIED_DATA`, stale | Record Sleep / Continue Tracking or reload |
| Journal | [7](7_sleep_journal.png), sessions by statistical date | loading | confirmed empty day ≠ 0h | auth/network/unverified | add session or retry |
| Record Detail | [8](8_sleep_record_detail.png), actual persisted record | loading | deleted/not found | stale or permission error | reload / back to Journal |
| Edit Record | [9](9_sleep_record_detail_edit.png), valid edit draft | saving | feeling optional | validation/revision conflict/unknown result | retain draft and reconcile |
| Goal Setup | [10](10_sleep_goal_setup.png), confirmed goal | saving | no active goal; 8h only suggestion | invalid/stale/unknown | retain prior goal; retry safely |
| Detail | summary + deterministic evidence + limitations | checking version / AI | no AI consent ⇒ factual explanation | AI invalid/unavailable ⇒ no AI output; stale version ⇒ reload | view source records / reload |
| Weekly | selected verified week, 6 of 7 illustrative coverage | loading | missing dates shown `—`, not `0h` | current week: no AI story; unverified: no story | switch completed week / retry |

## Reusable microcopy candidates (not backend enums)

- No data: “Record a sleep session to start exploring.”
- Too little evidence: “Not enough recorded sleep data for this insight yet.”
- Unverified: “Your records couldn't be fully verified. Please retry.”
- Stale: “Your sleep records changed. Refresh to see the latest insights.”
- AI unavailable: “AI explanation is unavailable. You can still review the evidence.”
- Save result unknown: “We haven't confirmed whether this record was saved. Check your journal before retrying.”

Prefer exact backend domain status semantics; these are proposed English UI phrases, not a guaranteed translated API schema. Never show “0 hours slept” for missing data.

## Visual coverage

The original six screens cover selected happy paths. New structure-only images 7–10 illustrate Journal/Detail/Edit/Goal and images 11–12 illustrate Insights NO_DATA/INSUFFICIENT_DATA. Their purple UI palette is explicitly NOT approved; corrected green wellness implementation is required. Loading, failed save, delete confirmation, DST ambiguity, unconfigured goal, network failures, AI opt-out/stale still lack accepted dedicated visual references. Distinguish unverified from empty; request green FE visual review.
