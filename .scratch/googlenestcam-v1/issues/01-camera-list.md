# 01: Camera list

**What to build:** A developer who has done Login can call `gnc.list_cameras()` and see every Camera on their account with its Google Home name and Google ID. `gnc.camera("Front door")` or `gnc.camera("<id>")` gives back that Camera. This works as a normal sync call, in a script and inside Jupyter, because it runs on the package's hidden background event loop (ADR 0002), which this ticket builds. Includes the small SDM client (list devices, run a device command) using the existing `GoogleAuth`, and the advanced `transport=` keyword so tests can use a fake Google.

**Blocked by:** None (can start immediately)

**Status:** resolved

- [x] `list_cameras()` returns every Camera that supports WebRTC, each with `.name` and `.id`.
- [x] RTSP-only Cameras and non-camera devices are left out.
- [x] Name falls back to the room name when the custom name is empty.
- [x] `camera()` finds a Camera by short ID, full `enterprises/.../devices/...` ID, or name.
- [x] Unknown name: clear error that lists the names that exist.
- [x] Two Cameras with the same name: clear error that lists their IDs.
- [x] No Token: the existing `on_missing_token` behaviour applies (Login or `MissingTokenError`).
- [x] Google errors become a package error with Google's message.
- [x] Sync call works inside a running event loop (as in Jupyter).
- [x] Unit tests through the public API with a fake httpx transport; one `real_camera` test.
- [x] `make check` and `make test` pass.

## Comments

- 2026-11-14: Merged to `main`. `make test_real_cameras` passed on real Cameras on 2026-10-07; `make check` and `make test` (149 tests) pass.
