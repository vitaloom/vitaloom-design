# Steps — analytics refresh

**Status:** PROPOSED visual implementation reference for FE/BE compatibility validation. Approved direction: preserve the mint Steps hero, strengthen chart axes and analytics, support light/dark. **This branch is a review handoff, not a production contract.**

## Screens

| ID | Reference | Purpose |
| --- | --- | --- |
| `STP-SCR-001` | [Steps — Light](final-light.svg) | Daily steps summary, hourly bars, peak hour and coverage information |
| `STP-SCR-001-D` | [Steps — Dark](final-dark.svg) | Equivalent layout with adaptive dark surfaces |

Vector previews reconstruct the accepted visual direction and use **illustrative fixtures**. They are not runtime components, evidence of endpoint output, or user data. Keep labels/date values runtime-derived. The original approved image in the design discussion is the aesthetic target; compare during implementation before final visual acceptance.

## Layout authority

1. Shared header and bottom navigation belong to [AppShell](../shared/health-metrics-sidebar/README.md), not Steps.
2. Preserve the mint hero and prominent recorded total. Display event count as **lượt ghi nhận**, never as a generic continuously tracked duration.
3. One analytics card: Ngày / Tuần / Tùy chọn, Y-axis with units, consistent horizontal grid, time-aware bar chart and tooltip.
4. Secondary insight tiles: peak bucket / period, number of nonempty buckets and count of accepted recorded increments when available.
5. Explanatory text separates **no accepted events** from **confirmed zero activity**. Never fabricate bars in empty or future buckets.

## Ownership / implementation

- [Steps behavior](BEHAVIOR.md), [canonical references & UI dependencies](REFERENCES.md).
- [Shared chart / theme conventions](../shared/analytics-components/README.md).
- [Global interaction standard](../BEHAVIOR_STANDARD.md), [global asset standard](../ASSET_MAPPING_STANDARD.md).
- If separately exported illustrations become available, create a Steps `ASSET_MAPPING.md` using actual paths. **No standalone illustration exports are provided in this branch**; the shoe illustration inside the SVG is part of the full-screen reference only.

## Required FE review

Use the canonical backend documentation at implementation time; validate all described data availability before connecting UI. Any unsupported insight must be disabled, omitted or marked OPEN; no synthetic KPI or substitute endpoint.
