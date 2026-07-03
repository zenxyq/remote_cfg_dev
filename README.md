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

- `*_required_version` — force-update gate (use `0.0.1` in dev to avoid blocking testers).
- `amenity_filters` — per-filter toggles; missing keys default to `true` in the app.
- `no_commission: true` — advertiser toggle = «bez prowizji»; `false` = legacy private-only.

## Raw URL

```
https://raw.githubusercontent.com/zenxyq/remote_cfg_dev/refs/heads/main/rentme_remote_config.json
```
