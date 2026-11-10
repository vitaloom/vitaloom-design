# Personal Health Profile — Reusable Artwork

This directory contains **one** original photorealistic, text-free, wide PNG banner for Personal Health Profile.

| Asset | Role | Source/art direction | Status |
|---|---|---|---|
| [profile-hero-photorealistic.png](profile-hero-photorealistic.png) | Background / hero | Photorealistic wellness subject + clipboard on right; mint/cream empty left for native text | `USER_SELECTED_VISUAL_DIRECTION`; screen compositions pending |

- [Per-screen mapping](../../personal-health-profile/ASSET_MAPPING.md) — `PHP-SCR-001`, `002`, `003`, `004`, `005`, `011` use this asset; other screens do not.
- [Manifest](asset-manifest.json) — explicit relative screen and asset paths.
- [Global standard](../../ASSET_MAPPING_STANDARD.md) — ownership, independent artwork and implementation rules.

The PNG must not contain app controls, user fields or editable text. Use `ImageBackground`/`expo-image` and overlay real React Native text; clip rounded hero cards, protect the subject while cropping, and let screen readers ignore purely decorative artwork. No medical or clinical claim is implied by the illustration.