# GitHub Org Setup

This guide walks you through creating a GitHub organization for your affiliate, forking the template, and enabling GitHub Pages. No prior GitHub experience required.

## Step 1: Create a GitHub account

If you don't already have one, sign up at [github.com/signup](https://github.com/signup). It's free.

Use a personal email you'll have access to long-term — not a work email that might go away.

## Step 2: Create a GitHub organization

An organization lets multiple people manage the repo. This is important for succession — if you step down, the next chair can take over without losing the site.

1. Go to [github's create org page](https://github.com/account/organizations/new?plan=free)
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

## Step 5: Enable GitHub Actions

The template includes an automated setup check that runs every time you push a change. It enables GitHub Pages for you, turns on security updates, and checks your config for unconfigured placeholder values.

To enable it on your fork:

1. In your forked repo, click the **Actions** tab
2. Click **I understand my workflows, go ahead and enable them**

That's all. Actions will run automatically on your next commit.

> **If you skip this step:** you can still use the site, but you'll need to enable GitHub Pages manually (Settings → Pages → Deploy from a branch → main → /) and you won't get the automated setup checklist.

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

After committing the config changes above, GitHub will rebuild your site (about 60 seconds). Check two things:

**Check your live site:** visit `https://your-org.github.io/your-repo-name/`. You should see the template with Podunk placeholder content — your changes will appear shortly.

**Check the setup report:** go to the **Actions** tab in your repo → click the most recent **Setup Check** run → click **Setup Check** in the left sidebar → click **Check configuration** to expand it. The job summary shows which fields still need your attention. The red 🔴 item (`admin/config.yml → repo`) must be fixed before the CMS will work; the yellow ⚠️ items are content you'll fill in through the CMS.

Visit `https://your-site-url/admin/` to see the CMS login screen. You'll set up authentication in the next step.

## Optional: Custom domain

If you need to register a domain name, [Porkbun](https://porkbun.com) is a good choice — competitive pricing, no dark-pattern renewal markups, and full ALIAS record support (which simplifies the DNS setup below).

If you have a domain name:

1. In your repo, go to **Settings** → **Pages**
2. Under "Custom domain," enter your domain — use the apex form (`podunklibertarians.org`) rather than `www` so both work
3. Click **Save**
4. At your domain registrar, add DNS records:

   **Apex domain** (`podunklibertarians.org`) — add an ALIAS record (sometimes called ANAME or CNAME flattening):
   ```
   ALIAS  @  your-org.github.io
   ```
   If your registrar doesn't support ALIAS records, add these four A records instead:
   ```
   A  @  185.199.108.153
   A  @  185.199.109.153
   A  @  185.199.110.153
   A  @  185.199.111.153
   ```

   **www subdomain** — add a CNAME record so `www.podunklibertarians.org` also works:
   ```
   CNAME  www  your-org.github.io
   ```

5. Wait for DNS propagation (usually a few minutes to a few hours; up to 24 hours in rare cases)
6. Back in repo Settings → Pages, check **Enforce HTTPS** once the domain is verified

Full reference: [GitHub's custom domain docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)

## Next step

→ [CMS Authentication Setup](03-cms-auth-setup.md)
