# Changelog

All notable changes to the LP Affiliate Site Template are documented here.

Affiliates: when a new release is published, check this file to understand what changed and whether it affects files you've customized. See [06 — Updating the Template](docs/06-updating-template.md) for instructions on applying updates to your fork.

---
## v1.1 — Soft modern redesign

**Visual refresh** — no structural or content changes; affiliates updating from v1.0 only need to replace `assets/css/main.css` and `_layouts/default.html`.

- Palette role-shift: LP yellow drops from dominant brand color to a true accent (buttons, key marks, hover hints). Warm off-white (`#FAF8F3`) replaces cream as the body background. Ink dominates dark sections.
- Typography: Instrument Serif replaces Roboto Slab for all display moments (headlines, card titles, footer brand, hero h1, post titles). Roboto remains for body and UI. Font import in `_layouts/default.html` updated accordingly.
- Floating glass nav: sticky pill nav with backdrop blur, ink-colored donate button.
- Hero is now a rounded card with soft shadow and inset margin instead of full-bleed. Layered radial + linear gradient overlay replaces the flat scrim.
- Principle cards are numbered with serif italic numerals (01, 02, 03) and a small yellow accent dash.
- Meetups section gets a faint radial yellow wash; the meeting card becomes a glass panel with backdrop blur. Next-meeting date is a yellow pill chip.
- News and resources use rounded card grids with soft shadows. Resource cards get a hover arrow.
- About intro becomes a large italic pull-quote.
- Footer brand title is set in serif; the top edge marker is a small centered yellow tab instead of a full border.
- Soft layered shadows and generous border-radius (16/24/32px) throughout.

**Files changed**
- `assets/css/main.css`
- `_layouts/default.html` (font import only)

---

## v1.0 — Initial release

**Stack**
- Jekyll 4.3, Sveltia CMS, GitHub Pages, GitHub PAT authentication
- Custom GitHub Actions workflow (bypasses the `github-pages` gem Jekyll version lock)

**Site sections**
- Hero with logo, geography eyebrow, headline, affiliate subheadline, Get Involved and Donate buttons
- Party of Principle (three pillars)
- Monthly Meetings (meeting card with location, time, schedule, notes, optional RSVP link)
- News & Announcements (two-column card grid, archive page)
- About (intro paragraph, officers card, party links card)
- Libertarian Resources (external links grid)
- Footer with social links, affiliation label, legal disclaimer, image attribution

**Configuration**
- All affiliate identity fields in `_config.yml`
- CMS-editable content (hero subheadline, officers, meeting details, resources, news posts) in `_data/site.yml`
- Optional Brevo signup form embed (`brevo_embed_url`) or external form link (`mailing_list_url`)
- Optional GoatCounter analytics (`goatcounter_code`)
- Optional RSVP link (`rsvp_url`)

**Documentation**
- Six guides in `docs/` covering setup, GitHub org creation, CMS authentication, content editing, troubleshooting, and updating the template
