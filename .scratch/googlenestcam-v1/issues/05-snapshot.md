# 05: Snapshot

**What to build:** `cam.snapshot()` and `await cam.snapshot_async()` give one Frame. They open a Stream with Audio off, wait for the first Frame, and close it. The docstring and design doc say it is slow and to use a Stream for many Frames.

**Blocked by:** 02

**Status:** resolved

- [x] Returns one Frame.
- [x] The Stream is always stopped at Google, even on error or timeout.
- [x] Clear timeout error if no Frame arrives; timeout can be set.
- [x] Docstring and design doc say it is slow.
- [x] Unit tests with the fake-Google kit; `real_camera` test written but not yet run.
- [x] `make check` and `make test` pass.

## Comments

- 2026-11-14: Merged to `main`. `make test_real_cameras` passed on real Cameras on 2026-10-07; `make check` and `make test` (149 tests) pass.
