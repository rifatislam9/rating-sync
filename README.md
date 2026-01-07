# Rating Sync (Emby plugin)

Refreshes **community ratings (IMDb)** and **critic ratings (Rotten Tomatoes)** for your library items, with smart scanning, rate limiting, progress tracking, and scan history.

## Features

- Updates **Movies**, **Series**, and optionally **Episodes**
- Supports **OMDb** and/or **MDBList** (configurable preferred source)
- Optional **IMDb scraping fallback** for episode ratings
- Built-in **rate limiting** + daily limits per API
- **Smart scanning**: rescan interval, prioritize recently added, skip already-rated (optional)
- **Progress API** + detailed results (updated/skipped/errors)
- **Scan history** + per-session reports

## Install

1. Download `RatingSync.dll` from the latest GitHub Release.
2. Copy it into your Emby plugins folder (commonly `...\Emby-Server\programdata\plugins\`).
3. Restart Emby Server.
4. Configure API keys in Emby Dashboard → Plugins → Rating Sync.

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
