# Personal Health Profile — Screen-to-Asset Mapping

**Status:** `PROPOSED / PENDING_VISUAL_ACCEPTANCE`. This document implements the repository-wide [ASSET_MAPPING_STANDARD.md](../ASSET_MAPPING_STANDARD.md).

**Source of truth:** [screen catalog](README.md) · [screen behavior](BEHAVIOR.md) · [asset inventory](../assets/personal-health-profile/README.md) · [machine manifest](../assets/personal-health-profile/asset-manifest.json).

## Shared photorealistic profile hero

- **Asset:** [`profile-hero-photorealistic.png`](../assets/personal-health-profile/profile-hero-photorealistic.png).
- **Role:** Background/hero artwork. Smiling wellness subject and health clipboard on the **right**, spacious mint/cream region on the **left** for native title/body text. No text embedded in asset.
- **Ownership:** Feature-owned, `assets/personal-health-profile/`; proposed for reuse across the Personal Health Profile screens only.
- **Provenance:** Newly generated original photorealistic illustration selected in this conversation; not a screenshot crop or medical measurement.
- **Visual status:** User-selected visual direction; full-screen compositions remain pending final visual acceptance.

## Per-screen mapping

| Screen ID | Full-screen reference | Independent assets / roles | Visual status |
|---|---|---|---|
| `PHP-SCR-001` | [01-profile-setup-basics.png](./01-profile-setup-basics.png) | [profile hero](../assets/personal-health-profile/profile-hero-photorealistic.png) — background/hero | `PENDING_VISUAL_ACCEPTANCE` |
| `PHP-SCR-002` | [02-profile-setup-lifestyle.png](./02-profile-setup-lifestyle.png) | [profile hero](../assets/personal-health-profile/profile-hero-photorealistic.png) — background/hero | `PENDING_VISUAL_ACCEPTANCE` |
| `PHP-SCR-003` | [03-setup-validation-error.png](./03-setup-validation-error.png) | [profile hero](../assets/personal-health-profile/profile-hero-photorealistic.png) — background/hero | `PENDING_VISUAL_ACCEPTANCE` |
| `PHP-SCR-004` | [04-profile-overview.png](./04-profile-overview.png) | [profile hero](../assets/personal-health-profile/profile-hero-photorealistic.png) — background/hero | `PENDING_VISUAL_ACCEPTANCE` |
| `PHP-SCR-005` | [05-profile-overview-empty.png](./05-profile-overview-empty.png) | [profile hero](../assets/personal-health-profile/profile-hero-photorealistic.png) — background/hero | `PENDING_VISUAL_ACCEPTANCE` |
| `PHP-SCR-006` | [06-profile-edit.png](./06-profile-edit.png) | **Not provided** (no independent hero asset on this state) | `PENDING_VISUAL_ACCEPTANCE` |
| `PHP-SCR-007` | [07-edit-partial-save.png](./07-edit-partial-save.png) | **Not provided** (no independent hero asset on this state) | `PENDING_VISUAL_ACCEPTANCE` |
| `PHP-SCR-008` | [08-concurrent-update.png](./08-concurrent-update.png) | **Not provided** (no independent hero asset on this state) | `PENDING_VISUAL_ACCEPTANCE` |
| `PHP-SCR-009` | [09-profile-load-error.png](./09-profile-load-error.png) | **Not provided** (no independent hero asset on this state) | `PENDING_VISUAL_ACCEPTANCE` |
| `PHP-SCR-010` | [10-save-unconfirmed.png](./10-save-unconfirmed.png) | **Not provided** (no independent hero asset on this state) | `PENDING_VISUAL_ACCEPTANCE` |
| `PHP-SCR-011` | [11-profile-save-success.png](./11-profile-save-success.png) | [profile hero](../assets/personal-health-profile/profile-hero-photorealistic.png) — background/hero | `PENDING_VISUAL_ACCEPTANCE` |

## Composition contract for the six hero screens

1. Root UI gradient / warm cream surface is rendered natively.
2. Card container clips rounded corners; background image fills the card with `cover`, right-aligned/crop tuned per viewport so the woman’s face/clipboard remain visible.
3. Add a left-to-right mint-tinted fade **natively** where necessary to keep text readable. The left side is intentionally blank for content.
4. Draw heading, explanatory copy, step indicator and progress as native React Native `Text`/`View` elements **above** the image; never bake text into the poster or use screenshots as UI.
5. Forms, cards, alerts, buttons, modal sheets, app navigation and validation messages remain native interactive UI. Do not use fixed screenshot coordinates for those elements.

Asset natural size is 1792 × 1024 px (wide landscape); actual rendered hero container is responsive. Respect safe areas and accessible text scaling. Decorative visual content is not itself user profile data.

## No-hero states

`PHP-SCR-006/007/008/009/010` deliberately render no shared hero and require no placeholder artwork. This preserves the high information density of edit/error/decision states.

## Implementation / review checklist

- [x] Every Screen ID maps to an existing reference PNG in the feature directory.
- [x] Exactly six screens reference the same real reusable asset (no duplicated hero binaries).
- [x] Background path resolves relative to the feature directory; manifest and Markdown agree.
- [ ] Confirm right-image clipping and left text legibility in Expo on compact and tall phones.
- [ ] Confirm accessibility and contrast at increased font sizes.
- [ ] Explicit visual approval of full-screen compositions.
- [ ] Update production FE static asset references and verify Metro `require` map.

**Scope:** This asset map does not override Business Rules or define API interactions.