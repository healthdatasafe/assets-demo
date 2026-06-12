# Changelog

Assets served at `https://healthdatasafe.github.io/assets-demo/` (GitHub Pages from `main`),
referenced by `demo.datasafe.dev` service-info → `assets.definitions`. The `version` field in
`apps/list.json` is the cache-buster consumers key on.

## 2026-06-12.1

- `apps/list.json`: **bridge-healthkit icon** — replaced the ❤️ emoji placeholder
  with the Apple Health app icon (128px PNG, base64 data URI, sourced from
  Wikimedia Commons `Icon_-_Apple_Health.png`).

## 2026-06-01.2

- `apps/list.json`: **removed `bridge-ryb`** entry. RYB adapter is not yet
  feature-complete (mucus, cervix, photos, custom_lines, and rule-engine
  outputs are deferred under plan 68). Exposing it in the user-facing
  catalog before those mappings ship would surface an incomplete import
  to end users. Will re-add once plan 68 closes the deferred mappings.
- Kept the bridge-femm icon fix from 2026-06-01.1 (broken base64 → inline SVG).

## 2026-06-01.1

- `apps/list.json`: added **`bridge-ryb`** (Read Your Body) — 4th app entry, hook points to
  `https://demo-bridge-cycles-files.datasafe.dev/ryb`. 10 permissions (5 RYB streams + 5
  shared item streams: BBT, sexual activity, OPK, pregnancy, cycle start). EN + FR copy.
- `apps/list.json` bridge-femm `icon`: replaced the inline base64 (which had become
  malformed — truncated mid-stream and rendering blank in the app catalog) with an
  inline SVG data URL: a square purple (#7c7eb0) tile with "FEMM" in white serif. Vector,
  self-contained, ~552 bytes (vs ~3 KB broken JPEG) (plan 68).

## 2026-05-29.2

- `apps/list.json` bridge-mira `lastSync` descriptor: added **`faultyField: "faulty"`** so
  hds-webapp can surface a "bridge unavailable/faulty" state when the bridge reports its
  upstream integration as faulty (plan 66).

## 2026-05-29.1

- `apps/list.json` bridge-mira: added **`needsReauthField: "needsReauth"`** to the `lastSync`
  descriptor; fixed the `resync.initiate` hook to send `body.returnUrl` + `openUrlField` so the
  reconnect flow reaches `/mira/resync`. Bumped `version` (plan 66).
