# Development notes

Shotlane is built as a native macOS utility rather than a web wrapper. This public log records product-level engineering decisions without publishing the production implementation.

## Interaction work

- Capture actions use immediate, single-click hit targets with native command routing.
- Selection toolbars follow the capture region continuously and prefer the lower-right edge when space allows.
- Annotation objects can be selected, moved, deleted individually, and reopened for editing.
- Text annotations use a transparent editing surface, preserve the selected color, and support double-click editing.
- Color history distinguishes sampled screen colors from the fixed annotation palette.
- Escape consistently ends nested modes before dismissing the full capture overlay.

## Layout and localization

- The settings UI uses consistent card geometry across supported languages.
- Labels are allowed to wrap where needed instead of being clipped inside fixed-width buttons.
- English, Simplified Chinese, Japanese, Korean, and Spanish are treated as first-class interface languages.
- Light, dark, increased-contrast, and reduced-motion behavior are included in visual checks.

## Release discipline

- Core behavior is covered by unit tests and native app test targets.
- The packaged app is checked for localized resources, privacy declarations, third-party notices, and OCR model integrity.
- App Store archives are validated for sandbox entitlements, distribution signing, symbols, and exportability before upload.
- Website claims are kept aligned with features that exist in the release build.

## Why this repository is not buildable

The public repository is intentionally limited to product evidence, engineering summaries, and feedback. Keeping the production repository private avoids publishing proprietary interaction details while still making the product direction and engineering standards visible.
