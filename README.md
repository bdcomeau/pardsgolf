# ⛳ Pards Golf

A mobile-first Progressive Web App for scoring golf rounds and tracking betting games with your regular group.

**Live app:** https://bdcomeau.github.io/pardsgolf/pards-golf.html  
**User manual:** https://bdcomeau.github.io/pardsgolf/pardsgolf-help.html  
**Current version:** v20.33

---

## What It Does

Pards Golf is a single-file HTML PWA that runs entirely on your iPhone — no App Store, no account, no server. Everything is stored locally on your device.

- **Full 18-hole scorecard** for 1–5 players with live handicap stroke calculation
- **8 betting games** running simultaneously: Nassau 2v2, Nassau 1v1, 6-Point, Stableford, Skins, Vegas, Snake 3-Putt, Match Cards
- **The International** — Hole 18 last-chance bet with full outcome table
- **Birdie Juice tracking** — gross birdie/eagle credits, streak detection, leaderboard
- **Golf Canada handicap integration** — fetch live indexes by Golf Canada member ID
- **140+ courses** — all tees, par, stroke index, slope, and rating pre-loaded
- **Live weather** per course in the course picker
- **Round History** with master scorecard, final totals, Share/Print, and Pards Leaderboard
- **Match Cards** — play Nassau against golfers in other groups, score them later from History

---

## Installing on iPhone

1. Open **Safari** and go to `https://bdcomeau.github.io/pardsgolf/pards-golf.html`
2. Tap the Share button → **Add to Home Screen**
3. Always launch from the Home Screen icon — not a Safari tab

> ⚠️ You must install to Home Screen for data to persist reliably. Do NOT use "Remove App" — it wipes all local data.

---

## Betting Games

| Game | Players | Description |
|---|---|---|
| Nassau 2v2 | 4–5 | High-Low team Nassau — Front 9, Back 9, Total. Auto-presses. |
| Nassau 1v1 | 2–5 | Individual Nassau matchups, multiple simultaneous. |
| The International | 2–5 | Hole 18 last-chance bet for the losing Nassau team. |
| 6-Point | 3–5 | Low net 4 pts, 2nd 2 pts, 3rd 0 pts per hole. Multiple groups. |
| Stableford | 2–5 | Points per net score, adjustable point values, $ per point. |
| Skins | 2–5 | Per-hole winner takes all, ties carry. Net or gross. |
| Vegas | 4–5 | Team scores combine low-digit-first. Birdie flips the number. |
| Snake 3-Putt | 2–5 | Holder of the snake after holes 3/6/9/12/15/18 pays the table. |
| Match Cards | 2–3 | Nassau vs players in other groups — scored later from History. |

---

## Courses

140+ courses across Canada and USA, organised by region:

| Region | Courses |
|---|---|
| Alberta | 28 — Derrick GWC, Edmonton CC, Royal Mayfair, Jasper, Banff Springs, Kananaskis, Glencoe, Mickelson National, and more |
| British Columbia | 24 — Whistler (2), Predator Ridge (2), Bear Mountain (2), Okanagan GC (2), Fairmont Hot Springs, Gallaghers Canyon, and more |
| Nova Scotia | 3 — Cabot Links, Cabot Cliffs, Cape Breton Highlands Links |
| PEI | 1 — Links at Crowbush Cove |
| Quebec | 3 — Royal Montreal GC (Blue, Dixie, Red) |
| Arizona | 18 — Troon North (2), Kierland (3), Boulders (6), Phoenician, and more |
| California | 21 — PGA West (9), Palm Springs / Coachella Valley area |
| Georgia | 9 — Reynolds Lake Oconee (7 courses) |
| Hawaii | 4 — Wailea (3), Makena Golf & Beach Club |
| North Carolina | 10 — Pinehurst No. 1–10 |
| Oregon | 5 — Bandon Dunes resort (all 5 courses) |

---

## Architecture

- **Single file:** `pards-golf.html` — HTML, CSS, JS, and all course data in one file (~3MB)
- **No build step** — deploy by uploading the file to GitHub Pages
- **localStorage** — all round data, player contacts, history, and settings stored client-side
- **Golf Canada API** — handicap fetches routed through a Cloudflare Worker proxy (`gc-proxy.bdapple.workers.dev`)
- **Weather** — Open-Meteo for non-Edmonton courses; WeatherLink for Edmonton-area courses
- **PWA** — installable, works offline after first load

---

## Version History

### v20.22–v20.33 — Game Tab Bar Polish & Round Flow
- **Game tab bar** (v20.10–v20.21): 2-row × 4-tab interface replaces accordion layout for all 8 betting games. Green dot indicators, minimum player guards, auto-scroll on expand, ▲ Collapse buttons wired to tab system.
- **Stableford/Skins** open with no players selected by default (v20.22)
- **Green dot guards** respect minimum player count — reducing players clears stale dots (v20.23)
- **Auto-scroll** when expanding a game tab (v20.24)
- **Snake green dot** now checks DOM checkbox since `G.snake.enabled` isn't set until `startRound()` (v20.26)
- **📜 View & Share Results** now navigates directly to History and auto-opens the completed round (v20.29)
- **Match Cards active round fix** — `viewAndShareResults()` fully retires the live round before navigating, clearing `G.scores`, `G.roundDate`, `G.roundEnd`, and `pards_G` localStorage (v20.33)

### v20.0–v20.9 — Player Tab Bar & UI Foundations
- **Player tab bar** — 1–5 tabs between Manage Players button and player card; labels show "Player 1 / Bruce C." format
- **Snake moved** inside the betting games section as the first game
- **Master scorecard score symbols** — red circle (birdie), double red circle (eagle), green diamond (hole-in-one), black square (bogey)
- **"BETTING GAMES" gold divider** between Start Round button and game tabs
- **Load My Favourites** button colour updated; Golf Canada ID copy button and labels added

### v19.x — Round Bar, Confirm Scores, Easter Eggs
- Slim gold round bar replaces full bottom nav during rounds
- ☰ Menu sheet: Return to Scorecard, Games, BJ, History, Mid-Round Settings, Save & End Round
- Complete Round button on hole 18 with toast + gold pulsing banner
- Auto-advance permanently removed — Confirm Scores is always ON
- Doug Boyer easter egg — fires on gross par, 21 rotating Astrolab Sauvignon Blanc messages, bogey streak detector
- Bill Burch "Billy's Bunker" (Hole 18 Derrick); Stu Curley "Stu's Bunker" (Hole 4 Derrick)

### v18.x — Course Picker Redesign
- Canada/USA region accordions with provincial/state flag icons
- Course Info overlay: live weather, full 18-hole scorecard, personal history
- Significant course database expansion

---

## Privacy

All data is stored exclusively in the device's browser localStorage. No analytics, no ads, no user accounts, no server. Golf Canada credentials are used only to fetch handicap indexes and are never transmitted to anyone other than Golf Canada's own API.

---

## User Manual

A full illustrated user manual with screenshots is available at:  
https://bdcomeau.github.io/pardsgolf/pardsgolf-help.html

---

*Built for Edmonton's golf community. May your drives be long, your putts be true, and your Birdie Juice credits never run dry.*
