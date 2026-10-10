# JUDGE BRIEF — Ahmedabad Transit Companion
*One page. Glance at this while presenting. Everything here is real and demoable offline.*

---

## THE 15-SECOND OPENING (say this first, naturally)

> "We built this on the metro ride here — and that's the point. Every transit app plans
> station-to-station. Ours plans **destination-to-destination**: type 'MSI Service Center,
> Bodakdev' and it tells you the station, the **exact exit gate**, the BRTS last mile, and
> the walk to the doorstep. And it does all of that in **airplane mode** — zero network
> calls, because a metro app is useless when you're 20 metres underground."

*(If they ask what's underground: tunnels on the Blue Line; platforms have no reliable signal.)*

## THE 3 WOW MOMENTS — show in this order

1. **AIRPLANE MODE FIRST.** Don't save it for last — prove resilience up front.
   Turn airplane mode ON in front of them. Banner appears: *"Offline mode — using locally
   stored Ahmedabad transit data."* Search "Civil" → route generates fully offline.
   Reload the page — the whole app boots again from cache. Say: *"No server. No fallback.
   This is the actual app, right now."*
2. **EXACT EXIT GATE.** Search "MSI" → MSI Service Center, Bodakdev.
   Route: Yellow → Red at Motera → Blue at Old High Court → exit Thaltej.
   Open route details: **"Exit Gate 1 — Sarkhej–Gandhinagar (SG) Highway"**,
   then BRTS 401/700 to Iskon Cross Road, 3-min walk. The last 400 metres are where
   newcomers actually get lost — that's what nobody else plans.
3. **DISRUPTION FALLBACK.** Disruptions (demo) panel → "Mark exit unavailable (Gate 1)".
   Route **recalculates instantly**, fallback reason banner shows. Clear it → original
   route returns. Say: *"The operator knows a gate is broken; the passenger finds out
   before they're stranded at the top of the stairs."*

Bonus if time: switch language to **ગુજરાતી** (whole UI + route steps re-render, still offline),
or the local SVG network map — no map tiles, loads underground.

**THE DIFFERENTIATOR (drop this line anytime):**
> "Official apps plan station-to-station. This plans **destination-to-destination**."

---

## JUDGE Q&A — 8 questions, answers you can say in one breath

**Q1. Where does the data come from? Is it real?**
Real Gujarat Metro network — all 54 stations across the 4 operational lines with names in
English, Hindi and Gujarati; fares from the published metro fare chart; exits, walking times
and BRTS connections hand-verified against station layouts and AMTS/BRTS route data, packaged
as a local dataset.

**Q2. Why a PWA and not an Android app?**
No app store, no install friction — a QR code on the station wall and you're using it in
seconds, which matters for tourists and one-time visitors. It also runs on iOS, any laptop
and any kiosk the metro installs, from one codebase.

**Q3. How would the metro actually deploy this?**
Zero integration: host the static bundle on their website or a station kiosk and print a
QR code. Deep links can embed "nearest station" prompts in tickets. When they later expose
real-time feeds, the disruption layer is already the ingestion point — swap demo data for a feed.

**Q4. What about privacy?**
Nothing leaves the device. No accounts, no analytics, no tracking — location stays in the
browser tab and history lives in local storage. We can't see where anyone went.

**Q5. Would you use GTFS or real metro APIs?**
The dataset is structured GTFS-shaped — stops, routes, transfers, footpaths — so it ports
cleanly. We deliberately went offline-first: GTFS data is already published data, so we ship
it with the app instead of fetching it, which is what makes the whole thing airplane-mode safe.

**Q6. What breaks at scale?**
Routing is the constraint, so it runs on a compact graph — 54 nodes — and answers in
milliseconds with no server. Scaling to 500 stations means a bigger local dataset and a
progressive-download pattern (route cache by home station), not new architecture.

**Q7. What does it cost to run?**
Almost nothing. It's static files on a CDN — a few rupees a month at current traffic.
No backend, no database, nothing to monitor for the operator.

**Q8. Why doesn't the official app already do this?**
Official apps optimise for ticketing and station operations — they assume you already know
which station serves your destination. The hard, unglamorous part is the curated
last-mile dataset — exits, gates, walking paths — which no one has built for Ahmedabad.
That's the moat we built tonight.

---

## IMPACT STAT BLOCK (for the closing slide)

| | |
|---|---|
| **54** stations | full operational network, all 4 lines |
| **4** lines | Blue · Red · Yellow · Violet |
| **33** destinations | hospitals, colleges, malls, railway, markets |
| **3** languages | English · હિન્દી · ગુજરાતી |
| **0** network calls | airplane-mode safe, start to finish |

**Last line to say:** *"Built on a moving metro train, for people riding it."*
