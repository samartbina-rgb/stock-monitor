# Compare — installable stock chart PWA

## What's in this folder
- `index.html` — the whole app (no build step, no dependencies to install)
- `manifest.json` — tells the phone how to install it (name, icon, colors)
- `sw.js` — service worker, caches the app shell so it opens instantly and works offline (price data itself still needs internet)
- `icon-192.png`, `icon-512.png` — home screen icons

## 1. Host it (free, ~2 minutes)
A PWA can only be installed from a real `https://` address — not from a file on your computer. Easiest free options:

**Netlify Drop** (no account needed)
1. Go to https://app.netlify.com/drop
2. Drag this whole folder onto the page
3. You'll get a live URL like `https://random-name-123.netlify.app`

**GitHub Pages** (if you already use GitHub)
1. Create a new repo, upload these files
2. Repo Settings → Pages → deploy from the `main` branch
3. Your URL will be `https://yourusername.github.io/reponame`

**Vercel**
1. `npm i -g vercel` then run `vercel` inside this folder, or drag-and-drop at vercel.com/new

## 2. Install it on your phone
**iPhone (Safari):** open your URL → Share icon → "Add to Home Screen"
**Android (Chrome):** open your URL → ⋮ menu → "Install app" (or "Add to Home screen")

It'll now appear as a real app icon, open full-screen with no browser bar, and stay installed.

## 3. Connect live data
Open the app, tap the 🔑 icon, paste a free API key from https://twelvedata.com (no card required). The key is saved only in the browser storage on your phone — nothing is sent anywhere except Twelve Data's API.

## Notes
- Free Twelve Data tier: 8 requests/minute, 800/day. The app fetches symbols one at a time with a short delay to stay under that.
- To update the app later, just re-upload the changed files to the same host — installed users get the new version next time they open it (the service worker refreshes the cache).
