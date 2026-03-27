# Getting Started

## What you have

A free, professional website template for your LP affiliate. It includes:

- A single-page site with all the sections a county or state affiliate needs
- A content editor at `/admin` (Sveltia CMS) so you can update text, officers, meetup details, resources, and news posts without touching code
- Free hosting on GitHub Pages ($0/month — you only pay for a domain if you want one)
- No external service dependencies

## What you need

1. **A GitHub account** — free at [github.com](https://github.com/signup)
2. **30–60 minutes** to set everything up
3. Optionally: a custom domain name (e.g. `podunklibertarians.org`)

## Setup overview

| Step | Time | Guide |
|------|------|-------|
| 1. Create a GitHub org and fork the template | 10 min | [GitHub Org Setup](02-github-org-setup.md) |
| 2. Generate a personal access token for the CMS | 5 min | [CMS Authentication](03-cms-auth-setup.md) |
| 3. Log into /admin and fill in your content | 15–30 min | [Editing Content](04-editing-content.md) |

That's it. No server to maintain, no monthly bill, no web developer needed after initial setup.

## How it works

Your site is a collection of text files stored in a GitHub repository. When you edit content through the CMS at `/admin`, Sveltia CMS saves those changes as file updates in your repo. GitHub Pages automatically rebuilds and publishes the site within about 60 seconds.

The CMS authenticates using a GitHub personal access token (PAT). You generate the token once, paste it in when you log in, and your browser remembers it.

## Next step

→ [GitHub Org Setup](02-github-org-setup.md)
