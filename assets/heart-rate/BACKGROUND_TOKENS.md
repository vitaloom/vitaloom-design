# Heart Rate — blush ambient page background

The approved Heart Rate UI uses a very **subtle warm/blush undertone**, unlike the mint Steps and Water screens. Apply the treatment **only within Heart Rate feature content**; keep AppShell drawer and native bottom navigation on their shared theme surfaces.

## Visual treatment

| Token / layer | Light | Dark |
| --- | --- | --- |
| Native base page gradient, top → bottom | `#FFF9FA` → `#FFF3F6` | `#211F29` → `#1A242B` |
| Optional transparent glow overlay | [hr-screen-ambient-light.svg](hr-screen-ambient-light.svg) | [hr-screen-ambient-dark.svg](hr-screen-ambient-dark.svg) |
| Standard analytics card | `#FFFFFF` | app theme elevated charcoal surface (reference `#2C2B35`) |
| KPI tile (HR) | `#FFF5F7` → `#FFE8ED` | dark muted mauve/charcoal; keep semantic contrast |
| HR line/dots accent | soft coral `#EC617F` | brighter coral `#FF8398` |

- The **ambient SVG is transparent**, containing only faint radial ellipses with fading edges. It is **not a complete page background** or a substitute for theme colors.
- Render the native gradient as the bottom-most feature-page background, then the ambient SVG anchored absolutely **behind scroll content**, with `pointerEvents="none"` and hidden from accessibility. Do not scroll-duplicate the glow in every card.
- If performance or platform SVG rendering is unsuitable, keep **native gradient alone**. The background still must feel gently rosy but not saturated red/pink.
- Native white/elevated cards keep readable contrast; the chart grid, axes and tooltip remain their semantic colors. No global CSS `background:red` or page-wide overlay over readable UI.
- On a 393dp phone, the blush should remain most visible around hero and margins, not obscure text. Check both modes on web and native.
- This only defines **visual tokens**; app's existing theme and contrast rules win if they conflict.

[Current HR assets](README.md) · [Screen asset mapping](../../heart-rate/ASSET_MAPPING.md).
