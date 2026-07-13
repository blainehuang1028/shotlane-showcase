# Architecture overview

This document describes Shotlane at a system-boundary level. It intentionally omits production source code, private implementation details, signing material, and build instructions.

## Design goals

Shotlane is designed around four constraints:

1. Capture should feel immediate and remain responsive while the selection changes.
2. Annotation should be editable instead of producing irreversible pixels too early.
3. OCR, color analysis, and export should run locally.
4. Windows, overlays, permissions, shortcuts, and menus should behave like native macOS surfaces.

## Major boundaries

```text
Global shortcut / menu command
            │
            ▼
     Capture coordinator
      ├── region or window selection
      ├── full-display capture
      ├── stitched scrolling capture
      └── screen color sampling
            │
            ▼
   Editable capture workspace
      ├── selection geometry
      ├── annotation object model
      ├── local OCR
      └── pinned-reference presentation
            │
            ▼
       Local export pipeline
      ├── clipboard
      ├── user-selected folder
      ├── PNG / JPG / WebP / PDF
      └── completion notification
```

## Native macOS integration

The application combines SwiftUI for settings and product surfaces with narrow AppKit integration for overlays, input routing, window levels, native menus, and precise screen interaction. System frameworks provide screen capture, text recognition, accessibility-aware scrolling, pasteboard access, notifications, and permission status.

## Editable annotation model

Annotations remain structured objects while the editor is open. Selection, dragging, deletion mode, tool-specific handles, text editing, color changes, and rendering operate on the same model. Rasterization happens only when a final image or document is exported.

## Local-first data flow

Captured pixels are passed only between in-process capture, annotation, recognition, clipboard, and export components. User-selected folders are accessed through macOS-scoped permissions. No account, cloud workspace, or screenshot upload is required.

## Reliability approach

Release checks cover core logic, native app builds, localization surfaces, packaged resources, privacy declarations, sandbox entitlements, signing, symbols, and the real archive/export path. Public details stay intentionally high-level so this repository remains a showcase rather than a parallel source distribution.
