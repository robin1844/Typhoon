# Typhoon

Typhoon is a compact, accessible Web Bluetooth spin-workout app for 3, 5, 8 and 10 minute efforts. It connects to an FTMS indoor bike, runs a race-style starting countdown, plays an automatically selected descending-tempo music sequence, stops precisely at the selected time and reports performance comparisons and personal bests.

When served from Robin's GitHub Pages account, Typhoon shares only its distance ledger with Cyclone. Existing Cyclone and Typhoon distances are imported automatically; Typhoon's performance history remains separate.

The persistent header **Back** button returns to the combined Cyclone/Typhoon launcher at `/Cyclone/`, including during countdown, workout and results screens.

The interface follows Cyclone's minimalist pattern: choose one of four ordinary large duration buttons, which are then replaced by the single large Connect button. That same button becomes Start after connection. Results are followed by distance totals at the finish.

## Workout behaviour

- Workout lengths: 3, 5, 8 and 10 minutes.
- Music follows the order 96, 94, 93, 92 and 90 BPM where possible, with a wrap-around jump only when needed to cover the workout.
- Eligible starting tracks rotate through persistent shuffled bags.
- Every track actually heard in the immediately preceding workout is excluded from the next one. If necessary, Typhoon cycles within the remaining pool so that exclusion is absolute even for consecutive 10-minute sessions.
- Live cadence announcements contain the number only, matching Cyclone, and occur only while a workout is running.
- At every whole-minute boundary after the start, the remaining time is announced. The final countdown is 30 seconds, 20 seconds, 10 seconds, then 5, 4, 3, 2, 1. These calls appear on screen and take priority over cadence speech.
- Cadence and speed continue to be recorded in saved sessions, but are intentionally omitted from the current results screen.
- Results include average and maximum Watts per kilo immediately after the two power results. Weight defaults to 75 kilograms, is saved with each workout, and can be changed only from the final Update weight button on the results screen.
- Reset uses an in-page two-tap confirmation and weight uses an in-page editor, avoiding native dialogs that may be suppressed by WebBLE.
- The countdown uses smooth sine-wave 500-hertz signals and a 1,000-hertz start signal, matching the documented Swiss Timing track-cycling pitches. The audio engine is opened when a duration is selected so Start has no artificial warm-up delay, and a full second of silence separates the start signal from the music.
- A single unlocked audio player is the only element allowed to play music. A permanently muted, never-played second element may preload the next file into the browser cache, preventing duplicate iOS/AirPods media sessions while minimising silence at song changes.
- A Next song button is available during a workout. It follows the descending playlist order and wraps to the top when necessary, while continuing to exclude songs heard in the preceding workout.
- On supported devices and browsers, the media-session next-track command, including the usual AirPods double-squeeze, invokes that same Next song action.
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
