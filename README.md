# sara-romero.com

> **Note on git history:** this repo was scaffolded and committed once from
> Cowork (commit `fefc698`), but a leftover `.git/index.lock` from that session
> can't be deleted by Cowork's sandbox, which blocks any further commits from
> here. On your own machine, either `rm .git/index.lock` and continue normally,
> or just `rm -rf .git && git init` fresh — the one scaffold commit isn't
> precious. Push to a new GitHub repo after that.

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
- `newfile_test.txt` (empty file, leftover from scaffolding — harmless, delete whenever)

## Theme / brand

Rethemed from the Forty default (dark navy background, white text) to the
palette in `Clients/SaraRomero/04_Brand/sara_romero_brand_guide_v1.html`:
white background, near-black ink for text/dark sections, "Azul Sinfonía"
(`#1F4FE0`) as the sole accent, Playfair Display headings + Source Sans Pro
body. All of it lives in `_sass/libs/_vars.scss` (see the comments there for
why `fg-bold` can't just be lightened — it also fills button/icon/logo
backgrounds, not just text) plus a `font-family-heading` wire-up in
`_sass/base/_typography.scss` and the Google Fonts `<link>` in
`_includes/head.html`.

Verified by compiling `assets/css/main.scss` with `dart-sass` outside Jekyll
(this Cowork sandbox can't reach rubygems.org for a real `bundle exec jekyll
build`) — it compiles clean and the output CSS has the right colors/fonts
in the right places. Still worth a visual check once you can actually run
`jekyll serve` — I verified the CSS is correct, not how it looks.

## Photos

Real photos from `Clients/SaraRomero/03_Assets_Raw/photos/` are in, resized/
compressed with ImageMagick (originals are 15-20MB camera JPEGs — much too
heavy to ship as-is):

- `assets/images/banner.jpg` — **HARAGAN ENSAYO CNV_3582.jpg** (2400px wide,
  ~410KB), the homepage hero. Per Damián's instruction 2026-08-11.
- `assets/images/pic07.jpg` — **DSC_5751.jpg** (1400px wide, ~250KB), Sara at
  the Dragon Ball Live Symphony rehearsal with an Orquesta Sincrophonía score
  visible — used as Trayectoria's tile image on the homepage and its own
  page-banner thumbnail (`trayectoria.md`'s `image:` field).
- `assets/images/pic08.jpg` — **DSC_5602.jpg** (1400px wide, ~215KB), backstage
  — used as Contacto's homepage tile image (`contacto.md`'s `image:` field;
  the `page` layout doesn't surface it anywhere else).

**Hero treatment note:** the theme's original banner overlay was a flat white
veil at 0.85 opacity — right for the dark-navy demo, but it would nearly erase
a real photo now that the site's bg is white. Replaced with a dark gradient
scrim (`_sass/layout/_banner.scss`) so the photo actually reads, and reversed
the hero's h1/tagline/CTA to white *only inside `#banner`* — nothing else on
the site changed color. This is a deliberate, scoped exception to the
white-bg/dark-ink brand system for the one full-bleed photo section; flag it
if you'd rather have a lighter scrim or a different photo that doesn't need
one (HARAGAN ENSAYO is quite dark/moody, which is why the scrim needs to be
fairly present to keep the tagline readable).

Placement of the other two is a first pass, not a locked decision — Phase 1
(content lock) is where photo selection actually gets Sara's sign-off per the
work plan.

## License / attribution

The Forty theme is free under CCA 3.0 (html5up.net/license), which requires
keeping the "Design: HTML5 UP" credit link in the footer. A one-time $19
[Pixelarity](https://pixelarity.com) license removes that requirement if an
unbranded footer matters to the client — Damián's call, not done by default.
