# Package 1 outline: from the pull to the two-five-one

> **Status: draft, not validated.** No musician has reviewed this outline. It will be checked by the project owner working through each lesson as the first learner: anything confusing, too fast or boring counts as a defect. This file moves to the content repository once that exists (ADR 0004).

This outline is the brief for writing package 1. Terms in **bold** are defined in [`GLOSSARY.md`](../GLOSSARY.md). Read [`docs/adr/`](adr/) before writing content, especially 0001, 0002, 0004, 0006, 0016, 0017 and 0018.

## Goal of the package

After lesson 10 the learner can **comp** a major ii-V-I in C and F (G optional) with seventh chords, four strums per bar at a slow swing tempo along with a play-along, and can recognise a ii-V-I by ear.

## Learner

- No theory, no notation, no teacher. Soprano (GCEA, re-entrant) or baritone (DGBE) ukulele.
- **Entry level:** plays C, Am, F and G7, changes between them slowly, and keeps a steady beat. The **entry check** confirms this before lesson 1.

## Rules for every lesson

1. **Sound first, name last.** A concept is named only in the closing **explanation** of the lesson in which the learner first played and heard it, never earlier. Lesson titles describe a sound or an action, never a term.
2. **Instrument-neutral content.** Lessons use chord symbols, bars and keys. They never contain **voicings**: the engine generates them per instrument (ADR 0002, 0003). A lesson only declares a voicing preference: `easiest` or `voice-led`.
3. **At least one ear test per lesson.** Package validation enforces this. In phase 1 ear tests are the only gate (ADR 0016). Every ear test is written as an **ear test recipe**, never as recorded clips (ADR 0018).
4. **Exercises declare mastery thresholds** even though phase 1 cannot measure them. They are enforced once detectors ship. See "Mastery thresholds" below for the values.
5. **Warm-up.** Every lesson from 2 onwards opens with one **warm-up** exercise repeating the previous lesson. It does not count towards mastery.
6. **Length.** One lesson fits in a single 15–20 minute practice session. Mastering it may take several sessions. Split any lesson that runs longer.
7. **Explanations go deep, in fret distances.** An explanation gives the name plus why it works, using **note names** and **fret distances** only. Every claim is shown on the fretboard diagram and comes with a replay button. Abstract interval names ("third", "tritone", "half step") are not used. Chord names such as "major seventh" are fine, because the learner has played those chords.
8. **One comping rhythm** throughout: four strums per bar, accented on beats 2 and 4. The play-along supplies the swing feel. No swing eighths, no other rhythms.
9. **Counting from home.** "Five-one" and "two-five-one" are introduced by counting letter names up from the home note (C=1, D=2, E=3, F=4, G=5). No scale knowledge is assumed.
10. **Stable step IDs.** Every step has an ID that never changes between package versions, so recorded mastery survives updates. A mastered lesson stays mastered whatever an update changes.

## Ear test kinds allowed in this package

| Kind | Question | First used |
| --- | --- | --- |
| Same or different | Were these two chords the same or different? | Entry check |
| Resolution | Did that end at home? | 1 |
| Accent | Is the accent on 2 and 4, or on 1 and 3? | 2 |
| Quality discrimination | Which chord colour was that? First 2 choices, later 3 | 3 |
| Voice-leading comparison | Same progression played twice: which version moves less? | 7 |
| Progression recognition | Which of these is a ii-V-I? | 9 |

Out of scope: naming root notes, intervals or chord degrees by ear.

## Mastery thresholds

These are the package defaults. A step may override them, but only with a reason. They are first test values, to be adjusted after the first-learner walkthrough.

**Ear tests:** mastered when 8 of the learner's last 10 answers are right. Replays are unlimited and there is no time limit.

**Exercises:**

| Steps | Mastery tempo | Bars in a row | Bars right |
| --- | --- | --- | --- |
| Entry check, lessons 1–6 | 60 bpm | 8 | 7 of 8 |
| Lessons 7–9 | 70 bpm | 8 | 7 of 8 |
| Lesson 10 | 80 bpm | 16 (the full form) | 14 of 16 |

A bar is right when the expected chord sounds and the change lands on time. How close to the beat counts as "on time" is a **detector threshold** (ADR 0007), not part of the package. Warm-ups have no mastery threshold.

### App behaviour the content can rely on

The content does not need to describe this behaviour; the app provides it for every package.

- Practice at any tempo below the **mastery tempo** is allowed but does not count.
- The learner's rolling count is always visible ("6 of your last 10 right, need 8").
- After a wrong ear-test answer, the app plays both options side by side. After 20 answers without reaching mastery, it offers **listening mode**.
- After 3 attempts at an exercise without reaching mastery, the app gives specific feedback and suggests practising 10 bpm slower. Voicings never change.
- A mastered lesson opens the next one. The learner decides when to start it.

## Entry check

- **Exercise:** C – Am – F – G7, one chord per bar, with the play-along at 60 bpm. Unmeasured in phase 1, so the entry check is only advisory until phase 3.
- **Ear test:** same or different.
- **On failure:** say exactly what is missing (for example "switching between C and G7 in time") and allow a retry. No external links.

## Lessons

| # | Working title | Key | Voicings | New material | Ear test | Named at close |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | The chord that wants to go home | C | easiest | G7 → C | Resolution | dominant seventh; tension and resolution |
| 2 | Jazz time | C | easiest | Comping G7 → C, accent 2 and 4, swing play-along | Accent | comping; backbeat |
| 3 | A dreamier home | C | easiest | G7 → Cmaj7 | Quality: 7 or maj7 | major seventh |
| 4 | The same pull, somewhere else | F | easiest | C7 → Fmaj7 | Resolution | five-one; key |
| 5 | The soft chord | C, F | easiest | Dm7, Gm7 | Quality: 7 / maj7 / m7 | minor seventh |
| 6 | One more step back | C | easiest | Dm7 → G7 → Cmaj7 | Resolution | two-five-one |
| 7 | Lazy fingers | C | voice-led | Same ii-V-I, voice-led | Voice-leading comparison | voice leading |
| 8 | The pattern travels | F | voice-led | Gm7 → C7 → Fmaj7 | Quality, inside a progression | nothing new |
| 9 | Spot the two-five-one | C, F | voice-led | Alternating ii-V-I in C and F | Progression recognition | changing key |
| 10 | First form | C, F, (G) | voice-led | 16-bar play-along (below) | Progression recognition + quality | review only |

### Explanation notes per lesson

Musical facts the explanations build on, so the content author doesn't have to work them out. All distances are in frets (rule 7).

1. G7 = G B D F. B wants to rise one fret to C, and F wants to fall one fret to E. Those two pulls are the tension, and C (C E G) is where they resolve.
2. Jazz accents beats 2 and 4. Most pop and folk strumming leans on 1 and 3.
3. Cmaj7 = C E G B. The added B sits one fret below the home note C, which gives the soft, unresolved "dreamy" colour.
4. C7 = C E G B♭ → Fmaj7 = F A C E. E rises one fret to F, and B♭ falls one fret to A. Counting up from F (F=1 … C=5), C is the five, so this is the same five-one as G7 → C.
5. Dm7 = D F A C, Gm7 = G B♭ D F. Compared with D7 (D F♯ A C), Dm7 has F where D7 has F♯. That one note sits one fret lower, and it gives the darker, softer colour.
6. Counting up from C, D is the two. Dm7 → G7 → Cmaj7 is the two-five-one, the most common chord sequence in jazz.
7. Dm7 → G7: C falls one fret to B, and F stays. G7 → Cmaj7: F falls one fret to E, and B stays. In voice-led voicings two notes do almost all the work, so the fingers barely move.
8. In F: Gm7 → C7 → Fmaj7. Same pattern, same finger movement, different starting place.
9. A key is the home a progression is pulling towards. Moving the two-five-one moves the home.
10. No new concept: the closing explanation reviews the names from lessons 1–9.

### Lesson 10 form

16 bars, one chord per bar:

```text
| Dm7  | G7   | Cmaj7 | Cmaj7 |
| Dm7  | G7   | Cmaj7 | Cmaj7 |
| Gm7  | C7   | Fmaj7 | Fmaj7 |
| Dm7  | G7   | Cmaj7 | Cmaj7 |
```

Optional bonus in G: `| Am7 | D7 | Gmaj7 | Gmaj7 |`.

## Engine requirements this outline implies (phase 0)

- A voicing generator with two modes: `easiest` (standalone voicing per chord) and `voice-led` (minimal movement across a progression), for both instruments.
- A play-along that supports swing feel, a one-chord-per-bar grid and an adjustable tempo.
- Generation of ear-test questions from ear test recipes, varying key, voicing and chords (ADR 0018).

## Open questions

- **What "done" means for this package** is brief topic 4, which should include the first-learner walkthrough.
