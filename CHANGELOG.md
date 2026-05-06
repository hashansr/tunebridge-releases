# TuneBridge — Changelog

## [Unreleased]
<!-- Claude Code: add entries here as changes are made during development -->
<!-- Format: `- Fix:` / `- Add:` / `- Change:` / `- Remove:` -->

## v0.125-rc.060526-1545 · 2026-05-06

## v0.124-rc.060526-1529 · 2026-05-06

## v0.123 · 2026-05-06

## v0.123 · 2026-05-06

## v0.122-rc.060526-1434 · 2026-05-06

## v0.121-rc.060526-1318 · 2026-05-06

## v0.120-rc.060526-1133 · 2026-05-06

## v0.119-rc.060526-1109 · 2026-05-06

## v0.119-rc.060526-0936 · 2026-05-06

## v0.118-rc.060526-0931 · 2026-05-06

## v0.117-rc.060526-0925 · 2026-05-06

## v0.116-rc.060526-0915 · 2026-05-06

## v0.115-rc.060526-0856 · 2026-05-06

## v0.114-rc.060526-0831 · 2026-05-06

## v0.113-rc.050526-1528 · 2026-05-05
- Fix: Sync modal no longer stalls at Step 2 (scanning) — `_syncScannedAt` was used but never declared, causing a ReferenceError that prevented the preview phase from loading

## v0.112-rc.050526-1524 · 2026-05-05

## v0.111-rc.050526-1511 · 2026-05-05

## v0.110-rc.050526-1509 · 2026-05-05
- Fix: Sync manifest no longer updated at scan time for files queued for copy — prevents failed copies from being silently marked as synced on the next scan
- Fix: Device→local copy now skips files where a different local file already exists at the destination path, with a clear error instead of a silent overwrite
- Fix: Path collision warnings now name all colliding local tracks and the winning track's reason notes the collision, instead of a generic warning with no track info
- Fix: Space pre-check before sync execute now re-stats source and destination files for fresh sizes, avoiding stale net-byte estimates from scan time
- Fix: sync_execute now validates that the requested DAP ID matches the scanned DAP, preventing a race where a second tab could trigger a copy to the wrong device
- Add: Device→local direction now has its own space check — selecting files to import from the DAP shows local disk free/needed and blocks sync if local storage is insufficient
- Fix: Dead duplicate sync function definitions removed (renderSyncPreview, syncSelectionChanged, executeSync, _syncApplySectionCollapse, toggleSyncSection, syncScanAgain, syncToggleAll)
- Fix: Sync modal "Scan Again" is now unblocked after a copy error — _syncScanInFlight was not being reset on error, requiring a modal close/reopen to retry

## v0.109-rc.050526-1441 · 2026-05-05

## v0.108-rc.050526-0906 · 2026-05-05

## v0.107-rc.050526-0840 · 2026-05-05

## v0.106-rc.050526-0828 · 2026-05-05

## v0.105-rc.050526-0826 · 2026-05-05

## v0.104-rc.050526-0822 · 2026-05-05
- Add: Home screen redesign — fixed 140px album art cards with centred play overlay, "Jump Back In" / "Listen Next" / "Recently Added" horizontal scroll rails, "See All" links, blue-gradient stats hero, inline dot-separated library summary
- Change: Home screen section spacing tightened (24px between sections), "Home" title enlarged to 28px/800 to distinguish from section headers
- Fix: First card in horizontal scroll rail no longer clips on hover due to scale transform

## v0.103-rc.050526-0803 · 2026-05-05

## v0.102-rc.050526-0753 · 2026-05-05

## v0.101-rc.050526-0749 · 2026-05-05

## v0.100-rc.050526-0737 · 2026-05-05

## v0.99-rc.040526-1914 · 2026-05-04

## v0.98-rc.040526-1857 · 2026-05-04
- Change: All table views (Tracks, Songs, Playlist, Favourite Songs, Edit Missing Tags) now render filter, sort, and column controls inside the table shell with a border-bottom separator — replaces the old separate pill-style toolbar above each table
- Add: Filter input added to the Tracks view and Favourite Songs view
- Add: Sort chips added to Tracks (#/Title/Album/Artist/Duration), Songs (Original/A–Z/Artist/Album/Year), and Favourite Songs (My Order/Recently Added/A–Z/Album) toolbars
- Change: Multi-disc albums render disc labels as inline section-header rows within a single table instead of separate tables per disc
- Fix: Filter clear button across all views now uses class-based visibility instead of inline display style

## v0.97-rc.040526-1617 · 2026-05-04

## v0.96-rc.040526-1600 · 2026-05-04

## v0.95-rc.040526-1511 · 2026-05-04
- Change: Tables across the web/macOS app now share a centralized TuneBridge table pattern for consistent row heights, headers, hover/selected states, toolbars, and column controls.

## v0.94-rc.040526-1447 · 2026-05-04
- Change: Page title typography and spacing now use shared TuneBridge title tokens across the web/macOS app for more consistent headers.

## v0.93-rc.040526-1404 · 2026-05-04

## v0.92-rc.040526-1354 · 2026-05-04

## v0.91-rc.040526-1330 · 2026-05-04

## v0.90-rc.040526-1316 · 2026-05-04

## v0.89-rc.040526-1250 · 2026-05-04
- Change: Left sidebar refreshed to the final minimal nav spec, with whitespace-separated groups, softer active states, promoted Sync Music CTA, and redesigned Library Status/Scan footer

## v0.88-rc.040526-1210 · 2026-05-04
- Fix: Play event elapsed time no longer inflated after app restore — if a track was paused mid-way in a previous session, resuming and stopping shortly after would record the restored seek offset as listening time; _startPlay() now anchors the session clock to the current playback position

## v0.87-rc.040526-1205 · 2026-05-04

## v0.86-rc.040526-1153 · 2026-05-04
- Change: Sync Music is now presented as a standalone promoted sidebar CTA above library scan status, separate from Library, Gear, and Insights navigation
- Change: History moved from Library section to Insights section in the sidebar
- Fix: History event rows no longer shift text on hover — delete button now uses visibility:hidden so it always reserves space without affecting layout
- Change: History view UI refreshed — stats rendered as individual cards, header integrated with controls, consistent padding and spacing with the rest of the app
- Change: "Clear ▾" button renamed to "Delete history" with trash icon; dropdown now shows a label ("Delete entries from…") and a separator before the destructive "Delete all history" option

## v0.85-rc.040526-1128 · 2026-05-04
- Fix: Listening History "Could not load history" error — undefined `_fmtDur` helper caused a silent ReferenceError in the event row template
- Fix: History view now defaults to 7-day period matching the active pill in the UI
- Add: Artist and album names in Listening History rows are now clickable navigation links
- Add: Per-row delete button (hover to reveal ✕) to remove individual history events
- Add: "Clear ▾" dropdown in History view to delete events from the last 7/30/90 days or all time
- Add: Listening charts in History view — plays-per-day bar chart and top artists list
- Add: Play count badges on album and songs view track rows showing how many times each track has been played

## v0.84-rc.040526-1120 · 2026-05-04

## v0.83-rc.040526-1108 · 2026-05-04

## v0.82-rc.040526-1041 · 2026-05-04

## v0.81-rc.040526-1023 · 2026-05-04

## v0.80-rc.030526-2101 · 2026-05-03

## v0.79-rc.030526-2003 · 2026-05-03
- Fix: Restore and Undo buttons in the Skipped & Not Duplicates section now work — WKWebView silently drops the request body on HTTP DELETE, causing the undo call to fail with a 400 error; both actions now use POST to dedicated endpoints.

## v0.78-rc.030526-1558 · 2026-05-03

## v0.77-rc.030526-1552 · 2026-05-03

## v0.76-rc.030526-1550 · 2026-05-03
- Change: "Skipped & Not Duplicates" section redesigned as a unified table — Type badge (Ignored / Unique), Title, Artist, Album columns with fixed widths; replaces the two separate flat div lists.

## v0.75-rc.030526-1536 · 2026-05-03

## v0.74-rc.030526-1533 · 2026-05-03

## v0.73-rc.030526-1529 · 2026-05-03
- Change: "Move to folder" destination in the Duplicates action modal is now remembered across uses — the last chosen path is pre-populated and "Move to folder" is pre-selected next time the modal opens.

## v0.72-rc.030526-1519 · 2026-05-03
- Fix: Consolidate/Remove action modal radio labels and descriptions no longer overflow and get clipped — removed conflicting `.modal` class from the shell element (it set a narrow 360px width and double-padding that overrode the 560px shell width), and gave the option body `flex:1` so it fills available space correctly.

## v0.71-rc.030526-1505 · 2026-05-03
- Fix: "Open in Finder" and "Unique" buttons in the Duplicates view now work correctly — all duplicate-related API calls were double-encoding their JSON bodies, causing 500 errors; body arguments are now passed as plain objects so the shared api() helper handles serialisation once.

## v0.70-rc.030526-1454 · 2026-05-03
- Fix: "Open in Finder" button now reliably calls the backend — path is stored in data attributes instead of an onclick string, eliminating any HTML-encoding edge cases.
- Fix: Duplicate group table columns no longer overlap — column widths are set via inline style on col elements (the only reliable method for table-layout:fixed) and all non-path columns use white-space:nowrap so headers stay on one line.
- Change: Action column widened (190px) to fit all three pills (Keep/Remove/Unique) without clipping; Finder column widened (136px) to fit "Open in Finder" text; Duration header shortened to "Dur" to fit the narrow column.

## v0.69-rc.030526-1417 · 2026-05-03
- Fix: "Open in Finder" button now correctly reveals the file — previously passed the track ID instead of the file path to the backend.
- Change: Duplicate view action column is now a 3-way pill per row — Keep, Remove, and Unique (was separate radio + checkbox + standalone "Not a duplicate" button). Selecting Unique immediately removes the track from the group; Keep/Remove are applied when clicking Delete marked or Consolidate.
- Change: "Remove marked" renamed to "Delete marked"; "Consolidate" renamed to "Consolidate &amp; fix playlists" — both buttons now carry descriptive tooltips explaining their behaviour.
- Change: Duplicate group table uses fixed-width columns so the path cell truncates with an ellipsis instead of expanding the table; full path visible on hover.

## v0.68-rc.030526-1401 · 2026-05-03

## v0.67-rc.270426-2021 · 2026-04-27
- Change: Duplicates view track selection redesigned — each row now has a unified Keep / Remove pill selector instead of separate radio and checkbox columns, preventing a track from being simultaneously marked as both keep and remove.
- Add: "Open in Finder" button on each duplicate track row — reveals the file in macOS Finder without leaving the app.
- Add: "Not a duplicate" button per track row in the Duplicates view — marks a track as excluded from its group; excluded tracks are remembered and no longer counted when determining duplicates.
- Add: Skipped & Not Duplicates section at the bottom of the Duplicates view — shows all ignored groups and individually excluded tracks with Restore/Undo buttons to reverse either action.
- Add: Sidecar file cleanup — when a music file is deleted or moved, associated `.lrc` lyric files and macOS `._filename` AppleDouble resource forks are automatically removed alongside it.
- Add: Empty folder cleanup — after deletion or move, TuneBridge detects directories that became empty and presents a checkbox list so you can remove them in one step.

## v0.66-rc.270426-1530 · 2026-04-27
- Add: Duplicate Tracks tool in Settings → Library — finds tracks with identical title, artist and album tags, groups them with format/bitrate/size/path columns, and lets you Ignore, Remove (Trash or move to folder preserving Artist/Album structure), or Consolidate (keep one copy, remap all playlist references) per group.
- Add: DAP duplicate scan — switch to DAP tab in the Duplicates view to scan a mounted player for duplicate files and delete them directly.
- Add: Sync integration — tracks deleted via the Duplicates tool are recorded in a `deleted_tracks` log; the sync engine automatically classifies matching DAP-only files as "Library deleted" instead of "device only", preventing deleted files from being copied back.

## v0.65-rc.270426-1342 · 2026-04-27
- Fix: Sync Step 3 footer alignment now matches modal standards more reliably by forcing full-width footer rails, anchoring summary width to modal content, and keeping the action cluster pinned to the bottom-right.

## v0.64-rc.270426-1324 · 2026-04-27
- Fix: Sync Step 3 footer no longer renders the extra dark gradient layer behind the summary/CTA area; footer now uses transparent background styling.
- Change: Sync Step 3 summary copy now follows the agreed format:
  `Tracks: <to add> • <to remove> • <skipped> • <playlists synced>`
  and
  `Space: <available> • <needed> • <available after sync>`.
- Change: Sync Step 3 action rail alignment was tightened so Back + Start Sync remain right-aligned in the footer.

## v0.63-rc.270426-0945 · 2026-04-27
- Change: Sync modal Step 2 now runs as a pure scanning phase with no `Back` / `Review Changes` action buttons; it advances to preview when scan reaches ready state.
- Change: Sync modal header typography spacing was loosened (step label, title, subtitle) for cleaner readability across all sync steps.
- Change: Sync Step 3 collapsed section headers now keep title/caret content vertically centered for more consistent accordion alignment.
- Change: Sync Step 3 row icons were simplified to a smaller flat style (removed glassy tile treatment), and playlist rows now use the playlist icon instead of the music-note icon.

## v0.62-rc.260426-2156 · 2026-04-26

## v0.61-rc.260426-2143 · 2026-04-26

## v0.60-rc.260426-2123 · 2026-04-26

## v0.59-rc.260426-2100 · 2026-04-26

## v0.58-rc.260426-2046 · 2026-04-26
- Fix: Sync Music Step 3 now opens with all sections collapsed by default, keeps the summary + action rail persistent at the bottom while content scrolls, and aligns `Start Sync` hover behavior with shared primary button interactions.
- Change: Sync modal step indicator is now unified across phases with a single consistent bottom rail (same size/position as Step 1), including Step 3 layout refinements for stable footer behavior.
- Fix: Prevented sync-state reset while a scan/copy job is already running; opening Sync during an active run now shows a clear in-progress message instead of risking inconsistent state.
- Add: Sync Music now includes `.lrc` lyric files in scan/diff/copy operations, so sidecar lyrics can be synced alongside audio files.

## v0.57-rc.260426-1917 · 2026-04-26
- Change: Sync Music Step 3 polish pass — removed `Unknown track -` prefixes from DAP-only titles, removed section header icons for cleaner accordion headings, improved Step 3 scroll behavior with expanded sections, and rewrote the bottom summary copy for clearer readability.

## v0.56-rc.260426-1847 · 2026-04-26
- Change: Sync Music Step 3 review rows refined — section headers now use normal-scale typography and left alignment, row paths now show full available file paths, `Skip` button labeling is standardized, size-mismatch copy is reduced to `Size difference` only, and expanded accordion content now scrolls reliably within the modal.

## v0.55-rc.260426-1735 · 2026-04-26
- Change: Sync Music Step 2 scan screen refined for cleaner focus — removed `To Device`/`To Local`/`Playlists` summary cards, centered the scan loader layout, and reduced `Scanning library data...` text size.
- Change: Sync Music Step 3 review screen typography and spacing were rebalanced to match app-wide modal scale, row actions were converted to proper pill buttons (`Sync` / `Skip` / `Delete from Device`), track rows now use the default empty-song icon, and DAP-only `Unknown track` rows now fall back to filename without extension.

## v0.54-rc.260426-1644 · 2026-04-26
- Change: Sync Music Step 3 (Review Changes) now follows the new mock styling with card-based discrepancy rows, refined section headers/icons/count pills, corrected text/action alignment, clearer action labels (`Sync`, `Skip`, `Delete from Device`), and updated footer CTA flow (`Back` + `Start Sync`) while preserving existing sync decision logic.

## v0.53-rc.260426-1535 · 2026-04-26

## v0.52-rc.260426-1533 · 2026-04-26
- Change: Sync Music Step 2 (Scanning Library) now matches the new mock structure with phase-specific header icon, warning-style progress banner, large scan progress ring, live summary stat cards (`To Device`, `To Local`, `Playlists`), and a dedicated Step 2 footer action row (`Back` + `Review Changes`) with left-aligned step rail.

## v0.51-rc.260426-1509 · 2026-04-26
- Change: Sync Music Step 1 section labels now read `Connected` and `Not Connected`; close button styling now matches the shared app-wide modal close control.
- Change: Sync modal shell sizing is now consistent across all sync steps (removed Step 1-only size overrides to prevent step-to-step resizing).

## v0.50-rc.260426-1029 · 2026-04-26
- Change: Sync Music Step 1 refined to match the finalized Stitch mock more closely with a tighter phase-specific shell, denser header/device-row spacing, `Connected`/`Not` device grouping, and compact footer rail/button alignment.
- Change: Step 1 DAP status chips now support three explicit states — `IN SYNC`, `OUT OF SYNC`, and `CHECK STATUS` — with corresponding pill styling.

## v0.49-rc.260426-0818 · 2026-04-26
- Change: Sync Music Step 1 modal refined to a tighter footprint and smaller typography for better alignment with app-wide modal scale; footer step indicator now sits inline with action buttons, the device connect hint row was removed, and device status chips now show `IN SYNC` / `OUT OF SYNC`.

## v0.48-rc.250426-1359 · 2026-04-25
- Change: Sync modal Step 1 (device selection) now aligns to the Stitch mock with grouped device sections (`Recommended` / `External Storage`), refined card density and status chips, updated dashed connect row, and Scan-first footer CTA styling.

## v0.47-rc.250426-1316 · 2026-04-25
- Change: Completed modal migration pass for insight/media/utility families by standardizing modal root overlays (`tb-modal-overlay`) and shared shell tiers (`tb-modal-shell` + size classes) across remaining non-onboarding modals.
- Add: Modal guardrail enforcement expanded from sync-only to app-wide modal contract checks (overlay class + shell tier validation, with explicit documented exceptions) in `scripts/check_modal_design_system.py`.
- Change: Design-system migration policy and audit matrix updated to mark Pass 1 + Pass 2 complete, with exceptions tracked for onboarding full-screen and custom IEM compare dialog shell.

## v0.46-rc.250426-1243 · 2026-04-25
- Add: Design System V1 contract docs (`docs/design-system/design-system-v1.md`) with canonical `--tb-*` tokens, semantic alias rules, and shared primitive usage guidance.
- Add: Modal governance docs (`modal-system-policy.md`, `modal-migration-audit-matrix.md`) including mandatory checklist and phased migration tracking.
- Add: Automated modal guardrail checker (`scripts/check_modal_design_system.py`) and build-time enforcement in `build_app.sh` to block non-compliant modal changes.
- Change: Sync modal now consumes shared modal primitives (`tb-modal-*`) and refreshed tokenized styling (compact shell, tighter spacing, bottom step rail retained, and Stitch-aligned header/icon hierarchy).
- Change: Core action/form modals now mount on shared modal shell tiers (`tb-modal-shell` + size variants) to centralize future design-system updates.

## v0.45-rc.250426-0837 · 2026-04-25

## v0.44-rc.250426-0802 · 2026-04-25

## v0.43-rc.250426-0800 · 2026-04-25
- Fix: ReplayGain tagger no longer stalls mid-run (e.g. stuck at 4 of 10); each file is now read inside a fresh daemon sub-thread with a 60-second timeout, bypassing macOS I/O priority throttling that blocks long-running daemon threads indefinitely on large FLAC reads
- Add: ReplayGain tagger progress banner now shows the filename currently being read and a "Waiting for drive…" message when a file stall is detected
- Change: Sync modal compactness pass — reduced shell dimensions and tightened Step 1 device-picker density (card spacing, sizing, and typography) for a less oversized presentation.

## v0.42-rc.240426-1633 · 2026-04-24
- Add: Smart Rules playlists — declarative rule builder (genre, artist, year, play count, never played, last played, energy, brightness, and more) with AND/OR matching, limit, sort, and 6 built-in templates (Unheard Library, Forgotten Favorites, Recently Added Unheard, High Energy Unheard, FLAC Only, Old Deep Cuts)
- Add: Smart playlists auto-refresh on open; "Smart" badge shown in playlist header
- Add: Warning banner when sonic rules (energy/brightness) are active but some tracks lack audio analysis
- Add: AI Mix generator now supports listening history filters — "Unheard only" and "Not heard in last 30/60/90 days" in Advanced options
- Add: History view — chronological play log grouped by date with stats bar (plays, hours, unique tracks, top artist) and valid-listens-only toggle
- Add: Library Coverage in Insights — heard/total progress bars for albums and artists, unheard album grid with one-click "Add to Playlist"
- Add: Database schema v6 with `smart_playlist_rules` table for persistent rule storage
- Add: New API routes: POST /api/playlists/smart/preview, POST /api/playlists/smart, GET/PUT /api/playlists/&lt;pid&gt;/smart, POST /api/playlists/&lt;pid&gt;/smart/refresh, GET /api/history, GET /api/insights/coverage

## v0.41-rc.240426-1607 · 2026-04-24
- Change: Sync modal header refinement — enlarged phase icon and centered it against the step/title/subtitle text block for cleaner visual alignment.
- Add: Playlist generation preview now supports play-history filters (exclude heard, heard-within-days, and min/max play count) via track play-stat lookups.

## v0.40-rc.240426-1352 · 2026-04-24
- Change: Sync modal layout refined again for tighter footprint and cleaner hierarchy: removed header/body separator lines, moved step indicator to a bottom dot/pill rail, and reduced modal width/height/padding across desktop and responsive breakpoints.

## v0.39-rc.240426-1311 · 2026-04-24
- Add: Sync Review Changes V2 data model with persistent per-DAP ignored discrepancy state (`sync_ignored_discrepancies`) keyed by normalized rel path + discrepancy type.
- Change: Sync scan payload now classifies actionable Step 3 buckets explicitly (`to_device_add`, `library_deleted_on_source`, `device_only_not_in_library`, `playlists_out_of_sync`) and separates filtered `ignored_tracks`.
- Change: Sync execute contract upgraded to action-specific lists (`add_to_device_paths`, `copy_to_local_paths`, `delete_on_device_paths`, `ignore_upserts`, `ignore_removals`, `playlist_ids`) while preserving playlist export behavior.
- Add: Safe device delete guardrails in sync execution to ensure deletions remain constrained to the configured DAP music root.
- Add: New ignored-discrepancy APIs (`GET/POST/DELETE /api/sync/ignored`) for Step 3 skip/unskip workflows.
- Change: Sync Step 3 UI redesigned to action-based sections with per-row decision controls, skipped-tracks section, rescan-required gating after un-ignore, and destructive delete confirmation preflight.

## v0.38-rc.240426-1059 · 2026-04-24

## v0.37-rc.240426-1056 · 2026-04-24
- Change: Sync modal refined to match latest UX mock (phase-specific header icons, cleaner separators, richer step-2 scan progress with verbose status and summary counters, and new bottom dot step indicator) with no functionality changes

## v0.36-rc.240426-1028 · 2026-04-24
- Change: Sync Music modal UI refreshed across all 5 steps (header hierarchy, step rail, progress visuals, section cards/lists, CTA styling, and responsive polish) without changing sync functionality

## v0.35-rc.240426-1012 · 2026-04-24

## v0.34-rc.240426-0931 · 2026-04-24

## v0.33-rc.240426-0919 · 2026-04-24
- Fix: Album Detail multi-disc tables now support multi-select correctly (including row highlight refresh and shift-range selection using global album row order across all discs)

## v0.32-rc.240426-0904 · 2026-04-24
- Change: Insights → IEM Fit scores now recalculate from the selected PEQ profile; section average pills and top IEM score update live when PEQ changes
- Add: Insights → IEM Fit now shows a `With PEQ` pill beside the IEM title when a PEQ profile is active
- Add: Insights → IEM Fit UI state persistence (expanded accordion, selected PEQ/source/genre overlay) now survives navigation and app relaunch
- Change: Insights → IEM accordion visual merge refined so expanded header and detail panel blend into one seamless card
- Add: Single-track tag editor now includes Disc #, Composer, and Comment fields (previously required Mp3tag for these)
- Add: "Edit Tags" entry in track right-click context menu — opens the single-track editor directly
- Add: "Edit Tags" button in the bulk action bar — select multiple tracks in Songs/playlist view then batch-edit shared fields
- Add: Insights stale banner — after any tag edit, a warning appears on the Insights page prompting re-analysis with a one-click "Analyse now" button

## v0.31-rc.230426-1901 · 2026-04-23
- Change: Home → Listening Stats typography and spacing refined to match app-wide scale (smaller stat values/labels, tighter card padding, and improved top-track row balance for long titles)

## v0.30-rc.230426-1805 · 2026-04-23

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
