# What Matters — paper cut-out short (YouTube video companion)

Status (2026-09-26): v1 rendered, 1:36, 1080p30, soft generated music + paper SFX.

- Style copied from Noah's reference clip ("What is the purpose of life?"): ransom-note letter tiles, handwritten captions on taped paper strips, torn-paper edges with white fringe, paper grain, round-headed stick characters, torn-edge page wipes between scenes.
- Content: condensed from Noah's talking-head script about saved time and "what matters". 9 scenes: title "What do we do with saved time?" → afternoon bar ripped into "1 hour" + "saved time" → three paths (go home / more work / keep building; "do you get to choose?") → two Saturdays split screen → worksheet vs invented game → Darwin quote card "a loss of happiness" → sketchbook vs buzzing phone (week 1-3) → the 10-minute experiment (3 cards) → sunset "GIVE IT A TURN."
- Pipeline: Node + @napi-rs/canvas (lib.js primitives, scenes.js/scenes2.js, main.js timeline) → raw frames → ffmpeg, rendered in 150-frame chunks (one long process ran out of memory). Fonts from @fontsource via npm (Titan One, Bowlby One, Caveat) converted to TTF. music.py makes the score (C–G/B–Am–F, plucks, pad, glockenspiel; quieter for the Darwin scene) and the SFX from cues.json.
- Render: ~2.5 min for the whole film on 2 cores.

Ideas not yet done: vertical 9:16 cut, Noah's real voiceover, a "your story" scene.
