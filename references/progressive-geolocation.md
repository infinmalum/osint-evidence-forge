# Progressive Geolocation with Predictive Verification

Derived from geolocation case practice (convoy/launcher-class investigations).
Load when an image or video must be located on the map.

## The pipeline

```text
observation → searchable discriminator → candidate area
→ assumed camera position → PREDICTED scene features
→ independent visual confirmation → route/scene continuity
```

### 1. Observation

Record what is actually visible before any guessing: road layout (lanes,
medians, curvature, markings), building types, signage, vegetation, terrain
slope, structures, shadows, unique objects (arches, fences, colored roofs).

### 2. Searchable discriminators

Convert observations into searchable terms. Highest-yield types:

- **text on signs** — shop names, abbreviations, gas-station shorthand; search
  them together with nearby settlement names;
- **named chains + settlement** — a supermarket chain plus a town name yields a
  short list of candidate sites on map services;
- **unusual road geometry** — dual carriageway with median trees, specific
  curves, on-ramps: searchable in satellite view;
- **claimed location tags** — treat as a starting hint only, never as truth.

### 3. Candidate area → assumed camera position

When road layout matches, derive where the camera must be. Camera elevation
itself is a clue: if the view is above nearby rooftops, the position must be a
hill or a tall building — check which exists in the candidate area.

### 4. Predictive verification (the core step)

Compatibility is not confirmation. Once a candidate position is assumed,
**predict what else must be visible from there, then check every prediction**:

- individual trees by position relative to the bend;
- junctions and their spacing;
- a specific colored roof at a specific point;
- building arches, fences, intersections in expected order.

Each confirmed prediction is independent support; each failure is a
contradiction. A location is accepted only after several predictions verify —
never on road-layout resemblance alone.

### 5. Independent confirmation layers

- satellite imagery match;
- ground-level/street-view imagery (virtual drive-through of the candidate);
- if street view exists, confirmation confidence rises sharply.

### 6. Continuity across multiple media

When several clips are geolocated along a route:

- order them using upload timestamps (convert UTC to local, mind DST) and
  lighting (dawn/dusk);
- use known endpoints to interpolate plausible intermediate locations;
- check intermediate candidates for features visible in the clip;
- a chain of located clips forming a coherent route mutually reinforces —
  but clips from the same upload stay in one independence group.

## Hard rules

- Download immediately any video of interest — sources get deleted.
- A claimed location tag is a hypothesis, not evidence.
- Never announce a location before predictive verification; a road that merely
  "looks like" the video is a candidate, not a finding.
- Record coordinates with the tool and imagery date used.
