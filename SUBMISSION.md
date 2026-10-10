# Ahmedabad Transit Companion — Hackathon Submission

**Public repo:** https://github.com/choksi2212/metro-hacks

**One-line pitch:** Ahmedabad Transit Companion takes newcomers from any destination to the right metro station, exit, bus connection, and doorstep—even without internet.

## What works right now

- **Destination-first search** — type "MSI Service Center" or "Bodakdev"; 33 curated places (hospitals, colleges, malls, railway stations, service centers) each resolve to a full door-to-door plan, not just a station name.
- **3 route options per query** — fastest, cheapest, and least-walking, computed by an offline Dijkstra over a combined metro + BRTS + walking graph. No server round-trip, no external routing APIs.
- **Exact exit gates** — every itinerary names the specific station exit and the landmark facing it (e.g. "Exit 2, toward Prahladnagar Garden"), so first-timers don't come up on the wrong side of the road.
- **BRTS last-mile connections** — where the metro stops short, the route continues with the BRTS/bus leg, auto-fare estimates, and walking time to the destination gate.
- **Fares & timing included** — metro fare slabs, BRTS fare, NCMC discount, and realistic walk/metro speeds are baked into every route card.
- **Trilingual UI** — English, हिन्दी, and ગુજરાતી across every screen, label, and instruction.
- **Disruption fallback** — toggle a blocked exit, closed interchange, or suspended BRTS stop and routes recompute around it live; if no route survives, the app says so explicitly instead of guessing.
- **Saved journeys** — pin frequent trips to the home screen and replay them offline (localStorage).
- **Fully offline PWA** — service worker + web manifest; airplane-mode tested end-to-end: shell, search, routing, language switch, saves, and map all load with zero network requests.
- **Schematic network map** — bundled local SVG metro map, no map tiles or CDNs required.

**100% offline, zero external APIs, zero accounts** — designed as a module that can be embedded in the official Ahmedabad Metro app.

**Hashtags:** #AhmedabadMetro #OfflineFirst #PWA #LastMileConnectivity #TransitForAll
