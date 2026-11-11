# Sleep Tracking — UI state matrix

| Area | Data-ready | Pending | Empty / insufficient | Error / stale | Required user feedback |
|---|---|---|---|---|---|
| Home/latest | Confirmed session and optional feeling | skeleton | `No recorded sleep yet` | network/auth failure, not an empty history | record action or retry |
| Home/goal | history-valid progress | load goal and day | no goal ⇒ don't show percent; optionally invite to set | unverified data ⇒ hide percentage | navigate Goal management |
| Home/featured | ≤1 eligible READY insight | load | none if ineligible | stale ⇒ hide claim | navigate Insights |
| Entry | valid local draft | `SAVING` | feeling is optional | invalid range/DST/future/overlap, offline, unknown result | inline error / retry or reconcile |
| Insights | eligible A/B/C cards | loading | `NO_DATA`, `INSUFFICIENT_DATA` per category | `UNVERIFIED_DATA`, stale | record more or reload |
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

The six selected screenshot PNGs illustrate happy paths only. Loading, failed save, overlapping record, DST ambiguity, AI opt-out, stale AI, no goal, empty/insufficient data, Journal and Goal Management have **no approved image** yet. Implement functional states as native UI and request visual review before treating them as accepted screenshots.
