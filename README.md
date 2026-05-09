# ruke.ba

Static site for **Ruke malih biznisa** — Artisan Studio za male biznise u BiH.

Domain: [ruke.ba](https://ruke.ba) · Hosting: Netlify · DNS: Cloudflare · Mail: Zoho

---

## Repo structure

```
.
├── public/                      ← Netlify deploys this folder
│   ├── index.html               ← Landing
│   ├── ruke-onboarding.html     ← Public onboarding form (Netlify Forms)
│   ├── privatnost.html          ← Privacy policy (BiH ZZLP)
│   ├── 404.html                 ← Friendly 404
│   ├── robots.txt
│   ├── sitemap.xml
│   └── *.png                    ← Brand assets (see below)
│
├── studio/                      ← NOT deployed — local working tools only
│   ├── RukeMalihBiznisa.html    ← Internal brief (2–3× iteration with klijent)
│   └── ruke-ponuda.html         ← Final offer (print → PDF)
│
├── netlify.toml                 ← Build config + redirects + headers
├── .gitignore
└── README.md
```

## Required brand assets

Drop these into `/public/` before first deploy. Site won't break without them
(everything has `onerror=hide`) but it will look gutted.

| File | Purpose | Specs |
|---|---|---|
| `logo.png` | Favicon + footer mark | square, ~512×512, transparent |
| `sticker-vizit.png` | Vizit package badge | square, ~400×400, transparent |
| `sticker-standard.png` | Standard package badge | square, ~400×400, transparent |
| `sticker-pro.png` | Pro package badge | square, ~400×400, transparent |
| `signature.png` | Hand-signed seal in contact section | wide, ~600×200, transparent |
| `og-card.png` | Social share preview | **1200×630**, PNG or JPG |

## Deploy

Netlify auto-deploys from `main` on push. To deploy manually:

1. Edit files in `/public/` (or `studio/` for working tools — these stay local)
2. Commit and push to GitHub
3. Netlify picks up within ~30s

## Form submissions

`ruke-onboarding.html` posts to Netlify Forms (free tier: 100/mo).
Notifications routed to `ponude@ruke.ba` via Netlify dashboard:
**Site config → Forms → Form notifications**.

## Studio tools (local only)

`/studio/` files are working documents — **not deployed**. Open them locally:

```
open studio/RukeMalihBiznisa.html
open studio/ruke-ponuda.html
```

Both use localStorage + JSON import/export. Workflow:

1. Klijent submits onboarding → JSON arrives in `ponude@ruke.ba`
2. You import JSON into `RukeMalihBiznisa.html` → iterate brief 2–3× with klijent
3. Final state imported into `ruke-ponuda.html` → print to PDF → sign → deal

## Privacy compliance

Site complies with **Zakon o zaštiti ličnih podataka BiH** (GDPR-equivalent):

- Privacy notice at `/privatnost.html`
- Required consent checkbox on onboarding form
- No third-party trackers, no cookie banners needed
- localStorage used only for form draft (service-essential, exempt)

If using Cloudflare Web Analytics, no banner needed (cookieless).

## Maintainer

Ruke malih biznisa · Sarajevo · [zdravo@ruke.ba](mailto:zdravo@ruke.ba)
