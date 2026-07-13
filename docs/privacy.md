# Privacy model

Shotlane is local-first by design. Its core screenshot workflow does not require an account or remote service.

## Data that stays on the Mac

- Screenshot pixels and annotations
- OCR input and recognized text
- Sampled colors and recent color history
- Clipboard output
- Window titles used during local selection
- Save locations, filenames, and cleanup preferences
- Shortcut configuration and local diagnostic records

Shotlane does not include product analytics, advertising identifiers, telemetry, remote crash reporting, or screenshot sync.

## Permissions

Shotlane requests macOS permissions only when a feature needs them:

- **Screen Recording** enables screen and window capture.
- **Accessibility** enables stitched scrolling capture by controlling the active scrollable surface.
- **Notifications** are optional and confirm completed local actions.
- **Folder access** is limited to locations the user selects.

The application explains permission-dependent behavior before directing the user to System Settings. Declining an optional permission does not upload data or create an account requirement.

## OCR

Text recognition runs locally using Apple Vision or an on-device recognition engine bundled with the app. Images and recognized text are not sent to a hosted OCR API.

## Public policy

The current user-facing privacy policy is available at [shotlane.vercel.app/privacy](https://shotlane.vercel.app/privacy/).
