# Changelog

All notable changes to Lorde OS are documented here. The format follows Keep a Changelog and the project uses semantic versioning.

## 1.0.1, 2026-11-09

First public release of Lorde OS, published with a proper release signature.

### Packaging and signing

- Release builds are signed with a dedicated Lorde Studios release key instead of the shared debug key. This removes a known trigger for the "signed with a debug key" Play Protect warning on sideloaded builds; a Play Protect notice can still appear for any app installed outside the Play Store.
- The full build keeps `targetSdk` at 28 by design. Executing the Wine, Box64 and Linux userspace binaries from the app's private storage is only permitted for apps targeting API 28 or lower on modern Android; targeting 29 or newer moves the process into a stricter SELinux domain where every extracted binary fails to launch. The same constraint keeps Termux and Winlator at API 28. Foreground services declare explicit service types anyway so the code is ready for future target changes, and the notification permission is requested when the user asks for an update check.
- The companion build supports Android 7.0 (API 24) and newer. The full build requires Android 7.1 (API 25) because its bundled graphics backend requires API 25.
- The companion build ships generated launcher icons (regular and round). The full build keeps its vector launcher icon.

### Developer environment

- The developer environment now bundles every pinned package inside the APK, so activation works fully offline and no longer depends on the Termux repository keeping old versions published. Fresh installs previously failed activation with "Bootstrap download failed with HTTP 404" when the repository removed five pinned packages.
- Five packages (libc++, libiconv, libxml2, ndk-sysroot, zlib) were repinned to the currently published versions; all 44 packages are verified by SHA-256 at activation.

### Settings

- Fixed duplicated settings rows. The Recovery and Developer sections re-rendered themselves on top of the existing content after an action, so every "Check now" or runtime operation appended a second copy of the section.
- Added a real update check. Settings, Recovery, Check for updates queries the public LordeStudios/LordeOS releases on GitHub, compares the result with the installed version, shows the outcome in place and posts a notification when a newer version has been published.
- The bundled runtime update is now its own entry, "Update bundled runtime", so the two operations are no longer conflated under one label.

### Known limitations

- Long form application workflows (for example a full Blender render, save and reload round trip), strong game benchmarks, final Wine link routing, recovery flows and embedded browser routing are still being verified on physical hardware.
