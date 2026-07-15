# Pards Golf v84.7

A single-file HTML Progressive Web App for scoring golf rounds and tracking betting games at Derrick Golf & Winter Club, Edmonton AB.

**Live:** https://bdcomeau.github.io/pardsgolf/pards-golf.html

---

## ⚠️ Installation — PWA Required

Pards Golf **must** be installed as a PWA (Progressive Web App). It will not work correctly in a browser.

**iPhone (Safari):**
1. Tap the **•••** button, then tap **□↑ Share**
2. Tap **Add to Home Screen** → **Add**
3. Launch from your home screen

**Android (Chrome):**
1. Tap the **⋮** menu → **Add to Home Screen** or **Install App**
2. Launch from your home screen or app drawer

---

## Supported Games

| Game | Players |
|------|---------|
| Snake 3-Putt | 2–5 |
| Nassau 2v2 (High-Low) | 4 |
| Nassau 1v1 | 2–5 |
| 6-Point Game | 3 |
| Stableford Points | 2–5 |
| Skins | 2–5 |
| Vegas Golf Game | 4 |
| Match Cards | 2–3 |
| Birdie Juice | 2–5 |

---

## First-Time Setup

On first launch the app walks you through setup:

1. **Create your "Me" profile** — Tap Manage Players, enter your name, handicap index, home course, and preferred tee deck, then tap Set as Me
2. **Add playing partners** — Name, handicap index, Golf Canada ID if available (10 digits, from the Golf Canada website — not their app)
3. **Sync Golf Canada handicaps** — Tap Refresh Handicaps in Manage Players, enter GC credentials once
4. **Set up Quick Adds & Buddies** — Up to 4 Quick Adds; unlimited Buddies
5. **Start a round** — Pick course, add players, choose betting games, tap Start Round

---

## Key Features

- Nassau betting — 2v2 High-Low and 1v1 with auto-press, The International
- Live standings — real-time $ standings mid-round
- Golf Canada handicap integration via Cloudflare Worker proxy (live sync)
- Weather — WeatherLink (Derrick) + Open-Meteo (all other courses)
- Birdie Juice — credit tracking for birdies and eagles
- Full round history with replay and edit
- Backup/Restore — local JSON export/import
- Side Bets — event betting (2026 Derrick Member Guest)
- 20+ courses with GPS coordinates and logo art
- Ball Toss team assignment
- Easter eggs — Doug Boyer's Astrolab, Billy's Bunker, Stu's Bunker, Greg's Quiet Zone

---

## Architecture

- **Single file:** `pards-golf.html` — all HTML + CSS + JS + assets (base64 encoded)
- **Size:** ~5.5 MB (images are the primary cost)
- **No server** — runs fully offline after first load
- **PWA:** Installable on iPhone via Safari → Add to Home Screen

---

## Deployment

Three files uploaded to GitHub Pages per release:
1. `pards-golf.html`
2. `index.html` (copy, root redirect)
3. `pards-golf-vXX.X.html` (versioned archive)

---

## Icon System (v84.x)

All 8 game icons are custom illustrated PNGs displayed in:
- Round setup game pills (landscape, height:56px)
- Mid-round settings game pills (same spec)
- Game popup headers (28px via `_MM_GAME_ICONS` array)

Manage Players icons:
- ⚡ Gold lightning bolt = active Quick Add
- ⚡ Black lightning bolt at 25% opacity = inactive Quick Add
- 👥 Gold buddies = active Buddy
- 👥 Black buddies at 25% opacity = inactive Buddy
- Me contact is always Quick Add + Buddy

UI icons are gold PNGs (not emoji) for: settings gear, cloud upload, golfer, flag, info "i", lightning bolt, two-golfers, birdie juice glass.

---

## Onboarding (v83.x)

Two-screen onboarding system on first launch:

**Screen 1 — Browser detected:** Shown when app is opened in a browser instead of as a PWA. Includes Safari/Android install instructions, copy-link button, and Pards Golf icon so users know what to look for on their home screen.

**Screen 2 — PWA first launch:** 5-step setup walkthrough. Dismissed permanently after tapping "Got it." Never shown again.

Returning users see neither screen.

---

## Technical Notes

- iOS compat: `function()` syntax in `renderMMSixPoint` (no arrow functions)
- Viewport: `interactive-widget=resizes-content` — do not remove
- Scroll: `history.scrollRestoration = 'manual'` at top of script — do not remove
- Syntax check: `node --check` on extracted script block after every change
- Weather: Edmonton courses → WeatherLink; all others → Open-Meteo
- Version bump: replace `CURRENT_VERSION` and `CACHE` strings only (exactly 2 occurrences)

---

## Version History

| Version | Highlights |
|---------|-----------|
| v84.7 | Manage Players icons fixed (gold active / black 25% inactive), Me auto-sets Quick Add + Buddy, onboarding syntax fix |
| v84.x | Onboarding browser detection, new Pards Golf icon, contact icon overhaul |
| v83.x | Onboarding system (Screen 1: browser install, Screen 2: PWA first launch), Safari copy-link, version stamp |
| v82.x | Side Bets live for all users, 2026 Derrick Member Guest teams loaded, BJ button sync fix, Side Bets sticky header |
| v81.x | Snake 3-Putt picker, Mid-Round Nassau matchups, Match Cards tabbed UI, starting hole picker, history course filter |
| v80.0 | Milestone — icon overhaul complete, game pill landscape fix |
| v75.x | Game pill landscape fix, popup header icons fixed |
| v74.x | Players/Hole pill redesigns, player number style |
| v73.x | Manage Players icons, info icons, opacity ternary fix |
| v72.x | Gold PNG icon system introduced throughout |
| v71.x | Haptic feedback, 6-Point overlay, help bar improvements |
| v70.x | Round preview removed, game pill labels removed |
| v68.x | Icon enlargement series |
