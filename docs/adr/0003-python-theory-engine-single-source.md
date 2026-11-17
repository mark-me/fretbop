# The Python theory engine is the single source of music theory

All theory (chords, voicings, fingerings) lives in the Python engine; the frontend receives voicings as JSON and does no theory of its own.

## Considered Options

- **tonal.js in the frontend** — rejected: it has voicing and voice-leading modules, but using it would create a second theory engine that drifts from the Python one.
