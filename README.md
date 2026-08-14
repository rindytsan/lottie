# Lottie

Lottie animations for Raccoon AI, hosted for use as URLs in Wix.

| File | Language | Canvas | Duration |
|---|---|---|---|
| `raccoon-flywheel-zh.json` | 繁體中文 | 1080 × 810 (4:3) | 13.2s, loops seamlessly |
| `raccoon-flywheel-en.json` | English | 1080 × 810 (4:3) | 13.2s, loops seamlessly |

The flywheel: GEO (獲客) → SERVICE (轉換) → CREW (團隊增效) drive each other.
Phase one plays the clockwise loop, phase two the counter-clockwise one.

Text is stored as vector outlines, so no fonts need to load on the page.
Transparent background — designed to sit on a light-coloured section.

## Using these in Wix

Paste the **jsDelivr** URL into the Lottie element's URL field:

```
https://cdn.jsdelivr.net/gh/rindytsan/lottie@main/raccoon-flywheel-en.json
```

jsDelivr is a real CDN and is the reliable option. The `raw.githubusercontent.com`
URL also works but GitHub asks that it not be used as a production CDN, and it is
rate limited.

## Source

Generated from the HyperFrames composition at `videos/raccoon-flywheel`.
To regenerate, see that project's `lottie/` directory and `BRIEF.md`.
