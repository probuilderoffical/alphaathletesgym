# WordPress Theme Mapping

This document describes a future conversion path from the static Alpha Athletes Gym site to a lightweight custom WordPress theme.

## Template mapping

- `header.php`: document head, schema/meta integration, sticky header, logo and WordPress navigation.
- `front-page.php`: ordered composition of all homepage template parts.
- `template-parts/hero.php`: hero copy, CTAs and approved hero media.
- `template-parts/about.php`: About section.
- `template-parts/programs.php`: loop over managed program entries.
- `template-parts/facilities.php`: render verified facilities only.
- `template-parts/why.php`: benefit cards.
- `template-parts/membership.php`: membership CTA without hardcoded pricing.
- `template-parts/gallery.php`: WordPress media/gallery fields with alt text.
- `template-parts/faq.php`: FAQ repeater and accessible disclosure UI.
- `template-parts/contact.php`: WhatsApp contact data and message form.
- `footer.php`: footer navigation/contact/social links and dynamic year.
- `functions.php`: enqueue local assets, register menus, theme supports, image sizes and any managed content structures.
- `assets/css/`, `assets/js/`, `assets/images/`: preserve the current asset organization.

## Content model

The values currently in `data/config.js` should become editable WordPress fields. Program and facility items can be repeater fields or dedicated post types if the site expands. Global WhatsApp/contact/social data should live in one options location.

Never seed unverified prices, address, hours, trainers, testimonials, achievements or facilities during migration.

## Implementation notes

Use WordPress escaping functions for dynamic output, enqueue assets instead of inline styles/scripts, retain semantic landmarks and keyboard behavior, and generate canonical/OG/schema data from verified site settings. Avoid proprietary page-builder dependencies.
