# TuneBridge

**Your personal music library, beautifully managed.**

TuneBridge is a local music manager for macOS built for people who care about their music collection. Browse your FLAC library by artist and album, build and export playlists to portable audio players, and listen in-app with a real-time parametric EQ. Everything runs on your Mac — no accounts, no cloud, no subscriptions.

---

## Download

**[Download TuneBridge v0.322 for macOS →](https://github.com/hashansr/tunebridge-releases/raw/main/TuneBridge-latest.dmg)**

Requires macOS 14 Sonoma or later.

---

## What You Can Do

- **Browse** your music library by artist, album, and track with album art
- **Build playlists** with drag-and-drop track ordering
- **Export playlists** to portable audio players (FiiO, Hiby, AP80, and more)
- **Sync music** bidirectionally between your Mac and a DAP or SD card
- **Play music** in-app with crossfade, shuffle, repeat, and a Web Audio parametric EQ
- **Analyse your library** with Insights — tag health, sonic profiles, and IEM matching
- **Manage headphones** — import frequency response measurements from squig.link and overlay PEQ profiles

---

## Requirements

- macOS 14 Sonoma or later
- A music library organised as `Artist / Album / tracks`
- Supported formats: FLAC, MP3, AAC, M4A, ALAC, OGG, OPUS, WAV, AIFF

---

## Installation

### 1. Download and open the DMG

Download `TuneBridge-latest.dmg` using the link above. Once downloaded, double-click it to mount the disk image.

<!-- SCREENSHOT: DMG window showing TuneBridge.app and the Applications folder shortcut -->
![TuneBridge DMG installer window](assets/screenshots/dmg-window.png)

### 2. Drag TuneBridge to Applications

Drag **TuneBridge** into the **Applications** shortcut in the same window. Wait for the copy to finish, then eject the disk image.

### 3. macOS Security Workaround

TuneBridge is distributed outside the Mac App Store and is not notarised by Apple, so macOS will block it the first time you open it. This is expected — follow either method below.

---

#### Method A — Right-click to open (quickest)

1. Open **Finder** and go to your **Applications** folder
2. **Right-click** (or Control-click) on **TuneBridge**
3. Select **Open** from the menu
4. Click **Open** in the dialog that appears

<!-- SCREENSHOT: Right-click context menu on TuneBridge.app showing the Open option -->
![Right-click TuneBridge and choose Open](assets/screenshots/rightclick-open.png)

<!-- SCREENSHOT: macOS "cannot verify developer" dialog with Open button -->
![macOS security dialog with Open button](assets/screenshots/security-dialog-open.png)

> You only need to do this once. After that, double-clicking works normally.

---

#### Method B — Privacy & Security settings

If you double-clicked TuneBridge first and were blocked, macOS will have shown a dialog saying it could not be opened. After dismissing that dialog:

1. Open **System Settings** → **Privacy & Security**
2. Scroll to the bottom of the page
3. Find the message **"TuneBridge was blocked from use because it is not from an identified developer"**
4. Click **Open Anyway**
5. Enter your Mac password if prompted
6. Click **Open** in the final confirmation dialog

<!-- SCREENSHOT: System Settings → Privacy & Security with the "Open Anyway" button visible at the bottom -->
![Privacy & Security — Open Anyway](assets/screenshots/privacy-security-open-anyway.png)

---

## First Launch

On first run, macOS will ask:

> **"TuneBridge would like to access files in your Documents folder."**

Click **Allow** — this permission is required for TuneBridge to read your music library.

<!-- SCREENSHOT: macOS TCC Documents folder access prompt -->
![macOS Documents folder permission prompt](assets/screenshots/documents-permission.png)

---

## Getting Started

Once TuneBridge is open:

### 1. Set your library path

Click the **Settings** icon in the sidebar → **Library** section → enter the path to your music folder (e.g. `/Volumes/Storage/Music/FLAC`) → click **Save**.

<!-- SCREENSHOT: Settings view with the Library path input field -->
![Settings — library path](assets/screenshots/settings-library.png)

### 2. Scan your library

Click **Rescan Library**. TuneBridge will index all tracks and cache metadata. A progress bar shows the scan status. This takes a minute or two on first run depending on library size.

### 3. Browse and play

Navigate to **Library** in the sidebar to browse by artist and album. Double-click any track to play it in the player bar at the bottom, or click the play button on any album or artist card to queue everything.

<!-- SCREENSHOT: Artist grid view showing album art cards -->
![Library — artist grid](assets/screenshots/library-artists.png)

### 4. Build a playlist

Click **+ New Playlist** in the sidebar. Browse to any artist or album and add tracks, whole albums, or an entire artist's catalogue to your playlist. Drag the handles to reorder.

<!-- SCREENSHOT: Playlist view with tracks and drag handles -->
![Playlist view](assets/screenshots/playlist-view.png)

### 5. Export to your DAP

Go to **Gear** → **Digital Audio Players** → add your device with its mount path and model preset. Open any playlist and click the export button for that device.

---

## Music Library Structure

TuneBridge expects your music organised like this:

```
Music/
  Artist Name/
    Album Name/
      01. Track Title.flac
      02. Another Track.flac
  Another Artist/
    ...
```

Files are identified by their embedded tags (not just filenames), so minor naming variations are handled gracefully.

---

## Privacy

TuneBridge runs entirely on your Mac. No usage data, analytics, or personal information is ever collected or transmitted.

The only optional outbound connection is to [squig.link](https://squig.link) when you add headphone frequency-response measurements in the **Gear** section. This is entirely user-initiated — TuneBridge never connects to any external service automatically.

---

## Licence

Copyright © 2026 Hashan Ranatunga. All Rights Reserved.

This software is provided for personal use only. Redistribution, modification, or commercial use is not permitted without explicit written consent from the author.
