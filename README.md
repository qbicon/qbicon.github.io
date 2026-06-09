# QBICON — Quantum Biosciences Consortium

The official website for the Quantum Biosciences Consortium — a plain,
hand-editable **multi-page static site** for hosting on GitHub Pages at
**qbicon.org**.

**No JavaScript. No framework. No build step.** Every word, icon, image, link,
and form field lives directly in the HTML. Open any `.html` file in a text
editor and what you see is what you edit; open it in a browser and it just works.

---

## Pages

Each page is its own `.html` file at the project root:

| File | Page |
|------|------|
| `index.html` | Home |
| `mission.html` | Mission & approach |
| `research.html` | Research themes |
| `consortium.html` | Consortium (founders + member institutions) |
| `qbisquared.html` | QBi² flagship event |
| `support.html` | Support — sponsorship & donations |
| `news.html` | News |
| `join.html` | Get involved |

To edit a page's text, headings, or links, open that file and change the words
between the tags. Nothing is loaded from anywhere else.

---

## How editing works

| To change… | Do this |
|------------|---------|
| **Any text, heading, or link** | Open the relevant `.html` file and edit it directly. |
| **The header menu or footer** | These are repeated at the top/bottom of **every** page. Edit them in each file, or use your editor's "find in files / replace across files" to change all at once. |
| **Colours and fonts** | Edit the variables in the `:root` block at the top of `styles.css`. Every colour is defined there once (the green/blue/coral tones come from the logo). The whole site uses Montserrat via `--font`. |
| **A research icon** | Each research card on `research.html` (and the three on `index.html`) contains an inline `<svg>`. Replace the SVG with any other inline SVG to swap the icon. |
| **A card's accent colour** | Cards, pillars, "why" blocks, and tiers carry an inline `style="--accent: var(--q-blue)"` (and `--icon`). Change `q-blue`/`blue-deep` to `q-green`/`green-deep` or `q-coral`/`coral-deep`. |
| **A photo** | Replace the file in `assets/img/` (keep the same name), or change the `src=""` on the `<img>` to a new file. Square images (e.g. 800×800) look best. |
| **The logo** | The header shows `assets/logo-mark.svg`. Replace that file. The full original logo is kept at `assets/logo-full.svg`. |

### Adding or removing items
Everything is a normal HTML block you can copy, paste, or delete:
- **A research theme** — copy one `<li class="card">…</li>` on `research.html` and edit its icon, accent, title, and text.
- **A founder** — copy a `<li class="founder">…</li>` on `consortium.html`.
- **A member institution** — add a `<li>Name</li>` to the `<ul class="institutions">` on `consortium.html`.
- **A news item** — copy a `<li class="news-card">…</li>` on `news.html`.
- **A sponsorship tier** — copy a `<li class="tier">…</li>` on `support.html`.
- **A QBi² speaker** — `qbisquared.html` has a commented-out speaker grid; uncomment it and fill in names/photos.

---

## The forms (Get involved + Sponsor/donate)

Both forms are plain HTML. By default their `action` points to a placeholder
(`https://formspree.io/f/your-form-id`). To make them work, pick one:

- **Easiest:** create a free form at a service like Formspree or Getform, then
  paste your endpoint URL into the `action="…"` of the `<form>` on
  `join.html` and `support.html`.
- **No service:** change the action to `action="mailto:hello@qbicon.org" method="post"`
  — submitting then opens the visitor's email app with the details.

The `<input type="hidden" name="_subject" …>` line sets the email subject.

---

## Adding a brand-new page

1. Copy an existing page (e.g. `news.html`) to `yourpage.html`.
2. Update the `<title>`, `<meta name="description">`, and `<link rel="canonical">`
   in the `<head>`.
3. Replace the content inside `<main>` with your sections.
4. Add a link to it in the header menu and/or footer of **every** page, and add
   a line to `sitemap.xml`.

---

## Hosting on GitHub Pages

1. Create a repository on GitHub (any name).
2. Upload **all files in this folder**, keeping the structure intact
   (`index.html` must be at the repository root).
3. Go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to *Deploy from a branch*,
   choose your branch (usually `main`) and the `/ (root)` folder, then **Save**.
5. Wait a minute; GitHub gives you a live URL.

### Custom domain (qbicon.org)
The `CNAME` file already contains `qbicon.org`. To finish:

1. At your registrar, add DNS records:
   - Four **A** records for the apex domain to GitHub's IPs:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - (Optional) a **CNAME** record for `www` to `your-username.github.io`.
2. In **Settings → Pages**, confirm `qbicon.org` is the custom domain and tick
   **Enforce HTTPS** when available.

`.nojekyll`, `robots.txt`, and `sitemap.xml` are included for clean indexing.

---

## Files

```
index.html  mission.html  research.html  consortium.html
qbisquared.html  support.html  news.html  join.html
styles.css            ← all design (colours/fonts at the top)
assets/               ← logo, favicons, social-share image
assets/img/           ← founder photos (and any speaker photos you add)
CNAME .nojekyll robots.txt sitemap.xml
```

There is intentionally no `content.js` or `app.js` — the previous version filled
the pages from JavaScript, which made them hard to edit. Everything now lives in
the HTML.

---

## Notes

- **QBi²** details were seeded from qbisquared.com (2026: Protein Spin Qubits,
  Oct 19–20, Chicago, sponsored by Biohub). The Register button and speaker
  line-up link out to qbisquared.com — update them as they firm up.
- **Founder photos** came from the co-founders' public university / lab pages.
- **Partner institutions, news, and sponsorship amounts** are starter
  placeholders — edit freely.
- The site is keyboard-accessible (skip link, visible focus states) and respects
  reduced-motion preferences.
