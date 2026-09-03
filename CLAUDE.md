# Typhoon project briefing

Typhoon is Robin's private short spin-session app, derived conceptually from Access Gym and Cyclone. Keep it as a dependency-free static web app suitable for GitHub Pages and the WebBLE iPhone browser.

Distance totals use the origin-wide `cyclone-typhoon-distances-v1` ledger shared with Cyclone. Keep performance/PB sessions in `typhoon-sessions-v1`; only distance is shared.

Keep the small header Back button visible in every Typhoon state and point it to the combined launcher at `/Cyclone/`.

## Non-negotiable behaviour

- FTMS service `0x1826`, Indoor Bike Data characteristic `0x2ad2`.
- Workout choices are 3, 5, 8 and 10 minutes.
- Race-start beeps precede the authoritative workout timer.
- Starting and finishing beeps use a smooth single-sine tone. The starting countdown uses 500 hertz with a 1,000-hertz final start signal. Open the Web Audio engine when the duration is selected so Start has no artificial warm-up delay; do not overlap the countdown with a "Get ready" VoiceOver announcement. Keep music muted while unlocking and leave one full second between the final signal and starting music. The finishing signal remains deliberately two-part.
- Music uses only the seventeen MP3 files in `audio/`, preferring descending BPM order from 97 to 90.
- Only `#music` may ever call `play()` or be unmuted. `#music-preload` is cache-only: keep it paused and muted, never swap it into active playback, to prevent concurrent iOS/AirPods media sessions.
- Starting tracks rotate. The automatic workout plan excludes every song actually heard in the immediately preceding workout and cycles within the remaining pool if needed.
- The in-workout Next song button first advances through the remaining planned tracks, skipping repeats already heard in the current workout, then draws from every other unplayed track in the full library before wrapping. An explicit user skip may therefore override the preceding-workout exclusion after the initial plan is exhausted.
- Register the Media Session `nexttrack` action to invoke the same guarded music-advance function, enabling AirPods and system media controls without introducing another audio player.
- The workout and music stop automatically at the exact selected duration.
- Cadence announcements use the number only and occur only during the workout.
- Announce every whole-minute boundary after the start, plus 30, 20, 10, 5, 4, 3, 2 and 1 seconds. Time calls are visible and always take precedence over cadence speech.
- Keep the muted `#music-preload` element cache-only so transitions are prepared without creating a second audible player.
- Keep exactly one hidden ARIA live element for spoken output; do not add named regions, status regions or page landmarks.
- Spoken units: spell out Watts and kilometres; RPM and KPH are acceptable.
- Spoken comparisons use commas rather than em dashes and do not repeat the workout duration.
- Compare performance metrics only with completed sessions of the same duration.
- Continue recording cadence and speed, but do not display them in results unless Robin asks to restore them.
- Display average and maximum Watts per kilo after average and top power. Default weight is 75 kilograms; persist the chosen weight and the weight used by each session. Keep Update weight as the final results-screen control.
- Do not use native `confirm()` or `prompt()` dialogs for results controls; WebBLE may suppress them. Keep reset confirmation and weight editing in-page.
- Never compare distance or treat it as a personal best. Report distance for this workout, last 7 days, last 30 days and all time.
- Preserve the local `Songs/` folder, but do not commit it; it contains the large lossless sources.

## Deployment

The intended repository is `https://github.com/robin1844/Typhoon`, with GitHub Pages serving the `main` branch root.
