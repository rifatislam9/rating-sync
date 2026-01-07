# Rating Sync (Emby plugin)

[![CI](https://github.com/pejamas/rating-sync/actions/workflows/ci.yml/badge.svg)](https://github.com/pejamas/rating-sync/actions/workflows/ci.yml)
[![Release](https://img.shields.io/github/v/release/pejamas/rating-sync?include_prereleases=true&sort=semver)](https://github.com/pejamas/rating-sync/releases)
[![License](https://img.shields.io/github/license/pejamas/rating-sync)](LICENSE)

Sync **IMDb community ratings** and **Rotten Tomatoes critic ratings** into Emby metadata, with smart scanning, rate limiting, progress tracking, and scan history.

## Features

- Updates **Movies**, **Series**, and optionally **Episodes**
- Supports **OMDb** and/or **MDBList** (configurable preferred source)
- Optional **IMDb scraping fallback** for episode ratings
- Built-in **rate limiting** + daily limits per API
- **Smart scanning**: rescan interval, prioritize recently added, skip already-rated (optional)
- **Progress API** + detailed results (updated/skipped/errors)
- **Scan history** + per-session reports
- Missing data views (e.g., missing IMDb id / ratings) and item-level scan history

## Install

1. Download `RatingSync.dll` from the latest GitHub Release.
2. Copy it into your Emby plugins folder (commonly `...\Emby-Server\programdata\plugins\`).
3. Restart Emby Server.
4. Configure API keys in Emby Dashboard → Plugins → Rating Sync.

## Quick start

1. Add at least one API key (OMDb and/or MDBList).
2. Pick your preferred rating source and what item types to update.
3. (Optional) Enable episode scraping fallback if you want episode ratings.
4. Go to the **Run** tab and start a refresh.

## UI tour

### Settings

Configure API keys, rating sources, item types, and rate limiting.

<img src="docs/screenshots/settings.png" alt="Rating Sync settings" width="900" />

### Smart scanning

Avoid redundant API calls by controlling how often items are rescanned and prioritizing recently added content.

<img src="docs/screenshots/smart-scanning.png" alt="Smart scanning" width="900" />

### Run

Trigger a refresh manually. You can run it for an entire library, or target a specific series/season/episode.

<img src="docs/screenshots/run.png" alt="Run rating refresh" width="900" />

### Scan report

After a scan, open the report for a detailed breakdown (updated/skipped/errors, API usage, and searchable results).

<img src="docs/screenshots/scan-report.png" alt="Scan report" width="900" />

### History

Browse recent scans, find items with missing data, and inspect item-level scan history.

<img src="docs/screenshots/history.png" alt="Scan history" width="900" />

> Screenshot files live in `docs/screenshots/`.

## Build

```powershell
dotnet build -c Release
```

Output:
- `bin\Release\RatingSync.dll`

### Building against a local Emby install (optional)

If you have Emby installed locally, you can build against its `System` DLLs:

```powershell
dotnet build -c Release -p:EmbyPath="C:\Program Files\Emby-Server\System"
```

## Release process (automated)

This repo is set up so that pushing a tag like `v1.2.3` will:
- Build `Release`
- Create a GitHub Release
- Upload `RatingSync.dll` (and a zip) as release assets

See [RELEASING.md](RELEASING.md).

## Versioning

Uses Semantic Versioning: `MAJOR.MINOR.PATCH`
- **PATCH**: bug fixes, small changes
- **MINOR**: new features (backwards compatible)
- **MAJOR**: breaking behavior/config/API changes
