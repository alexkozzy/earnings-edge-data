# earnings-edge data

Public snapshot data consumed by the
[earnings-edge-dashboard](../earnings-edge-dashboard) Vercel deployment.

The scanner publishes signals to this repo; GitHub Pages serves the JSON
files at `https://<user>.github.io/earnings-edge-data/data/...`.

## Files

- `data/signals_latest.json` — most recent live signals snapshot
- `data/calibration_summary.json` — settled-signal calibration summary
- (future) `data/signals_history.jsonl` — full append-only history

## Schema

The Signal shape is defined canonically in
`../earnings-edge-dashboard/lib/types.ts`. Both files in `data/` are
validated against that schema by
`../earnings-edge-dashboard/tools/validate_snapshot.ts` before publish.

This file `signals_latest.json` is currently a sample placeholder so the
dashboard renders meaningfully on first deploy. The scanner overwrites
it on every run.

## Publishing (scanner side)

The scanner project (~/Dropbox/claude shenanigans/earnings-edge/) has a
snapshot writer that emits dashboard-shaped JSON, then commits + pushes
this repo on a cron cadence. See INTEGRATION_NOTES.md in the dashboard
repo for the schema-mapping contract.
