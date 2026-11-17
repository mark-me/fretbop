# Fretbop

Learn jazz on fretted string instruments — chord progressions first, then soloing — without a teacher and without reading sheet music.

> **Status:** concept. No code yet. Design decisions are recorded in [`docs/adr/`](docs/adr/), domain terms in [`GLOSSARY.md`](GLOSSARY.md).

## What it is

Fretbop is a self-hosted web app that teaches jazz to players who know their instrument a little, but know no music theory and cannot read notation. It starts with soprano and baritone ukulele and is designed to extend to guitar and bass guitar.

- **Learn by ear and by shape.** Chord diagrams, fretboard views and playable audio for every chord, lick and progression.
- **Feedback through the microphone.** The app listens, checks what you played and tells you what to fix — which string isn't sounding, which chord change came late.
- **Theory just in time.** Concepts are named after you have played and heard them, never before.
- **Runs on your home server.** Your recordings and progress stay with you.

## Roadmap

| Phase | Deliverable |
|---|---|
| 0 | Theory engine, voicing generator, SVG fretboard, playback |
| 1 | One content package (seventh chords, ii-V-I) with play-along |
| 2 | Tuner, single-note pitch detection, signal-quality checks |
| 3 | Chord verification and per-string diagnosis |
| 4 | Opt-in local recordings and threshold tuning |

## Planned stack

Flask · Flask-Babel · htmx · Bootstrap · PyYAML · Pydantic · pychord · pitchy · Meyda · Tone.js · svguitar · custom SVG fretboard · abcjs (later)

Lessons live as YAML content packages in a separate repository.

## License

Code: [MIT](LICENSE). Lesson content (separate repository): CC-BY-4.0.
