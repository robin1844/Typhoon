# Typhoon project briefing

Typhoon is Robin's private short spin-session app, derived conceptually from Access Gym and Cyclone. Keep it as a dependency-free static web app suitable for GitHub Pages and the WebBLE iPhone browser.

## Non-negotiable behaviour

- FTMS service `0x1826`, Indoor Bike Data characteristic `0x2ad2`.
- Workout choices are 3, 5, 8 and 10 minutes.
- Race-start beeps precede the authoritative workout timer.
- Music uses only the five MP3 files in `audio/`, preferring the descending order 96, 94, 93, 92, 90 BPM.
- Starting tracks rotate. Exclude every song actually heard in the immediately preceding workout; cycle within the remaining pool if needed, allowing a larger BPM wrap-around jump rather than violating that exclusion.
- The workout and music stop automatically at the exact selected duration.
- Cadence announcements use the number only and occur only during the workout.
- Announce every whole-minute boundary after the start, plus 30, 20, 10, 5, 4, 3, 2 and 1 seconds. Time calls are visible and always take precedence over cadence speech.
- Use the two alternating audio elements to preload and hand off between songs with minimal silence.
- Keep exactly one hidden ARIA live element for spoken output; do not add named regions, status regions or page landmarks.
- Spoken units: spell out Watts and kilometres; RPM and KPH are acceptable.
- Spoken comparisons use commas rather than em dashes and do not repeat the workout duration.
- Compare performance metrics only with completed sessions of the same duration.
- Continue recording cadence and speed, but do not display them in results unless Robin asks to restore them.
- Display average and maximum Watts per kilo after average and top power. Default weight is 75 kilograms; persist the chosen weight and the weight used by each session. Keep Update weight as the final results-screen control.
- Never compare distance or treat it as a personal best. Report distance for this workout, last 7 days, last 30 days and all time.
- Preserve the local `Songs/` folder, but do not commit it; it contains the large lossless sources.

## Deployment

The intended repository is `https://github.com/robin1844/Typhoon`, with GitHub Pages serving the `main` branch root.
