# GitHub Org Setup

This guide walks you through creating a GitHub organization for your affiliate, forking the template, and enabling GitHub Pages. No prior GitHub experience required.

## Step 1: Create a GitHub account

If you don't already have one, sign up at [github.com/signup](https://github.com/signup). It's free.

Use a personal email you'll have access to long-term — not a work email that might go away.

## Step 2: Create a GitHub organization

An organization lets multiple people manage the repo. This is important for succession — if you step down, the next chair can take over without losing the site.

1. Go to [github.com/organizations/plan](https://github.com/account/organizations/new?plan=free)
2. Choose the **Free** plan
3. Organization name: something like `PodunkLibertarians` or `LP-Podunk` (this appears in your site URL if you don't use a custom domain)
4. Contact email: your affiliate's official email
5. Select "My personal account" when asked who the org belongs to
6. Skip the "Add members" step for now — you can invite people later

## Step 3: Invite co-admins

Don't be the only owner. Invite at least one other trusted officer as an **Owner** so the org survives leadership transitions.

1. Go to your org page → **People** tab → **Invite member**
2. Enter their GitHub username or email
3. Set their role to **Owner**

## Step 4: Fork the template

1. Go to [github.com/LPOregon/lp-affiliate-template](https://github.com/LPOregon/lp-affiliate-template)
2. Click the **Fork** button (top right)
3. Under "Owner," select **your organization** (not your personal account)
4. Repository name: choose something meaningful — e.g. `website`, `podunk-lp-site`, or your domain name like `podunklibertarians.org`
5. Click **Create fork**

You now have your own copy of the template. All your edits happen here — you're not editing the original template.

## Step 5: Enable GitHub Pages

1. In your forked repo, go to **Settings** → **Pages** (left sidebar)
2. Under "Source," select **Deploy from a branch**
3. Branch: **main**, folder: **/ (root)**
4. Click **Save**
5. Wait about 60 seconds, then refresh — you'll see a URL like `https://your-org.github.io/your-repo-name/`

Your site is now live (with placeholder content).

## Step 6: Update two config values

Before you start editing content, you need to tell the site (and the CMS) where it lives.

### 6a. Update `_config.yml`

In your forked repo on GitHub, click on `_config.yml`, then click the pencil icon to edit.

Change these two lines:

```yaml
url: "https://your-org.github.io"       # ← your GitHub org name
baseurl: "/your-repo-name"              # ← your forked repo name
```

If you're using a custom domain (e.g. `podunklibertarians.org`), set:

```yaml
url: "https://www.podunklibertarians.org"
baseurl: ""
```

Click **Commit changes** at the bottom.

### 6b. Update `admin/config.yml`

Click on `admin/config.yml`, then the pencil icon. Change the `repo` line:

```yaml
backend:
  name: github
  repo: YourOrgName/your-repo-name    # ← must match your fork exactly
  branch: main
```

Click **Commit changes**.

## Step 7: Verify

Wait about 60 seconds for GitHub Pages to rebuild, then visit your site URL. You should see the template site with Podunk placeholder content.

Visit `https://your-site-url/admin/` to see the CMS login screen. You'll set up authentication in the next step.

## Optional: Custom domain

If you have a domain name:

1. In your repo, go to **Settings** → **Pages**
2. Under "Custom domain," enter your domain (e.g. `www.podunklibertarians.org`)
3. Click **Save**
4. At your domain registrar, add a CNAME record pointing `www` to `your-org.github.io`
5. Wait for DNS propagation (can take up to 24 hours, usually faster)
6. Check "Enforce HTTPS" once the domain is verified

Full instructions: [GitHub's custom domain docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)

## Next step

→ [CMS Authentication Setup](03-cms-auth-setup.md)
