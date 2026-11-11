# Steps — canonical references and UI dependency map

**Policy:** This file is a link/navigation layer, not a copy of Backend contracts, persistence models, request/response examples or calculation rules. For all API/model/BR questions use the canonical document **at implementation time**.

## Authority

- **Statistics and ingestion API (canonical):** [Steps API Contract](https://github.com/vitaloom/vitaloom-backend/blob/main/docs/api/metrics/steps.md)
- **Persistence/model and data semantics (canonical):** [Steps Data Model](https://github.com/vitaloom/vitaloom-backend/blob/main/docs/architecture/steps-data-design.md)
- **Cross-metric API conventions:** [API Contract Index](https://github.com/vitaloom/vitaloom-backend/blob/main/docs/api/api-contract.md)
- **Business rules / use cases:** [Automated Health Metrics](https://github.com/vitaloom/vitaloom-business-docs-and-tools/tree/main/docs/usecase_spec/automated-health-metrics)
- **UI interaction:** [Steps BEHAVIOR](BEHAVIOR.md)
- **Reusable UI conventions:** [Shared analytics components](../shared/analytics-components/README.md)

## Mapping by UI responsibility (NOT DTO documentation)

| UI section | Canonical dependency | FE implementation verification |
| --- | --- | --- |
| Hero: period total and recorded increments | Steps Statistics **Daily/Weekly/Custom** | Confirm how accepted totals and event counts are represented for selected period. Do not treat missing total as zero. |
| Chart bars + time labels | Steps Statistics current period route | Use response bucket boundaries and backend timezone; show gaps for buckets without records. |
| Peak bucket | Steps Statistics buckets | Derive as a view-only insight from nonempty values with deterministic ties; no persisted new metric. |
| Number of buckets with recorded data | Steps Statistics buckets | Count only buckets with accepted records; do not call it “tracked hours” or observation coverage. |
| Custom date UI | Steps Statistics **Custom** | Respect canonical range/date rules and return errors. |
| Ingestion context | Steps ingestion + architecture references | Mobile must not simulate authoritative totals or ingest through read UI. |

**Agent checkpoint:** If an endpoint, field or a required insight differs from the latest canonical source, record it as a design/API compatibility gap; do not silently change the backend contract to satisfy the mockup. Do not copy API JSON schema here.
