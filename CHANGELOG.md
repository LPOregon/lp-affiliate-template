# Changelog

All notable changes to the LP Affiliate Site Template are documented here.

Affiliates: when a new release is published, check this file to understand what changed and whether it affects files you've customized. See [06 — Updating the Template](docs/06-updating-template.md) for instructions on applying updates to your fork.

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
