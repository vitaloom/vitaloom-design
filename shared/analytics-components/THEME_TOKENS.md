# Analytics theme guidelines

**Status:** PROPOSED **visual fallback**, not a new global design-system source of truth. App tokens and accessibility standards take precedence.

| Role | Light visual direction | Dark visual direction |
| --- | --- | --- |
| Canvas | Soft off-white/mint tint | Deep blue-charcoal |
| Card | White with restrained shadow | Slightly lighter charcoal surface |
| Primary text | Near-black teal | Pale mint-white |
| Muted text | Blue-gray | Desaturated mint-gray |
| Steps accent | Emerald/teal | Slightly luminous mint-teal |
| Heart accent | Coral/rose | Soft luminous coral |
| HR min/max whisker | Coral at reduced opacity, still legible | Brighter rose at controlled opacity |
| Grid | Fine pale dashed lines | Subdued teal-gray dashed lines |
| Tooltip | Contrast-rich light surface | Elevated dark surface with readable border |

Reference screens: [Steps light](../../steps/final-light.svg), [Steps dark](../../steps/final-dark.svg), [HR light](../../heart-rate/final-light.svg), [HR dark](../../heart-rate/final-dark.svg). Keep the same layout semantics and actual data in both themes. A dark visual is not permission to ship an independent hardcoded theme implementation.
