# TuneBridge — Changelog

## [Unreleased]
<!-- Claude Code: add entries here as changes are made during development -->
<!-- Format: `- Fix:` / `- Add:` / `- Change:` / `- Remove:` -->

## v0.29-rc.230426-1742 · 2026-04-23

## v0.28-rc.230426-1547 · 2026-04-23
- Fix: ReplayGain tagger no longer deadlocks at 0% on cancel+restart; removed the I/O semaphore that caused new threads to block indefinitely waiting for a cancelled thread still inside sf.read()

## v0.27-rc.230426-1525 · 2026-04-23

## v0.26-rc.230426-1519 · 2026-04-23
- Fix: ReplayGain tagger now skips M4A/AAC files (and other formats soundfile cannot decode) entirely — they no longer appear in the track count or progress, preventing the tagger from stalling at 0%

## v0.25-rc.230426-1510 · 2026-04-23
- Fix: ReplayGain tagger "Tag Missing Tracks" button is now disabled while tagging is in progress, preventing accidental double-starts
- Fix: Clicking Cancel during ReplayGain tagging now immediately hides the progress banner
- Fix: ReplayGain tagger no longer stalls at "1 of N" after a cancel+restart; a global I/O semaphore serialises file reads so a still-running cancelled thread cannot starve the new thread's drive access

## v0.24-rc.230426-1441 · 2026-04-23
- Fix: Startup mute restore now requires explicit user mute intent (`muteExplicit`) before applying persisted `muted=true`; stale legacy mute flags no longer force muted startup on new RC launches.
- Fix: App shutdown now hard-stops playback on both window `closing` and `closed` events, with a macOS failsafe exit timer, preventing audio from continuing after the window is closed.
- Fix: Home → Jump Back In now resolves cards against current library metadata after tag edits/renames, preventing stale artist/album values and dead/blank navigation targets.
- Fix: Tag edit APIs now invalidate Home + metadata caches immediately so Home rails refresh with updated artist/album values without waiting for cache TTL.
- Fix: Artist tag edits now auto-update `album_artist` when both previously matched, so Home rails (Jump Back In/Recently Added) stop showing stale old-artist album cards.
- Fix: Home album cards now include a fallback `track_id` resolution path, so opening/playing cards still works even if artist/album labels changed after metadata edits.
- Change: Home → Listening Stats redesigned to match the new compact card-grid layout (hero + plays/albums/artists + top artist/album/track + days active/top genre) using current design system styling.
- Change: Home → Listening Stats listening time is now displayed in minutes (`min`) for all periods.

## v0.23-rc.230426-0854 · 2026-04-23
- Add: In-app ReplayGain tagger — Settings → Library now shows tag coverage (X of Y tracks tagged) and a "Tag Missing Tracks" button that measures EBU R128 loudness and writes REPLAYGAIN_* tags directly to FLAC, MP3, and M4A files in the background; audio streams are never re-encoded
- Add: ReplayGain tagging runs as a cancellable background task with live progress bar; tracks are grouped by album so album gain is computed accurately alongside track gain
- Add: After a library scan completes, a toast notification appears if any tracks are missing ReplayGain tags, with a prompt to tag them in Settings
- Add: pyloudnorm dependency added to requirements.txt and PyInstaller build for .app / DMG packaging

## v0.22-rc.230426-0832 · 2026-04-23

## v0.21-rc.230426-0808 · 2026-04-23
- Add: Gapless playback — next track is pre-buffered into the standby audio element while the current track plays; when crossfade is off, tracks transition with zero gap or silence
- Add: ReplayGain support — reads REPLAYGAIN_TRACK_GAIN / REPLAYGAIN_ALBUM_GAIN / REPLAYGAIN_TRACK_PEAK / REPLAYGAIN_ALBUM_PEAK tags from FLAC, MP3, and M4A files during library scan
- Add: ReplayGain mode toggle (Off / Track / Album) in the PEQ popover; gain applied via Web Audio GainNode — lossless float32 multiplication, no re-encoding; clipping guard ensures output never exceeds measured peak
- Change: DB schema v4 — four new nullable ReplayGain columns added to tracks table; existing libraries migrated automatically on startup

## v0.20-rc.220426-1457 · 2026-04-22
- Fix: Insights Sonic Profile analysis banner no longer re-appears on every navigation after a successful run; it shows for 10s after completion then stays hidden until the user explicitly triggers a new analysis
- Fix: Analysis error state now stays persistent (no auto-hide) until a successful run clears it

## v0.19-rc.220426-1310 · 2026-04-22

## v0.18-rc.220426-1146 · 2026-04-22

## v0.17-rc.220426-1138 · 2026-04-22

## v0.16-rc.220426-1120 · 2026-04-22

## v0.15-rc.220426-1027 · 2026-04-22

## v0.14-rc.220426-0937 · 2026-04-22

## v0.13-rc.220426-0914 · 2026-04-22

## v0.12-rc.220426-0848 · 2026-04-22
- Add: Insights Tag Health now includes a Track # completeness pill alongside Title, Artist, Album, Year, and Genre
- Change: Insights Sonic Profile now shows Library Tonal Demand chart before the Spectral Centroid and Dynamic Energy histograms
- Change: Insights Sonic Profile histogram charts renamed to Spectral Centroid Distribution and Dynamic Energy Distribution with explanatory subtitles; RMS stat row now shows relative spread percentage instead of raw floats
- Change: Insights IEM match scores now include a small modifier (max 8%) from the 5 derived dimensions (soundstage, timbre, masking, layering, tonality), making the list scores consistent with the radar chart
- Change: Insights Library Overview stat card badges updated to Music Library, Unique Albums, Unique Artists, and Genre Distribution; section description removed as self-explanatory
- Change: Insights IEM match section description rewritten; score legend (green/amber/red thresholds) added above IEM list; Blindspot Detector renamed to Weak Genre Coverage
- Fix: Removed all em dashes from user-facing Insights copy
- Fix: Tag Health card footer gap tightened; section description formatting cleaned up
- Change: Insights IEM detail FR chart controls reordered to Source, Genre overlay, PEQ, Overlays for a more natural flow
- Fix: Insights → Edit Missing Tags row save now accepts Track # inline edits (including `N/M` format) and correctly keeps Track # in missing-tag validation
- Change: Unified global page rail alignment so back button uses equal top/left inset and Home/Insights/Gear content aligns to the same left gutter as back navigation
- Change: Refined global nav spacing: back-button top/left rail now targets ~25px on desktop, with larger gap between back button and page titles for cleaner hierarchy
- Change: Finalized app-wide nav/content spacing to match UI spec: 15px back-button top/left inset, 15px back-button-to-title vertical gap, and 35px content left inset
- Change: Applied 15/15/35 nav spacing tokens globally across Home, Insights, Gear, and shared views so back navigation and content rail stay visually consistent
- Fix: Startup restore now remains paused until user intent; restore-time file-load errors are muted (no playback-error toast / auto-skip on launch)
- Fix: Album Detail `Track #` sort now prioritizes explicit disc tags and avoids conflicting path-based disc heuristics when disc tags are present
- Fix: Album Detail sort logic now applies disc ordering only for true multi-disc albums; single-disc/no-disc albums sort as one flat table by the selected column/order
- Change: Sync Music Step 3 playlists section now supports the same collapse/expand accordion behavior as track sections
- Change: Increased Player PEQ popover surface opacity/contrast (panel + controls) for better readability over artwork backgrounds
- Fix: Hardened queue handoff between collections by clearing standby prebuffer on Play All/collection shuffle and validating gapless standby source before swap (prevents wrong-track playback/UI mismatch)
- Fix: Player startup mute restore now parses persisted booleans safely (e.g., string `\"false\"` no longer restores as muted); first launch defaults to unmuted unless last state explicitly saved mute on
- Fix: Album Detail `Track #` sort now prioritizes explicit disc tags and avoids conflicting path-based disc heuristics when tags are present (prevents incorrect mixed ordering)

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
