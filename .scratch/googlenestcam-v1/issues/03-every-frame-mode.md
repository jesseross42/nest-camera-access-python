# 03: Every-frame mode

**What to build:** A developer who must not miss a Frame calls `cam.stream(frames="all")` and gets every Frame in order. They can set `queue_size`. When the queue is full, the next read raises a clear error by default, or with `on_full="drop_oldest"` the oldest Frame is dropped, a warning is given once, and `s.dropped` counts the drops.

**Blocked by:** 02

**Status:** resolved

- [x] `frames="latest"` stays the default; `frames="all"` gives every Frame in order.
- [x] `queue_size` can be set.
- [x] Full queue raises a clear error from `frames()` by default.
- [x] `on_full="drop_oldest"` drops the oldest, warns once, and `s.dropped` gives the count.
- [x] Unit tests use the fake-Google kit sending fast and a slow reader.
- [x] `make check` and `make test` pass.

## Comments

- 2026-11-14: Merged to `main`. `make check` and `make test` (149 tests) pass.
