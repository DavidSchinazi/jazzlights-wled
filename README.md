# WLED with JazzLights

Release images of [WLED](https://github.com/wled/WLED) with the
[JazzLights](https://github.com/DavidSchinazi/jazzlights) usermod, which lets a WLED device
sync patterns with JazzLights devices over Wi-Fi and Bluetooth. The usermod and its build
live in the JazzLights repository; see
[extras/docs/WLED.md](https://github.com/DavidSchinazi/jazzlights/blob/main/extras/docs/WLED.md).

This repository only holds the releases. Images built with the usermod point WLED's
update page here. To update, download the asset of the latest release whose name ends in
`_<version>_<release name>.bin`, where the release name is the device's, such as
`ESP32_JazzLights`, and upload it on WLED's update page. WLED refuses stock images, which
would remove the usermod.

WLED's one-click update looks for that same asset, but downloads it through WLED's
`download.wled.me` mirror, which only serves an allowlist of repositories that doesn't
include this one. Until it does, one click fails without flashing anything.

| Image | Board |
|---|---|
| `WLED_<version>_ESP32_JazzLights.bin` | ESP32, such as an M5Stack ATOM Matrix |
| `WLED_<version>_ESP32-S3_8MB_none_JazzLights.bin` | ESP32-S3 with 8 MB of flash, such as an M5Stack ATOM S3 Lite |
| `WLED_<version>_ESP32-S3_8MB_opi_JazzLights.bin` | ESP32-S3 with 8 MB of flash and 8 MB of octal PSRAM, such as an M5Stack ATOMS3R |
| `WLED_<version>_ESP32-C3_JazzLights.bin` | ESP32-C3, such as an M5Stamp C3U |
| `WLED_<version>_ESP32-C6_4MB_JazzLights.bin` | ESP32-C6 with 4 MB of flash, such as an M5Stack NanoC6 (no Bluetooth) |

Versions are WLED's version followed by `-jl.<n>`, where `<n>` counts releases from this
repository, for example `17.0.0-devV5-jl.3`.

## Publishing a release

In this repository's Actions tab, run the **Release** workflow, with the JazzLights branch,
tag or commit to build (`main` by default). It runs `extras/wled/build.sh` from that
JazzLights commit, which builds WLED at the commit pinned there, and publishes the images as
a new latest release.
