# 03 — OAuth Setup

The CMS at `/admin` uses GitHub to verify that editors have permission to make changes. To enable this, you need to create a **GitHub OAuth app** in your organization. This is a one-time setup that takes about 5 minutes.

---

## What This Does

When an editor clicks "Login with GitHub" in the CMS, GitHub checks whether they have access to your repository and, if so, lets them in. The OAuth app is what allows this handshake to happen.

You are not granting anyone new access to your repo by doing this. Only people who already have write access to the repository (set up in the previous guide) can log into the CMS.

---

## Part 1 — Create the OAuth App

The OAuth app should be owned by your **organization**, not your personal account.

1. Go to your GitHub org page: `github.com/your-org-name`
2. Click **Settings** (in the org's top menu — not your personal settings)
3. In the left sidebar, scroll down to **Developer settings** → **OAuth Apps**
4. Click **New OAuth App**

Fill in the form:

| Field | Value |
|---|---|
| **Application name** | `Podunk Libertarians CMS` (or any recognizable name) |
| **Homepage URL** | Your site URL, e.g. `https://podunk-libertarians.github.io/website` |
| **Authorization callback URL** | `https://your-site-url/admin/` — see note below |

> **Callback URL is critical.** It must exactly match the URL of your `/admin` page, including the trailing slash. For a GitHub Pages site without a custom domain, this is:
> ```
> https://your-org-name.github.io/your-repo-name/admin/
> ```
> For a custom domain:
> ```
> https://yourdomain.org/admin/
> ```

5. Click **Register application**

---

## Part 2 — Copy the Client ID into Your Repo

After registering, GitHub shows you your app's **Client ID** — a short alphanumeric string like `Ov23liABC123XYZ`.

1. Copy the Client ID
2. Go to your repo and open `admin/config.yml`
3. Click the pencil icon to edit
4. Find this line:
   ```yaml
   client_id: YOUR_OAUTH_CLIENT_ID
   ```
5. Replace `YOUR_OAUTH_CLIENT_ID` with your actual Client ID:
   ```yaml
   client_id: Ov23liABC123XYZ
   ```
6. Commit the change

---

## Part 3 — The Client Secret

On the same OAuth app page, you can generate a **Client Secret**. 

**Do not put the Client Secret in your repo.** Your repo is public, and committing a secret there exposes it.

The Decap CMS implicit OAuth flow used by this template does not require the Client Secret to be stored anywhere — GitHub handles authentication without it. You can leave the Client Secret field blank or note it somewhere secure (a password manager) in case you need it for future tooling.

> **If you generated a secret:** GitHub only shows it once. If you didn't copy it and need it later, you can rotate it from the OAuth app settings page (Settings → Developer settings → OAuth Apps → your app → Generate a new client secret). Rotating does not break the CMS — only the old secret is invalidated.

---

## Part 4 — Test the CMS Login

1. Go to your site's `/admin` URL, e.g.:
   ```
   https://your-org-name.github.io/your-repo-name/admin/
   ```
2. Click **Login with GitHub**
3. GitHub will ask you to authorize the app — click **Authorize**
4. You should arrive at the CMS dashboard

If you see an error instead, the most common causes are:

| Error | Fix |
|---|---|
| "redirect_uri_mismatch" | The callback URL in your OAuth app doesn't match your `/admin/` URL exactly. Check for a missing trailing slash or a typo. |
| "Not Found" at /admin/ | GitHub Pages hasn't finished building yet — wait 60 seconds and try again. |
| Blank screen or spinning forever | Check that `client_id` in `admin/config.yml` matches exactly (no extra spaces). |
| "Unable to authenticate" after login | The logged-in GitHub account doesn't have write access to the repo. Add them as a collaborator (see doc 02, Part 6). |

---

## Part 5 — Managing Editors Over Time

**To add an editor:** Give them write access to the repo (Settings → Collaborators) AND have them authorize the OAuth app by logging into `/admin/` once.

**To remove an editor:** Remove their collaborator access in repo Settings → Collaborators. They will no longer be able to authenticate through the CMS on their next login attempt.

**If you hand off to a new maintainer:** Make them an Owner of the GitHub org. The OAuth app lives in the org and does not need to be recreated.

**If you need to rotate the OAuth app** (e.g. a maintainer left on bad terms): Go to org Settings → Developer settings → OAuth Apps → your app. You can delete the app and create a new one, then update `client_id` in `admin/config.yml`. All editors will need to re-authorize on next login.

---

## Summary

At this point you should have:

- [ ] A GitHub OAuth app created under your org
- [ ] The Client ID copied into `admin/config.yml` and committed
- [ ] Successfully logged into the CMS at `/admin/`

---

**Next:** [04 — Editing Content](04-editing-content.md)
