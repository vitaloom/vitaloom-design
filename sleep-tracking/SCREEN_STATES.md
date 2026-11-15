# Sleep Tracking — UI states (F1/F2, updated 2026-11-15)

> Design-state mapping only; see [BEHAVIOR](BEHAVIOR.md), [RECENT_INSIGHT_DESIGN](RECENT_INSIGHT_DESIGN.md), [F2 rules](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f2-sleep-goals-insights/rules.md). Historic screens 11/12 are structure-only; their purple palette is not accepted.

| Surface | READY / verified | Loading | NO_DATA / INSUFFICIENT_DATA | UNVERIFIED / stale / error |
| --- | --- | --- | --- | --- |
| Sleep Home | last confirmed MAIN, goal/progress only if verified, <=1 READY feature | skeleton | no MAIN → Journal CTA; no Goal → set Goal invitation | no invented 0h/progress; auth/network notice |
| Journal / Record | confirmed sessions by statistical day; Main-only | loading/saving | verified missing record → `Chưa ghi nhận` | edit/delete restricted to latest in calendar week; uncertain save outcome != success |
| Goal | confirmed value/history | saving | 8h is suggestion not active by default | preserve prior confirmed Goal on error |
| Recent Report `SLT-SCR-010` | verified [D−6,D] coverage, mean over recorded MAIN, 0–3 READY highlights | metrics skeleton | NO_DATA → record MAIN; insufficient insight → metrics + empty insight area | unverified → individual facts only, no aggregate/AI |
| AI Recent Story section | consent ON + eligible READY evidence, validated <=2 observations | **independent** skeleton after Report metrics | no qualifying READY → no generated Story | consent OFF → entire section hidden; stale/cooldown/error → server deterministic fallback clearly non-AI if provided |
| All Insights `SLT-SCR-003` | A/B READY sorted by backend relevance; Locked after READY, status only | list skeleton | none READY → suitable empty message, no Group C | unverified claims hidden |
| Insight Detail `SLT-SCR-004` | one of nine code-specific charts + verified period/sample + limitations | check latest status | non-READY → state instead of chart/evidence/AI; sources not invented | stale evidence → hide stale metrics/AI and refetch |
| AI Explanation (inline) | consent ON, READY, user clicked: three parts <=150 Vietnamese words | independent button/loading state | not requested → no AI call; consent OFF → deterministic evidence only | cooldown/error → server-approved factual fallback from current evidence if available |
 
## State principles

- **Verified missing MAIN != 0 hours slept.** Missing feeling != Tired. Missing Goal does not imply failure. No projected quality labels.
- `NO_DATA` vs `INSUFFICIENT_DATA` vs `UNVERIFIED_DATA` are distinct, and eligibility can differ for each insight.
- Detail evidence must remain aligned with current `insightCode`, sample and fingerprint. Linked Story detail may become non-READY.
- Story only requests on Report focus when consent ON/eligible. Explanation only after user click; no timers or polling.
- Accessibility: use readable color contrast, screen reader status labels and native chart summaries. Purple is only a minor accent.

## Microcopy suggestions (not backend enums)

- No data: “Ghi nhận giấc ngủ để bắt đầu khám phá.”
- Insufficient: “Chưa đủ dữ liệu cho nhận xét này.”
- Unverified: “Dữ liệu chưa được xác minh đầy đủ. Vui lòng thử lại.”
- Stale: “Dữ liệu giấc ngủ đã thay đổi. Đang cập nhật nhận xét.”
- AI fallback: “Tóm tắt từ dữ liệu đã ghi nhận” (not labeled AI).
- Locked insight: “Chưa đủ dữ liệu”; do not show fabricated counts to unlock.
