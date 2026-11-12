# Hackathon Plan

The single source of truth for what we are building and when. Any Claude session
should read this file before doing hackathon work. This repository (`shared_repo_test`)
is only for practice; on Saturday 09:00 the real repository is created and this file is
copied into it as the first commit.

_Last updated: 2026-11-13 by chumasov_

## Event

- NASA hackathon 2026 (format looks like NASA Space Apps).
- Runs from **Saturday 09:00 to Sunday 23:59** (2026-11-14 to 2026-11-15).
- Team of two:
  - **alekastryzhevska-hue** – UI/UX designer; owns visual design and screen layout.
  - **chumasov** – "backend": data, calculations, health rules. Claude writes the code;
    chumasov decides what to build, checks results in the browser and owns the
    health content (indicators, thresholds, advice).
- To check in the official rules (not done yet): what is allowed before the start,
  submission format and licence, whether AI use must be disclosed.

## Challenge (summary)

Build a **visual tool** that helps astronauts on long missions assess their own health
and gives guidance on treatment and improvement.

- NASA Human Research Program lists five hazards: space radiation, isolation and
  confinement, distance from Earth, gravity fields, hostile closed environment.
- Resulting problems: immune changes, bone loss, cardiovascular events, poor nutrition,
  behavioral health.
- Suggested indicators: blood pressure, heart rate, blood sugar, body temperature,
  sleep hours, mood. Any input is allowed (keyboard, clicks, camera).
- Questions to answer per indicator: Which measurements can be done in space? Why is
  the exam needed? How do hazards affect it? When does a result need attention from
  the crew or flight surgeons? What actions prevent a critical condition?
- Organizers' ideas: clickable human figure, measurement reminders, gamification,
  dynamic charts, color coding, simple explanations (do not assume astronauts know
  how to assess their health).
- Check the challenge "Resources" tab on Saturday morning; more material may be added.

## Product concept

Core loop: **collect → compare with the astronaut's personal baseline → explain →
suggest an action → check whether it helped.**

Demo story (to finalize with the designer): one astronaut, around day 94 of a Mars
transit, 20-minute communication delay; the tool notices a developing problem (for
example worse sleep + higher resting heart rate + lower mood) and guides the astronaut.

### Screens (only three)

1. **Main screen – human figure** with clickable, color-coded zones:
   - head: mood, sleep
   - chest: heart rate, blood pressure
   - abdomen: blood sugar, nutrition
   - legs / skeleton: bone load (exercise minutes as a proxy)
   - whole body: temperature, accumulated radiation dose
2. **Indicator card**: current value, trend chart vs personal baseline, status,
   explanation, recommended action.
3. **Daily check-in / guided measurement**: short instruction on how to measure,
   input, then explanation of the result.

### Status colors

- Green – normal.
- Yellow – act yourself or tell the crew.
- Red – contact flight surgeons on Earth.

Thresholds are illustrative, not medical; say so openly in the app and the pitch.

### Indicators (8)

Heart rate, blood pressure, blood sugar, body temperature, sleep hours, mood,
nutrition, exercise minutes. Plus radiation dose as context.

## Technical decisions

- Web app in the browser (React), **no server, no login, no cloud**; data stays
  local. "Works without a link to Earth" is part of the pitch.
- Past data comes from a **synthetic data generator**: one astronaut, ~180 days,
  with 2–3 built-in problems.
- Baseline = first ~2 weeks of data; deviation via simple statistics, no ML.
- Health rules live in one table: indicator → how to measure → why → spaceflight
  effect → yellow / red thresholds → what to do. chumasov writes it in plain words.
- Hosted on a free static host (Vercel or GitHub Pages) for a public demo link.
- Public repository. **No passwords or keys in the repo.**

## Scope

Must have (MVP): data generator, human-figure screen with statuses, indicator card
with trend chart, alerts with explanation and action, daily check-in.

Nice to have, only if MVP works: action tracking ("done" → see if the indicator
recovered), check-in streak (gamification), "time to measure" reminder.

Out of scope (mention only as "future work" slide): LLM assistant, report for
flight surgeons, privacy levels, camera / ultrasound, different environments,
real devices.

## Schedule

### Friday 2026-11-13 (preparation, no project code)
- [x] Tools installed and GitHub access working for both (chumasov done).
- [x] Shared workflow tested: designer → chumasov works.
- [ ] Return test: designer's Claude reads chumasov's STATUS entry.
- [ ] Practice page to learn the ask → check → commit → push cycle (small, to save limits).
- [ ] Call with the designer: rules, demo story, three screens, indicator list.
- [ ] Draft the health rules table (if the rules allow prep work).
- [ ] Sleep.

### Saturday
| Time | Goal |
|---|---|
| 09:00–11:00 | Create real repo, copy this plan + workflow files, empty app online |
| 11:00–14:00 | Data generator, 180 days with built-in problems |
| 14:00–19:00 | Human-figure screen and charts (plain style) |
| 19:00–23:00 | Baseline logic, alerts, advice from the rules table |

By Saturday night the demo story must work end to end, even if ugly.

### Sunday
| Time | Goal |
|---|---|
| 09:00–14:00 | Apply the designer's mockups, check-in screen |
| 14:00–16:00 | Action tracking if time allows |
| 16:00 | **Feature freeze**, fixes only |
| 16:00–20:00 | Demo video, slides, project description |
| by 21:00 | Submit (3 hours of buffer) |

## Working rules

- Follow `CLAUDE.md` (pull at start, update own STATUS section, English in the repo).
- Small steps; check each one in the browser; commit and push after every working step.
- Work in `main`, no branches. Designer and chumasov edit different files.
- Usage limits (Claude Pro): use Opus 5.5 by default, not Fable; start a new session
  for each new task; keep requests short; the weekly limit resets Sunday 15:00.
  During limit pauses, work on content, slides and the demo script.

## Where we stopped

Update this section at the end of every session.

- 2026-11-13 ~01:00: tools and GitHub ready; shared workflow files exist; chumasov's
  STATUS entry pushed as the return test, waiting for the designer to confirm.
  Next: practice page, then the call with the designer.
