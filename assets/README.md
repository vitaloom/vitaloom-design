# UI assets — VitaLoom Design

This directory stores **small, reusable visual parts used inside application screens**, not full-screen mockups. See the [global asset mapping standard](../ASSET_MAPPING_STANDARD.md) for how each owning screen references these parts.

## Folder convention

- [shared/](shared/): brand marks, decorative leaves, common illustrations, reusable icons and backgrounds shared across features.
- [onboarding/](onboarding/): transparent welcome/track/habits/progress heroes and legacy per-screen landscape SVG fallbacks; the active landscape is a shared six-piece PNG composite with screen-level manifest.
- [water/](water/): water bottles, drops, water banner artwork and other water-only UI pieces.
- For future modules, create `assets/<feature>/` **when the first actual asset is added**; do not create empty placeholder folders.

## What belongs here?

| Put in `assets/` | Keep in a feature screen folder |
| --- | --- |
| Transparent bottle PNG, water drop SVG, leaf decorations, illustrative icon, custom badge | Whole Water landing screen PNG |
| Reusable background/wave texture, app brand mark | Whole Login / Signup artboard |
| Feature-specific illustration exported separately | Whole Heart Rate default/error/loading screen SVG |

**Rule:** full-screen design images remain next to the owning feature's `README.md` and `BEHAVIOR.md`, such as `water/water-intake-tracking.png`. Do not confuse a screenshot/mockup with an app asset.

## Naming and formats

- Prefer descriptive, ASCII, kebab-case names: `water-bottle-mint.png`, `leaf-cluster-left.png`, `health-wave-bg.svg`.
- Prefer `SVG` for vector shapes/icons and `PNG` with transparency for cut-out raster illustrations; use `WebP` only if supported by the intended app workflow.
- Avoid spaces, diacritics, `final-v2` suffixes, duplicate exports and opaque names such as `image-123.png`.
- Store only assets with rights suitable for project use; never commit fonts or unrelated stock images.
- Track large files, repeated variants and source links carefully. Design mocks are visual references, **not runtime UI code**.

## Referencing assets in Markdown

From `water/README.md` or `water/BEHAVIOR.md`, use **relative links** to existing assets in this folder, e.g.:

```md
![Water bottle](../assets/water/water-bottle-mint.png)
![Shared leaf](../assets/shared/leaf-cluster-left.png)
```

These names are examples of future files, not assets already committed. Add links only when the corresponding files exist. From the repository root, prefix with `assets/`.

## Ownership and reuse

- If an image is reused across multiple screens or features, prefer `assets/shared/` and link to it from both feature docs.
- If only one feature uses it, put it in `assets/<feature>/`.
- Do not duplicate identical binary files across folders.
- When a feature has independent artwork, maintain a screen-to-asset mapping under `<feature>/ASSET_MAPPING.md` and link it from feature README/behavior documents, following [ASSET_MAPPING_STANDARD.md](../ASSET_MAPPING_STANDARD.md).
- Do not create placeholder mappings or claim visual approval for new art merely because a full-screen mockup is approved. Functional controls stay native UI.

See [BEHAVIOR_STANDARD.md](../BEHAVIOR_STANDARD.md) for screen interaction documentation.
