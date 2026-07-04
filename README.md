# ⛳ Pards Golf

A single-file Progressive Web App (PWA) for tracking golf scores and betting games — built for the Derrick Golf & Winter Club and other courses on request.

**Live App:** https://bdcomeau.github.io/pardsgolf/

---

## Features

### Score Tracking
- Up to 5 players per round
- Score wheel with swipe / tap / arrow input
- Hole-by-hole gross scoring with handicap strokes applied
- Real-time score strip above each player wheel showing all 18 holes with birdie/eagle/bogey indicators
- Shotgun start support with Shift Scores to fix hole alignment mid-round
- Auto-advance or manual confirm mode

### Betting Games
All games support gross or net scoring, configurable bet amounts, and live money totals:
- **Nassau** — 2v2 and 1v1, with optional presses and The International (double-or-nothing on hole 18)
- **6-Point Game** — point allocation per hole based on relative scores
- **Stableford** — points vs par, full live leaderboard
- **Skins** — carry-over skins with configurable tie rules
- **Vegas** — 2v2, scores combined into two-digit numbers, team difference per point
- **Snake 3-Putt** — snake passes on every 3-putt, settles at round end
- **Birdie Juice** — credits earned for birdies/eagles, redeemable for cash

### Golf Canada Integration
- Fetch live handicap indexes by 10-digit Golf Canada ID
- Automatic handicap adjustments per tee deck (Deck 1–4 offsets)
- Stroke index applied per hole for each player

### Player Management
- **Manage My Players** — full contact list with edit, tee preference, typical score, and Golf Canada ID
- **Me contact** — designated player for career earnings tracking; protected from accidental deletion
- Load up to 5 favourites with one tap
- A–Z alphabet rail for fast scrolling in large contact lists

### Course Library
Pre-loaded courses with full hole-by-hole par, stroke index, and yardage for multiple tee decks:
- Derrick Golf & Winter Club (Edmonton)
- Glendale Golf & Country Club (Edmonton)
- Windermere Golf & Country Club (Edmonton)
- The Ranch Golf & Country Club (Acheson)
- Jagare Ridge Golf Club (Edmonton)
- Broadmoor Golf Club (Sherwood Park)
- River Ridge Golf Club (Spruce Grove)
- The Rise Resort (Vernon, BC)
- Predator Ridge Golf Resort — Ridge & Predator courses (Vernon, BC)
- + more

### Weather
- Live weather on the score entry screen: icon + temp left of hole number, condition right
- Edmonton courses via WeatherLink; all others via Open-Meteo GPS
- Weather at round start captured for history records

### Side Bets (Event Mode)
A standalone tournament overlay for special events (e.g. Member-Guest):
- Load team roster from CSV (up to 90 teams)
- Hold-to-activate team betting (700ms hold)
- WIN / LOSS settlement with career earnings tracking
- Triple backup: dedicated localStorage, live History checkpoint, silent save on settle
- A–Z alphabet quick-jump rail
- Visible on event day only (configurable date)

### Round History
- All rounds saved locally with full scores, games, and money results
- Exportable as PDF or shareable scorecard image
- Career earnings per player tracked across all rounds
- Edit past rounds to correct WIN/LOSS outcomes

---

## Technical Details

| Item | Detail |
|------|--------|
| Architecture | Single HTML file — all JS, CSS, assets inlined |
| Storage | `localStorage` only, no backend |
| PWA | Installable via Safari "Add to Home Screen" |
| Service Worker | Offline-capable with cache-first strategy |
| Golf Canada API | Via configurable Cloudflare Worker proxy |
| Weather APIs | Open-Meteo (GPS-based) + WeatherLink (Edmonton) |
| Supported Platforms | iOS Safari, Chrome, desktop browsers |

---

## Deployment

1. Edit `pards-golf.html` as needed
2. Upload to the `bdcomeau/pardsgolf` GitHub repository via browser
3. GitHub Pages auto-deploys — allow ~2 minutes
4. Force a cache refresh on devices by visiting the app and waiting for the service worker update prompt

---

## Configuration (Developer)

Key constants near the top of the main `<script>` block:

```javascript
const CURRENT_VERSION = 'pards-v16.5';   // Bump on every release

const SIDE_BETS_EVENT = {
  date: '2026-07-17',                    // Event date (YYYY-MM-DD)
  name: 'Member Guest 2026',
  teams: [...]                           // Load from CSV before event
};

const EDMONTON_COURSE_IDS = new Set([...]);  // Use WeatherLink for these
const COURSE_COORDS = {...};                  // GPS coordinates per course
```

Golf Canada API credentials are stored in `localStorage` under `gcConfig` — set via the in-app settings screen.

---

## July 17, 2026 — Pre-Event Checklist

- [ ] Load real 90-team CSV into `SIDE_BETS_EVENT.teams`
- [ ] Confirm `SIDE_BETS_EVENT.date` is `'2026-07-17'`
- [ ] Remove Bruce Comeau test mode from `isSideBetsDay()` and `isSideBetsVisible()`
- [ ] Verify Me contact is correct on all devices
- [ ] Test Side Bets 💰 button appears on event morning
- [ ] Confirm Golf Canada API credentials are set on all devices

---

## Version History (Recent)

| Version | Summary |
|---------|---------|
| v16.5 | Me contact protected from deletion; hold-to-confirm delete for all players |
| v16.4 | Duplicate Start Round button fix |
| v16.3 | Start Round button: course photo watermark, live player names, lime-green pulse |
| v16.2 | BJ tracking toggle now respected in scorecard-only mode |
| v16.1 | Course name strip re-added to score screen |
| v16.0 | Major UI refresh: condensed score screen, weather in hole nav, Mid Round Settings pill, score strip above wheel |
| v15.25 | Stable base — renderOneMatchCard restored, score screen layout, Who Strokes panels inline |

---

## License

Private — Bruce Comeau. Not for redistribution.
