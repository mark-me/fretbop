# All audio analysis runs in the browser

Pitch detection, chroma analysis and onset detection run client-side (Web Audio API, AudioWorklet). This gives low latency and keeps audio on the device; it leaves the device only when the learner explicitly enables recording.

## Considered Options

- **Server-side analysis in Python** — rejected: round-trip latency is too high for real-time feedback, and it would send all audio to the server by default.
