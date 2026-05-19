# TuneBridge Privacy Policy

**Last updated: May 2026**

TuneBridge is a local music manager that runs entirely on your Mac. This policy describes what data stays on your device and what leaves it.

---

## The short version

- No analytics, no crash reporting, no telemetry. Ever.
- No accounts, no sign-in, no user profiles
- Your listening history is stored on your Mac only and never transmitted anywhere
- External services are only contacted to fetch information (artwork, lyrics, measurements). Nothing from your library is published or uploaded
- Some external services are optional and only activate if you configure them

---

## What stays on your device

Everything TuneBridge creates is stored locally in `~/Library/Application Support/TuneBridge/`:

| Data | Where | Notes |
|---|---|---|
| Music library index | `tunebridge.db` | Track metadata scanned from your files |
| Playlists | `tunebridge.db` | Names, track order, timestamps |
| Listening history | `tunebridge.db` | Opt-in only (see Listening history section) |
| DAP configurations | `tunebridge.db` | Device names, mount paths, export settings |
| IEM profiles | `tunebridge.db` | Names, squig.link URLs, PEQ profiles, cached measurements |
| Cached artwork | `artwork/`, `artist_artwork/` | Downloaded from external services (see below) |
| Lyrics | Alongside your music files | Saved as `.lrc` files next to each track |
| Settings | `tunebridge.db` | App preferences, API keys if configured |

None of this data is sent to any server. TuneBridge has no backend.

---

## Listening history

TuneBridge can record what you play locally to power features like recently played and listening statistics. This is stored only in `tunebridge.db` on your Mac.

- Recorded: track title, artist, album, time played, how long you listened, whether you skipped
- Not recorded: audio content, files, ratings, or any personal information
- Not transmitted: listening history is never sent anywhere
- You can clear it at any time from Settings

Listening history is enabled by default. You can turn it off in **Settings**.

---

## External services

TuneBridge may contact the following services to fetch information. All connections are read-only. Nothing from your library is uploaded or published to any of them.

### Always available (no account or key required)

| Service | What it fetches | What is sent |
|---|---|---|
| [iTunes Search API](https://www.apple.com/legal/privacy/) | Album and artist artwork | Artist name, album name |
| [MusicBrainz](https://musicbrainz.org/doc/MusicBrainz_API) | Artist and release IDs (used to look up Fanart.tv images) | Artist name, album name |
| [lrclib.net](https://lrclib.net) | Synchronized lyrics | Track name, artist name, album name, duration |
| [squig.link](https://squig.link) | Headphone frequency response measurements | The file key from the share URL you enter |
| [GitHub](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement) | Version information for update checks | Nothing (read-only fetch of a public file) |

### Optional (only active if you add your own API key in Settings)

| Service | What it fetches | What is sent |
|---|---|---|
| [Last.fm](https://www.last.fm/legal/privacy) | Artist and album artwork | Artist name, album name, your API key |
| [Fanart.tv](https://fanart.tv/legal/privacy-policy/) | Artist and album artwork | MusicBrainz ID, your API key |

These services are never contacted unless you enter an API key in Settings. TuneBridge does not scrobble or send play data to Last.fm.

### Image downloads

When artwork is downloaded from any of the above services, TuneBridge fetches the image from that service's content delivery network. These requests include standard HTTP headers (User-Agent, Referer). Downloaded images are cached locally and reused without re-fetching.

---

## API keys

If you configure a Last.fm or Fanart.tv API key, it is stored in plaintext in the local settings database. It is sent to the respective service with each artwork request. It is never sent to any other service or to TuneBridge's developer.

---

## Update checks

TuneBridge periodically checks for updates by fetching a small version file from the public GitHub releases repository. No information about your device, library, or usage is included in this request. You can change the update channel or disable checks in **Settings**.

---

## What is never collected

- No analytics or usage statistics
- No crash reports or error logs sent externally
- No audio content or file data
- No personal information (name, email, location)
- No device identifiers
- No advertising identifiers

---

## Data you can delete

You can remove all data TuneBridge has stored by deleting `~/Library/Application Support/TuneBridge/`. Uninstalling the app does not automatically remove this folder.

Lyrics files (`.lrc`) are saved next to your music files. Removing them requires deleting those files separately.

---

## Third-party services

When TuneBridge contacts an external service, that service's own privacy policy applies to the request. Links to each service's policy are included in the table above.

---

## Contact

TuneBridge is developed by Hashan Ranatunga. For privacy questions, contact [hashan.sr@gmail.com](mailto:hashan.sr@gmail.com).

---

## Changes to this policy

If this policy changes in a way that affects what data leaves your device, the updated date at the top of this document will change and the change will be noted in the release changelog.
