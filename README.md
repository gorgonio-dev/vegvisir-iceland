# Vegvísir — Iceland 3D Trail Explorer

A mobile-first, single-file web app that flies over **real 3D satellite terrain of Iceland** with 26 curated hikes, waterfalls and viewpoints as tappable cairn pins, color-coded by difficulty:

- 🟩 **Easy** — walk-up spots (Gullfoss, Reynisfjara, Jökulsárlón…)
- 🟧 **Moderate** — real hikes (Glymur, Reykjadalur hot river, Stuðlagil…)
- 🟥 **Hard** — big days (Fimmvörðuháls, Laugavegur, Hvannadalshnúkur, Askja)

Everything runs from one `index.html` — no build step, no API keys, no server code.

## Accounts

| Role  | Username | Password    | Can do |
|-------|----------|-------------|--------|
| Guest | — (button) | —         | View map, pins, photos, list |
| Hiker | `Sydney` | `Hiker121!` | Everything above + save ♥ favourites |
| Admin | `admin`  | `grincho`   | Everything above + add / edit / delete pins |

> ⚠️ **Honest security note:** this is a static site, so logins are checked in the browser and the credentials are visible to anyone who reads the page source. Treat them as a demo gate, not real security. Real auth would need a small backend (Render web service + database) — happy next step if you want it.

## Tech (all free, no keys)

- **Map engine:** MapLibre GL JS v4 (open source)
- **Satellite imagery:** Esri World Imagery tiles (free with attribution, kept in the map)
- **3D elevation:** AWS Open Data / Mapzen Terrarium terrain tiles (free, no key)
- **Photos:** fetched live from each destination's **Wikipedia article lead image** (Wikimedia Commons, freely licensed) — this guarantees every photo actually belongs to that exact place. Credit line shown under each photo.
- **Pins & favourites:** saved in the browser (localStorage), so admin edits persist per device.

## Deploy free on Render (~2 minutes)

1. Push this folder to a GitHub repo (just `index.html`, `README.md`, `render.yaml`).
2. In [Render](https://render.com): **New → Static Site**, pick the repo.
3. Settings:
   - **Build command:** *(leave empty)*
   - **Publish directory:** `.`
4. Click **Create Static Site** → you get a free `https://your-name.onrender.com` URL.

(Or skip GitHub: Render also accepts "Deploy from public Git URL". The included `render.yaml` makes it a one-click Blueprint deploy too.)

## Using it on a phone

- **Tap a cairn** → bottom sheet with photo, difficulty, distance/time/terrain, and a **Navigate ↗** button that opens Google Maps directions to the exact coordinates.
- **Chips** filter Easy / Moderate / Hard / Hikes / Spots / ♥ Saved.
- **3D** button toggles terrain + tilt; drag with two fingers to tilt/rotate yourself.
- **☰** opens the full sortable list; **⌂** resets to the whole-island view.
- **Admin:** tap **+**, then tap the map to drop a pin and fill in the form. Edit/Delete appear inside every pin's sheet.

## Data honesty

Coordinates and facts were curated from well-known values for each site (heights, distances, typical times). Distances/times are typical ranges — always check [safetravel.is](https://safetravel.is) and [vedur.is](https://vedur.is) before hiking in Iceland; conditions change fast, and Reynisfjara sneaker waves and highland roads are genuinely hazardous.
