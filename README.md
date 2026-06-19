# Momentum — GitHub Pages + Home-Screen Install

This folder is a ready-to-host version of Momentum. Once it's on GitHub Pages,
you (and customers) can open it on a phone and **Add to Home Screen** — it launches
full-screen with your botanical icon, like a real app.

## What's in here
- `index.html` — the Momentum app (with the install/offline setup added)
- `manifest.webmanifest` — tells phones the app name, colours, and icon
- `sw.js` — service worker (enables install + offline; serves your latest version)
- `icon-192.png`, `icon-512.png` — home-screen icons
- `icon-maskable-512.png` — icon padded so Android's circle crop never clips it
- `apple-touch-icon.png` — the icon iPhones use

## Setup (about 5 minutes)

1. **Make a NEW repository** for this — keep it separate from your Task Tracker
   repo. (Two apps sharing one repo is what caused the old "wrong version on
   Android" problem, because both want to be the repo's `index.html`.)
2. Upload **all** the files in this folder to the new repo (drag them into the
   "Add file → Upload files" box). They must sit at the repo root, next to each other.
3. In the repo: **Settings → Pages →** Build and deployment → Source: *Deploy from
   a branch* → Branch: `main` (or `master`) → `/ (root)` → **Save**.
4. After a minute, GitHub gives you a URL like
   `https://yourname.github.io/your-repo/`. That's your live link.

## Add to Home Screen
- **iPhone (Safari):** open the link → Share button → **Add to Home Screen**.
- **Android (Chrome):** open the link → ⋮ menu → **Install app** / **Add to Home screen**.

The botanical icon appears with the label **Momentum**.

## Good to know
- **HTTPS is automatic** on GitHub Pages — that's required for the install to work.
- **Updating the app:** just replace `index.html` in the repo. The service worker
  fetches your latest version whenever someone opens it online, so customers won't
  get stuck on an old build. (If you change icons or the manifest, bump `momentum-v1`
  to `momentum-v2` at the top of `sw.js` so phones pick up the new files.)
- **Customer data is safe across updates.** Their tasks live in the browser's storage
  for your site's address, which is separate from these files — updating the app
  never erases their data.
- **Change the home-screen name:** edit `short_name` in `manifest.webmanifest` and
  `apple-mobile-web-app-title` in `index.html`.
- The app's fonts load from Google when online; a first launch with no connection
  falls back to system fonts — the app still works fully either way.
