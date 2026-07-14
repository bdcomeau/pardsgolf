# Pards Golf v80.0

A single-file HTML Progressive Web App for scoring golf rounds and tracking betting games at Derrick Golf & Winter Club, Edmonton AB.

**Live:** https://bdcomeau.github.io/pardsgolf/pards-golf.html

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

---

## Architecture

- **Single file:** `pards-golf.html` — all HTML + CSS + JS + assets (base64 encoded)
- **Size:** ~4.6 MB (images are the primary cost)
- **No server** — runs fully offline after first load
- **PWA:** Installable on iPhone via Safari → Add to Home Screen

---

## Deployment

Three files uploaded to GitHub Pages per release:
1. `pards-golf.html`
2. `index.html` (copy, root redirect)
3. `pards-golf-vXX.X.html` (versioned archive)

---

## Key Features

- Nassau betting — 2v2 High-Low and 1v1 with auto-press, The International
- Live standings — real-time $ standings mid-round
- Golf Canada / GolfNet handicap integration via Cloudflare Worker proxy
- Weather — WeatherLink (Derrick) + Open-Meteo (all other courses)
- Birdie Juice — credit tracking for birdies and eagles
- Full round history with replay and edit
- Backup/Restore — local JSON export/import
- 20+ courses with GPS coordinates and logo art
- Ball Toss team assignment
- Easter eggs — Doug Boyer's Astrolab, Billy's Bunker, Stu's Bunker, Greg's Quiet Zone

---

## Icon System (v80.0)

All 8 game icons are custom illustrated PNGs displayed in:
- Round setup game pills (landscape, height:56px)
- Mid-round settings game pills (same spec)
- Game popup headers (28px via _MM_GAME_ICONS array + innerHTML)

UI icons are gold PNGs (not emoji) for: settings gear, cloud upload, golfer, flag, info "i", lightning bolt, two-golfers, birdie juice glass.

---

## Technical Notes

- iOS compat: function() syntax in renderMMSixPoint (no arrow functions)
- Viewport: interactive-widget=resizes-content — do not remove
- Scroll: history.scrollRestoration = 'manual' at top of script — do not remove
- Syntax check: node --check on extracted script block after every change
- Weather: Edmonton courses → WeatherLink; all others → Open-Meteo

---

## Version History

| Version | Highlights |
|---------|-----------|
| v80.0 | Milestone bump — icon overhaul complete, pill landscape fix |
| v75.x | Game pill landscape fix, popup header icons fixed |
| v74.x | Players/Hole pill redesigns, player number style |
| v73.x | Manage Players icons, info icons, opacity ternary fix |
| v72.x | Gold PNG icon system introduced throughout |
| v71.x | Haptic feedback, 6-Point overlay, help bar improvements |
| v70.x | Round preview removed, game pill labels removed |
| v68.x | Icon enlargement series |
