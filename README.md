# ⛳ Pards Golf

A mobile-first Progressive Web App for scoring golf rounds and tracking betting games with your regular group.

**Live app:** https://bdcomeau.github.io/pardsgolf/pards-golf.html  
**Current version:** v40.0

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
| Nassau 2v2 | 4–5 | High-Low team Nassau — Front 9, Back 9, Total. Auto-presses. |
| Nassau 1v1 | 2–5 | Individual Nassau matchups, multiple simultaneous. |
| The International | 2–5 | Hole 18 last-chance bet for the losing Nassau team. |
| 6-Point | 3–5 | Low net 4 pts, 2nd 2 pts, 3rd 0 pts per hole. Multiple groups. |
| Stableford | 2–5 | Points per net score, adjustable point values, $ per point. |
| Skins | 2–5 | Per-hole winner takes all, ties carry. Net or gross. |
| Vegas | 4–5 | Team scores combine low-digit-first. Birdie flips the number. |
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

- **Single file:** `pards-golf.html` — HTML, CSS, JS, and all course data in one file (~3MB)
- **No build step** — deploy by uploading the file to GitHub Pages
- **localStorage** — all round data, player contacts, history, and settings stored client-side
- **Golf Canada API** — handicap fetches routed through a Cloudflare Worker proxy
- **Weather** — Open-Meteo for non-Edmonton courses; WeatherLink for Edmonton-area courses
- **PWA** — installable, works offline after first load

---

## Version History

### v40.0 — Manage Players Rebuild + Round Setup Redesign *(July 11, 2026)*

This is the largest single release in Pards Golf history. Two complete screen rewrites.

#### Manage Players — Complete Redesign
- **Two-panel slide-over** — clean list screen slides to full player profile/edit screen
- **List screen** — star (tap to instantly favourite/unfavourite), Me badge, name, GC Index, lifetime earnings, › chevron; hint line explains interactions
- **Player profiles** — full career stats: Career Birdie Juice (scanned from all history), Overall Match Record, vs Me record, Career Earnings, Total Rounds Played, Last Round Played
- **Golf Canada ID lock** — field is read-only once set; hold 🔒 for 2 seconds to unlock
- **Fetch HCP button** — activates live as a valid 10-digit GC ID is typed
- **Custom bottom sheet pickers** — Preferred Tee (coloured badges + yardage), Score Wheel Default (with descriptions), Home Course (alphabetical)
- **Home Course ↔ Tee sync** — changing Home Course immediately updates the Preferred Tee picker to that course's tees
- **Me chip protection** — tap shows immediate warning dialog; requires 2-second hold on "Hold to Confirm" to change the Me player
- **Dirty state tracking** — Save Changes hidden until fields actually change; instant save for Favourite toggle
- **Unsaved changes** — tapping ‹ Players with changes shows Save & Return / Discard & Return / Cancel action sheet
- **Favourite rules** — Me always counts; maximum 4 additional favourites (5 total)

#### Round Setup — Compact Redesign
- **No more player tabs** — all player rows visible at once, stacked vertically
- **Player rows** — name button · tee button · Adj HCP · ↻ refresh; one clean line per player
- **Player picker** — styled bottom sheet (Me → Favourites → alphabetical); ＋ New Player opens Manage Players
- **Tee auto-load** — selecting a player fetches their saved preferred tee for the active course and recalculates HCP immediately
- **Compact 3-pill strip** replaces Reset button, player count card, starting hole card, and round options accordion:
  - 👥 **Players** — bottom sheet +/− counter
  - 🚩 **Starts** — 18-hole grid picker
  - ⚙️ **Options** — Games toggle, Birdie Juice toggle, 🧹 Reset (hold 2s to confirm)
- **Load My Favourites + Manage Players** — equal width side by side
- **Start Round button** — streamlined; shows player count + course name only
- **Default state** — 4 players, Me in slot 1, 3 empty slots ready; applies on fresh load, end round, abandon, and reset

#### Course Additions (v30.19–v30.22)
- PGA West Nicklaus Private (6 tees)
- PGA West Greg Norman (5 tees)
- PGA West Tom Weiskopf (6 tees)
- Northern Bear Golf Club — Sherwood Park, AB (7 tees)

#### Other Fixes
- Round Launch Summary: improved handicap display, team/single game field name fixes
- Match Cards: up to 4 opponents, all 4 in history snapshot
- History edit auto-save on close
- Backup screen redesigned (buttons at top, Nassau Golf legacy import in collapsed accordion)

---

### v30.0–v30.10 — Match Cards 4-Opponent Tabs & Course Updates
- Match Cards overhaul: opponent limit raised to 4; new 4-tab purple interface; sequential tab locking; Clear button replaces ×
- Palm Valley CC Championship: all 6 tees updated
- Every version bump now produces three files: `pards-golf.html`, `index.html`, `pards-golf-vXX.X.html`

### v20.22–v20.33 — Game Tab Bar Polish & Round Flow
- Game tab bar: green dot guards, auto-scroll, collapse buttons
- View & Share Results navigates directly to completed round in History

### v20.0–v20.21 — Game Tab Bar & Player Tabs
- Player tab bar (1–5 tabs, live labels)
- 2-row × 4-tab game tab bar replacing accordion layout

### v19.x — Round Bar & Confirm Scores
- Slim gold round bar, ☰ Menu sheet
- Auto-advance permanently removed — Confirm Scores always ON

---

## Privacy

All data is stored exclusively in the device's browser localStorage. No analytics, no ads, no user accounts, no server. Golf Canada credentials are used only to fetch handicap indexes and are never transmitted to anyone other than Golf Canada's own API.

---

*Built for Edmonton's golf community. May your drives be long, your putts be true, and your Birdie Juice credits never run dry.*
