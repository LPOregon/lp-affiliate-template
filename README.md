# LP Affiliate Site Template

A free, forkable website template for Libertarian Party county and state affiliates. Built with Jekyll, Sveltia CMS, and GitHub Pages. See it live at [lporegon.github.io/lp-affiliate-template](https://lporegon.github.io/lp-affiliate-template)

## What you get

- A professional single-page site with all the sections an LP affiliate needs
- A content editor at `/admin` (Sveltia CMS) — update text, officers, meeting details, resources, and news posts without touching code
- Free hosting on GitHub Pages — total cost: **$0** (domain registration only, if you want a custom domain)
- No *required* external service dependencies — just GitHub. Donation platform, mailing list, and event RSVP integrations (Anedot, Brevo/Mailchimp, Luma/Eventbrite) are all optional — the site renders cleanly with any or none of them configured

## Before you start

Setting this up takes an hour or two and involves creating a GitHub org, forking a repo, generating a personal access token, and editing a config file. None of the steps are difficult, but they assume you're comfortable following written instructions and copying values between browser tabs. If that describes you, you'll be fine. If it doesn't, consider pairing with someone technically inclined for the initial setup — after that, day-to-day editing happens entirely in the CMS with no code involved.

This template is maintained on a volunteer basis. Issues and pull requests are welcome, but response times aren't guaranteed. If you run into trouble, start with the [troubleshooting guide](docs/05-troubleshooting.md); if that doesn't help, open an issue on the template repo.

## Quick start

| Step | Time | Guide |
|------|------|-------|
| 1. Create a GitHub org and fork this repo | 10 min | [docs/02-github-org-setup.md](docs/02-github-org-setup.md) |
| 2. Generate a personal access token | 5 min | [docs/03-cms-auth-setup.md](docs/03-cms-auth-setup.md) |
| 3. Log into /admin and fill in your content | 15–30 min | [docs/04-editing-content.md](docs/04-editing-content.md) |

**Total setup time: 30–60 minutes.** Full walkthrough starts at [docs/01-getting-started.md](docs/01-getting-started.md).

## Monthly maintenance

Depends on which RSVP tool you use:

**Luma** — update the meeting card each month after creating a new event:

1. In Luma, open the new event → **Manage → More → Embed Registration Button**
2. Copy the `evt-XXXXXXXXX` ID from the code snippet
3. Open the CMS → **Site Settings → Meetup → Luma event ID** — paste the new ID
4. Update **Next event date** with the display date, e.g. `May 1, 2025`
5. Click **Save** — the site updates within about 60 seconds

**Eventbrite (organizer page)** — no monthly task. Set your Eventbrite organizer page URL (`eventbrite.com/o/your-org`) as the RSVP URL in the CMS → Site Settings → Meetup. That page always lists your current events automatically.

**Eventbrite (per-event URLs)** — update the RSVP URL in the CMS → Site Settings → Meetup each month to point to the new event.

## Stack

- **Jekyll 4.3** — static site generator
- **Sveltia CMS** — Git-based headless CMS (drop-in Decap CMS replacement, faster and actively maintained)
- **GitHub Pages** — free static hosting
- **GitHub PAT authentication** — personal access token, no OAuth app setup required

## Site sections

- Hero with background image, mailing list signup, and donate button
- Party of Principle (three pillars)
- Monthly Meetings (meeting card + RSVP link)
- News & Announcements (blog posts, archive page)
- About (intro text, officers card, party links)
- Libertarian Resources (external links grid)
- Footer with social links and legal disclaimer

## CMS-editable content

Through the admin interface at `/admin`:
- News posts (create, edit, delete)
- Officers (names and roles)
- Meeting details (location, time, schedule, notes, Luma RSVP fields)
- Resources (name, URL, description)
- Hero subheadline and affiliation label

Site identity, social links, and other settings are in `_config.yml` (edit on GitHub directly — you'll set these once during setup). Meeting and RSVP details are in the CMS under Site Settings.

## Documentation

| Guide | What it covers |
|-------|---------------|
| [01 — Getting Started](docs/01-getting-started.md) | Overview, what you need, how it works |
| [02 — GitHub Org Setup](docs/02-github-org-setup.md) | Create account, create org, fork, enable Pages |
| [03 — CMS Auth Setup](docs/03-cms-auth-setup.md) | Generate a PAT, log into the CMS |
| [04 — Editing Content](docs/04-editing-content.md) | How to use the CMS, what to edit where |
| [05 — Troubleshooting](docs/05-troubleshooting.md) | Common problems and how to fix them |
| [06 — Updating Template](docs/06-updating-template.md) | How to pull in upstream improvements |

## Recommended external services

The template integrates with several external services via simple URLs or embed codes. If you're not already committed to a particular tool:

- **Mailing list:** [Brevo](https://brevo.com) (formerly Sendinblue) is free up to 300 emails/day, has a clean embed form that works directly with this template's built-in Brevo iframe section, and doesn't require your subscribers to confirm via a third-party landing page. Mailchimp works too but costs more and has a less straightforward embed path.
- **Event RSVPs:** [Luma](https://lu.ma) is free, produces a clean RSVP popup that opens without leaving your site (built into this template), and automatically emails attendees an ICS calendar invite. Eventbrite works but is oriented toward ticketed events and adds friction for free meetups.

If you're already using Mailchimp or Eventbrite and have an existing list or attendee history there, stick with what you have — both work fine with this template.

## Succession and recovery

This template is designed to survive leadership transitions. Key principles:

- **Repo owned by an org, not a person.** Multiple people should have Owner access to the GitHub org. If the webmaster steps down, the next person can take over without losing anything.
- **No required external service dependencies.** The site runs entirely on GitHub Pages. There's no Netlify account, no Cloudflare worker, no database, no paid service that could lapse. Optional integrations (Brevo for email signups, Anedot for donations, Eventbrite or Luma for RSVPs) are just links or embeds — the site continues to function if any of them are unavailable.
- **Domain registrar controlled by the org.** Make sure at least two officers have registrar login credentials.
- **Personal access tokens are personal.** Each editor has their own. When someone leaves, remove their collaborator access on the repo — their token stops working immediately.

### If the original maintainer disappears

1. Any org Owner can still access the repo, push changes, and manage collaborators
2. Any org Owner can generate a new PAT and log into the CMS
3. The site continues to work with zero intervention — it's static files on GitHub Pages
4. If the domain expires, the site is still accessible at `https://your-org.github.io/your-repo-name/`

## Assets

| File | Notes |
|------|-------|
| `assets/images/logo.png` | Replace with your own county LP logo |
| `assets/images/skyline.jpg` | Replace with a public domain photo of your city |

## License

Content template is CC0. Jekyll, Sveltia CMS, and all dependencies retain their own licenses.
