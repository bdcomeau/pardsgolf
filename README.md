# ⛳ Pards Golf

**A mobile scorecard, betting tracker, and Birdie Juice ledger for golf groups.**

> Nassau · 6-Point · Stableford · Skins · Vegas · Snake · Match Cards · The International

---

## Live App

**[https://bdcomeau.github.io/pardsgolf/pards-golf.html](https://bdcomeau.github.io/pardsgolf/pards-golf.html)**

Install to your iPhone Home Screen from Safari for the full PWA experience.

---

## What It Does

Pards Golf is a single-file HTML Progressive Web App. Everything runs on your device — no server, no accounts, no ads, no data collection. Your round data never leaves your phone.

- **Scorecard** — 1–5 players, any course, any tee, handicap-adjusted strokes per hole
- **Betting games** — Nassau (1v1 and 2v2 High-Low), 6-Point, Stableford, Skins, Vegas, Snake 3-Putt, Match Cards, The International
- **Birdie Juice** — automatic credit tracking for birdies, eagles, holes-in-one. Streak names: Turkey, Four-Bagger, Badger, Six-Pack, Legend
- **125+ courses** — all tees, par, stroke index, ratings, and slopes pre-loaded. No internet required for scoring.
- **Golf Canada integration** — live handicap index via GolfNet API
- **Round History** — lock, edit, export, share, print

---

## Current Version

**v20.0** — July 2026

### What's New in v20.0
- **Slim round bar** — replaces full bottom nav during a round. One tap back to scorecard, ☰ Menu for everything else. Eliminates accidental navigation.
- **Confirm Scores always ON** — auto-advance removed permanently. Every hole requires an explicit confirmation tap.
- **Complete Round flow** — hole 18 shows "✓ Complete Round 🏆". Saves immediately, shows gold pulsing banner with Start New Round and View & Share Results.
- **Mid-Round Settings** via ☰ Menu with all 11 sections accessible
- **27% smaller file** — 3.9 MB → 2.9 MB via logo deduplication
- **Doug Boyer Easter Egg** 🥂 — because some things need to be documented

---

## Courses

125+ courses across Canada and USA, organized by region:

| Region | Highlights |
|--------|-----------|
| **Alberta** | Derrick GWC, Banff Springs, Kananaskis, Jasper Park Lodge, Glencoe, Mickelson National |
| **British Columbia** | Predator Ridge, Bear Mountain, Gallaghers Canyon, Chateau Whistler, Nicklaus North |
| **Nova Scotia** | Cabot Links, Cabot Cliffs, Cape Breton Highlands Links |
| **Prince Edward Island** | Links at Crowbush Cove |
| **Quebec** | Royal Montreal Golf Club (Blue, Dixie, Red) |
| **Arizona** | Troon North, Boulders, Kierland, Pinnacle Peak, Phoenician |
| **California** | PGA West (all 9), Desert Willow, Indian Ridge, The Lakes CC |
| **Georgia** | Reynolds Lake Oconee (9 courses) |
| **Hawaii** | Wailea Golf Club (3), Makena |
| **North Carolina** | Pinehurst No. 1–10 |
| **Oregon** | Bandon Dunes (all 5 courses) |

---

## Installing on iPhone

1. Open **Safari** and go to the live URL above
2. Tap the **Share button** (↑)
3. Tap **"Add to Home Screen"**
4. Always launch from the Home Screen icon

> ⚠️ Do NOT use "Remove App" — this permanently erases all local data.

---

## Betting Games

| Game | Description |
|------|-------------|
| **Nassau** | Front 9 · Back 9 · Total 18. Auto-press. 1v1 or 2v2 High-Low. |
| **The International** | Available after Hole 17 — Hole 18 can void, double, or leave the Nassau pot unchanged. |
| **6-Point** | 3-player. Low net = 4pts, second = 2pts, third = 0. |
| **Stableford** | Net scoring: Double bogey=0, Bogey=1, Par=2, Birdie=3, Eagle=4, Albatross=5. |
| **Skins** | Win outright or skin carries. Gross or Net. |
| **Vegas** | 2v2. Combine scores low-digit first. Birdie flips opponent's number. |
| **Snake** | 3-putt penalty game. Settles every 3 holes. |
| **Match Cards** | 1v1 Nassau vs players in other groups. Enter their scores later. |
| **Birdie Juice** | Birdie=1cr · Eagle=2cr · Albatross=4cr · Hole-in-One=5cr. Redeem for drinks. |

---

## Tech Stack

- Single HTML file (~2.9 MB) — HTML + CSS + JavaScript, no frameworks
- PWA with service worker for offline use
- All data in `localStorage` — nothing leaves the device
- Golf Canada handicap via Cloudflare Worker proxy → GolfNet API
- Weather via Open-Meteo (all courses) and WeatherLink (Edmonton courses)

---

## Privacy

- No analytics
- No ads
- No user accounts
- No server
- Golf Canada credentials stored only on your device, used only to fetch handicap index

---

## Development

Single developer — Bruce Comeau ([@bdcomeau](https://github.com/bdcomeau)).

Built and maintained with assistance from Claude (Anthropic). All course data validated against Golf Canada GolfNet database.

---

*May your drives be long, your putts be true, and your Birdie Juice credits never run dry.* ⛳
