# ⛳ Pards Golf

A mobile-first Progressive Web App for scoring golf rounds and tracking betting games with your regular group.

**Live app:** https://bdcomeau.github.io/pardsgolf/pards-golf.html  
**Current version:** v60.0

---

## What It Does

Pards Golf is a single-file HTML PWA that runs entirely on your iPhone — no App Store, no account, no server. Everything is stored locally on your device.

- **Full 18-hole scorecard** for 1–5 players with live handicap stroke calculation
- **8 betting games** running simultaneously: Nassau 2v2, Nassau 1v1, 6-Point, Stableford, Skins, Vegas, Snake 3-Putt, Match Cards
- **The International** — Hole 18 last-chance bet with full outcome table
- **Birdie Juice tracking** — gross birdie/eagle credits, streak detection, leaderboard
- **Golf Canada handicap integration** — fetch live indexes by Golf Canada member ID
- **141 courses** — all tees, par, stroke index, slope, and rating pre-loaded
- **Live weather** per course in picker and on the scorecard header
- **Round History** with search/filter, master scorecard, final totals, Share/Print
- **Match Cards** — play 1v1 Nassau against up to 4 golfers in other groups
- **Full player profiles** — career earnings, birdie juice history, preferred tee per course

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
| Nassau 2v2 | 4–5 | High-Low team Nassau — Front 9, Back 9, Total. Ball toss to pick teams. Auto-presses. |
| Nassau 1v1 | 2–5 | Individual Nassau matchups, multiple simultaneous. Per-match bet amounts. |
| The International | 2–5 | Hole 18 last-chance bet for the losing Nassau team. |
| 6-Point | 3–5 | Low net 4 pts, 2nd 2 pts, 3rd 0 pts per hole. Multiple groups. |
| Stableford | 2–5 | Points per net score, adjustable point values, $ per point. |
| Skins | 2–5 | Per-hole winner takes all, ties carry. Net or gross. Play-order aware. |
| Vegas | 4–5 | Team scores combine low-digit-first. Birdie flips the number. Ball toss to pick teams. |
| Snake 3-Putt | 2–5 | Holder of the snake after holes 3/6/9/12/15/18 pays the table. |
| Match Cards | 2–5 | 1v1 Nassau vs up to 4 players in other groups — scored later from History. |

---

## Courses

141 courses across Canada and USA, organised by region:

| Region | Courses |
|---|---|
| Alberta | 28 — Derrick GWC, Edmonton CC, Royal Mayfair, Jasper, Banff Springs, Kananaskis, Glencoe, Mickelson National, Northern Bear, and more |
| British Columbia | 24 — Whistler (2), Predator Ridge (2), Bear Mountain (2), Okanagan GC (2), Gallaghers Canyon, and more |
| Nova Scotia | 3 — Cabot Links, Cabot Cliffs, Cape Breton Highlands Links |
| PEI | 1 — Links at Crowbush Cove |
| Quebec | 3 — Royal Montreal GC (Blue, Dixie, Red) |
| Arizona | 18 — Troon North (2), Kierland (3), Boulders (6), Phoenician, and more |
| California | 21 — PGA West (9 including Nicklaus Private, Greg Norman, Tom Weiskopf), Palm Valley CC, Palm Springs area |
| Georgia | 9 — Reynolds Lake Oconee (7 courses) |
| Hawaii | 4 — Wailea (3), Makena Golf & Beach Club |
| North Carolina | 10 — Pinehurst No. 1–10 |
| Oregon | 5 — Bandon Dunes resort (all 5 courses) |

---

## Architecture

- **Single file:** `pards-golf.html` — HTML, CSS, JS, and all course data in one file (~3MB)
- **No build step** — deploy by uploading the file to GitHub Pages
- **localStorage** — all round data, player contacts, history, and settings stored client-side
- **Golf Canada API** — handicap fetches routed through a Cloudflare Worker proxy
- **Weather** — Open-Meteo for non-Edmonton courses; WeatherLink for Edmonton-area courses
- **PWA** — installable, works offline after first load

---

## Version History

### v60.0 — Mid-Round Redesign, Bug Fixes, UI Polish *(July 2026)*

**Mid-Round Settings complete redesign** — replaced 11 accordion rows with a clean dark green sheet: Players & Handicaps inline card, Starting Hole + Birdie Juice side by side, 8 game pills matching setup screen order (green dot = active), each pill opens a config sub-panel.

**Return to Scorecard on all game screens** — Game Cards, 6-Point, Snake, Stableford, Skins, Vegas, and Birdie Juice all have a sticky ⛳ Scorecard button. No more getting stuck.

**Birdie Juice always ON by default** — fixed at the initializer, all reset paths, and localStorage restore.

**Round reset fully clean** — Save & Pause, Abandon, New Round, and View & Share Results all return to a completely fresh setup screen with no game dots, no previous players, BJ on, Games on.

**Hole shift game recalculation** — Stableford, Skins, and Vegas now correctly recalculate using play order after a starting hole change.

**Player picker search** — live search in the setup player dropdown, keyboard-aware.

**History improvements** — round count + Backup shortcut; search + course filter; W–L–T record.

**Clear Player mid-round** — replaces Remove Player. Blanks name/handicap, keeps slot and scores.

**BJ toggle in Round Preview** — toggle Birdie Juice before starting without going back to setup.

---

### v50.0 — Game Setup Redesign Complete *(July 2026)*

All 8 game setup overlays restyled dark green with inline config pattern. Ball toss added to Vegas. Nassau 1v1 single-row matchups. Per-match bet display in round preview.

### v40.0 — Manage Players Rebuild + Round Setup Redesign *(July 11, 2026)*

Two complete screen rewrites. Manage Players two-panel slide-over with career stats. Round Setup compact pill strip with player picker bottom sheet.

### v30.0 — Match Cards 4-Opponent + Course Updates

Match Cards raised to 4 opponents. PGA West courses added (Nicklaus Private, Greg Norman, Tom Weiskopf). Northern Bear Golf Club added.

### v19.x — Round Bar & Confirm Scores

Slim gold round bar. Auto-advance permanently removed.

---

## Privacy

All data stored exclusively in device browser localStorage. No analytics, no ads, no user accounts, no server. Golf Canada credentials used only for handicap fetches.

---

*Built for Edmonton's golf community. May your drives be long, your putts be true, and your Birdie Juice credits never run dry.*
