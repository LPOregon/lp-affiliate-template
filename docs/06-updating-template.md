# 06 — Updating the Template

When the upstream template is updated (bug fixes, new features, design improvements), you can pull those changes into your fork manually. This guide explains how.

---

## How Updates Work

Your site is a fork of [github.com/LPOregon/lp-affiliate-template](https://github.com/LPOregon/lp-affiliate-template). LPOregon may publish updates to that template — new features, bug fixes, security improvements, or design changes.

Because your fork is your own copy, updates to the upstream template do **not** automatically apply to your site. You have to apply them yourself. This is intentional — it means upstream changes can never unexpectedly break your live site.

---

## Before You Update

1. **Check the changelog** — Before pulling any changes, read [CHANGELOG.md](https://github.com/LPOregon/lp-affiliate-template/blob/main/CHANGELOG.md) or the [Releases page](https://github.com/LPOregon/lp-affiliate-template/releases) to understand what changed and whether it affects files you've customized.

2. **Note which files you've changed** — The files most likely to have your customizations are:
   - `_data/site.yml` (your affiliate content — managed by CMS)
   - `_config.yml` (your url, baseurl, and all affiliate settings)
   - `admin/config.yml` (your repo path)
   - Any images in `assets/images/`

   Template updates are unlikely to touch these files, but check the changelog to be sure.

---

## The Manual Copy Approach

The simplest way to apply an update is to copy changed files from the upstream repo into your fork.

### Step 1 — Identify what changed

Go to the upstream template repo and look at recent commits:
```
https://github.com/LPOregon/lp-affiliate-template/commits/main
```

Click into commits since the last time you updated to see which files were changed.

### Step 2 — View the updated file

For each changed file:
1. Navigate to it in the upstream repo (e.g. `_layouts/default.html`)
2. Click the file to open it
3. Click the **Raw** button to see the plain text content

### Step 3 — Update your fork

1. In your forked repo, navigate to the same file
2. Click the pencil icon to edit
3. Replace the contents with the updated version from upstream
4. **Important:** Re-apply your customizations if any. For example, if `_config.yml` was updated upstream, make sure your `baseurl`, `url`, and other affiliate-specific values are still correct after pasting.
5. Commit the change with a message like: `Apply upstream template update: default.html (2026-06)`

### Step 4 — Verify the site still builds

After committing, check the deployment status in your repo's **Deployments** section (right sidebar) or at **Settings → Pages**. Wait for it to show a successful deployment, then visit your live site and confirm everything looks correct.

---

## Files Safe to Update Without Customization Concerns

These files contain no affiliate-specific content and can be copied wholesale from upstream:

- `_layouts/default.html`
- `_layouts/post.html`
- `_includes/nav.html`
- `_includes/footer.html`
- `assets/css/main.scss`
- `index.html`
- `news.html`
- `404.html`
- `Gemfile`
- `.gitignore`
- `.github/workflows/setup-check.yml`
- `.github/workflows/dependabot-auto-merge.yml`
- `.github/dependabot.yml`

---

## Files That Require Care

These files contain values specific to your fork — **do not overwrite blindly:**

| File | What to preserve |
|---|---|
| `_config.yml` | Your `url`, `baseurl`, and all affiliate settings |
| `admin/config.yml` | Your `repo:` path |
| `_data/site.yml` | All of your affiliate content (managed by CMS) |
| `assets/images/` | Your logo and hero image |

When updating these files from upstream, copy only the structural changes (new fields, renamed keys) and leave your values intact.

---

## GitHub's Built-In Sync (Advanced)

GitHub offers a **Sync fork** button on your fork's main page. This merges upstream changes into your fork automatically. It works well if you haven't edited any of the same files that changed upstream. If there are conflicts (you and upstream both changed the same file), GitHub will flag them and you'll need to resolve them manually.

For most affiliates, the manual copy approach above is safer and easier to understand.

---

## Jekyll Version Cap

This template uses native GitHub Pages deployment, which builds with the `github-pages` gem. That gem locks Jekyll to version 3.x (currently 3.10). Jekyll 4.x features are not available. This is an intentional trade-off — native deployment requires no GitHub Actions setup, but gives up version choice. If you need Jekyll 4+, you would need to reintroduce a custom Actions workflow.

---

## If an Update Breaks Your Site

The fastest path to recovery is to revert the file you just changed:

1. Go to your repo's commit history
2. Find the commit just before your update
3. Click into that commit, find the file, and click **Raw**
4. Edit the file in your repo and paste the previous version back in
5. Commit — your site will rebuild from the working version

If something still looks wrong after reverting, see [05 — Troubleshooting](05-troubleshooting.md).
