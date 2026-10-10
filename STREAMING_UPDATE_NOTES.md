# AK TV streaming / programme guide update

## API integration
- Channel directory: `GET https://livetgtv.lovable.app/api/public/channels`
- Fresh playback resolution immediately before starting a channel: `GET /api/public/channels/{id}`
- Programme guide: `GET /api/public/guide/{id}`

## Changes
- Reads every playback source returned by the channel resolver instead of assuming only `sources[0]` will work.
- Uses Media3's media-source detection and explicitly recognizes `.mpd` (DASH) and `.m3u8` (HLS) URLs. Added the Media3 HLS module.
- Preserves ClearKey DRM support when the API returns a `drm` object.
- If a source fails, advances to the next returned source rather than re-fetching and retrying the same URL indefinitely.
- Adds current and next programme titles/times to the player info overlay.
- Loads programme details for channels shown in the channel guide and caches them in memory for the session.

## Validation status
- XML resources parse successfully.
- This environment did not have the Gradle wrapper JAR or a Gradle installation, so a complete Android build and real TV-device playback test could not be run here. Build and test on an Android SDK/Gradle environment before distributing an APK.
