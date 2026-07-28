# INVISIBLE WINDS — web edition

This is the complete web edition of the photo book **"Invisible Winds — Stories You Can Not
See"** (36 pages), with a realistic page-turn animation. Everything the book needs — pages, photos,
fonts, and the page-flip engine — is inside this folder. There is no database, no server
code, and no build step: any static web host can serve it as-is.

| File / folder | What it is |
|---|---|
| `embed.html` | **The page you embed on your website.** A chromeless viewer that fills whatever frame it's placed in. |
| `index.html` | A reading portal with a page-inspector view. Optional; handy for checking pages. |
| `iframe-demo.html` | A mock web page with the book embedded, to preview how it looks in context. |
| `pages/`, `pages.js` | The 36 book pages. |
| `assets/` | Photos and fonts. |
| `vendor/` | [StPageFlip](https://github.com/Nodlik/StPageFlip) (MIT license), the page-turn animation. |

---

## Embedding the book on your website

The book is currently hosted at:

```
https://sojodojo.github.io/INVISIBLEWINDS/embed.html
```

On Squarespace (Business plan or higher), edit the page where the book should appear,
add a **Code** block, and paste:

```html
<div style="position:relative;width:100%;padding-bottom:58%;height:0;overflow:hidden;">
  <iframe
    src="https://sojodojo.github.io/INVISIBLEWINDS/embed.html?bg=%23ffffff"
    style="position:absolute;top:0;left:0;width:100%;height:100%;border:0;"
    loading="lazy"
    allowfullscreen
    title="Invisible Winds — flip through the book">
  </iframe>
</div>
```

Tips:
- `?bg=%23ffffff` sets the color behind the book (URL-encoded CSS color; `%23ffffff` is
  white). Match it to your page background.
- `padding-bottom:58%` reserves the height. Increase it if the book looks cramped.
- Readers can turn pages by dragging the page corners, the ‹ › buttons, or arrow keys.

---

## Hosting it yourself (recommended)

Hosting under your own account means the book lives as long as your website does, with no
dependency on anyone else. It also lets you serve it from your own subdomain, e.g.
**book.artsonthemoveonline.com**, so nothing about the embed points anywhere but your own
domain. It's free either way. Two good options:

### Option A — GitHub Pages (what this copy uses)

1. Create a free account at [github.com](https://github.com) if you don't have one.
2. Download this repository: on the repository page, click the green **Code** button →
   **Download ZIP**, and unzip it.
3. In your own GitHub account, create a **new public repository** (any name, e.g.
   `INVISIBLEWINDS`), then upload the unzipped files: **Add file → Upload files**, drag
   everything in, and commit. (If the upload page balks at the folder size, upload the
   folders one at a time — `assets/media` is the big one.)
4. In the repository: **Settings → Pages** → under "Build and deployment", set Source to
   **Deploy from a branch**, branch **main**, folder **/ (root)**, and save.
5. After a minute or two the book is live at
   `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/embed.html`.

**To serve it from book.artsonthemoveonline.com:**

6. In Squarespace: **Settings → Domains → artsonthemoveonline.com → DNS Settings**, add:
   - Type: **CNAME** · Host: `book` · Value: `YOUR-USERNAME.github.io`
7. Back in GitHub: **Settings → Pages → Custom domain**, enter
   `book.artsonthemoveonline.com`, save, and once the check passes tick
   **Enforce HTTPS** (the certificate is provisioned automatically; can take up to an
   hour).
8. Update the iframe `src` to `https://book.artsonthemoveonline.com/embed.html?bg=%23ffffff`.

### Option B — Netlify Drop (no account needed to try)

1. Download and unzip this repository as above.
2. Go to [app.netlify.com/drop](https://app.netlify.com/drop) and drag the whole folder
   onto the page. You'll get a live URL immediately.
3. For the custom subdomain: create the free account when prompted, then
   **Domain settings → Add custom domain** → `book.artsonthemoveonline.com`. Netlify will
   show you the CNAME value to add in Squarespace's DNS settings (same place as above).

---

## Updating the book

If the book's content is ever revised, you'll receive replacement files. Upload them over
the old ones (same names, same folders) and the site updates automatically — nothing else
to do.

## Notes

- **Fonts:** the embedded fonts (Futura, Avenir Next, and others) are commercial webfonts
  licensed to the book's production platform, not to this site. For a community,
  non-commercial page the practical risk is low, but a strictly commercial use should
  substitute open-license fonts.
- **Photos** are 1400px display renditions — sharp for screens. Higher-resolution
  originals exist if ever needed.
- **Content:** the text and artwork belong to the book's creators. This package exists so
  they can publish their own work on their own site.
