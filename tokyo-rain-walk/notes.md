# Tokyo Rain Walk: code-only rainy night city walk

Status (2026-09-27): the live page is version 6, "Buildings & objects sheet": https://claude.ai/artifact/GPH9E1TvceKwHWrqtP9G7J
Earlier versions stay in the artifact's version history. Version 2 was the realistic one.

## What Noah asked for
- A cinematic first-person walk through Tokyo at night in the rain. The camera walks by itself.
- A record button that saves an MP4 with the sound included.
- Background sound effects and music.
- It should run as long as possible or loop, walking to different places.
- v2: more realistic and detailed.
- v3: restyle to his reference image, "Minimal cinematic low-poly Tokyo — matte clay materials, simple geometry, neon reflections, soft fog, no detailed textures". The humans should match exactly.
- v4: fix a black block that appeared on mobile, and fix ghosted multiple reflections on the ground.
- v5: follow his character and vehicle design sheet.
- v6: follow his "Tokyo Night (Rain) 3D asset sheet": buildings (modular), street modules, street props, environment objects, nature/background and small objects.

## Art direction as built
- Palette and lighting: deep blue fog; soft blue environment light and a strong hemisphere fill; bloom with a clean grade; no lightning.
- Buildings: chamfered clay volumes in slate-blues; facade shader draws recessed window frames, light sills, floor slab bands and window crosses.
  - Archetypes: small shop (warm walls, sloped awning, green tree), hotel (two pink ホテル vertical signs), 東京 high-rise (large violet vertical sign), office (blue antenna beacon).
  - Rooftop kit: AC units, water tanks on legs, antenna masts with red or blue beacons, roof railings.
- Signs: pastel lightboxes with icons; atlas cells ホテル, 東京, カフェ, 本, ラーメン, plus 新聞, a phone-booth interior, a ねこカフェ ad, a コーヒー board and a 居酒屋 lantern.
- Street modules and props: bus stop shelters, benches, trash bins, planters, potted plants, crates with flowers, cardboard boxes, red mailboxes, news stands, glowing phone booths, round street signs, cone and barrier road works, izakaya red lanterns, ラーメン pole signs, wall AC units, utility poles with sagging wires, road mirrors, manholes.
- Shrine module (occasional lot): red torii, glowing stone lanterns, stone path, steps, small hall with red chochin, green trees.
- Street furniture: dome lamps, orb posts, cherry trees, street trees, topiary, festoon bulbs in lanes, an elevated railway with a lit train, a glowing lattice tower on the skyline.
- Pedestrians: instanced chibi clay figures (girl, boy, woman, office worker, student, elderly, kid in yellow raincoat, tourist); mostly clear 8-panel umbrellas.
- Vehicles: toy-rounded taxi, compact, kei car, van, ねこ便 delivery truck, white/teal bus, kei flatbed, coupe; silver train with teal stripe; parked scooters and bicycles; street cats.
- Wet ground uses a jittered, mip-blurred smear. An HDR sanitize pass stops mobile black blocks.

## Not yet built from the v6 sheet
- River or canal module with a bridge (needs a change to the street grid).
- Moving cyclists and scooter riders.

## Unchanged systems
- Endless seeded street grid, signals and districts with real chōme names.
- Synthesised audio and a generative city-pop score.
- MP4 recording with audio.

## Files in this folder
- tokyo-rain-walk.html — the full page as published on 27 Sep (includes your latest edits); open in Chrome.
- assets/walker.json — a supporting file that was published alongside the page (not referenced by the current version).
