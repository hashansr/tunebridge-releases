# TuneBridge — Changelog

## [Unreleased]
<!-- Claude Code: add entries here as changes are made during development -->
<!-- Format: `- Fix:` / `- Add:` / `- Change:` / `- Remove:` -->

## v0.6-rc · 2026-04-20
- Add: Backend crossfade via dual mpv instances — EQ and crossfade now stay on the lossless mpv path instead of falling back to Web Audio
- Add: Gapless playback between tracks when mpv is active and exclusive mode is off
- Add: HI-RES badge tier — shows when exclusive mode is on with lossless source and DSP (EQ or volume change) active
- Change: Crossfade no longer forces a switch to the Web Audio API — lossless output is preserved throughout
- Change: Web Audio AudioContext now matches the source sample rate to avoid browser resampling of hi-res files

## v0.5-rc · 2026-04-19

## v0.5-rc · 2026-04-19

## v0.5-rc · 2026-04-19

## v0.5-rc · 2026-04-19
- Fix: bash 3.2 incompatibility in build script (replaced ^^ with tr)
- Add: CHANGELOG.md published to tunebridge-releases with every DMG build
- Add: Release notes prompt during interactive build menu

## v0.4-dev · 2026-04-19
- Fix: Version display showed "unknown" in bundled app — version.json now bundled via PyInstaller
- Fix: All app modes (dev server + built app) now share the same App Support database — no more missing favourites/listening history
- Fix: App no longer errors with "Another TuneBridge instance" when a server is already running on port 5001
- Add: Update channel picker (Dev / RC / Prod) in Settings → App
- Add: In-app update check — shows available version, auto-checks on channel switch
- Add: Channel-aware update checks and downloads (each channel has its own version file and DMG)
- Add: Interactive build menu — run `bash build_app.sh` with no flags for a numbered prompt
- Add: All DMG builds (dev/rc/prod) now publish to tunebridge-releases with per-channel filenames
- Add: version_full field in version.json (e.g. 0.4-dev, 0.4-rc, 0.4)

## v0.3-prod · 2026-04-19
- Initial versioned release
- Build channels: dev / rc / prod auto-detected from git branch and tag
- Distributable DMG via PyInstaller with bundled Python deps
