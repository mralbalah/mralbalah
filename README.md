# CodeLine Studio: Website

Official website of **CodeLine Studio**, a web & brand studio that designs and builds the complete online presence for startups and small businesses: logo, website and launch content.

**Live site:** https://codeline-studio.akgunbalah.workers.dev

![CodeLine Studio website](docs/screenshot-desktop.png)

## Features

- **Fast static site.** Hand-written HTML, CSS and vanilla JavaScript with no framework, self-hosted fonts and long-term caching.
- **Content managed from a Google Sheet.** Headlines, photos, packages and news load at runtime from a Google Apps Script API. If the sheet can't be reached, the site falls back to its built-in text, so it never shows up empty.
- **Contact form & lead capture.** Form submissions are saved to Google Sheets with an email notification, and a honeypot field filters out spam.
- **Client reviews page** (`review.html`), where clients submit testimonials.
- **Newsletter.** Visitors sign up on the site, posts go out by email every 10 minutes, and every email has an unsubscribe link.
- **Packages & pricing** with a downloadable PDF price list.
- **SEO & sharing:** meta tags, Open Graph image, `sitemap.xml`, `robots.txt` and favicons.
- **Security headers** through Cloudflare `_headers` (nosniff, frame options, referrer and permissions policy).
- **Responsive** layout built mobile first, plus a WhatsApp contact button.

<p align="center"><img src="docs/screenshot-mobile.png" width="260" alt="Mobile view"></p>

## Tech stack

| Layer | Tools |
|---|---|
| Front end | HTML5, CSS3, JavaScript (ES5, no dependencies) |
| Back end / CMS | Google Apps Script, Google Sheets, Google Drive |
| Hosting | Cloudflare Workers / Pages |
| Design | Adobe Creative Suite, custom brand system (Sora + DM Sans) |

## Project structure

```
├── index.html            # Main one-page site
├── review.html           # Client review form
├── 404.html              # Custom not-found page
├── _headers              # Cloudflare security & cache headers
├── robots.txt / sitemap.xml
├── assets/
│   ├── styles.css
│   ├── main.js           # Forms, CMS loading, newsletter, UI
│   ├── fonts/            # Self-hosted WOFF fonts
│   └── img/
└── apps-script/
    └── Code.gs           # Google Apps Script back end (forms, CMS API, newsletter)
```

## Run locally

No build step is needed. Serve the folder with any static server:

```bash
npx serve .
# or
python -m http.server 8080
```

## Deploy

1. **Back end.** Create a Google Sheet, open **Extensions → Apps Script** and paste in `apps-script/Code.gs`. Set `NOTIFY_EMAIL`, run `setup()` once, then **Deploy → Web app** (access: *Anyone*).
2. **Front end.** In `assets/main.js`, replace `YOUR_APPS_SCRIPT_WEB_APP_URL` with your web-app URL.
3. **Hosting.** Upload the folder to Cloudflare Pages or Workers static assets. The `_headers` file is applied automatically.

## Author

**Rashed Al-Balah**: Founder & Lead Developer, CodeLine Studio
[GitHub](https://github.com/mralbalah) · mralbalah@gmail.com

---

© 2026 CodeLine Studio. The code is shared as a portfolio piece. The brand name, logo, text and images are not licensed for reuse.
