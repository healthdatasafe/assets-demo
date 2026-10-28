# Changelog

Assets served at `https://healthdatasafe.github.io/assets-demo/` (GitHub Pages from `main`),
referenced by `demo.datasafe.dev` service-info → `assets.definitions`. The `version` field in
`apps/list.json` is the cache-buster consumers key on.

## 2026-10-28.1

- `apps/list.json` **bridge-cyclefeminin and bridge-femm grant the streams bridge-cycles-files
  writes**: `app-cyclefeminin` + its 5 sub-streams (was `cyclefeminin-custom*`), `app-femm` + its 3
  sub-streams (was `bridge-femm*`). The importer stopped at "Preview changes" with `Stream provisioning
  failed … app-cyclefeminin`: its access had no right on its own stream tree. Item grants aligned too:
  Cyclefeminin `symptom-pain-pelvic` replaces `symptom-gastrointestinal-cramps` (the adapter's item
  since data-model 3.2.0); FEMM no longer asks for `fertility-cycles-average-length` / `-period`, which
  it does not write. `lastSync.streamId` follows the base streams. (`_plans/BUGS.md` B-2026-10-26-5)
- `apps/list.json` connector entries may carry **`deviceName`** (the device the connector reads, used
  to label the values it writes) and **`deviceItems`** (item keys the device measures; absent means
  every value the connector writes). bridge-mira: `Mira`, the five urine-hormone items.
- `apps/list.json` new top-level **`partnerApps`** list: apps the person uses in their own window
  with their own sign-in, listed so the HDS app can show a card and recognise the connection. They are
  not connectors (no hook, no permissions), so they live outside `apps`, which every reader treats as
  connectors. Entry: `id`, `appCode` (what the partner's grant carries), `grant` (`access`: an app
  access named `appCode`; `cmc`: a CMC relationship with `clientData.cmc.appCode === appCode`), `name`,
  `description`, `icon` (as for `apps`), `category`, `provider`, `urls` per client platform (`web`,
  `ios`, `android`; a platform absent from `urls` shows no card, there is no default), optional
  `embedFrom` (origins the partner's site lets frame it). Listed: Cycle Intelligence, DysNet (staging
  registry `dev.dysnet.org`, the one serving the demo platform).

## 2026-09-28.1

- `apps/list.json`: **bridge-femm and bridge-ryb icons** are now 128px PNG base64 data URIs
  (`type: "base64"`), rasterized from their previous SVG tiles, which were `type: "url"` SVG data URLs.
  app-web-user-account (upstream v0.5.0+, deployed 2026-09-25) accepts only absolute http(s) `url` icons
  and raster `base64` images (SVG is script-capable), so both apps showed no icon on the consent screen.
  (`_plans/BUGS.md` B-2026-09-25-4)

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
