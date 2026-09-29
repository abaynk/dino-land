# Dino Land

**Live site:** https://abaynk.github.io/dino-land/

A bilingual (English / Russian) dinosaur picture book for little kids: 20 cartoon dinosaurs, read-aloud facts, roars, and three simple games.

It's a plain static site. There's no build step and no server code, so any static host works.

## Editing

Everything lives in `index.html`, unminified:
- `DINOS` holds the facts, sizes and dates in English and Russian.
- `ART` holds the cartoon drawings as point lists that are smoothed into SVG paths.
- `T` holds the interface text in both languages.
- The `Sound` and `Voice` modules handle the synthesised roars and the recorded voice packs.

New or changed spoken lines need new recordings in `audio/`. Until they exist, the page falls back to the device's voice for them.

## Put it online

This repo is set up for **GitHub Pages**: Settings → Pages → Deploy from a branch → `main` / `(root)`. It also works on any other static host:

**Netlify Drop (easiest, no tools):** open https://app.netlify.com/drop, sign in, and drag this whole folder onto the page. You get a public `*.netlify.app` link in a few seconds. You can rename it under Site configuration → Change site name.

**Vercel:** in this folder run `npx vercel --prod` and accept the defaults.

**Cloudflare Pages:** go to Workers & Pages → Create → Pages → Upload assets, and upload this folder.

The site must be served over HTTP. The voice recordings in `audio/` are fetched by the page, and browsers block that when you double-click `index.html` from disk. In that case the site falls back to the device's robot voice.

To try it locally: `npx serve .` or `python3 -m http.server`, then open the printed address.

## On a phone or tablet

Open the link and use **Add to Home Screen** (Safari: Share button; Chrome: ⋮ menu). It then opens full-screen with its own icon and no browser bar.

## What's inside

| Path | What it is |
|---|---|
| `index.html` | The whole app: drawings, facts, games, styles and code |
| `audio/en/*.json`, `audio/ru/*.json` | Recorded voice lines, one pack per dinosaur (MP3, base64) |
| `icons/`, `manifest.webmanifest` | Home-screen icon and app manifest |

## Credits and license

- English voice: [Kokoro-82M](https://github.com/hexgrad/kokoro), voice `af_heart` (Apache 2.0).
- Russian voice: [Piper](https://github.com/rhasspy/piper) `ru_RU-ruslan-medium`, trained on the [RUSLAN corpus](https://ruslan-corpus.github.io/) (CC BY-NC-SA 4.0). Because of this voice, keep the site **free and non-commercial**, and keep the credits line in the footer.
- Drawings, text and code were made for this site.
