# Fretbop

Fretbop teaches jazz chord progressions and soloing on fretted string instruments to players without theory or notation knowledge, learning without a teacher.

## Content structure

**Package**:
A versioned set of lessons that is published and installed as one unit.
_Avoid_: Course, module, content pack

**Lesson**:
An ordered sequence of steps that works towards one learning goal.
_Avoid_: Unit, chapter

**Step**:
The smallest unit inside a lesson and the unit at which mastery is recorded. Every step is exactly one of: exercise, ear test or explanation.
_Avoid_: Task, item

**Exercise**:
A step in which the learner plays something on the instrument.
_Avoid_: Drill, playing step

**Ear test**:
A step in which the learner listens and answers a question about what they heard, without playing.
_Avoid_: Quiz, listening exercise, listening question

**Ear test recipe**:
The description in a package of what an ear test asks and which sounds it may use. The app generates each question from it, so no two runs need sound alike.
_Avoid_: Question bank, template, clip set

**Warm-up**:
An exercise at the start of a lesson that repeats material from the previous lesson. It does not count towards the lesson's mastery.
_Avoid_: Review, recap

**Entry check**:
A short lesson before the first package lesson that confirms the learner has the entry level. It is not counted among the package's lessons.
_Avoid_: Lesson 0, placement test, intake

**Explanation**:
A step that names or explains a concept the learner has already played and heard. It has no mastery of its own.
_Avoid_: Theory step, info

## Music

**Chord quality**:
The kind of seventh chord regardless of its root: dominant seventh, major seventh or minor seventh.
_Avoid_: Chord type, flavour

**Voicing**:
A specific way of playing a chord on an instrument: which note sounds on which string and fret.
_Avoid_: Shape, grip, fingering

**Voice-led**:
Describes voicings chosen so that moving from one chord to the next changes as few notes as possible, by the smallest steps.
_Avoid_: Smooth voicings, close movement

**Fret distance**:
The distance between two notes, counted in frets along one string. It is how Fretbop describes intervals to learners.
_Avoid_: Interval, semitone, half step

**Comping**:
Playing chords as rhythmic accompaniment. In the first package this means four strums per bar, accented on beats 2 and 4.
_Avoid_: Strumming, rhythm playing

## Progress

**Mastered**:
The state of a step whose mastery threshold has been met. Mastery is permanent. A lesson is mastered when all of its ear tests are mastered and all of its exercises except warm-ups are mastered or unmeasured.
_Avoid_: Completed, passed, done

**Unmeasured**:
The state of an exercise that could not be measured because the app lacked the detector it needs, either now or when its lesson was mastered. An unmeasured exercise does not block its lesson.
_Avoid_: Provisionally mastered (that state is reserved for self-assessment after a measurement failure), skipped

**Mastery threshold**:
The teaching rule a step must meet to be mastered, such as "8 of the last 10 answers right" or "8 bars in a row at 70 beats per minute". It belongs to the content.
_Avoid_: Threshold (on its own), pass mark, criteria

**Mastery tempo**:
The lowest play-along tempo at which playing an exercise counts towards its mastery. Practice at any slower tempo is allowed but does not count.
_Avoid_: Target tempo, required speed

**Listening mode**:
An ear-test aid that plays labelled examples of each possible answer without asking questions. It is offered when an ear test is not going well.
_Avoid_: Practice mode, training mode, hint

**Chord verification**:
Checking whether the chord an exercise expects is sounding. Fretbop only ever verifies an expected chord; it never works out which chord is being played from sound alone.
_Avoid_: Chord recognition, chord detection, chord identification

**String check**:
A check in which the learner plucks a chord one string at a time, so each string's note can be judged separately. It is how Fretbop tells the learner which string is wrong.
_Avoid_: Per-string detection, arpeggio test

**Detection level**:
How much of an exercise the app can measure on a given instrument: full, without chord verification, string check only, or none.
_Avoid_: Fallback mode, degraded mode, support level

**Calibration**:
A one-time tap-along per device that measures how late that device's microphone signal arrives, so timing can be judged fairly.
_Avoid_: Latency test, sync

**Detector threshold**:
A technical limit that decides what the app accepts as a measurement, such as minimum signal level or pitch confidence. It belongs to the installation, not to the content.
_Avoid_: Threshold (on its own), sensitivity

**Entry level**:
What a learner must already be able to do before lesson 1: play a few open chords, change between them slowly, and keep a steady beat.
_Avoid_: Prerequisites, beginner level
