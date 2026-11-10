# Pool Test Guide

A phone web app that walks you through a Taylor professional pool test kit one step at a time. It covers which reagent to add, how many drops, what color to look for and which comparator value to tap. At the end you get a finished entry for the commercial pool log.

## What it does

- **Two kits supported**
  - **Taylor K-2006 (FAS-DPD):** you count drops for chlorine. Tap a big **+1 drop** button for each drop and the app converts the count to ppm (0.2 ppm per drop at 25 mL, 0.5 at 10 mL).
  - **Taylor K-2005 (DPD):** you match the pink color against the comparator for chlorine.
- **Tests:** free, combined and total chlorine; pH; acid/base demand; total alkalinity (R-0007 / R-0008 / R-0009, ×10); calcium hardness (R-0010 / R-0011L / R-0012, ×10); cyanuric acid (R-0013 and the view tube); water temperature.
- **Log entry:** checks each result against target ranges you can edit, works out the Langelier saturation index, and records whether the main drain is visible, chemicals added, notes and initials.
- **Pool log:** saved on the phone. You can copy any entry as text or export everything as a CSV.
- **Works offline** once it's installed, and keeps the screen awake during a test.

## Deploy to Vercel

1. Put this folder in its own GitHub repository.
2. In Vercel: **Add New → Project → Import** that repo. Framework preset **Other**. No build command, no output directory.
3. Deploy. You'll get a URL like `https://pool-test-guide.vercel.app`.

No build step. It's plain HTML, CSS and JavaScript.

## Put it on your home screen

- **iPhone (Safari):** open the URL, tap **Share → Add to Home Screen**.
- **Android (Chrome):** open the URL, tap **⋮ → Add to Home screen** (or **Install app**).

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app |
| `manifest.webmanifest` | Home-screen name, icon and colors |
| `sw.js` | Offline cache. Change `VERSION` when you edit `index.html` |
| `icons/` | App icons |
| `vercel.json` | Cache headers for the service worker |

## Important

The steps follow Taylor's published K-2006 / K-2005 procedures. Always check them against the instruction card in your own kit. If your card says something different, follow the card. The colors on screen are only approximate, so do the actual matching against the comparator block. The target ranges are common guidelines. Set them to whatever your health department and facility require (**Settings → Target ranges**).

Log data lives in the phone's browser storage. Clearing Safari/Chrome website data erases it, so export a CSV regularly.
