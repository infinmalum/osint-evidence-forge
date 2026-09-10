# Source Recovery and Attribution Uncertainty

Derived from video-verification and flight-data practice. Load when the task
is finding the original source of a video/image, or reasoning from tracker or
database attributions.

## Video source recovery

1. **Download immediately** anything of interest — uploads get deleted;
   deletion is itself a provenance fact worth recording.
2. Reverse-search **keyframes**, not whole videos: screenshots at the start
   and at distinctive moments, plus platform-generated thumbnails (thumbnail
   tools extract them and offer one-click reverse search).
3. Thumbnail hits may no longer display on live pages — **cached search-result
   snapshots** can still reveal which video carried the thumbnail, leading to
   the original title.
4. Search the recovered title, sort uploads by date, take the **oldest**
   upload as the likely original.
5. Profile the uploader: role-consistent history (official, military, local)
   raises confidence that this upload is the source.
6. Recycled content is common: check for mismatched chyrons, wrong-language
   audio, or seasonal/weather inconsistency with the claimed event.

## Attribution vs observation reliability

Tracker and registry data mix several reliabilities — never let a strong one
bleed into a weak one:

- **position/measurement reliability** — usually high for the sensor itself;
- **attribution reliability** — ownership/operator databases can be stale or
  misleading, especially for private or transferred assets;
- **coverage completeness** — receiver networks are uneven; absence of a
  signal is not absence of the aircraft/vessel/device (transmitters may be
  off, non-compliant, or in coverage gaps);
- **classifier reliability** — automated or LLM-assisted category labels carry
  hallucination risk; treat as hints, never as ground truth.

Independent corroboration rule: a registry entry and a tracker plot are only
independent if they derive from different underlying fact-sources. Verify
ownership claims through a second source before treating them as established.

## Baseline comparison

A single observation means little without a baseline. To claim "unusually
high activity", first query the normal level over the same area/type/heading
filters across a comparison period, then compare — the anomaly is the
difference from baseline, not the raw count.
