# Typhoon

Typhoon is a compact, accessible Web Bluetooth spin-workout app for 3, 5, 8 and 10 minute efforts. It connects to an FTMS indoor bike, runs a race-style starting countdown, plays an automatically selected descending-tempo music sequence, stops precisely at the selected time and reports performance comparisons and personal bests.

The interface follows Cyclone's minimalist pattern: choose one of four ordinary large duration buttons, which are then replaced by the single large Connect button. That same button becomes Start after connection. Results are followed by distance totals at the finish.

## Workout behaviour

- Workout lengths: 3, 5, 8 and 10 minutes.
- Music follows the order 96, 94, 93, 92 and 90 BPM where possible, with a wrap-around jump only when needed to cover the workout.
- Eligible starting tracks rotate through persistent shuffled bags.
- Every track actually heard in the immediately preceding workout is excluded from the next one. If necessary, Typhoon cycles within the remaining pool so that exclusion is absolute even for consecutive 10-minute sessions.
- Live cadence announcements contain the number only, matching Cyclone, and occur only while a workout is running.
- At every whole-minute boundary after the start, the remaining time is announced. The final countdown is 30 seconds, 20 seconds, 10 seconds, then 5, 4, 3, 2, 1. These calls appear on screen and take priority over cadence speech.
- Cadence and speed continue to be recorded in saved sessions, but are intentionally omitted from the current results screen.
- The countdown and finish use layered, high-impact race signals.
- Two alternating, pre-unlocked audio players preload consecutive tracks to minimise silence at song changes.
- Distance is not treated as a performance comparison or personal best. Typhoon reports distance for the completed workout, last 7 days, last 30 days and all time.
- Performance comparisons are made only against completed workouts of the same selected duration.

## Accessibility

Typhoon is designed for VoiceOver on iPhone. Spoken output uses an assertive ARIA live region. All controls have visible labels, results use full spoken-friendly units, and the race countdown uses audible beeps.

On iPhone, open the live HTTPS page in a Web Bluetooth browser such as WebBLE. Plain Safari does not expose Web Bluetooth.

## Project structure

- `index.html` — the complete application, with inline CSS and JavaScript.
- `audio/` — the five selected tracks encoded as compact, high-quality MP3 files.
- `manifest.webmanifest` — installable web-app metadata.
- `Songs/` — local lossless source audio and working splits; intentionally excluded from Git.
- `CLAUDE.md` — implementation and maintenance notes.

There is no build step and no runtime dependency.
