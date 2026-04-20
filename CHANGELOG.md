# TuneBridge — Changelog

## [Unreleased]
<!-- Claude Code: add entries here as changes are made during development -->
<!-- Format: `- Fix:` / `- Add:` / `- Change:` / `- Remove:` -->

## v0.6-rc · 2026-04-20
- Fix: App crash (SIGSEGV in libmpv) during crossfade — eliminated use-after-free race between mpv property reads and instance teardown by holding locks for full read duration
- Add: Gear → DAP detail now includes “Sync All Playlists” to export all out-of-sync playlists in one action
- Add: Sync Music step 3 now includes out-of-sync playlist selection, allowing tracks and playlists to be synced in one workflow

## v0.6-rc · 2026-04-20
- Fix: AP80 sync scan now canonicalizes Unicode/diacritics/apostrophes in path matching to prevent false “present on device only” results (e.g. `Mötley` vs `Motley`, `C’mon` vs `Cmon`)

## v0.6-rc · 2026-04-20
- Fix: Playlist empty-state icon now renders centered in full-cover mode in both playlist grid and detail views
- Change: Increased empty-state SVG scale for playlist and album placeholders to better match card proportions

## v0.6-rc · 2026-04-20
- Add: Backend crossfade via dual mpv instances — EQ and crossfade now stay on the lossless mpv path instead of falling back to Web Audio
- Add: Gapless playback between tracks when mpv is active and exclusive mode is off
- Add: HI-RES badge tier — shows when exclusive mode is on with lossless source and DSP (EQ or volume change) active
- Add: Native macOS media key integration for Play/Pause, Next, and Previous controls
- Add: Dedicated Insights "Missing Tags" page with filterable track table and navigation from Tag Health
- Add: Bulk tag editing for missing metadata (multi-select + batch apply for artist/album/album artist/year/genre)
- Change: Crossfade no longer forces a switch to the Web Audio API — lossless output is preserved throughout
- Change: Web Audio AudioContext now matches the source sample rate to avoid browser resampling of hi-res files
- Change: Playlist empty-state art now uses the square add icon style and larger placeholder visual scale
- Change: Empty-state artwork icons across album/artist/song/playlist are larger for improved readability
- Fix: Media key Next/Previous handling on macOS by supporting additional hardware key mappings and safer dispatch fallback
- Fix: Playlist empty cover fallback now renders consistently in playlist grid/detail contexts
- Fix: Insights tag health year coverage and missing-tags workflow reliability
- Fix: Genre normalization now treats naming variants consistently (e.g., Hip-Hop/Hip Hop, Nu-Metal/Nu Metal) across analysis paths

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
