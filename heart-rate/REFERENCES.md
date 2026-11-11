# Heart Rate — canonical references and UI dependency map

**Single Source of Truth policy:** design owns presentation and interaction only. The links below are authority for endpoint names, DTOs, business rules, timestamp semantics, data models and calculations. Do not clone their content into this repo.

- [Heart Rate API Contract — latest and aggregated Statistics](https://github.com/vitaloom/vitaloom-backend/blob/main/docs/api/metrics/heart-rate.md)
- [Heart Rate Data Model & Persistence Design](https://github.com/vitaloom/vitaloom-backend/blob/main/docs/architecture/heart-rate-data-design.md)
- [Backend API Contract Index](https://github.com/vitaloom/vitaloom-backend/blob/main/docs/api/api-contract.md)
- [Automated Health Metrics use cases](https://github.com/vitaloom/vitaloom-business-docs-and-tools/tree/main/docs/usecase_spec/automated-health-metrics)
- [Health Insights Reports use cases](https://github.com/vitaloom/vitaloom-business-docs-and-tools/tree/main/docs/usecase_spec/health-insights-reports)
- [UI behavior](BEHAVIOR.md) and [shared analytics UX](../shared/analytics-components/README.md)

## UI-to-contract dependency map (no endpoint/DTO duplication)

| UI region | Canonical source | Compatibility questions to verify |
| --- | --- | --- |
| Latest-recorded hero + measured-at | HR **Summary** read API | Source timestamp is original measurement instant; latest independent from selected date. |
| Day average / status badge | HR **Summary** read API | Status may be partial or historical-unverified; average may be missing independently of latest. |
| Line dots and min/max ranges | HR **Aggregated Time Series Daily/Weekly/Custom** | Confirm buckets' average/extrema/count semantics and calendar resolution. |
| Range min/max insight tiles | Selected aggregated time series | Derive from nonempty buckets only; never invent a metric for empty data. |
| Average insight for Week/Custom | Canonical time-series API (and Statistics design owner) | Verify whether a sample-weighted result can be presented without precision errors; if not, label as OPEN/omit. |
| Sample count + nonempty intervals | HR aggregated Statistics | A count of observed samples does not prove continuity or completeness. |
| Calendar/Custom constraints | HR API contract | Respect date-range/zone handling; no invented route or param. |

### Integration checkpoint

**Do not use the legacy design README's obsolete `/api/heart-rate/summary` path.** The current Statistics-owned summary path is defined in the canonical contract. Agents must consult that source afresh, not copy this note into hardcoded API clients without verification.

If production data/API differs, record a compatibility issue with the missing capability, its impact on a named UI region, and a proposed fallback. Backend changes require separate approval. No duplicated request/response examples or database schema in this repo.
