# Alpha Athletes Gym — Official Website

A fast, mobile-first static website for **Alpha Athletes Gym, Pakistan**, focused on WhatsApp membership inquiries and gym visits.

## Stack

- Semantic HTML5
- Modular CSS with design tokens
- Vanilla JavaScript
- Central editable content in `data/config.js`
- No runtime dependencies or page builder
- GitHub Pages compatible

## Local setup

No build step is required. Clone this repository and serve its root with any static server. For example, with Python:

```bash
python -m http.server 8080
```

Then open `http://localhost:8080`.

## Content editing

Most repeatable content lives in `data/config.js`. Update programs, verified facilities, gallery entries, FAQs and WhatsApp defaults there. The WhatsApp number is `923084929506`.

**Verification rule:** do not add trainer names, testimonials, prices, address, opening hours, facilities, achievements, or social URLs unless the business has verified them.

### Images

The current gallery and hero deliberately use labeled placeholders because no approved business photography was supplied in the repository. To add gallery photos:

1. Add optimized WebP/AVIF images under `assets/images/`.
2. Set each gallery item's `src` in `data/config.js` to a relative path such as `./assets/images/gym-floor.webp`.
3. Replace the placeholder label with accurate alt text.
4. Replace `assets/images/og-placeholder.svg` and update `og:image` in `index.html` when an approved social preview image is available.

Keep images appropriately sized and compressed. Gallery images are lazy-loaded.

### Address, map and facilities

Address and facilities are intentionally unverified. Once verified, update the Contact section and populate the `facilities` array. Add a Google Maps embed only after confirming the exact public location.

## GitHub Pages deployment

The workflow at `.github/workflows/pages.yml` deploys the repository root on pushes to `main`. In repository **Settings → Pages**, set the source to **GitHub Actions** if it is not already enabled.

Expected project URL:

`https://probuilderoffical.github.io/alphaathletesgym/`

The canonical, Open Graph URL, sitemap and robots file currently use that project URL. If a custom domain is connected later, update all four together.

## Accessibility and performance

The site includes keyboard-accessible navigation, visible focus states, a skip link, semantic sections, accessible FAQ controls, reduced-motion support, labeled form fields, responsive layouts and high-contrast text. It avoids webfont requests and large third-party scripts to protect Core Web Vitals.

Before release with real images, run Lighthouse and verify image dimensions/compression, contrast, keyboard navigation and mobile overflow.

## Future WordPress Conversion

The static architecture maps cleanly to a custom WordPress theme:

| Current area | WordPress target |
| --- | --- |
| Site header + navigation | `header.php` |
| Footer | `footer.php` |
| Single-page composition | `front-page.php` |
| Hero, Programs, Facilities, Why, Membership, Gallery, FAQ, Contact | `template-parts/` |
| CSS / JavaScript / images | `assets/` |
| Asset enqueueing, menus, theme supports | `functions.php` |
| `data/config.js` content | Customizer, ACF, core fields or theme options |

During conversion, preserve CSS variables and reusable section/card classes. Move content into WordPress-managed fields rather than duplicating markup. No proprietary page builder is required.

See `WORDPRESS-MAPPING.md` for the detailed mapping.

## Pre-publish checklist

- Confirm program availability.
- Add only verified facilities.
- Add approved gym photography.
- Confirm public address and only then add a map.
- Add verified Instagram/Facebook links.
- Confirm opening hours.
- Test every WhatsApp CTA on mobile and desktop.
- Run Lighthouse / accessibility checks after final content and images are added.
