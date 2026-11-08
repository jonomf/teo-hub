# Teo's Learning Hub

Home screen for Mateo's learning apps, served at https://jonomf.github.io/teo-hub/.
Plain static files, no build step. GitHub Pages serves `main` / root.

Every app follows the conventions in the "Mateo Learning Games" project doc `hub-conventions.md`.

## Add an app
Add one entry to `apps.json`:

```json
{ "id": "word-quest", "name": "Word Quest", "emoji": "📖", "path": "/duo-teo/",
  "color": "#2fbf4f", "description": "Spelling and reading" }
```

- `path` must be root-relative (`/<repo>/`). The hub skips `/`, `//…` and full URLs.
- `color` is a hex color (`#rgb` or `#rrggbb`). It's used for the tile accent.

## What the hub reads and writes
- Reads `hub:app:<id>` from localStorage for each tile's progress (`lastPlayed`, `streak`, `xp`, `status`).
  Missing or invalid JSON shows "Not played yet". A streak only shows if `lastPlayed` was today or yesterday.
- Reads and writes `hub:theme` (`dark` default, `light`, `auto`) using the 🌙 button.
- Touches no other keys and never calls `localStorage.clear()`.

## Home screen
`manifest.webmanifest` has `start_url: /teo-hub/` and `scope: /`, so one installed icon opens the hub
and the apps open inside it.
