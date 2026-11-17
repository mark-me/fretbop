# Architecture Decisions

| # | Decision | Rationale |
|---|----------|-----------|
| 1 | Target audience: players of fretted instruments without notation or theory knowledge, learning without a teacher. Soprano and baritone ukulele first; guitar and bass guitar later | Drives didactics: sound, shapes and patterns first; theory introduced just in time |
| 2 | Instruments as data (tuning, fret count, re-entrant flag) | Extend to other fretted instruments without code changes |
| 3 | Python theory engine is the single source of truth; frontend receives voicings as JSON | One theory implementation |
| 4 | Content as YAML packages in a separate repository, versioned independently | Edit content without a software release |
| 5 | All audio analysis runs in the browser | Low latency; no audio leaves the device unless recording is enabled |
| 6 | Mastery via microphone and ear tests; self-assessment only after a diagnosed measurement failure, capped at "provisionally mastered" | Reliable mastery model |
| 7 | Detector thresholds as configuration (YAML), overridable per installation | Tune without a release |
| 8 | Target platform: home servers (Docker, SQLite, HTTPS via reverse proxy) | Self-hosted; microphone access requires a secure context |
| 9 | Roles: learner, course_author, admin; combinable; authorization by permission | Extensible without code changes |
| 10 | Dependencies: permissive licenses only, enforced in CI | No copyleft in an MIT project |
| 11 | License: MIT (code), CC-BY-4.0 (content) | Open reuse |
| 12 | Phased delivery (0–4); roles, donation and catalogue deferred | Hobby project, 1–2 users |
| 13 | Code, identifiers, YAML keys and configuration in English; all user-facing text via translation keys; locales `en` (default, fallback), `nl-NL` later | Multilingual app without language-specific logic |
| 14 | Project documentation in English | Consistent with code; accessible to international contributors |
| 15 | Project name: Fretbop | Instrument-neutral across fretted instruments; no clashes found on PyPI, npm or GitHub |
| 16 | Phase 1 lessons are gated by ear tests only; exercise thresholds are declared and enforced once detectors ship | No microphone in phase 1; keeps ADR 0006 intact without self-assessment |
| 17 | Explanations use note names and fret distances, never interval names | Depth without naming anything the learner has not played or heard (ADR 0001) |

## Phases

| Phase | Deliverable |
|---|---|
| 0 | Theory engine, voicing generator, SVG fretboard, playback |
| 1 | One content package (seventh chords, ii-V-I) with play-along |
| 2 | Tuner, single-note pitch detection, signal-quality checks |
| 3 | Chord verification and per-string diagnosis |
| 4 | Opt-in local recordings and threshold tuning |

## Stack

Flask · Flask-Babel · htmx · Bootstrap · PyYAML · Pydantic · pychord · pitchy · Meyda · Tone.js · svguitar · custom SVG fretboard · abcjs (later)
