# jekyll-site

Jekyll conversion of the New Total Pest Control website (Constructify Bootstrap template).

- `jekyll build` to build it for hosting (output goes to `_site/`)
- `jekyll serve` to build and listen for changes locally
- Change the `_config.yml` based on prod or staging — `robots.txt` and `sitemap.xml` pick up `url` automatically:

	# STAGING (example)
	title: "Total Pest Control"
	url: "https://<org>.github.io/total-pest-control-staging"
	baseurl: "/total-pest-control-staging"

	# PROD
	title: "Total Pest Control"
	url: "https://www.totalpestcontrol.us"
	baseurl: "/"

## Structure

- `_layouts/default.html` — page skeleton (head, header, main, footer, scripts)
- `_includes/` — shared partials: `head.html`, `header.html`, `footer.html`, `scripts.html`, `page-title.html` (breadcrumb banner)
- Root `*.html` files — one per page, front matter sets `title`, `body_class`, `permalink`, and `active_nav`; pages render at pretty URLs (e.g. `service-details.html` → `/service-details/`)
- `assets/`, `forms/` — copied through as-is

## ToDo

- Home page, header, and footer are branded for Total Pest Control per `design-inspo.png`; the hero uses the real `hero-image.png`, but the about/services/CTA photos are still stock Constructify construction imagery — replace with real pest control photos
- Subpages (`terms`, `privacy`, `service-details`, `project-details`, `starter-page`, `404`) still carry stock Constructify copy
- Confirm the production domain in `_config.yml` (currently `https://www.totalpestcontrol.us`, taken from the design's email address)
- `forms/contact.php` requires the pro "PHP Email Form" library and a real receiving email address (design says info@totalpestcontrol.us)
