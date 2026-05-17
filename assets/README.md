# 2:20 Partners — 220partnersplc.com

Static website for **2:20 Partners Design & Construction PLC**, Addis Ababa, Ethiopia. Pure HTML/CSS/JS — no build step. Deploy to Cloudflare Pages from a GitHub repo.

---

## File structure

```
website/
├── index.html              ← Home page
├── services/
│   └── index.html          ← Services page
├── projects/
│   └── index.html          ← Projects portfolio (filterable)
├── woodworks/
│   └── index.html          ← 2:20 Woodworks page
├── contact/
│   └── index.html          ← Contact (form + map)
├── assets/
│   └── site.css            ← Shared stylesheet for sub-pages
├── images/
│   ├── hero-rendering.png  ← Hero image (already included)
│   ├── studio-desk.jpg     ← (drop yours here when ready)
│   └── projects/
│       ├── commercial-midrise.jpg  ← (drop yours here)
│       ├── villa.jpg               ← (drop yours here)
│       └── apartment.jpg           ← (drop yours here)
├── favicon.svg
├── robots.txt
├── sitemap.xml
├── _headers                ← Cloudflare cache + security headers
├── _redirects              ← www→apex, trailing-slash normalization
├── .gitignore
└── README.md               ← (this file)
```

The site works **right now** even without the project images — gradient placeholders show by default. Drop a real image into `/images/projects/` with the filename listed above and it appears automatically.

---

## Deploy in 5 minutes

### 1. Put the code on GitHub

**Easiest way (no command line):**

1. Go to [github.com/new](https://github.com/new), create a new public or private repo named `220partnersplc-website`. Skip the "Initialize with README" option.
2. Click **"uploading an existing file"**.
3. Drag every file and folder from this `website/` folder into the upload box.
4. Commit.

**Or with the command line:**

```bash
cd website
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/220partnersplc-website.git
git push -u origin main
```

### 2. Connect Cloudflare Pages

1. In Cloudflare dashboard → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
2. Authorize Cloudflare to read GitHub, select the `220partnersplc-website` repo.
3. Build settings:
   - **Framework preset:** None
   - **Build command:** *(leave blank)*
   - **Build output directory:** `/`
4. Click **Save and Deploy**. First deploy takes about 60 seconds.

### 3. Bind your domain

1. In the Pages project → **Custom domains** → **Set up a custom domain** → enter `220partnersplc.com`.
2. Cloudflare auto-creates the CNAME (since the domain is already on Cloudflare). Wait a minute for DNS to propagate.
3. Repeat for `www.220partnersplc.com` if you want — the `_redirects` file already forwards www→apex.

That's it. Site is live.

---

## Updating the site

1. Edit any file (e.g. `index.html`) directly on GitHub via the web UI, or locally with VS Code.
2. Commit / push to `main`.
3. Cloudflare auto-rebuilds within ~30 seconds.

---

## Where to swap copy and images

| What                  | Where                                                              |
|-----------------------|--------------------------------------------------------------------|
| Hero headline         | `index.html` — search for `Where <span class="it">vision</span>`   |
| Phone number          | `index.html` + `woodworks/index.html` — search for `937174816`    |
| Email                 | search for `220partnersplc@gmail.com`                              |
| Service blurbs        | `index.html` — `<div class="services-grid">`                       |
| Partner names/roles   | `index.html` — `<div class="partners-grid">`                       |
| Project tile titles   | `index.html` — `<div class="projects ...">`                        |
| Project images        | drop into `/images/projects/` (see filenames in that folder's README) |
| Studio/About image    | drop into `/images/studio-desk.jpg`                                |
| Logo                  | `favicon.svg` (and inline SVG in nav of `index.html`)              |
| Hero image            | replace `/images/hero-rendering.png`                               |
| Map embed             | `index.html` — search for `google.com/maps?q=`                     |

---

## SEO checklist (do this within 7 days of launch)

The on-site SEO (title, meta, JSON-LD `LocalBusiness` + `FAQPage` + `OfferCatalog` schema, sitemap, robots) is already done. The remaining wins are off-site:

### Week 1 — set up the basics

- [ ] **Google Search Console** ([search.google.com/search-console](https://search.google.com/search-console))
  - Add property: `https://220partnersplc.com`
  - Verify via Cloudflare DNS TXT record (Cloudflare → DNS → Add Record)
  - Submit `https://220partnersplc.com/sitemap.xml`
- [ ] **Google Business Profile** — you already have a 5★ listing. Now:
  - Add the website URL `https://220partnersplc.com`
  - Complete every field: hours, services, founding year (2012), categories ("Architect", "General Contractor", "Construction Company")
  - Upload at least 10 photos (the renderings)
- [ ] **Bing Webmaster Tools** ([bing.com/webmasters](https://www.bing.com/webmasters)) — small but free traffic in Ethiopia
- [ ] **Apple Maps Connect** ([mapsconnect.apple.com](https://mapsconnect.apple.com)) — free, helps iPhone users

### Weeks 2–4 — local citations (Ethiopian directories)

- [ ] [2merkato.com](https://2merkato.com) — list business
- [ ] [ethiopianbusinessdirectory.com](https://www.ethiopianbusinessdirectory.com)
- [ ] [ezega.com](https://www.ezega.com) business directory
- [ ] OpenStreetMap — add the business as a node
- [ ] Ethiopian Architects Association (if applicable)

### Ongoing — reviews and content

- [ ] Push every recent client to leave a Google review (target 20+ within 90 days)
- [ ] Add 1 blog post per month targeting a long-tail keyword. Example titles:
  - *"How much does it cost to build a luxury home in Addis Ababa in 2026?"*
  - *"Stone vs glass facades for Addis Ababa: a designer's guide"*
  - *"What to look for in an architect in Addis Ababa"*
- [ ] Get 5–10 backlinks: feature on local design blogs, guest post, get listed in roundups

---

## What's already optimized

- **Lighthouse-friendly:** preconnects, image preload + `fetchpriority`, lazy loading, font `display: swap`, minified single-file CSS.
- **Mobile-first:** floating tap-to-call FAB, 44px+ tap targets, 16px form inputs (no iOS zoom), iPhone safe-area padding.
- **Schema.org JSON-LD:** `LocalBusiness` + `GeneralContractor` + `ArchitecturalService` + `Organization` + `FAQPage` + `OfferCatalog` (rich results in Google).
- **Open Graph + Twitter Card:** good link previews when shared.
- **`hreflang="en"`** with placeholder for Amharic version.
- **Semantic HTML:** one `<h1>`, logical heading hierarchy, descriptive alt text with location keywords.

---

## Contact (for later edits)

Hosted by Cloudflare Pages. Code on GitHub. Domain managed on Cloudflare DNS.

Phone: +251 93 717 4816
Email: 220partnersplc@gmail.com
Office: Megenagna, Addis Ababa, Ethiopia
