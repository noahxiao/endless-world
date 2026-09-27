# Sierra Painter — paint-then-alive scene (2026-09-24)

Reference: Albert Bierstadt, *Among the Sierra Nevada, California* (1868), public domain (Wikimedia Commons).

Pipeline (code only, pure function of time `render(t)`):
1. **Analysis** — reference read into a 128×76 colour map, k-means to 64 colours (embedded as one char/cell). Geometry (cliff line, skyline, lake, tree line, falls, deer, ducks) measured by hand on gridded crops.
2. **Painting timeline (0–30 s)** — graphite sketch (1.2–6.5) → tonal wash → 3 Hertzmann-style underpainting passes (R=34/15/7, strokes follow tonal contours, colour sampled from the map) → mid glaze → detail passes (cloud impasto, snow massifs with lit/shadow faces, rock facets, cliff striations, falls, conifer silhouettes, oak crowns, lake streaks, grass, reeds, log).
3. **Alive (30 s →)** — WebGL compositor over the painted canvas using masks: sky flow-map drift, lake ripples + glints, wind sway on trees/grass, waterfall streaks, fbm mist, god rays; 2D overlay for deer (grazing), ducks, birds, light motes. Camera static.

Outputs: artifact player (scrub/phase jumps/speed/wallpaper mode) https://claude.ai/artifact/97qaDfTVLo5TRiebM2oQty ; MP4s rendered headless (Playwright + SwiftShader → ffmpeg): full 60 s paint-to-alive video + seamless 30 s wallpaper loop (crossfade).

Source lived in the session workspace (`scene/engine.js`, `data.js`, `page.html`, `build.js`, `render.js`). Reusable for other references: swap REF_GRID/REF_PAL + geometry block `G`.
