# Heart Rate — metric-specific UI icons

These are **independently authored self-contained SVG artwork assets**, designed for the KPI tiles and analytics header. They are not photos, fonts, UI screenshots, medical diagnostics, or runtime data. Each metric SVG has a **64 × 64 viewBox**, including its own themed circular badge, and should be rendered at approximately **30–40dp** (depending on card width). The analytics heading icon uses a **48 × 48 viewBox**, normally rendered at **28–32dp**.

| UI position | Light SVG | Dark SVG | Intent |
| --- | --- | --- | --- |
| Minimum (Thấp nhất) | [hr-min-light.svg](hr-min-light.svg) | [hr-min-dark.svg](hr-min-dark.svg) | Mint downward arrow, softly tinted pill/circle |
| Average (Trung bình) | [hr-avg-light.svg](hr-avg-light.svg) | [hr-avg-dark.svg](hr-avg-dark.svg) | Coral stylized pulse line in blush badge |
| Maximum (Cao nhất) | [hr-max-light.svg](hr-max-light.svg) | [hr-max-dark.svg](hr-max-dark.svg) | Rose upward arrow in blush badge |
| Analytics heading | [hr-analytics-light.svg](hr-analytics-light.svg) | [hr-analytics-dark.svg](hr-analytics-dark.svg) | Rose heartbeat-line accent |

## Usage

- Use the matching light/dark variant from app theme state. **Do not display both variants at once** or tint a light-only raster asset to fake dark.
- Place the icons inside the appropriate **native KPI tile**, near its label/value. Number, BPM unit, trend caption and touch target remain native UI.
- Asset already contains its circular background; **do not stack a second colored badge behind it**.
- KPI cards should not change their calculation, values, dates or statuses because of an icon.
- Unlike shared line-icons, these illustrations use **fixed thematic colors**; they do not rely on `currentColor`.
- Do not turn the average pulse line into a real-time ECG or claim clinical significance.

[Heart Rate asset catalog](../README.md) · [Screen composition mapping](../../../heart-rate/ASSET_MAPPING.md) · [UI enhancement handoff](../../../UI_ENHANCEMENT_HANDOFF.md).
