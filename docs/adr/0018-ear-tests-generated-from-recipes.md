# Ear test questions are generated from recipes, not stored as recordings

An ear test is mastered when 8 of the learner's last 10 answers are right. With a fixed set of recorded questions, a learner could pass by recognising individual clips instead of the sound being taught. Packages therefore describe each ear test as a recipe (what is asked and which sounds may be used), and the Python theory engine generates each question from it, varying key, voicing and chords within the recipe. This also keeps all music creation in the engine (ADR 0003) and keeps packages free of audio files.

## Considered Options

- **Recorded clips in the package**: rejected. Simple to build, but clips can be learned by heart, and they make packages large and instrument-specific.

## Consequences

- The engine must generate ear-test questions from recipes before package 1 can be used. This is a requirement for phase 0 or phase 1 (brief topic 4).
- The generated sound is synthesised, not a recording of a real ukulele.
