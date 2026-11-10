# Standard — Screen Behavior Documentation

**Purpose:** Define what a person can do on a designed screen, what feedback they see, how the screen changes and where they go next. Keep this contract close to its **actual image** in the same feature directory.

## 1. Folder and file ownership

```text
vitaloom-design/
├── BEHAVIOR_STANDARD.md          # This common convention
├── assets/                       # Small reusable UI imagery
│   ├── shared/                   # Shared visual elements
│   └── water/                    # Water-only images/icons
├── water/
│   ├── README.md                 # Screen catalog and references
│   ├── BEHAVIOR.md               # Feature-screen interactions
│   ├── water-intake-tracking.png # Full-screen design
│   ├── chi tiết nhập nước.png    # Full-screen design
│   └── tiến độ nước.png          # Full-screen design
├── heart-rate/
│   └── README.md                 # Existing combined behavior & UI spec
└── shared/                       # App-shell designs and contracts
    └── health-metrics-sidebar/
        └── README.md
```

- `README.md` is the directory's discovery page and screen inventory.
- `BEHAVIOR.md` is a feature's interaction contract for small/medium features; for a complex feature, use `behavior/<screen-id>.md` files with `BEHAVIOR.md` as the index.
- Keep full-screen references in the feature folder. Place small reusable icons, transparent PNG cutouts, illustrations and decorative backgrounds under [`assets/`](assets/README.md).
- No migration of existing artwork is necessary. Never duplicate the shared drawer's behavior inside a feature.

## 2. Authority and status

| Source | Responsible for |
| --- | --- |
| Feature `BEHAVIOR.md` | Triggers, visible feedback, navigation, UI states, interaction accessibility |
| Business Use Cases / Business Rules | Domain validation, eligibility, data rules, constraints, conflicts |
| Backend API contract | Actual endpoints, request/response and error schema |
| Frontend source | Concrete routes, components, persistence of UI state |

Approved business rules and API contracts take precedence over image text or draft UX behavior.

Use **CONFIRMED** only for behavior backed by an approved specification or user-approved explicit design decision; **PROPOSED** for UX recommendations awaiting acceptance; **OPEN** for missing decisions. Include evidence links/IDs where possible.

## 3. IDs and relative links

- Give screens stable IDs such as `WAT-SCR-001`, actions IDs such as `WAT-ACT-001`. Never use the image filename as a permanent ID.
- Link real screen images relatively: `[Water landing](./water-intake-tracking.png)`.
- For the existing non-ASCII filenames, use percent-encoded Markdown URLs. Do not rename the images in this PR.
- Link cross-feature destinations by screen/document if it exists; otherwise mark that target `OPEN`.
- Link small imagery only if it actually exists: e.g. `../assets/water/water-bottle-mint.png` after that file is uploaded.

## 4. Required BEHAVIOR.md sections

1. Scope/status, canonical BR/UC and other references.
2. **Screen registry:** stable ID, full-screen image, entry conditions and exit.
3. **Navigation flow:** source screen, action, target screen/overlay and any condition.
4. **Interaction contract:** action ID, UI element, trigger, feedback, successful/alternate/error outcome.
5. **UI states:** default, selection, loading, empty, success, validation error, network error. Link state images when they exist.
6. **Validation and recovery:** reference authoritative domain rules; define how the UI displays and recovers.
7. **Accessibility:** labels, screen reader state, keyboard/back handling, touch targets and contrast.
8. **Acceptance checklist:** observable pass/fail examples tied to action IDs.
9. Open decisions, change log and optional **Visual asset mapping** to `assets/`.

## 5. Sample interaction table

| Action ID | Screen / control | Trigger | Immediate UI behavior | Result | Status / source |
| --- | --- | --- | --- | --- | --- |
| `ABC-ACT-001` | `ABC-SCR-001` / Detail | Tap | Start navigation | Open `ABC-SCR-002` | PROPOSED |
| `ABC-ACT-002` | `ABC-SCR-002` / Save | Submit valid form | Show pending state and prevent duplicate save | Success → `ABC-SCR-001`; error → retain form with retry | PROPOSED |

## 6. Validation checklist for design changes

- [ ] Every screen ID points to an existing, clickable local image.
- [ ] Every visible action has a trigger, immediate feedback, target and error outcome as relevant.
- [ ] Navigation is described by intended screen IDs, not hard-coded guessed app routes.
- [ ] Distinguish **empty data** from **loading** and **network/server failure**.
- [ ] Proposed UX is not mislabeled an approved business rule.
- [ ] Shared components are linked rather than duplicated.
- [ ] Icons/backgrounds and feature screenshots go in their intended directories.
- [ ] Docs do not claim that a design image equals implemented or tested frontend behavior.

## 7. Adopted references

- [Onboarding — four approved first-launch screens](onboarding/BEHAVIOR.md)
- [Authentication — welcome, sign in, sign up and profile invitation](authentication/BEHAVIOR.md)
- [Water — screen registry and interaction contract](water/BEHAVIOR.md)
- [Heart Rate — existing combined design specification](heart-rate/README.md)
- [Shared sidebar — existing interaction contract](shared/health-metrics-sidebar/README.md)
- [Small/reusable assets policy](assets/README.md)

This convention does **not** introduce new business requirements or API contracts.
