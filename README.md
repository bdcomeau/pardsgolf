# ⛳ Pards Golf

**A mobile scorecard, betting tracker, and Birdie Juice ledger for golf groups.**

Nassau · 6-Point · Stableford · Skins · Vegas · Snake · Match Cards · Birdie Juice

---

## 🚀 Install on Your iPhone

Pards Golf is a Progressive Web App. **Do not use the App Store** — install directly from Safari:

1. Open **Safari** on your iPhone
2. Go to: **https://bdcomeau.github.io/pardsgolf/pards-golf.html**
3. Tap the **Share** button (square with arrow, bottom toolbar)
4. Tap **"Add to Home Screen"**
5. Tap **"Add"**
6. Always launch from the **Home Screen icon** — not a Safari bookmark

> ⚠️ **Important:** Do NOT use "Remove App" on the Home Screen icon — this permanently wipes all local data. Export a backup first.

---

## 🎮 Games

### Nassau (2v2 High-Low)
Two teams of two. Each team contributes their low ball and high ball net score. A gold ✓ marks which score counted. Auto-presses tracked automatically. Ball Toss mode selects teams automatically based on where balls land.

### Nassau (1v1)
One-on-one matchups — run multiple simultaneously. Full front 9, back 9, and total tracking.

### The International (The Big I)
Available to the losing team after Hole 17. A single Hole 18 can cancel, double, or leave unchanged the entire Nassau pot.

### 6-Point Game
Three-player. Each hole: low net wins 4 pts, second 2, third 0. Ties for low give 3 each.

### Stableford
Points for net score: Double bogey or worse = 0 · Bogey = 1 · Par = 2 · Birdie = 3 · Eagle = 4 · Albatross = 5

### Skins
Win outright → win the skin. Tie → skin carries over. Gross or net. Void or Last Hole Sweeps after 18.

### Vegas (2v2)
Two-against-two. Scores combine low digit first (4 and 5 = 45). The Flip: opponent birdie flips your number (45 → 54).

### Snake 3-Putt
Whoever 3-putts picks up the snake. Settles every 3 holes. Snake holder at holes 3, 6, 9, 12, 15, 18 pays everyone.

### Match Cards
Play 1v1 Nassau vs golfers in other groups. Your scores tracked live — opponents' entered later in the clubhouse.

### Birdie Juice
Gross birdies = 1 credit · Eagles = 2 · Albatross = 4 · Hole-in-One = 5. Works in Games mode and Scores-Only mode.

| Streak | Name |
|--------|------|
| 3 consecutive birdies | 🦃 Turkey |
| 4 | ⚾ Four-Bagger |
| 5 | 🦡 Badger |
| 6 | 🍺 Six-Pack |
| 7+ | 👑 Legend |

---

## 📱 Features

- **140+ courses** built in — Alberta, BC, Nova Scotia, PEI, Quebec, Arizona, California, Georgia, Hawaii, North Carolina, Oregon
- **Live handicap fetching** from Golf Canada
- **Live weather** on setup screen and during round
- **Ball Toss** — tap the two closest balls to auto-generate 2v2 matchups
- **Shotgun starts** — set starting hole, shift scores mid-round if needed
- **Mid-Round Settings** — add/remove players, change handicaps, add games, all back-calculated
- **Round History** — view, edit, lock, share all past rounds
- **Backup & Restore** — full JSON export/import of all data
- **Birdie celebrations** — popup animations for birdies, eagles, hole-in-ones, streaks
- **Offline** — no internet required once installed

---

## 🔒 Privacy & Data

- **Everything stays on your device.** All round data, player names, handicaps, and Golf Canada IDs are stored exclusively in your iPhone's browser storage.
- Golf Canada credentials are used only to fetch handicap indexes and are never transmitted to anyone other than Golf Canada's own secure API.
- No analytics. No ads. No user accounts. No server.

---

## 💾 Backing Up Your Data

> ⚠️ iOS can wipe PWA storage when you remove the Home Screen icon or run low on storage. Back up regularly.

1. Tap **Backup** in the setup screen utility bar
2. Tap **📤 Export Backup**
3. Save to Files, iCloud Drive, or email

To restore: tap **Backup** → **📥 Import Backup** → select your backup file.

---

## 🔄 Updating the App

Tap **Update App** in the setup screen utility bar. If still outdated, force-close and reopen Safari, or clear Safari site data for `bdcomeau.github.io`.

---

## 🛠️ Technical Details

- **Type:** Single-file HTML Progressive Web App (PWA)
- **Size:** ~4.3MB (includes all course data, icons, and assets)
- **Storage:** localStorage (no server, no cloud sync)
- **Weather:** WeatherLink (Edmonton courses) · Open-Meteo (all other courses)
- **Handicaps:** Golf Canada API via Cloudflare Worker proxy
- **Course data:** GolfNet API

---

## 📋 GolfNet Course Lookup Tool

A companion tool for finding GolfNet course IDs and exporting course data:

**https://bdcomeau.github.io/pardsgolf/golfnet-lookup.html**

Add to your iPhone Home Screen for quick access.

---

## 📖 User Manual

Tap **Settings / Help** in the setup screen utility bar to open the in-app manual.

---

*Built with ❤️ in Edmonton, AB · Pards Golf v70.4*
