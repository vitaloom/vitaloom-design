# Shared chart interaction rules

**Status:** PROPOSED interaction pattern, subject to accessibility/design review and current backend semantics.

1. **Axes:** Show unit-bearing Y axis, 3–5 primary horizontal guide lines, readable X ticks. Adjust Y bounds to include true min/max and avoid excessive exaggeration. Sparse charts remain sparse.
2. **Selection:** Touch or hover highlights a bucket and opens a tooltip. Keyboard focus can reach each observed bucket. Tooltip shows local bucket start/end and data, never invents a raw measurement.
3. **Time scope:** Day/Week/Custom controls change both data source/view and axis. Dates/ranges must pass the canonical endpoint's validation. Changing scope clears stale tooltip selection.
4. **Absent bucket:** Missing/null data means **no accepted observations in that bucket**, not a guaranteed 0. For HR, do not connect line across missing buckets. For Steps, do not render missing as zero-height colored bars.
5. **Current day:** Never draw future measurements. A present bucket may be incomplete. Tooltip can state it is in progress; do not extrapolate.
6. **Tooltip placement:** Keep within card bounds, avoid cover/overflow in 320px layouts, dismiss on outside tap/Escape/Back, show focused/selected state without color alone.
7. **Loading/error:** Maintain user scope and chart skeleton where fetching. Empty is not failed. Error has Retry; do not mutate prior chart points into misleading current data.
8. **Accessibility:** Spoken value + unit + local time + available range/sample info. At least 44px touch targets where meaningful; chart has text summary or list alternative.
9. **Theme:** Axis, grid, min/max and selected state visible in both themes, reduced-motion respected.

## Feature differences

- **Steps:** Sparse bars from accepted event increments. Peak and bucket-count insights computed only from event-bearing buckets. Use bar selection.
- **Heart Rate:** Connected average dots on adjacent nonempty buckets only. A translucent min–max vertical range behind each dot; read summary latest separately from dated average. Use dot selection and sample-count context.

**Canonical data authority:** See [Steps references](../../steps/REFERENCES.md) and [Heart Rate references](../../heart-rate/REFERENCES.md). This document intentionally does not duplicate response schemas or aggregation formulas.
