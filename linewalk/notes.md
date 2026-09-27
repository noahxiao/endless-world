# Linewalk — code-only endless line-drawing animation

Status (2026-09-24): working framework + 100 s demo video + live studio artifact.

- Renders any length (pure function of seed + time; world generated per segment). Node + @napi-rs/canvas → ffmpeg MP4; browser studio for live preview.
- Drawing order (per Noah's feedback): nothing exists ahead of the pen except faint, wavering graphite guesses that settle as the pen approaches → the pen inks the lines → colour is brushed in afterwards with a ragged brush front; land/hill paint trails behind the pen. Config: style.ghost, style.lineShare, style.paintLag, style.revealAt (0.8).
- Looks: `watercolor` (per-chapter palettes, sky gradients, hill/ground washes, misregistered fills, grain, vignette; colours cross-fade between chapters) and `ink` (classic single-colour line art with themes).
- Chapters: town, park, countryside, seaside, city, jurassic, deepsea (walkers swim with helmets + bubbles), space (moon-bounce, helmets), iceland (aurora, geysers, puffins), swiss (chalets, cows, cable car, alps), fantasy (mushrooms, castle, wizard tower, dragon), candy (lollipops, gingerbread, cupcakes).
- Walkers: kid with balloon + dog on leash; jump cracks/puddles.
- Extend via registerElement / registerBiome; `scripts/gallery.js <biome>` renders an element catalogue.
- Studio artifact: https://claude.ai/artifact/PeWsbkVfVok6EhBeAqYPo6
- Render time: ~5 s of compute per 1 s of 1080p video on 2 cores (100 s demo ≈ 9 min).

Ideas not yet done: vertical 9:16 layout tuning, music/sfx track, more walkers, per-chapter title cards.
