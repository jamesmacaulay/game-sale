# Games & TTRPG Purge Sale — GitHub Pages Site

A single-file static site (`index.html`) for browsing secondhand board games and TTRPG books.
Hosted via GitHub Pages. No build step required.

## Structure

```
games-purge/
├── index.html          # Entire site — HTML, CSS and JS all inline
├── images/             # Web-optimised photos (88 × JPEG, ~47 MB total)
│   └── IMG_4833.jpeg … IMG_4920.jpeg
├── CLAUDE.md           # This file
└── .gitignore
```

## How to edit products

All product data lives in the `PRODUCTS` array near the top of the `<script>` block in `index.html`.

Each entry looks like:
```js
{
  id: 1,                          // unique integer, don't reuse
  title: "Product Name",
  publisher: "Publisher Name",
  system: "System / Format",      // shown on card as small label
  category: "World of Darkness",  // must match a value in CATEGORIES array
  images: ["IMG_4833.jpeg", "IMG_4839.jpeg"],  // front first
  price: null,                    // null = "Price TBD", "SOLD" = sold, "$25" = price
  notes: "Any condition notes or extra info"
}
```

### Setting a price
Change `price: null` to `price: "$25"` (or whatever currency/amount you like).

### Marking an item sold
Change `price: null` to `price: "SOLD"`.

### Adding a new category
Add it to the `CATEGORIES` array below the `PRODUCTS` array.

## GitHub Pages setup

1. Create a GitHub repo (e.g. `games-purge`)
2. From this folder: `git remote add origin https://github.com/YOUR_USERNAME/games-purge.git`
3. `git push -u origin main`
4. In GitHub repo Settings → Pages → Source: **Deploy from branch** → `main` / `/ (root)`
5. Your site will be live at `https://YOUR_USERNAME.github.io/games-purge/`

Note: the images directory is ~47 MB. GitHub's soft limit for repo size is 1 GB, so this is fine.
If the image folder ever grows large, consider moving images to Git LFS or an external host (e.g. Cloudflare R2, Bunny CDN).
