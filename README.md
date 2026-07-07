# RentMe / MojDom — dev remote config

Public JSON for **debug/profile** app builds. Production release builds read
[DolasPro/RentMe-App-Config](https://github.com/DolasPro/RentMe-App-Config).

## File

- `rentme_remote_config.json` — served via GitHub raw URL on `main`

## Schema

```json
{
  "config": {
    "ios_required_version": "0.0.1",
    "android_required_version": "0.0.1",
    "services_sticky_bar_enabled": true,
    "amenity_filters": {
      "has_balcony": true,
      "has_terrace": true,
      "has_ogrod": true,
      "has_air_conditioning": true,
      "no_commission": true,
      "pets_allowed": true,
      "has_separate_kitchen": true
    }
  }
}
```

### `*_required_version`

Force-update gate. In dev use `0.0.1` so testers are not blocked.

### `services_sticky_bar_enabled`

Sticky bar on the home feed (link to contractor services WebView).

| Value | App behaviour |
|-------|----------------|
| omitted / `false` | **Hidden** (default) |
| `true` | Shown until user dismisses it |

### `amenity_filters`

Extra filter chips in the filter screen (LLM-enriched listing flags).

**Default in app: all keys are `false` if omitted.** Set `true` explicitly to show a chip.

| Key | UI label (EN) | Notes |
|-----|----------------|-------|
| `has_balcony` | Balcony | |
| `has_terrace` | Terrace | |
| `has_ogrod` | Garden | |
| `has_air_conditioning` | Air conditioning | |
| `no_commission` | No commission | `true` → advertiser toggle = bez prowizji; `false` → legacy private-only (`agency`) |
| `pets_allowed` | Pet friendly | Shown only for **Rent**; filter matches listings with `pets_allowed = true` only |
| `has_separate_kitchen` | Separate kitchen | |

Omit the whole `amenity_filters` block → no extra chips (same as all `false`).

## Raw URL

```
https://raw.githubusercontent.com/zenxyq/remote_cfg_dev/refs/heads/main/rentme_remote_config.json
```

## App wiring

- Debug/profile: `RemoteConfigUrls.dev` (this repo)
- Release: `RemoteConfigUrls.prod` (DolasPro/RentMe-App-Config)
- Loaded once per session in `AppRemoteConfig.tryLoad()` (splash / returning user)
