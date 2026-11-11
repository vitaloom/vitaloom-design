# Statistic — Standalone PNG asset catalog

**Asset directory:** `assets/statistic/` (**singular**), owned by the Statistics overview module in [`statistics/`](../../statistics/README.md). These eight independent PNG files are provided by the user in commits [2fbcbfc](https://github.com/vitaloom/vitaloom-design/commit/2fbcbfcd200895a6202fb88e62c2ff0d186be8d1) / [f152c19](https://github.com/vitaloom/vitaloom-design/commit/f152c19df06696bc150cf8878cfd0b02ea125d01). This catalog only documents existing files and does not create or redraw artwork.

## Illustration assets

| File | Visual role |
| --- | --- |
| [heart.png](heart.png) | Heart Rate graphic |
| [shoe.png](shoe.png) | Steps graphic |
| [blue_bottle.png](blue_bottle.png) | Water graphic |
| [sleeping_star_pillow.png](sleeping_star_pillow.png) | Sleep graphic |

## Graph-like and soft color assets

| File | Visual role |
| --- | --- |
| [pink_graph.png](pink_graph.png) | Pink trend-like graphic, suggested for Heart Rate artwork context |
| [pink_smooth.png](pink_smooth.png) | Pink ambient/soft color layer behind graphic |
| [green_graph.png](green_graph.png) | Green trend-like graphic, suggested for Steps artwork context |
| [green_smooth.png](green_smooth.png) | Green ambient/soft color layer behind graphic |

Treat `*_graph.png` as **static art** unless the design calls for a purely decorative accent. Production metric charts and values must be data-driven and accessible; a graph PNG cannot be passed off as recorded readings. Match its exact placement against each source screenshot when implementing; `pink`/`green` association is a suggested mapping based on visual category, pending FE QA.

**Import note:** transparent/isolated artwork is the intended usage; verify actual PNG alpha/background and content bounds before choosing React Native `Image` size/`resizeMode="contain"`. Do not infer measurements from pixels. Light/Dark may reuse the same illustration file and change the native card/ambient background instead of duplicating asset binaries.

## Documentation

- [Four screen references and mandatory Day order correction](../../statistics/README.md)
- [Per-screen roles, layering and status](../../statistics/ASSET_MAPPING.md)
- [Behavior/state contract](../../statistics/BEHAVIOR.md)
- [Machine-readable asset manifest](asset-manifest.json)
- [Global asset mapping rules](../../ASSET_MAPPING_STANDARD.md)

**Important:** The two Day screenshots have an incorrect section order. **All four variants** must render **Heart Rate → Steps → Water → Sleep**, with Sleep last. Day Sleep uses recorded feeling + text instead of the Week chart. No specific Day feeling PNG was uploaded to this folder; any reuse of Sleep Tracking feelings is conditional and should be visually validated.
