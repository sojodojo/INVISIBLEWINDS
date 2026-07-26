# svg-book-viewer — "My Life Stories" web edition

A fully self-contained, static web edition of the photo book **My Life Stories**
(36 pages), with the same page-flip animation Mixbook uses in its preview
(the open-source, MIT-licensed [StPageFlip](https://github.com/Nodlik/StPageFlip) engine).

No server code, no build step, no external requests — every page, photo, and font is in
this folder. It can be hosted on any static web host.

## What's in the folder

| File / folder | Purpose |
|---|---|
| `embed.html` | **The page you embed.** Chromeless viewer sized to fill an iframe. |
| `index.html` | Evaluation portal (Read tab + page-inspector grid). Not required in production, but harmless to keep. |
| `pages.js` | All 36 pages as inline SVG (bundled so no fetch/CORS issues). |
| `pages/` | The same 36 pages as individual `.svg` files (reference / reprocessing). |
| `assets/media/` | 94 photos & backgrounds (originally from Mixbook's CDN). |
| `assets/fonts/` | Font CSS + WOFF files used by the book text. |
| `vendor/page-flip.browser.js` | StPageFlip v2.0.7 (MIT). |

Total size ≈ 61 MB.

## Deploying (the site owner does this once)

The destination site (artsonthemoveonline.com) runs **Squarespace 7.1**, which cannot host
these files itself (Squarespace has no arbitrary-file hosting). Host this folder on any
free static host and embed it with an iframe:

**Option A — Netlify Drop (easiest, no account tooling):**
1. Go to https://app.netlify.com/drop
2. Drag this whole folder onto the page.
3. You get a URL like `https://something.netlify.app` — that's it.

**Option B — Cloudflare Pages / GitHub Pages / any web server:** upload the folder as-is;
`embed.html` must be reachable at a public URL.

## Embedding in Squarespace 7.1

> Requires a Squarespace **Business plan or higher** (Code Blocks).

1. Edit the target page → add a block → **Code**.
2. Paste (replace `YOUR-HOST` with the deploy URL from above):

```html
<div style="position:relative;width:100%;padding-bottom:58%;height:0;overflow:hidden;">
  <iframe
    src="https://YOUR-HOST/embed.html?bg=%23ffffff"
    style="position:absolute;top:0;left:0;width:100%;height:100%;border:0;"
    loading="lazy"
    allowfullscreen
    title="My Life Stories — flip through the book">
  </iframe>
</div>
```

Notes:
- `?bg=` sets the background behind the book (URL-encoded CSS color, `%23ffffff` = white).
  Match it to the Squarespace page background.
- `padding-bottom:58%` reserves the aspect ratio (two square pages side by side + controls).
  Increase it if the book looks cramped.
- Readers can flip by dragging page corners, the ‹ › buttons, or arrow keys.

## Caveats / licensing

- **Fonts**: the embedded fonts (Futura, Avenir Next, etc.) are Monotype-licensed webfonts
  originally served by Mixbook. For a community/non-commercial page the practical risk is
  low, but for strict compliance substitute open-alternative fonts (the SVGs reference
  families by name in `assets/fonts/*.css`).
- **Images**: pages embed Mixbook's 1400px display renditions. Higher-resolution originals
  exist and can be re-extracted if deeper zoom is ever needed.
- **Content**: the book text and artwork belong to the book's creators; this package is for
  their own publication of their own work.
