# Phase 1 lessons are gated by ear tests only

In phase 1 the app has no microphone input, so it cannot measure exercises. Rather than relax ADR 0006 by allowing self-assessment, phase 1 lessons are gated by their ear tests alone. Exercises are shown and practised but do not gate progress. Each exercise still declares its mastery thresholds in the package, and those thresholds are enforced once the matching detectors ship (single notes in phase 2, chords in phase 3). Content is therefore written once, against the final mastery model.

## Considered Options

- **Self-assessment for exercises in phase 1**: rejected. It would contradict ADR 0006 and turn self-assessment into the normal path, which is exactly what that ADR prevents.
- **No gating at all in phase 1**: rejected. Ear tests are measurable without a microphone, so dropping them would throw away the one reliable signal phase 1 has.

## Consequences

- Every lesson needs at least one ear test, or it has no gate in phase 1.
- When a detector ships, learners who mastered a lesson in phase 1 have unmeasured exercises. How their progress is treated then belongs to the mastery model (brief topic 2).
