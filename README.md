# trouvez-notre-camping-car.fr

Static website to help recover a stolen campervan belonging to Gérard and Michelle Le Blonde.

---

## Quick start (local preview)

No build step required — it's plain HTML.

```bash
# Option A: Python (built-in)
python -m http.server 3000
# then open http://localhost:3000

# Option B: Node (if installed)
npx serve .
# then open http://localhost:3000
```

---

## Adding photos (most important first step)

Photos live in the `images/` folder. The site references these filenames:

| File                       | Where used                  | Recommended size      |
|----------------------------|-----------------------------|-----------------------|
| `images/campervan-hero.jpg`| Hero section (top of page)  | 1400 × 780 px, < 200 KB |
| `images/campervan-1.jpg`   | Gallery photo 1             | 800 × 600 px, < 150 KB  |
| `images/campervan-2.jpg`   | Gallery photo 2             | 800 × 600 px, < 150 KB  |
| `images/campervan-3.jpg`   | Gallery photo 3 (damage)    | 800 × 600 px, < 150 KB  |
| `og-image.jpg`             | Social share preview (root) | 1200 × 630 px, < 200 KB |

**Steps to add a photo:**

1. Save the compressed image into the `images/` folder with the correct filename.
2. Open `index.html` and find the matching photo section (search for `campervan-1.jpg`).
3. Delete the `<div class="gallery-ph">` placeholder block.
4. Uncomment the `<img ...>` block directly above it.
5. Done — no rebuild needed.

**Compress images for free:** squoosh.app or tinypng.com

**Adding more gallery photos:** copy any `.gallery-item` block inside `<div class="gallery-grid">` and update the `src`, `alt`, and caption text.

---

## Updating content

All editable content is in `index.html`. Search for `REPLACE:` to jump to each editable block.

| What to change           | Search for in index.html              |
|--------------------------|---------------------------------------|
| Phone number             | `REPLACE: phone number`               |
| Contact name             | `REPLACE: contact name`               |
| Registration plate       | `REPLACE: registration plate`         |
| Location / date          | `REPLACE: location` / `REPLACE: date` |
| Story paragraphs         | `REPLACE: French story` / `English story` |
| Share text               | JS constants `SHARE_FR` / `SHARE_EN`  |
| Police report reference  | `REPLACE: police-ref`                 |
| Last updated date        | `REPLACE: update this date`           |
| Page URL (after going live) | JS constant `PAGE_URL`             |

---

## Enable the QR code block

1. In `index.html`, find `id="qr-section"`.
2. Change `style="display:none"` to `style="display:block"`.
3. Generate a QR code pointing to `https://trouvez-notre-camping-car.fr` (free: qr-code-generator.com).
4. Save it as `images/qr-code.png`.
5. Swap the `<div class="qr-ph">` for `<img src="images/qr-code.png" alt="QR Code" width="160" height="160">`.

---

## Add the police report reference

In `index.html`, find this comment in the footer:

```html
<!-- REPLACE: uncomment and fill in once you have the police report reference -->
```

Remove the comment tags and fill in the reference number and gendarmerie name.

---

## Deploying

### Netlify (recommended — free, fastest)

1. Go to [netlify.com](https://netlify.com) → sign in → "Add new site" → "Deploy manually"
2. Drag and drop the entire `campervan-site/` folder onto the Netlify dashboard.
3. The site is live in ~10 seconds.
4. To connect your domain (`trouvez-notre-camping-car.fr`): Site settings → Domain management → Add custom domain.
5. To update: drag-drop the folder again, or connect a GitHub repo for automatic deploys.

### Vercel

1. Install Vercel CLI: `npm i -g vercel`
2. In the project folder: `vercel`
3. Follow the prompts. Domain can be added in the Vercel dashboard.

### GitHub Pages

1. Push this folder to a GitHub repository.
2. Go to Settings → Pages → Source: "Deploy from branch" → `main` → `/ (root)`.
3. Add your custom domain in the Pages settings.

---

## Social sharing checklist

Before making the site public:

- [ ] Replace all placeholder photos with real images
- [ ] Create `og-image.jpg` (1200 × 630 px) — this is the preview image on Facebook/WhatsApp
- [ ] Update `PAGE_URL` constant in the `<script>` block at the bottom of `index.html`
- [ ] Verify Open Graph tags using: developers.facebook.com/tools/debug/
- [ ] Verify Twitter card using: cards-dev.twitter.com/validator
- [ ] Test click-to-call on a real mobile device
- [ ] Test WhatsApp share on a real mobile device

---

## File structure

```
campervan-site/
├── index.html          ← entire site (HTML + CSS + JS, all in one file)
├── favicon.svg         ← browser tab icon
├── vercel.json         ← Vercel deployment config
├── netlify.toml        ← Netlify deployment config
├── README.md           ← this file
└── images/
    ├── .gitkeep        ← keeps the folder in git
    ├── campervan-hero.jpg   ← ADD: hero section photo
    ├── campervan-1.jpg      ← ADD: gallery photo 1
    ├── campervan-2.jpg      ← ADD: gallery photo 2
    ├── campervan-3.jpg      ← ADD: gallery photo 3 (show the damage)
    └── og-image.jpg         ← ADD: social share preview (goes in root)
```

---

*Page created to help recover a stolen vehicle — Gérard Le Blonde, Orsinval (59), 11 mars 2026.*
