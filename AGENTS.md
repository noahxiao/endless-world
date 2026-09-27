# AGENTS.md — Endless World

Code-driven video and animation project. Each topic or episode is a self-contained folder; only genuinely reusable material lives in `shared/`.

## Core rule: one episode = one folder

Every new topic or episode gets its own folder under `episodes/`. Everything needed to produce that video lives inside it: script, storyboard, scenes/code, episode-specific assets, voiceover, captions, render config, and outputs.

An agent working on an episode should not need to touch anything outside that folder except to **read from** `shared/`.

Promote something to `shared/` only when it is used, or clearly will be used, by more than one episode. If in doubt, keep it in the episode. Promote it later when a second episode needs it.

## Repository layout

```
endless-world/
├── AGENTS.md                 # this file
├── package.json              # root workspace (tooling, scripts)
├── shared/                   # reused across episodes, read-only from an episode's point of view
│   ├── brand/                # logos, color tokens, fonts, intro/outro stingers, watermark
│   ├── music/                # licensed music beds, SFX (with LICENSES.md)
│   ├── captions/             # caption styles/components, subtitle tooling (SRT/VTT helpers)
│   ├── components/           # reusable animation components (titles, lower-thirds, transitions)
│   ├── skills/               # agent skills/playbooks (e.g. new-episode, render, captioning)
│   └── templates/
│       └── episode/          # scaffold copied when creating a new episode
└── episodes/
    └── 001-some-topic/       # one folder per episode
```

### Episode folder layout

```
episodes/NNN-slug/
├── README.md          # status, one-line pitch, target length/format, links, decisions log
├── episode.json       # metadata: id, title, slug, status, aspect ratio, fps, duration, platforms
├── script.md          # narration / on-screen text, broken into numbered scenes
├── storyboard.md      # per-scene visual plan, timings, notes
├── src/               # animation code for this episode (scenes, compositions, local components)
│   ├── index.ts       # entry / composition registration
│   └── scenes/        # one file per scene: 01-intro.tsx, 02-....tsx
├── assets/            # images, footage, data, and fonts used only by this episode
├── audio/             # voiceover takes, episode-specific SFX, final mix stems
├── captions/          # generated .srt/.vtt for this episode
├── research/          # sources, notes, references for the topic
└── out/               # renders (git-ignored): drafts, finals, thumbnails
```

## Naming conventions

- Episode folders: `NNN-kebab-slug`, zero-padded and sequential (for example `001-black-holes` or `002-how-tides-work`). Never renumber an existing episode.
- Scene files: `NN-short-name` in play order.
- Use kebab-case for asset names. Include a version suffix only when you need several versions (`hero-v2.png`).
- Renders: `out/<slug>-<format>-<draft|final>-<YYYYMMDD>.mp4` (for example `black-holes-16x9-final-20260925.mp4`).

## Creating a new episode

1. Find the next free number in `episodes/`.
2. Copy `shared/templates/episode/` to `episodes/NNN-slug/`.
3. Fill in `episode.json` and `README.md` (pitch, target length, aspect ratio, platforms).
4. Draft `script.md`, then `storyboard.md`, before writing any animation code.
5. Build scenes in `src/scenes/`, one scene per file, and register them in `src/index.ts`.
6. Generate captions into `captions/` with the shared caption tooling.
7. Render drafts into `out/` and review them. Render the final only after sign-off.

If a `shared/skills/new-episode` skill exists, follow it instead of the steps above.

## Rules for working with `shared/`

- Episodes **import** from `shared/`. They never modify shared files as a side effect of episode work.
- A change to a shared component can alter already-finished episodes. Before you change one, check which episodes use it (`grep -r "shared/components/<name>" episodes/`). Make the change backward-compatible, or add a new variant.
- Brand values (colors, fonts, logo usage, intro/outro) come only from `shared/brand/`. Don't hardcode brand colors in an episode.
- Every music or SFX file in `shared/music/` needs an entry in `shared/music/LICENSES.md` (source, license, attribution text).

## Code conventions

- Default stack: **Remotion** (React + TypeScript) for compositions and rendering. Changing the stack is a project-level decision, so record it here if it happens.
- Animation must be deterministic and driven by the frame number (`useCurrentFrame`). Don't use wall-clock time, unseeded randomness, or network calls during render.
- Put timings in seconds × fps, with constants at the top of each scene. Avoid magic frame numbers scattered through the code.
- Keep each scene self-contained and previewable on its own.
- Default output formats: 1920×1080 at 30 fps (16:9) and 1080×1920 at 30 fps (9:16) for shorts. Each episode sets its own values in `episode.json`.

## What goes where: quick reference

| Thing | Location |
|---|---|
| Logo, brand colors, fonts, intro/outro | `shared/brand/` |
| Background music used in many episodes | `shared/music/` |
| Caption style, SRT/VTT generator | `shared/captions/` |
| Title card or lower-third used everywhere | `shared/components/` |
| Agent skills and playbooks | `shared/skills/` |
| Script, storyboard, research for one topic | `episodes/NNN-slug/` |
| An illustration made for one episode | `episodes/NNN-slug/assets/` |
| Voiceover for one episode | `episodes/NNN-slug/audio/` |
| Generated captions for one episode | `episodes/NNN-slug/captions/` |
| Rendered video | `episodes/NNN-slug/out/` (git-ignored) |

## Git

- Ignore: `episodes/*/out/`, `node_modules/`, and large raw footage. Use Git LFS for large binary assets you need to keep.
- Commit messages should start with the scope: `ep001: add scene 3 animation`, `shared/brand: update logo`.
