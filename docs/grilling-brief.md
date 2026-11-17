# Grilling Brief

Input for a `/grill-with-docs` session. Read together with the ADRs in [`adr/`](adr/).

## Context

Fretbop is a self-hosted Python web app that teaches jazz chord progressions and soloing on fretted string instruments (soprano and baritone ukulele first; guitar and bass later). The audience has no notation or theory knowledge and learns without a teacher. It is a hobby project with one or two users at first, about 10 hours per week of development time.

## Settled — do not re-open

ADRs 0008–0015 (platform, roles, licensing, phasing, language, documentation, name).

**Topic 1, didactic sequence** (grilled 2026-11-18): the entry check and the first 10 lessons, what each lesson must achieve, and when theory is named. See [`package-1-outline.md`](package-1-outline.md), ADR 0016 (phase 1 gated by ear tests only), ADR 0017 (explanations in fret distances) and the content terms in [`GLOSSARY.md`](../GLOSSARY.md).

## Grill me on

Topic numbers are kept stable so that the parked questions below can refer to them.

- **Topic 2, Mastery** — the thresholds, and when the app moves a learner on, slows down or offers an easier variant.
- **Topic 3, Phase 3 risk** — what happens if chord detection on ukulele turns out to be unreliable. What is the fallback, and how do I find out early?
- **Topic 4, Definition of done** — what "finished" means for phase 0 and phase 1.
- **Topic 5, Instrument extension** — what in ADRs 0001–0007 would break or need to change when guitar and bass are added.

## Parked questions

These questions came up while grilling topic 1 but belong to other topics or to later work.

### For topic 2 (mastery)

- What thresholds do the exercises in package 1 declare? The outline currently has placeholders.
- What tempo does the play-along start at, and what tempo counts as mastered?
- What happens when a learner fails an ear test: retry straight away, a slower or easier variant, or a pointer back to an earlier lesson?
- ADR 0016: when a detector ships, how are lessons treated that were mastered in phase 1 without their exercises being measured? Kept, re-measured, or marked "provisionally mastered"?
- What are the entry check's thresholds?

### For topic 4 (definition of done)

- The owner's first-learner walkthrough is the only check of package 1. Is completing it part of phase 1's definition of done, and what counts as a passed walkthrough?
- A review by a jazz musician would be nice but is unlikely. Is phase 1 done without one?
- Phase 0 must deliver a voicing generator with two modes (`easiest` and `voice-led`) for both ukuleles, and a play-along with swing feel, a one-chord-per-bar grid and an adjustable tempo. Are these part of phase 0's definition of done?

### For topic 5 (instrument extension)

- Package 1 is written for chord instruments. How does it work on bass guitar, which plays mostly single notes rather than chords?
- Keys C and F were chosen for how they sit on ukulele. Do they also work on guitar, or does a key choice become instrument-dependent, which would break "one sequence for all instruments"?
- On a 6-string guitar, which 4 notes does a voice-led seventh-chord voicing use, and is that the engine's choice or the lesson's?

### Later content and packages

- Package 2 scope: jazz blues, minor ii-V-I, swing eighths and other comping rhythms, ear tests for roots and intervals, and when interval names may be introduced (ADR 0017).
- When the entry check fails, the app gives no external links. Where does a learner who is not yet at entry level go?
- Lesson 5 is the only lesson that introduces chords without a resolution. Check during the walkthrough whether that works.
- The outline moves to the content repository once that exists (ADR 0004).

### Not discussed, noticed along the way

- Lesson text is user-facing, but packages are YAML in a separate repository. How do packages fit the rule that user-facing text goes through translation keys (ADR 0013)? Is a package translated per locale, and by whom?
