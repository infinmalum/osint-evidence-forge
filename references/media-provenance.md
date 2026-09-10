# Media Provenance and Transcoding Notes

Use this reference when media passed through a messaging platform before analysis.

## Provenance questions

Record the chain when known:

```text
camera capture → gallery edit → platform upload → GIF/video conversion
→ forwarding → desktop download → analyst copy
```

For each step, note whether it may resize, crop, strip tags, remove audio, remux,
or assign a new filename or creation time. Unknown steps stay `unknown`.

## Messaging-platform GIF/video behavior

A chat animation described as a “GIF” may be delivered or downloaded as an MP4
containing H.264 video with no audio stream. Common consequences include:

- non-camera dimensions after resizing;
- stripped GPS, device, lens, and software tags;
- no audio even when the sequence resembles a video;
- generic MP4 brands and handler names;
- platform- or conversion-generated creation fields;
- a download/export filename unrelated to capture time.

Treat these as provenance indicators, not proof of a specific client or path.

## Timestamp authority

| Timestamp | Typical meaning after transcoding | Default confidence |
|---|---|---|
| Filesystem timestamps | local copy/download activity | low |
| Downloaded filename date | export/save event | low |
| MP4 container creation | mux/platform conversion | low |
| Video-track creation | track muxing; sometimes copied | low–medium |
| Camera EXIF with device fields | claimed capture metadata | medium |
| Server message timestamp | upload/send event | medium–high |
| Independent dated observation | corroborated event | high |

A local UTC offset changes filesystem display but does not by itself explain a
platform-generated container timestamp.

## Artifact tests

A candidate detail is more likely real when it persists across source frames,
moves with perspective, has compatible edges, or appears independently. It is
more likely an artifact when it changes erratically, follows macroblocks, appears
only after aggressive enhancement, or vanishes at original resolution.
