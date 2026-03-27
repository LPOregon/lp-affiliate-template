# LP Affiliate Site Template

A free, forkable website template for Libertarian Party county and state affiliates. Built with Jekyll, Sveltia CMS, and GitHub Pages.

**Live example:** [multnomahlibertarians.com](https://www.multnomahlibertarians.com) (the site this template is based on)

## What you get

- A professional single-page site with all the sections an LP affiliate needs
- A content editor at `/admin` (Sveltia CMS) — update text, officers, meetup details, resources, and news posts without touching code
- Free hosting on GitHub Pages — total cost: **$0** (domain registration only, if you want a custom domain)
- No external service dependencies — just GitHub

## Quick start

| Step | Time | Guide |
|------|------|-------|
| 1. Create a GitHub org and fork this repo | 10 min | [docs/02-github-org-setup.md](docs/02-github-org-setup.md) |
| 2. Generate a personal access token | 5 min | [docs/03-cms-auth-setup.md](docs/03-cms-auth-setup.md) |
| 3. Log into /admin and fill in your content | 15–30 min | [docs/04-editing-content.md](docs/04-editing-content.md) |

**Total setup time: 30–60 minutes.** Full walkthrough starts at [docs/01-getting-started.md](docs/01-getting-started.md).

## Stack

- **Jekyll 4.3** — static site generator
- **Sveltia CMS** — Git-based headless CMS (drop-in Decap CMS replacement, faster and actively maintained)
- **GitHub Pages** — free static hosting
- **GitHub PAT authentication** — personal access token, no OAuth app setup required

## Site sections

- Hero with background image
- Values strip
- Get Involved (mailing list + donate buttons)
- Party of Principle (three pillars)
- Monthly Meetups (event card + Eventbrite/Luma link)
- News & Announcements (blog posts, archive page)
- About (intro text, officers card, party links)
- Libertarian Resources (external links grid)
- Footer with social links and legal disclaimer

## CMS-editable content

Through the admin interface at `/admin`:
- News posts (create, edit, delete)
- Officers (names and roles)
- Meetup details (location, time, schedule, notes)
- Resources (name, URL, description)

Site identity, social links, and other settings are in `_config.yml` (edit on GitHub directly — you'll set these once during setup).

## Documentation

| Guide | What it covers |
|-------|---------------|
| [01 — Getting Started](docs/01-getting-started.md) | Overview, what you need, how it works |
| [02 — GitHub Org Setup](docs/02-github-org-setup.md) | Create account, create org, fork, enable Pages |
| [03 — CMS Auth Setup](docs/03-cms-auth-setup.md) | Generate a PAT, log into the CMS |
| [04 — Editing Content](docs/04-editing-content.md) | How to use the CMS, what to edit where |
| [05 — Adding Candidates](docs/05-adding-candidates.md) | Future feature — not yet implemented |
| [06 — Updating Template](docs/06-updating-template.md) | How to pull in upstream improvements |

## Succession and recovery

This template is designed to survive leadership transitions. Key principles:

- **Repo owned by an org, not a person.** Multiple people should have Owner access to the GitHub org. If the webmaster steps down, the next person can take over without losing anything.
- **No external service dependencies.** The site runs entirely on GitHub Pages. There's no Netlify account, no Cloudflare worker, no database, no paid service that could lapse.
- **Domain registrar controlled by the org.** Register your domain under the affiliate's name, not an individual's. Make sure at least two officers have registrar login credentials.
- **Personal access tokens are personal.** Each editor has their own. When someone leaves, remove their collaborator access on the repo — their token stops working immediately.

### If the original maintainer disappears

1. Any org Owner can still access the repo, push changes, and manage collaborators
2. Any org Owner can generate a new PAT and log into the CMS
3. The site continues to work with zero intervention — it's static files on GitHub Pages
4. If the domain expires, the site is still accessible at `https://your-org.github.io/your-repo-name/`

## Assets

| File | Source | Notes |
|------|--------|-------|
| `assets/images/logo.png` | [lp.org/resources](https://www.lp.org/resources/) | LP Torch Eagle logo — download from LP national |
| `assets/images/skyline.jpg` | [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Formerly_Piero_della_Francesca_-_Ideal_City_-_Galleria_Nazionale_delle_Marche_Urbino.jpg) | "Ideal City" (c. 1470), anonymous — public domain |

Replace these with your own logo and hero image. Keep the filenames the same, or update the references in `index.html` and `_includes/nav.html`.

## License

Content template is provided for LP affiliate use. Jekyll, Sveltia CMS, and all dependencies retain their own licenses.
