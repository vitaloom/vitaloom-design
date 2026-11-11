# VitaLoom Design

A public collection of UI design references and component specifications for VitaLoom.

## Shared design

- [Health Metrics Sidebar — component specification](shared/health-metrics-sidebar/README.md)
- [Sidebar: closed (default)](shared/health-metrics-sidebar/sidebar-closed.svg)
- [Sidebar: open](shared/health-metrics-sidebar/sidebar-open.svg)
- [Sidebar: active states](shared/health-metrics-sidebar/sidebar-active-states.svg)
- Existing assets: [Home](shared/home.png) · [Poster](shared/poster.png)

## Feature references

- [Water designs](water/)
- [Heart Rate — **analytics refresh** (light/dark + interaction)](heart-rate/README.md)
- [Steps — **analytics refresh** (light/dark + interaction)](steps/README.md)
- [Shared analytics UI patterns](shared/analytics-components/README.md)

## Usage

The designs in this repository are **visual and behavioral specifications**. Their presence does not mean the app has implemented reusable components. Frontend agents should implement an `AppShell`/navigation-drawer component in the app's own repository and keep feature content separate from shared navigation.

**Health Metrics Sidebar defaults to closed**. It opens via the menu button, overlays the current feature page, and closes via the close icon, backdrop tap, Escape/Back, or successful navigation. The sidebar is never copied into each individual metric feature image as an independent UI implementation.

SVG files are editable vector designs and can be previewed directly on GitHub. No phone frame, chalk border, fake connected-device status, ECG or realtime indicator is part of the shared component.

## Screen behavior and small assets

- [Screen behavior documentation standard](BEHAVIOR_STANDARD.md) — screen IDs, interaction contracts, UI states, navigation, and traceability.
- [Global screen-to-asset mapping standard](ASSET_MAPPING_STANDARD.md) — feature screens, standalone artwork, roles, ownership and implementation handoff.
- [Reusable visual assets](assets/README.md) — small icons, transparent illustrations, leaves, backgrounds; [shared assets](assets/shared/README.md) and [Water assets](assets/water/README.md).
- [Water screen catalog](water/README.md) and [Water behavior](water/BEHAVIOR.md) — links to the three existing Water PNG screens without moving or renaming them.

**Conventions:** Full-screen mockups stay next to their feature documentation; small reusable artwork goes in `assets/shared/` or `assets/<feature>/`. Existing Heart Rate and shared-sidebar specifications remain authoritative until deliberately standardized.

## Approved first-use and authentication designs

- [Introductory Onboarding — 4 approved screens](onboarding/README.md) · [Onboarding behavior](onboarding/BEHAVIOR.md) · [Onboarding asset mapping](onboarding/ASSET_MAPPING.md)
- [Authentication — 4 approved screens](authentication/README.md) · [Authentication behavior](authentication/BEHAVIOR.md)

**Flow:** Introductory Onboarding (4 slides) → Authentication welcome (Sign In / Create Account) → bottom-sheet form → authenticated app or optional first-time Personal Health Profile invitation. The Introductory Onboarding carousel is distinct from optional health-profile setup after account creation.

The approved screen artwork is stored as optimized WebP images with relative image links in each module. `BEHAVIOR.md` links visible interactions and navigation to stable Screen IDs and references canonical Business Rules, without inventing API contracts.

## Personal Health Profile

- [Personal Health Profile — 11 proposed screens](personal-health-profile/README.md) · [Behavior](personal-health-profile/BEHAVIOR.md) · [Asset mapping](personal-health-profile/ASSET_MAPPING.md) · [Reusable photorealistic hero](assets/personal-health-profile/README.md).

The realistic hero direction is user-selected; screen compositions remain `PENDING_VISUAL_ACCEPTANCE`. These are design references, not deployed frontend screens.

## Sleep Tracking UI baseline

- [Sleep Tracking — screen registry and selected design baseline](sleep-tracking/README.md) · [Behavior](sleep-tracking/BEHAVIOR.md) · [Asset mapping](sleep-tracking/ASSET_MAPPING.md) · [Expo handoff](sleep-tracking/FE_HANDOFF.md).
- **Available:** six selected screen PNGs, one overview, and nine independently generated transparent PNG assets are [committed](sleep-tracking/SCREEN_IMPORT.md); [asset catalog](assets/sleep-tracking/README.md) includes optional SVG fallbacks.

## Current analytics design baseline (Steps + Heart Rate)

**Implementation / BE readiness review:** [Agent handoff and compatibility audit checklist](AGENT_HANDOFF.md).

- [Steps — latest design and behavior](steps/README.md) · [canonical API/model links](steps/REFERENCES.md)
- [Heart Rate — latest design and behavior](heart-rate/README.md) · [canonical API/model links](heart-rate/REFERENCES.md)
- [Chart interactions + theme guidance](shared/analytics-components/README.md)

These design documents **do not duplicate Backend API schemas or database models**. Read canonical Backend and Business Docs linked from `REFERENCES.md` when implementing. Old Heart Rate MVP screens are [historical only](heart-rate/legacy/README.md).

**Review status:** Proposed light/dark vector implementations of the approved concept; BE compatibility and final visual sign-off are separate. This branch is for agent investigation and implementation, not an auto-approved merge.
