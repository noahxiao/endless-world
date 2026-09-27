# Skyward Voyage: code-only 3D flying journey

Status (2026-09-25): live page published (version 7): https://claude.ai/artifact/Np9XAtBMu1JAqr9a2P5vsq
Local project (2026-09-25): ~/proj/skyward-voyage on Noah's Mac. It is a Vite + npm project.

- Files in the local project: index.html (HUD markup), styles.css, src/main.js (the whole world, one ES module), scripts/setup-hands.mjs (copies the MediaPipe wasm and downloads the hand model into public/mediapipe on postinstall).
- Commands: `npm install`, then `npm run dev` (http://localhost:5173) or `npm run build` (writes dist/).
- The local project is the source of truth for future edits; skyward-voyage.html here is the published single-file version.

## Features (up to v6)
- Three.js (r160): bloom, colour grading, ACES tone mapping, sun shadows, height fog, detailed terrain with surf and wet sand, sun-lit billboard clouds, optional GTAO.
- Quality menu: Low, High (default), Ultra.
- Travel menu: jump to the next land of a chosen type (time of day kept).
- Mounts: Storm drake (default), Phoenix, Sky eagle. Camera: Chase or Rider view (key C).
- 15 lands, including Arcane highlands, Beast sanctuary, The frozen march, Walled heartland, Corsair seas.
- Ground events: war, deer hunt, naval battle, festival, capital parade.
- Generative music with a mood per land (key M). Recording: key R saves an MP4 with music.

## v7 (2026-09-25)
- Steering: Auto / Reins / Hands. Arrows/WASD, Shift boost, gamepad; drag to steer in Reins mode; autopilot resumes 2.5 s after input.
- Hand gestures (MediaPipe): both hands up/down to climb/dive, lower one hand to turn, hands toward camera to speed up. Works through the local project (the artifact viewer blocks the camera).
- Physics: obstacle cylinders stop passing through towers, walls, islands, giants etc.
- Symbolic sights per land (titans, army of the dead, viaduct steam train, thunderbird, sea king).
- Realism: jointed capsule people with GPU walk cycle, world-space surface detail, swaying trees, soft smoke.

Known issues: heavy on the GPU; frozen march terrain sometimes blends with neighbours.
Next ideas: CC0 rigged glTF models, weather, a city siege, split src/main.js into modules.
