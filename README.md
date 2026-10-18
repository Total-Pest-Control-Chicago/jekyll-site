# jekyll-site

Jekyll conversion of the New Total Pest Control website (Constructify Bootstrap template).

- `jekyll serve` to build and listen for changes locally

## Building & Deploying

Run these from the `tpc-jekyll-site` folder. Both write the built site to `_site/`, replacing the previous build.

**Prod**

	jekyll build

Copy the contents of `_site/` into the prod site repo.

**Staging**

	jekyll build --config _config.yml,_config_staging.yml

Copy the contents of `_site/` into the `new-total-pest-control-website` repo.

The staging command loads `_config.yml` first, then applies `_config_staging.yml` on top. That swaps in the staging `url`/`baseurl`, adds the `noindex` tag, and leaves out `sitemap.xml` and `robots.txt`.

Copying a build over an existing repo doesn't remove files that are no longer part of the build. For the first staging deploy with this setup, delete the old `robots.txt` and `sitemap.xml` from the staging repo.

## Sitemap & robots.txt

- Prod only: `sitemap.xml` and `robots.txt` pick up `url` from `_config.yml` at build time
- Staging builds leave out `sitemap.xml` and `robots.txt` and add `<meta name="robots" content="noindex, nofollow, noarchive">` to every page instead. A `robots.txt` in the staging subfolder would be ignored by search engines, since they only read it at the domain root

## Structure

- `_layouts/default.html` — page skeleton (head, header, main, footer, scripts)
- `_includes/` — shared partials: `head.html`, `header.html`, `footer.html`, `scripts.html`, `page-title.html` (breadcrumb banner)
- Root `*.html` files — one per page, front matter sets `title`, `body_class`, `permalink`, and `active_nav`; pages render at pretty URLs (e.g. `service-details.html` → `/service-details/`)
- `assets/`, `forms/` — copied through as-is

## ToDo

- Home page, header, and footer are branded for Total Pest Control per `design-inspo.png`; the hero uses the real `hero-image.png`, but the about/services/CTA photos are still stock Constructify construction imagery — replace with real pest control photos
- Subpages (`terms`, `privacy`, `service-details`, `project-details`, `starter-page`, `404`) still carry stock Constructify copy
- Confirm the production domain in `_config.yml` (currently `https://www.totalpestcontrol.us`, taken from the design's email address)
- `forms/contact.php` is unused — the contact and estimate forms now submit directly to Formspree
