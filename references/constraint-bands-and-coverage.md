# Constraint Bands and Search Coverage

Two agent-specific disciplines: physical measurements produce bands, and
absence becomes evidence only after coverage.

## Constraint bands, not points

Every physical or verbal measurement carries error; propagate it as a band:

| Input | Output constraint |
|---|---|
| "about 20 minutes away" (mode unknown) | wide, mode-dependent isochrone band |
| shadow ratio (height/shadow length) | ring/band of equal solar elevation |
| ridge bearing from image | angular sector, widened by camera-roll uncertainty |
| estimated height/distance | interval, not a value |

Shadow measurement prerequisites: known date and time (clock, livestream
frame, or verified metadata — metadata may be wrong); a vertical object at
right angles to the camera casting onto near-level ground. Violating these
expands the band — it does not invalidate the method, and must never be
compressed into false precision ("measured 47°, therefore these exact
coordinates").

Intersecting bands from different measurement types narrows the search area
honestly; overlapping bands from the same underlying measurement add nothing.

## Search coverage ledger

Large-area visual search (satellite imagery, street view) without coverage
tracking produces two failures: searching the same cells repeatedly, and
claiming "not found" without having looked systematically.

Divide the area into grid cells (fixed size appropriate to the target's
minimum detectable size) and record:

```yaml
cell: G14
searched: true
source: "satellite imagery 2026-02, provider X"
features_checked: [road geometry, ridge profile, building footprints]
result: no-match
quality: good          # imagery resolution, cloud cover, viewing angle
time: 2026-03-09T14:20Z
```

Rules:

- a cell is `searched` only for the features actually checked — record them;
- `no-match` in low-quality imagery is weak negative evidence; state quality;
- negative evidence is valid only when coverage and detectability are
  established: "I looked for half an hour and saw nothing" is not evidence;
- coverage enables team division and later re-search of skipped cells;
- export coverage state so work survives handoff.

## Detection bias

Absence in one search engine is not absence everywhere: reverse-image engines
have disjoint indexes and different recall. "No results" bounds nothing
unless the engine's coverage for that content class is known.
