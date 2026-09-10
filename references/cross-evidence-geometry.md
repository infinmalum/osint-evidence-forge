# Cross-Evidence Geometry and Chronolocation

Derived from multi-evidence site-reconstruction practice. Load when several
clues must jointly constrain one place or one time.

## Beyond per-clue scoring

Per-clue weighting asks "does E support candidate C?". Stronger question:

```text
If E1 and E2 are both true, what geometric, temporal, or causal
relationship MUST exist between them?
```

Examples:

- smoke-trail direction (a line in space) + photographer position (a point)
  → the trail origin must lie on the correct bearing from the photographer
  at a plausible distance;
- surface scorching that appears between two satellite image dates
  → bounds the event date AND the event location to that field;
- multiple clips along a route + upload times
  → constrains travel direction and speed between located points.

Two clues that individually look plausible but are mutually inconsistent
falsify the shared hypothesis. Two clues that must intersect in physical space,
and do, are much stronger than two independent soft matches.

## Evidence types with joint constraints

- directional observations (smoke, flight paths, sight lines);
- before/after imagery pairs (fields, construction, destruction) — bound both
  time and place;
- audio/witness direction reports;
- official imagery of variable quality (a low-resolution intelligence image
  can still confirm geometry already established from open sources).

Record for every joint: the physical constraint, whether each pair satisfies
it, and what would falsify it.

## Chronolocation: time as an interval, not a date

Sources of time evidence, layered:

1. **asserted time** — what a post or person claims;
2. **encoded time** — file metadata, EXIF;
3. **upload time** — platform/server timestamp (convert UTC to local, mind
   daylight saving);
4. **environmental time** — season, foliage, weather, solar elevation/shadows;
5. **change-state time** — features that existed/changed: storefronts, banners,
   construction sites, graffiti, building facades, schedules, public-transport
   lines, artworks on display.

### Chronological intersection

Each clue yields a bound:

```text
banner campaign started 2017-04-03  → earliest
post date 2014-10-11                → latest
building not yet built in 2019       → latest (if unbuilt)
foliage = summer                     → seasonal constraint
sun elevation = morning              → time-of-day constraint
```

Intersect all bounds and report `T ∈ [earliest, latest]`. Do not guess a
precise date when the evidence supports only an interval. Often only one
bound is recoverable; state which.

## Change-state lookups

For any feature that changed over time: find dated imagery of that feature
(photos posted to social media, review sites, map services) before and after
the source image, and bracket the change. Street-view historical imagery is a
primary tool. A unique detail (letters on a distant building, a temporary
structure) is often enough to bracket a date to weeks.
