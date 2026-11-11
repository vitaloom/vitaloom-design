# Analytics theme guidelines

**Status:** PROPOSED **visual fallback**, not a new global design-system source of truth. App tokens and accessibility standards take precedence.

| Role | Light visual direction | Dark visual direction |
| --- | --- | --- |
| Canvas (Steps / Water) | Soft off-white/mint tint | Deep blue-charcoal |
| Canvas (Heart Rate **only**) | Warm blush `#FFF9FA` → `#FFF3F6` | Deep mauve-charcoal `#211F29` → `#1A242B` |
| HR ambient decoration | Optional transparent [light glow](../../assets/heart-rate/hr-screen-ambient-light.svg) | Optional transparent [dark glow](../../assets/heart-rate/hr-screen-ambient-dark.svg) |
| HR KPI icon variants | [Light Min / Avg / Max](../../assets/heart-rate/icons/README.md) | [Dark Min / Avg / Max](../../assets/heart-rate/icons/README.md) |
| Card | White with restrained shadow | Slightly lighter charcoal surface |
| Primary text | Near-black teal | Pale mint-white |
| Muted text | Blue-gray | Desaturated mint-gray |
| Steps accent | Emerald/teal | Slightly luminous mint-teal |
| Heart accent | Coral/rose | Soft luminous coral |
| HR min/max whisker | Coral at reduced opacity, still legible | Brighter rose at controlled opacity |
| Grid | Fine pale dashed lines | Subdued teal-gray dashed lines |
| Tooltip | Contrast-rich light surface | Elevated dark surface with readable border |

Reference screens: [Steps light](../../steps/final-light.svg), [Steps dark](../../steps/final-dark.svg), [HR light](../../heart-rate/final-light.svg), [HR dark](../../heart-rate/final-dark.svg). Keep the same layout semantics and actual data in both themes. A dark visual is not permission to ship an independent hardcoded theme implementation.

## HR-specific warm tint

Only Heart Rate receives the subtle rosy canvas. Do not apply a global red/pink background to Steps, Water, or the shared navigation. Keep white/elevated cards for readable contrast, with pink limited to edge ambience, chart accents and hero. Use exact standalone icon variants from [HR assets](../../assets/heart-rate/icons/README.md); [background composition tokens](../../assets/heart-rate/BACKGROUND_TOKENS.md) are authoritative for design direction only, not new global FE theme values.
