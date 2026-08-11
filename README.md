# sara-romero.com

Jump Higher Design build for Sara Romero — proposal JHD-20260810-2232. Static
Jekyll site, Tier 1 CMS (Sveltia), Netlify-hosted. See the client's project
folder for the full work plan: `Clients/SaraRomero/sara_romero_website_work_plan.md`.

Scaffolded from the [Forty Jekyll theme](https://github.com/andrewbanchich/forty-jekyll-theme)
(Jekyll port of HTML5 UP's "Forty," CCA 3.0 license).

## Pages

- `index.md` — Inicio
- `trayectoria.md` — Trayectoria (AMA UNAM, Ediciones Vivace; Orquesta Sincrophonía
  gets a mention + link only, not its own block — per client instruction 2026-08-10)
- `contacto.md` — Contacto (email + social links; no contact form — out of scope)

## Local dev

```
bundle install
bundle exec jekyll serve
```

## Deploy

Netlify, building from `netlify.toml` (`bundle exec jekyll build` → `_site`).
Custom domain `sara-romero.com` is already purchased (client, SquareSpace,
3 years) — point its DNS at this Netlify site once it exists (Phase 3 of the
work plan).

## CMS (Sveltia, Tier 1)

`/admin` — see `admin/config.yml`. Backend is `git-gateway`, which requires
**Netlify Identity + Git Gateway enabled on the Netlify site** (Site configuration
→ Identity → Enable, then Services → Git Gateway → Enable). That's a Netlify
dashboard step, not something set from the repo — do it once the site is
connected to Netlify, then invite Sara as an Identity user so she can log into
`/admin`.

## Cleanup

This repo was scaffolded from the full Forty theme, which ships sample blog/
portfolio content this site doesn't use. These are disconnected from navigation
(`nav-menu: false` / `show_tile: false`) and safe to delete locally whenever
convenient — none of it is required for the 3 real pages above:

- `generic.md`, `landing.md`, `all_posts.md`, `404.md` (keep 404.md — it's the
  real 404 page, just harmless to leave named as-is)
- `_posts/` (6 sample blog posts)
- `.github/workflows/*.yml` (GitHub Pages auto-deploy — disabled, this site
  deploys via Netlify instead)
- `.github/FUNDING.yml`, `.gitlab-ci.yml` (leftover from the upstream template)
- `elements.md`, `forty_jekyll_theme.gemspec`

## License / attribution

The Forty theme is free under CCA 3.0 (html5up.net/license), which requires
keeping the "Design: HTML5 UP" credit link in the footer. A one-time $19
[Pixelarity](https://pixelarity.com) license removes that requirement if an
unbranded footer matters to the client — Damián's call, not done by default.
