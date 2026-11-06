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
- [Heart Rate screen — two metrics and UI states](heart-rate/README.md)

## Usage

The designs in this repository are **visual and behavioral specifications**. Their presence does not mean the app has implemented reusable components. Frontend agents should implement an `AppShell`/navigation-drawer component in the app's own repository and keep feature content separate from shared navigation.

**Health Metrics Sidebar defaults to closed**. It opens via the menu button, overlays the current feature page, and closes via the close icon, backdrop tap, Escape/Back, or successful navigation. The sidebar is never copied into each individual metric feature image as an independent UI implementation.

SVG files are editable vector designs and can be previewed directly on GitHub. No phone frame, chalk border, fake connected-device status, ECG or realtime indicator is part of the shared component.
