# The microphone verifies expected chords; per-string diagnosis comes from a string check

Chord detection on ukulele is risky: chords such as Dm7 and F6 share all their notes, re-entrant tuning hides the root, and the notes are quiet and short. Fretbop therefore narrows what the microphone must do. In a strum it only verifies that the chord the exercise expects is sounding, and checks timing after a per-device calibration. To tell the learner which string is wrong, it asks them to pluck the chord one string at a time and judges each note with the single-note detector from phase 2. That detector is mature technology, which is why the string check ships in phase 2 as feedback that does not count towards mastery.

## Considered Options

- **Chord recognition (working out which chord is played)**: rejected. It is much harder, cannot tell chords with the same notes apart, and exercises always know which chord to expect.
- **Per-string diagnosis from the strum**: rejected. Separating individual strings in a polyphonic strum is the least reliable part of the problem, and the string check gives the same answer with proven technology.

## Consequences

- Before phase 1, a time-boxed detection spike (about 20 hours) measures chord verification, the string check and timing on recordings of both ukuleles. It uses the same feature-extraction code as the browser.
- Each instrument gets a detection level from what the spike shows: A (full), B (no chord verification), C (string check only) or D (exercises stay unmeasured, as in phase 1). The result is recorded in its own ADR, and a later release may change it without touching recorded mastery.
- Problems with one learner's setup are still handled by ADR 0006, not by changing the detection level.
