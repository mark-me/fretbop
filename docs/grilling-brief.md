# Grilling Brief

Input for a `/grill-with-docs` session. Read together with the ADRs in [`adr/`](adr/).

## Context

Fretbop is a self-hosted Python web app that teaches jazz chord progressions and soloing on fretted string instruments (soprano and baritone ukulele first; guitar and bass later). The audience has no notation or theory knowledge and learns without a teacher. It is a hobby project with one or two users at first, about 10 hours per week of development time.

## Settled — do not re-open

ADRs 0008–0015 (platform, roles, licensing, phasing, language, documentation, name).

## Grill me on

1. **Didactic sequence** — the first 10 lessons: what comes first, what each lesson must achieve, and when theory is named.
2. **Mastery** — the thresholds, and when the app moves a learner on, slows down or offers an easier variant.
3. **Phase 3 risk** — what happens if chord detection on ukulele turns out to be unreliable. What is the fallback, and how do I find out early?
4. **Definition of done** — what "finished" means for phase 0 and phase 1.
5. **Instrument extension** — what in ADRs 0001–0007 would break or need to change when guitar and bass are added.
