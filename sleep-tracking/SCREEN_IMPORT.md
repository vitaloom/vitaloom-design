# Sleep Tracking — Approved PNG import (pending)

**Current status:** The user selected the six-screen visual baseline and separately generated original transparent PNG assets. These binary images are available in the ChatGPT conversation workspace, but this GitHub connector route cannot transfer those local raster file bytes directly. The PR therefore contains **no claim** that these PNGs have already been uploaded. Keep the approved images unchanged.

## Target repository paths

Full-screen screenshots go next to their feature docs:

```text
sleep-tracking/
  00-sleep-design-overview.png
  01-sleep-home.png
  02a-sleep-entry-time-range.png
  02b-sleep-entry-duration-only.png
  03-sleep-insights.png
  04-ai-insight-detail.png
  05-ai-weekly-sleep-story.png
```

Original, independently generated transparent assets live under feature assets:

```text
assets/sleep-tracking/
  moon-cloud-stars.png
  sleep-cloud.png
  pillow-stars.png
  star-smiling.png
  feeling-comfortable.png
  feeling-normal.png
  feeling-tired.png
  trend-up.png
  bars.png
```

Use the exact PNG source from the conversation package. These are new standalone artworks, **not masked screenshot crops**. The committed `icons/*.svg` are **optional PROPOSED fallback icons**, not substitutes for the approved generated PNG imagery.

## Completion gate

1. Upload exact binary assets to the paths above without changing dimensions/alpha.
2. Validate PNG magic signature and that all nine standalone artwork files have an alpha channel. The full screen PNGs may be opaque.
3. Verify each relative path resolves under the PR branch.
4. Convert filename-only references in README and ASSET_MAPPING into clickable relative Markdown image links.
5. Update `screen-manifest.json` / `asset-manifest.json` status only **after** the corresponding files exist, then run the mapping checklist.
6. Review with product owner that PNGs match selected visual baseline and that alternate-state visuals are still pending.

Never merge an unverified placeholder screenshot or claim that a local ZIP proves the GitHub file exists.
