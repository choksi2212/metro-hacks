# DEMO — Ahmedabad Transit Companion

**Pitch (say this first):**
> "Most metro apps plan station-to-station. Ahmedabad Transit Companion plans destination-to-destination — and it works with zero internet. Type where you want to go; it tells you the station, the exact exit gate, the bus connection, and the last 400 metres to the doorstep."

**Before demoing:** open the app once while online (refresh once), then it's cached — everything below works in airplane mode.

---

## Demo 1 — Flagship: Mahatma Mandir → MSI Service Center, Bodakdev

*The real first-timer problem that inspired the app.*

1. Home screen → type **"MSI"** in the search box.
2. Tap **MSI Service Center — Bodakdev**.
3. Origin: tap **Use current location** (simulated at Mahatma Mandir).
4. Show **3 route cards**: Fastest / Cheapest / Least walking.
   - Fastest: Yellow Line → Red Line at Motera → Blue Line at Old High Court → Thaltej → BRTS → Iskon Cross Road.
5. Open **Route details** — walk through the steps:
   - board the Yellow Line toward Mahatma Mandir
   - change at Motera Stadium, change at Old High Court
   - **exit from Gate 1 at Thaltej — "Sarkhej–Gandhinagar (SG) Highway"**
   - BRTS 401/700 toward Iskon Cross Road, 3 min walk to the service center
6. Point out: **total time, ₹cost, walking minutes, accessibility info on every gate**.

## Demo 2 — Language switcher

1. Top-right → **ગુ** (Gujarati). The whole UI + route steps re-render in Gujarati.
2. Switch to **हिं** (Hindi) if asked. Zero network calls — translations are local.

## Demo 3 — Airplane mode (the money shot)

1. Turn **airplane mode ON** (or Wi-Fi off). The banner appears: *"Offline mode — using locally stored Ahmedabad transit data."*
2. Search **"Civil"** → tap Civil Hospital.
3. Use current location → route generates fully offline: Red Line → Blue Line → Kalupur → BRTS to Civil Hospital stop.
4. Open route details, show the exit gate + step list.
5. **Save the journey** (bookmark icon) → go Home → Saved journeys → it's there after close/reopen.

## Demo 4 — Disruption fallback (operator view)

1. Plan any route that exits at Thaltej Gate 1 (e.g. MSI demo above).
2. In **Disruptions (demo)** panel → tap **"Mark exit unavailable (Gate 1)"**.
3. The route **recalculates instantly** and shows a fallback reason banner.
4. Tap **Clear all disruptions** → original route returns.
5. Say: *"The metro knows a gate is broken. The passenger finds out before they're stranded at the top of the stairs."*

## Demo 5 — Saved journeys survive restart

1. With a saved journey present, close the browser tab completely.
2. Airplane mode still ON. Reopen the app.
3. Home → **Saved journeys** → the journey is there, offline.

## Demo 6 — Network map

1. Tap **Network map** — schematic SVG of the full 4-line network (Blue/Red/Yellow/Violet).
2. With a route planned, the map shows the highlighted station path.
3. Say: *"No map tiles, no Google Maps — this is a local SVG, so it loads underground."*

---

## One-line answers for judges

- **"Does it use Google Maps?"** — No. Zero external APIs. The map is a local SVG; search is over local JSON.
- **"Where does the data come from?"** — Real GMRC network (54 stations, 4 lines, real interchanges). Walking/BRTS times are realistic approximations, stated as assumptions.
- **"How would the metro use this?"** — Embed as a module in the official Ahmedabad Metro app; the ticket flow ends at the gate today, this carries the passenger to the doorstep.
- **"What happens underground?"** — Everything is cached by the service worker; airplane mode is a supported mode, not an edge case.
- **"Why not native Android?"** — The core value is the offline journey-planning logic; a PWA demos on any device and can be wrapped in WebView later.

## Timing (2-minute version)

0:00–0:20 — pitch + Demo 1 route
0:20–0:40 — Demo 3 airplane mode (do it early, it's the wow)
0:40–1:10 — Demo 4 disruption fallback
1:10–1:25 — Demo 2 language
1:25–2:00 — saved journeys + map + judge questions
