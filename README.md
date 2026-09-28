# Pulse Board — launcher PWA

An installable home-screen app that opens Mike's live Pulse Board on claude.ai.
All data, sync, and the morning update stay on claude.ai; this app is the icon,
splash screen, and one-tap entry point. It opens offline too (showing an
offline note), and auto-opens the board on launch (toggle on the splash).

## Files
- `index.html` — splash + launcher. The board link is `BOARD_URL` near the top of the script.
- `manifest.webmanifest` — app name, colors, icons, "Open board now" shortcut.
- `sw.js` — caches the launcher shell (never the board itself).
- `icons/` — app icons (standard, maskable, Apple touch, favicon).

## Deploy (pick one — any static HTTPS host works)

**GitHub Pages (free)**
1. Create a new repo (e.g. `pulse-board`), upload everything in this folder to its root.
2. Settings → Pages → Source: *Deploy from a branch* → `main` / root → Save.
3. After a minute it's live at `https://<you>.github.io/pulse-board/`.

**Netlify Drop (fastest)** — drag this folder onto https://app.netlify.com/drop.

**Azure Static Web Apps / BIW hosting** — upload the folder as-is; no build step.

## Install
- **iPhone:** open the URL in Safari → Share → *Add to Home Screen*.
- **Android / Chrome / Edge:** open the URL → tap *Install* on the splash (or browser menu → *Install app*).

## Notes
- **iPhone sign-in:** home-screen apps on iOS keep their own cookies, separate
  from Safari. The first time you open the board from the icon, sign in to
  claude.ai once; it remembers you after that.
- **Android:** the board opens in a Chrome tab that shares your existing
  claude.ai login (or in the Claude app, if it handles the link).
- If the board's URL ever changes, edit `BOARD_URL` in `index.html` and bump
  `CACHE` in `sw.js` (e.g. `pulse-launcher-v2`) so installed copies update.
