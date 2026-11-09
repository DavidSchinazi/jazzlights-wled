# WLED with JazzLights

Release images of [WLED](https://github.com/wled/WLED) with the
[JazzLights](https://github.com/DavidSchinazi/jazzlights) usermod, which lets a WLED device
sync patterns with JazzLights devices over Wi-Fi and Bluetooth. The usermod and its build
live in the JazzLights repository; see
[extras/docs/WLED.md](https://github.com/DavidSchinazi/jazzlights/blob/main/extras/docs/WLED.md).

This repository only holds the releases, so that WLED's one-click update keeps a device on
images with the usermod. Images built with the usermod point WLED's update page here, and
WLED installs the asset of the latest release whose name ends in
`_<version>_<release name>.bin`, where the release name is the device's, such as
`ESP32_JazzLights`.

| Image | Board |
|---|---|
| `WLED_<version>_ESP32_JazzLights.bin` | ESP32, such as an M5Stack ATOM Matrix |
| `WLED_<version>_ESP32-S3_8MB_none_JazzLights.bin` | ESP32-S3 with 8 MB of flash, such as an M5Stack ATOM S3 Lite |
| `WLED_<version>_ESP32-C3_JazzLights.bin` | ESP32-C3, such as an M5Stamp C3U |
| `WLED_<version>_ESP32-C6_4MB_JazzLights.bin` | ESP32-C6 with 4 MB of flash, such as an M5Stack NanoC6 (no Bluetooth) |

Versions are WLED's version followed by `-jl.<n>`, where `<n>` counts releases from this
repository, for example `17.0.0-devV5-jl.3`.

## Publishing a release

In this repository's Actions tab, run the **Release** workflow, with the JazzLights branch,
tag or commit to build (`main` by default). It runs `extras/wled/build.sh` from that
JazzLights commit, which builds WLED at the commit pinned there, and publishes the images as
a new latest release.
