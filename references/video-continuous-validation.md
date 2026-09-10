# Continuous-Interval Validation for Short Video

Use when a conclusion depends on a feature visible for only part of a clip:
skylines, ridges, reflections, signs, gestures, screens, or object motion.

## Discovery versus proof

A sparse contact sheet is a discovery index. It can answer “where should I look?”
but not reliably direction, persistence, ordering, or complete shape.

## Procedure

1. Record duration, frame rate, and reported frame count.
2. Make a cheap contact sheet to locate candidate intervals.
3. Extract source frames without resizing:

   ```text
   terminal(command="mkdir -p '<derived>/all-frames' && ffmpeg -hide_banner -loglevel error -i '<video>' -fps_mode passthrough '<derived>/all-frames/frame-%04d.png' -y")
   ```

4. Count extracted frames and compare with the reported count.
5. Review the entire useful interval; presentation filmstrips do not replace
   inspection of intervening frames.
6. Match supplied screenshots to candidate frames and inspect neighbors.
7. Trace the actual boundary; image `y` increases downward. Do not use a tilted
   sill, sash, substitute horizon, or camera roll as a slope reference.
8. Separate image-space direction, camera orientation, and geographic bearing.
9. Preserve correction history and invalidate dependent downstream claims.

## Validation tests

A claim is conclusion-grade only when it persists across neighboring frames, is
not an occluder/frame/reflection/artifact, remains consistent under camera motion,
and states visible versus hidden portions separately.

## Efficient escalation

Start cheap, then escalate when a decisive transient clue appears or a visual
claim is disputed. For a short clip with a few hundred frames, full local
extraction is usually cheap and avoids repeated external-model calls.
