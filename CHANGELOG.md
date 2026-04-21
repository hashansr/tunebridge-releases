# TuneBridge — Changelog

## [Unreleased]
<!-- Claude Code: add entries here as changes are made during development -->
<!-- Format: `- Fix:` / `- Add:` / `- Change:` / `- Remove:` -->

## v0.11-rc.220426-0741 · 2026-04-22

## v0.10-rc.210426-2136 · 2026-04-21

## v0.9-rc.210426-2125 · 2026-04-21

## v0.8-rc.210426-1554 · 2026-04-21

## v0.7-rc.210426-1531 · 2026-04-21

## v0.6-rc.210426-1508 · 2026-04-21

## v0.6-rc · 2026-04-21
- Fix: Songs table header/data alignment issue by removing duplicate Genre cell and restoring correct column order (Time/Favourite/Genre/Year)
- Change: Track-table row action hover states are now icon-color only (blue for standard actions, red for delete) with no circular hover background
- Fix: Table headers now consistently use single-line labels to prevent wrap-related drift and readability regressions
- Fix: Album Detail multi-disc grouping now recognizes additional disc metadata aliases and filename/path multi-disc patterns for more reliable per-disc table rendering
- Add: Album Detail column chooser now exposes the full ID3/audio column set (matching Songs), including Disc #, Album Artist, Format, Bitrate, Sample Rate, Bit Depth, Date Added, and Filename
- Fix: Album Detail multi-disc section heading (`Disc N`) spacing and typography for cleaner separation above each disc table
- Fix: Album Detail multi-disc tables now use per-disc horizontal scroll wrappers to prevent header/data overlap when many columns are enabled
- Fix: Album Detail track tables now use responsive wide-table sizing (`max-content` + horizontal scroll) to avoid column compression with extended ID3 fields
- Fix: Library scanner now extracts Disc # metadata for FLAC/MP3/M4A/WAV and persists it in SQLite, so `Disc #` column and album disc grouping are driven by actual tags (with path heuristics as fallback)
- Add: Core tabular views now support drag-to-resize column widths from table headers, with per-table width persistence
- Change: Table cell content in core library/playlist/favourites track tables is now left-aligned for consistent readability
- Change: Table column visibility is now stored per view context (Songs, Album/Artist Detail, Playlist, Favourite Songs) to support view-specific defaults and behavior
- Change: Album Detail first-load visible columns are now: Track #, Title, Artist, Album, Genre, Favourite, Actions
- Fix: Album Detail disc grouping now prioritizes true `disc_number` metadata values before path/folder fallback; disc headings updated to match app typography scale/style
- Fix: Album Detail track tables now use the same responsive width behavior as Songs (`max-content` + `min-width:100%`) so table width adapts when columns are shown/hidden

## v0.6-rc · 2026-04-21

## v0.6-rc · 2026-04-21

## v0.6-rc · 2026-04-21
- Change: Table column control is now an icon-only button that matches the app’s compact toolbar style
- Fix: Column selector popover now repositions to stay inside the viewport (prevents right-edge cutoff on album detail)
- Fix: Column selector now shows context-relevant columns per table, so toggles apply predictably in Album Detail, Songs, Playlist, and Favourite Songs views
- Add: Album Detail table now separates multi-disc albums with `Disc N` divider rows when sorted by track number
- Add: Songs table column selector now includes additional ID3/audio fields: Disc #, Format, Bitrate, Sample Rate, Bit Depth, Date Added, and Filename
- Change: Album Detail layout tightened by reducing vertical gap between hero section and table controls
- Change: Multi-disc Album Detail now renders dedicated per-disc tables (`Disc 1`, `Disc 2`, etc.) while single-disc albums keep the current single-table layout
- Fix: Album Detail row actions are now consistently visible (with hover emphasis) to avoid missing action controls
- Change: Added explicit `Actions` header label across core song/track tables globally
- Fix: Multi-disc Album Detail grouping now uses stronger detection (disc tag + folder-aware fallback) so multi-disc albums reliably split into per-disc tables
- Fix: Player startup now always enters paused state on launch (prevents unintended auto-play after fresh build/session restore)
- Fix: Suppressed restore-time playback error toast when a restored/preloaded track is inaccessible at startup

## v0.6-rc · 2026-04-21
- Add: Songs table now includes inline `Edit tags` action icon for quicker metadata updates
- Add: New shared `Columns` visibility picker for Songs, Tracks, Playlist Detail, and Favourite Songs tables (persisted per user)
- Change: Songs/Favourites/Actions table headers are streamlined (no redundant text on icon-only action columns)
- Fix: Prevent header label wrapping on core track tables for cleaner, stable table layout

## v0.6-rc · 2026-04-21
- Change: Missing Tags editor now uses the universal navigation back flow and removes the duplicate in-page back button
- Add: Inline per-row tag editing in Missing Tags table with in-place save for missing fields (title/artist/album/year/genre)

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
