# Changelog

Assets served at `https://healthdatasafe.github.io/assets-demo/` (GitHub Pages from `main`),
referenced by `demo.datasafe.dev` service-info → `assets.definitions`. The `version` field in
`apps/list.json` is the cache-buster consumers key on.

## 2026-05-29.2

- `apps/list.json` bridge-mira `lastSync` descriptor: added **`faultyField: "faulty"`** so
  hds-webapp can surface a "bridge unavailable/faulty" state when the bridge reports its
  upstream integration as faulty (plan 66).

## 2026-05-29.1

- `apps/list.json` bridge-mira: added **`needsReauthField: "needsReauth"`** to the `lastSync`
  descriptor; fixed the `resync.initiate` hook to send `body.returnUrl` + `openUrlField` so the
  reconnect flow reaches `/mira/resync`. Bumped `version` (plan 66).
