# Explanations use note names and fret distances, not interval names

ADR 0001 says theory is named only after the learner has played and heard it, but learners also want to know *why* a sound works. Explanations therefore go deep, but only in terms the learner can see and hear: note names and fret distances, shown on the fretboard diagram with a replay button. Abstract interval names ("third", "tritone", "half step") are not used. Chord names such as "major seventh" are allowed, because they name chords the learner has already played.

## Considered Options

- **Short explanations (name plus a sentence about the sound)**: rejected. Too shallow to show why a progression works.
- **Full explanations using standard interval names**: rejected. Every interval name would be a term the learner has never played or heard, which breaks ADR 0001.

## Consequences

- Interval names can only be introduced in a later package, after the learner has met those intervals as fret distances.
