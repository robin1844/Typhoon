# Typhoon

Typhoon is a compact, accessible Web Bluetooth spin-workout app for 3, 5, 8 and 10 minute efforts. It connects to an FTMS indoor bike, runs a race-style starting countdown, plays an automatically selected descending-tempo music sequence, stops precisely at the selected time and reports performance comparisons and personal bests.

The interface follows Cyclone's minimalist pattern: choose one of four large duration buttons, use the single large button to connect and then start, and receive the results followed by distance totals at the finish.

## Workout behaviour

- Workout lengths: 3, 5, 8 and 10 minutes.
- Music always follows the order 96, 94, 93, 92 and 90 BPM.
- Eligible starting tracks rotate through a persistent shuffled bag, avoiding an immediate repeat whenever possible.
- A workout never wraps from 90 BPM back to 96 BPM.
- Live cadence announcements contain the number only, matching Cyclone.
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
