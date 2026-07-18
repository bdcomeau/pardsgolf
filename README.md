# ⛳ Pards Golf

**A single-file Progressive Web App for tracking golf betting rounds among a regular group of senior golfers.**

Live at: **[bdcomeau.github.io/pardsgolf/pards-golf.html](https://bdcomeau.github.io/pardsgolf/pards-golf.html)**

---

## What It Does

Pards Golf is a mobile-first scorecard and betting calculator built specifically for Safari on iPhone. It handles everything from score entry to real-time money calculations across multiple simultaneous betting games.

### Betting Games Supported
- **Nassau 2v2** (High-Low) — with ball toss, swing team, press tracking, and International ("Big I")
- **Nassau 1v1** — with full press and International support
- **6-Point** — three simultaneous 1v1 matches with points and money
- **Snake 3-Putt** — hole-by-hole 3-putt penalty tracking
- **Stableford** — points-based scoring
- **Skins** — per-hole with carryover
- **Vegas** — combined digit scoring, 2v2 with flip-on-birdie rule
- **Match Cards** — 1v1 Nassau vs players from other groups, scored separately
- **Birdie Juice** — side bet pool, per-hole birdie accumulation
- **Side Bets** — custom per-round bets between any players

### Key Features
- 🏌️ **Live scoring** — score wheel with instant feedback, auto-advance, confirm & next hole
- 💰 **Real-time money** — running totals per player across all active games
- 🌍 **International ("Big I")** — full pot calculation, what-if scenarios, Taylor/Toma Rules variant
- 📋 **Scorecards overlay** — mid-round view of all game cards + live standings in one tap
- 🏆 **Round history** — full searchable history with edit, rematch, and share/print
- 👥 **Manage Players** — Golf Canada ID lookup, handicap fetch, career money, last round from GC
- 🏫 **131 courses** — full tee data (rating, slope, yardages, par, SI) across Canada
- 🌤️ **Live weather** — temperature and wind at the course, updates every 5 minutes
- 🔄 **Auto-update** — silently checks for new versions every 90 seconds

---

## Version History

### v90.0 — July 2026 (Current)
- **Colour-coded score strip** — Hole in One 🟢, Albatross 🟣, Eagle 🟠, Birdie 🔴, Par 🔵, Bogey ⬜, Double+ ⬛
- **Score-to-par pill** on every player card — shows +3, -2, or EVEN live
- **Cream par/score strip backgrounds** — dramatically improved readability
- **Scorecards button** replaces Game Cards — one tap shows Live Standings + all game cards mid-round
- **Taylor/Toma International Rules** — unsettled games void when International triggers; toggle on Nassau setup screens
- **ME required gate** — mandatory setup before first round
- **Career money + last GC round** on Manage Players cards (24hr cache)
- **Pinch to Zoom** per-user setting
- **Canyon Meadows Golf & Country Club** added (Calgary AB, 8 men's tees)
- **Setup affordance cues** — pulse glow and "Tap to select" on empty player/tee pills
- **Money pill** redesigned — white text on green/red/gold

### v87.x — July 2026
- Manage Players redesign with Golf Canada score history
- Nassau 2v2 swing team mid-round fix
- Handicap locked in history edit mode
- International popup restored after hole 17

### v86.x — July 2026
- Picture Butte Golf Club added (3 courses)
- GC member search redesign (separate first/last name fields)
- Vegas setup screen fixes

### v85.x and earlier
See in-app release notes (Settings → Update App).

---

## Architecture

### Single File
The entire app — HTML, CSS, JavaScript, all 131 course datasets, and all embedded logos — lives in **one HTML file** (`pards-golf.html`). This makes it trivially deployable and cacheable as a PWA.

### Deploy Files
Every release pushes three files to this repo:
| File | Purpose |
|---|---|
| `pards-golf.html` | The app |
| `index.html` | Identical copy (so both URLs work) |
| `pards-golf-vXX_X.html` | Versioned snapshot for rollback |

### Update Checker
The app fetches the live `index.html` from GitHub Pages every 90 seconds, regex-searches for the version string, and shows an update banner if a newer version is available. No GitHub API required.

### Backend
All Golf Canada API calls go through a **Cloudflare Worker** at `gc-proxy.bdapple.workers.dev` which handles:
- Authentication tokens
- Member search
- Handicap lookup
- Score history (last N rounds)
- Facility detail (address, amenities)
- Course search and detail

### Storage
All data is stored in `localStorage` — no server, no accounts, no sync. Backup is manual via JSON export.

---

## Companion Tools

| Tool | URL | Purpose |
|---|---|---|
| Handicap Calculator | `/hcp-calculator.html` | Look up any player's adjusted handicap for any course/tee |
| GC Member Search | `golfnet-member-search.html` | Search Golf Canada members, copy GC IDs |
| GolfNet Course Lookup | `golfnet-lookup.html` | Look up full course detail by GolfNet ID |

---

## Technical Notes

- **Requires Safari on iPhone** — uses iOS-specific PWA APIs, viewport-fit=cover, safe area insets
- **Add to Home Screen** for best experience — runs full-screen with gold scorecard icon
- **No build step** — plain HTML/CSS/JS, edit and deploy directly
- **Syntax check** before every deploy using `node --check` on extracted script block

---

## Development

Built iteratively by Bruce Comeau with Claude (Anthropic) as coding partner. All development happens in a single Claude project with full session continuity.

*Pards Golf · v90.0 · bdcomeau.github.io/pardsgolf*
