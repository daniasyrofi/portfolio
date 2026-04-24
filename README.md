# daniasyrofi.com

Personal portfolio site for Muhammad Dani Asyrofi, Senior Product Designer based in Jakarta, Indonesia.

Built as a static site. No build step, no dependencies, no framework. HTML, CSS, and a little vanilla JavaScript. Typography via Google Fonts (Instrument Serif and Geist).

## Structure

```
portfolio/
├── index.html          Main page, all sections, inline CSS & JS
├── 404.html            Custom 404 page (matches site style)
├── netlify.toml        Netlify config: headers, redirects, cache
├── robots.txt          Crawling rules
├── sitemap.xml         Sitemap for search engines
├── site.webmanifest    Web app manifest (PWA basics)
├── humans.txt          Credits
├── .gitignore
├── README.md
└── assets/
    ├── favicon.svg           Primary icon (SVG)
    ├── favicon-16x16.png     Legacy browser fallback
    ├── favicon-32x32.png     Legacy browser fallback
    ├── apple-touch-icon.png  iOS home screen (180x180)
    └── og-image.png          Social share card (1200x630)
```

## Local preview

Open `index.html` in any browser, or run a simple server:

```bash
# Python 3
python3 -m http.server 8000

# Node
npx serve .
```

Then visit `http://localhost:8000`.

## Deploy to GitHub

From inside this folder:

```bash
git init
git branch -M main
git add .
git commit -m "Initial portfolio site"

# Create an empty repo on github.com/new first, then:
git remote add origin https://github.com/daniasyrofi/portfolio.git
git push -u origin main
```

Later updates:

```bash
git add .
git commit -m "Update work section"
git push
```

## Deploy to Netlify

### Connect the GitHub repo (recommended)

1. Sign in at [app.netlify.com](https://app.netlify.com) with GitHub.
2. `Add new site` → `Import an existing project` → `Deploy with GitHub`.
3. Pick `daniasyrofi/portfolio`.
4. Build settings:
   - Build command: leave empty
   - Publish directory: `.` (root)
5. Click `Deploy site`.

Netlify assigns a default URL like `random-123.netlify.app`. Rename it under `Site settings → Change site name` to something like `daniasyrofi.netlify.app`.

Every `git push` to `main` triggers an auto deploy.

### Custom domain (later, when purchased)

After buying `daniasyrofi.com`:

1. Netlify: `Domain settings → Add custom domain` → enter `daniasyrofi.com`.
2. At your domain registrar, set DNS:
   - `A` record, host `@`, value `75.2.60.5`
   - `CNAME`, host `www`, value `<your-site-name>.netlify.app`
3. Back in Netlify, click `Verify DNS configuration`. Propagation takes 5–30 minutes.
4. Enable HTTPS (free Let's Encrypt, automatic).

If using Cloudflare DNS, set records as `DNS only` (gray cloud) during setup.

## Editing content

Everything lives in `index.html`. Find each section by its comment header:

| Section        | Purpose                           |
| -------------- | --------------------------------- |
| `HERO`         | Top intro                         |
| `NUMBERS`      | Verifiable stats                  |
| `WORK`         | Client and employment case studies|
| `EXPLORATIONS` | Dribbble shots                    |
| `EXPERIENCE`   | Timeline                          |
| `WRITING`      | Medium articles                   |
| `ABOUT`        | Bio                               |
| `CONTACT`      | Email, socials                    |

Image paths currently use Dribbble's CDN directly. For production stability, download and host under `/assets/`.

## SEO & social

- `og-image.png` (1200x630) is the card shown on Twitter, LinkedIn, WhatsApp, iMessage, Slack, etc.
- JSON-LD `Person` and `WebSite` schemas are in the `<head>` of `index.html`.
- `sitemap.xml` points to the homepage only — extend if sub-pages are added.
- `robots.txt` references the sitemap.

Regenerate image assets with:

```bash
python3 /tmp/gen_assets.py   # See the original script if you need to change branding
```

## Tech notes

- Typography: Instrument Serif (display), Geist (body), Geist Mono (utility)
- Dark mode: follows system preference, persists user override in `localStorage`
- Animation: CSS only, respects `prefers-reduced-motion`
- Responsive: mobile first, breakpoints at 540px and 960px
- No tracking, no analytics. Add [Plausible](https://plausible.io) or [Fathom](https://usefathom.com) if desired.
- Security: CSP, HSTS, X-Frame-Options, Permissions-Policy — see `netlify.toml`.

## Credits

Design inspired by the best of 2026 designer portfolios:
Jakub Krehel, Emil Kowalski, Rauno Freiberg, Brittany Chiang, Olivia Ng.

Site hand built with care. Shaping future design, pixel by pixel.

## License

Personal portfolio, all content and design copyright Muhammad Dani Asyrofi 2026. Feel free to study the structure and CSS approach for learning, but do not clone wholesale.
