# ⛳ Pards Golf

A mobile-first Progressive Web App for scoring golf rounds and tracking betting games with your regular group.

**Live app:** https://bdcomeau.github.io/pardsgolf/pards-golf.html
**Current version:** v50.0

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
- **Match Cards** — play 1v1 Nassau against up to 4 golfers in other groups, score them later from History
- **Full player profiles** — career earnings, birdie juice history, match records, preferred tee per course

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
| Nassau 1v1 | 2–5 | Individual Nassau matchups, multiple simultaneous. |
| The International | 2–5 | Hole 18 last-chance bet for the losing Nassau team. |
| 6-Point | 3–5 | Low net 4 pts, 2nd 2 pts, 3rd 0 pts per hole. Multiple groups. |
| Stableford | 2–5 | Points per net score, adjustable point values, $ per point. |
| Skins | 2–5 | Per-hole winner takes all, ties carry. Net or gross. |
| Vegas | 4–5 | Team scores combine low-digit-first. Birdie flips the number. Ball toss to pick teams. |
| Snake 3-Putt | 2–5 | Holder of the snake after holes 3/6/9/12/15/18 pays the table. |
| Match Cards | 2–5 | 1v1 Nassau vs up to 4 players in other groups — scored later from History. |

---

## Courses

140+ courses across Canada and USA, organised by region:

| Region | Courses |
|---|---|
| Alberta | 28 — Derrick GWC, Edmonton CC, Royal Mayfair, Jasper, Banff Springs, Kananaskis, Glencoe, Mickelson National, Northern Bear, and more |
| British Columbia | 24 — Whistler (2), Predator Ridge (2), Bear Mountain (2), Okanagan GC (2), Fairmont Hot Springs, Gallaghers Canyon, and more |
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

- **Single file:** `pards-golf.html` — HTML, CSS, JS, and all course data in one file (~3.1MB)
- **No build step** — deploy by uploading the file to GitHub Pages
- **localStorage** — all round data, player contacts, history, and settings stored client-side
- **Golf Canada API** — handicap fetches routed through a Cloudflare Worker proxy
- **Weather** — Open-Meteo for non-Edmonton courses; WeatherLink for Edmonton-area courses
- **PWA** — installable, works offline after first load

---

## Version History

### v50.0 — Game Setup Redesign Complete + Bug Fixes *(July 2026)*

Full dark-green redesign of all 8 game setup overlays. Every game config screen now matches the app aesthetic — no more white cards or light backgrounds in setup.

**Bug fixes:**
- Nassau 2v2 pill no longer shows phantom green dot on fresh launch or after deselecting toss partners
- Games OFF now correctly hides the game pill row (not just the sections below)
- 🧹 Start Over button restored to ⚙️ Settings overlay

**Nassau 1v1:** Selecting a matchup no longer creates a duplicate row. Single inline row handles both inactive and active states — expands with bet buttons and Remove on tap.

**Round preview:** Nassau 2v2, 1v1, and Vegas now show correct per-match bet amounts when different bets are set per matchup. Mixed bets show a gold chip per row.

**6-Point Game:** Restyled dark green. Inline combo rows, 25¢–$10 bet range. Default $1/pt.

**Stableford:** Restyled dark green. Player toggle chips, inline points table with +/− spinners, bet per point row. Default $1/pt.

**Skins:** Restyled dark green. Player toggles, inline config with Value/Scoring/Carry/After-18 options.

**Vegas:** Restyled dark green. Ball toss added — identical to Nassau 2v2 (pick 2 partners, swing team for 5-player groups). Manual team selection available via link. Per-match $/point, Gross/Net, Flip on/off all inline.

**Match Cards:** Restyled dark green. Checkbox replaced with Enable/Disable button. Opponent cards dark-themed with gold labels, dark inputs, green GC Fetch button. Default $5/side.

---

### v40.0 — Manage Players Rebuild + Round Setup Redesign *(July 11, 2026)*

Two complete screen rewrites — the largest single release in Pards Golf history.

**Manage Players:** Two-panel slide-over with full player profiles, career stats (Birdie Juice, match record, earnings, rounds played), GC ID lock, custom bottom sheet pickers, dirty state tracking, unsaved changes action sheet.

**Round Setup:** No more player tabs — all rows visible at once. Compact 3-pill strip (Players/Starts/Options). Player name button opens styled bottom sheet picker. Tee auto-loads from saved preference. Default: 4 players, Me in slot 1.

---

### v30.0–v30.37 — Match Cards 4-Opponent Tabs & Course Updates

Match Cards overhaul: opponent limit raised to 4; new tab interface; sequential tab locking. Course additions: PGA West Nicklaus Private, Greg Norman, Tom Weiskopf; Northern Bear Golf Club.

---

### v19.x — Round Bar & Confirm Scores

Slim gold round bar replaces full bottom nav during active rounds. Auto-advance permanently removed — Confirm Scores always ON.

---

## Privacy

All data is stored exclusively in the device's browser localStorage. No analytics, no ads, no user accounts, no server. Golf Canada credentials are used only to fetch handicap indexes and are never transmitted to anyone other than Golf Canada's own API.

---

*Built for Edmonton's golf community. May your drives be long, your putts be true, and your Birdie Juice credits never run dry.*
