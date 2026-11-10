# Global Standard — Screen-to-Asset Mapping

**Scope:** Repository-wide for all features with independent UI artwork, including onboarding, authentication, water, sleep, heart rate, steps and shared surfaces. This document standardizes **mapping and asset composition**, not business behavior or the visual style of any feature.

**Related:** [Screen behavior standard](BEHAVIOR_STANDARD.md) · [Asset storage policy](assets/README.md).

## 1. Source of truth and boundaries

- `<feature>/README.md` contains the screen catalog and its approved full-screen design references.
- `<feature>/ASSET_MAPPING.md` is the **feature-level implementation of this global standard**: mapping each stable Screen ID to its actual artwork assets, roles, relative paths, composition and review status.
- `assets/<feature>/README.md` inventories the independent visual elements. Optional `asset-manifest.json` provides a machine-readable screen/asset registry.
- `<feature>/BEHAVIOR.md` owns interactions, navigation, states, recovery and accessibility. Backend API and approved business rules take precedence over illustrative text/data in a mockup.
- A full-screen design is **not** an independently reusable artwork asset. A screen approved as a reference does **not** automatically approve independently redrawn assets.

## 2. Ownership and lifecycle

```text
vitaloom-design/
├── ASSET_MAPPING_STANDARD.md        # Global rules
├── assets/
│   ├── shared/                      # Reused across features
│   └── <feature>/                   # Standalone feature artwork
│       ├── README.md
│       └── asset-manifest.json      # Optional, recommended
└── <feature>/
    ├── README.md                    # Screen inventory / mockups
    ├── BEHAVIOR.md                  # Behavior when applicable
    └── ASSET_MAPPING.md            # Needed when screen has separate assets
```

Keep complete screen mockups beside the owning feature, and independent visuals in `assets/<feature>/`. Only artwork reused by **multiple** features belongs in `assets/shared/`. Avoid binary duplication and empty folders. Use stable Screen IDs, descriptive ASCII kebab-case filenames, relative links and approved project-use rights. Prefer editable SVG for vectors, transparent PNG for raster illustrations, or WebP when supported by the app.

**Legacy designs:** Existing feature mockups remain in place. A feature with no independent visual assets does not need a placeholder mapping; adopt this standard when it receives or revises separable artwork.

## 3. Minimum screen mapping contract

Each feature mapping must document, **per screen with separate assets**:

| Field | Requirement |
| --- | --- |
| Screen ID | Stable catalog/behavior ID, never derived from a filename |
| Approved full-screen reference | Real file, link and visual approval status |
| Independent assets | Real links by explicit roles (hero, scenery/background, ornament, icon, etc.) |
| Composition | Bottom-to-top layer order, overlap, alignment and relevant size/aspect rules |
| Ownership | Feature-owned asset vs. shared reusable asset |
| Provenance | Original redraw, authored vector, project-provided raster, or other approved source |
| Visual status | `APPROVED`, `PENDING_VISUAL_ACCEPTANCE`, `PROPOSED` or `OPEN`; keep screen status separate from asset status |

If no independent asset exists for a role, write **not provided**. Do not invent files or links. Maintain a separate row or section for each meaningful state/variant when its image differs. Do not silently swap or remove an approved mapping.

## 4. Composition and frontend contract

Use **only roles present in the actual design**. Recommended semantics:

1. `background`: native screen gradient or surface color where possible.
2. `scenery`: decorative hills, waves, clouds and abstract shapes.
3. `hero`: the main isolated subject/illustration.
4. `decoration`: optional leaves, accents, shared ornamentation.
5. `surface`: native card or content panel when functional.
6. `interactive-ui`: real controls: buttons, forms, navigation, pager, toasts and status.

These are **role descriptions, not a fixed mandatory layer count**. Specify z-order and sizing for each feature. Use a common illustration coordinate stage for matched assets **only when they share a design viewBox**; never enforce Onboarding's `390 × 570` artboard or mint colors globally. Respect responsive width, safe areas, scrolling and accessibility.

For independent hero/scenery artwork use clean self-contained outlines and transparent root canvases, unless an opaque background is explicitly itself the design asset. When tasked to **create new artwork**, do not crop/mask an old screenshot and claim it was freshly drawn. Keep OS chrome and functional UI separate from decorative images. Decorative imagery is hidden from screen readers; meaningful illustrations require accessible alternatives as appropriate.

## 5. Machine-readable mapping (optional)

Place `asset-manifest.json` under the owning `assets/<feature>/` directory. Declare `screenAssets` with each Screen ID, approved full-screen reference, independent assets/roles, and review status. Asset paths must be explicit and documented relative to the manifest directory.

Existing manifests may use named roles such as `hero` and `landscape`. More complex modules may use a `layers` array with entries containing `role`, `path` and optional `order`. **Do not** force every module to use exactly two layers or rename an existing, documented manifest schema without coordinating its consumers. Keep Markdown and machine mapping in sync.

## 6. Documentation and agent handoff

- The feature `README.md` must link its `ASSET_MAPPING.md` once standalone assets exist.
- The mapping must link the real screen reference, each real asset, its asset catalog, this global standard and its machine manifest (if any).
- The feature behavior document must include a Visual Asset Mapping link/section but must not duplicate behavioral rules inside the asset map.
- Frontend agents should read the feature screen catalog + mapping + behavior document before implementation, choose only appropriate reviewed artwork, and implement functional elements as **native components**.
- Do not present sample health measurements inside illustrations as account data. No image in this repo proves frontend/API functionality.

## 7. Validation checklist

- [ ] Stable Screen ID in mapping matches the owning screen catalog.
- [ ] Full-screen reference exists and remains untouched unless a design change was approved.
- [ ] Every **real** linked asset path resolves; no placeholder links.
- [ ] Roles, z-order, size/alignment and feature/shared ownership are documented.
- [ ] Transparency, clean outlines, source rights and asset review status are clear.
- [ ] Markdown and JSON manifest represent the same set of screens and asset roles.
- [ ] Native controls, business logic and navigation are not replaced by static screenshots.
- [ ] Accessibility, small-screen layout, density and visual similarity are reviewed.
- [ ] Redrawn candidates are **not** claimed approved without visual sign-off.
- [ ] Existing behavior/UI design authority is preserved.

## 8. Current adoption

- [Onboarding implementation](onboarding/ASSET_MAPPING.md), [illustration catalog](assets/onboarding/README.md) and [manifest](assets/onboarding/asset-manifest.json).
- Other existing feature references continue to be authoritative as documented; introduce mapping in those features **when independent artwork is available**, without implying their adoption has already been completed.
