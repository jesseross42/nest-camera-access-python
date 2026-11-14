# 07: Audio

**What to build:** Audio is on by default. `s.audio()` gives Audio chunks with `.samples` (NumPy, 48 kHz) and `.time` on the same clock as Frame time. `cam.stream(audio=False)` turns it off and saves CPU. `frames()` and `audio()` can be read at the same time from two threads. Unread Audio is kept only for the last few seconds, so leaving it on never fills memory. Fix the design doc sketch to show the two-thread way.

**Blocked by:** 02

**Status:** resolved

- [x] `cam.stream()` has Audio on; `audio=False` turns it off and Audio is not decoded.
- [x] Chunks have `.samples` at 48 kHz and `.time` on the same clock as `Frame.time`.
- [x] `frames()` and `audio()` work together from two threads.
- [x] Unread Audio is bounded; oldest chunks are dropped.
- [x] `stream_async()` has the same Audio.
- [x] Design doc shows reading Frames and Audio in two threads.
- [x] Unit tests with the fake-Google kit sending made-up sound; `real_camera` test written but not yet run.
- [x] `make check` and `make test` pass.

## Comments

- 2026-11-14: Merged to `main`. `make test_real_cameras` passed on real Cameras on 2026-10-07; `make check` and `make test` (149 tests) pass.
