# pkg-polo (Menta Linux)

Debian packaging of [Polo](https://github.com/KeremSoke/polo), the Wayland
compositor/session for MATE, built from the latest upstream commit.

Version: `1.0.1+git20261113.1154525-1menta1` (`<meson version>+git<date>.<commit>-<rev>menta<N>`).
The CI clones that exact commit, runs `meson subprojects download` to vendor the
patched Weston into the orig tarball, and builds on `debian:unstable` against the
Menta `libmate-desktop` (from `menta-linux/pkg-mate-desktop` `latest` release).

Meson options: all sensible ones on (`xwayland`, `shell-ui`, `systemd`); off:
`tests` (needs a display backend), `test-protocol`, `debug-protocol`,
`debug-kill`, `fuzz`, `strict` (dev/CI-only options, "never in releases").
The private libweston lives in `/usr/lib/<triplet>/polo/`; its headers and
pkg-config files are not shipped.

Every push to `master` publishes the rolling `latest` release; `menta/*` tags
publish a versioned one.
