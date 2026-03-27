# 05 — Troubleshooting

This guide covers problems that can occur after your site is up and running. For setup problems, see [01 — Getting Started](01-getting-started.md) and [03 — CMS Auth Setup](03-cms-auth-setup.md).

---

## Site isn't rebuilding after a save

**Symptom:** You saved something in the CMS but the live site hasn't changed after a few minutes.

1. Check the build status at:
   ```
   https://github.com/your-org/your-repo/actions
   ```
2. If you see a red X on the latest run, click into it to read the error.
3. Common causes:

| Error in the build log | Fix |
|---|---|
| `Invalid date` in a post | Open the post in the CMS and correct the date field |
| `Liquid syntax error` | A content field contains a `{` or `}` character — escape it or rephrase |
| `No such file` for an image | An image was referenced in a CMS field but not uploaded — re-upload the image |
| Build timed out | Re-run the workflow from the Actions tab (click "Re-run jobs") |
| Error mentioning Ruby, Bundler, or a gem name | See "Build stopped working after a GitHub update" below |

If the Actions tab shows no recent runs at all, GitHub Pages may have been accidentally disabled. Go to Settings → Pages and confirm it's still set to deploy from the `main` branch.

---

## CMS login stopped working

**Symptom:** Clicking "Sign in with personal access token" produces an error or loops back to the login screen.

**"Bad credentials" or "Not Found" error on login:**
- Make sure the `repo` field in `admin/config.yml` exactly matches your fork (e.g. `YourOrg/your-repo-name`)
- Make sure your token has Contents: Read and write permission on the correct repository
- If using a fine-grained token with an org as resource owner, check that the org hasn't blocked fine-grained tokens (org Settings → Personal access tokens)

**"Not authorized" after logging in:**
The editor's collaborator access to the repo was removed. Re-add them under repo Settings → Collaborators.

**Token expired:**
Generate a new token following the steps in [03 — CMS Auth Setup](03-cms-auth-setup.md), then paste it in on the next login.

**Blank screen or spinner at /admin/:**
- Hard-refresh the page (Cmd+Shift+R / Ctrl+Shift+R)
- Check that `admin/config.yml` still has the correct `repo:` value
- Confirm the site build is succeeding (check Actions tab)

---

## A maintainer left and we're locked out of the CMS

**If the departing maintainer was the only org Owner**, you may be locked out of managing repo settings.

**If you still have a GitHub account with write access to the repo:**
You can still use the CMS — CMS access requires only repo write access, not org ownership. Generate your own PAT and log in normally.

**If you need to regain org ownership:**
GitHub allows org members to request ownership if all owners are gone. See [GitHub's documentation on recovering org ownership](https://docs.github.com/en/organizations/managing-peoples-access-to-your-organization-with-roles/maintaining-ownership-continuity-for-your-organization).

**To revoke a departed editor's access:**
Remove their collaborator access under repo Settings → Collaborators. Their personal access token stops working immediately — no further action needed.

**Prevention:** Always keep at least two org Owners. Review the owner list when officers change.

---

## Changes saved in the CMS but the wrong thing appears on the site

**Symptom:** You updated a field, the build succeeded, but the site shows old or unexpected content.

- **Browser cache:** Hard-refresh the page (Cmd+Shift+R / Ctrl+Shift+R) or open in a private/incognito window.
- **Wrong field:** Some content appears in multiple places. For example, the footer description and hero subheadline are separate fields — confirm you edited the right one.
- **Build used an older commit:** Occasionally GitHub Actions queues multiple builds and the most recent one wins. Check the Actions tab to confirm the latest successful build corresponds to your most recent save.

---

## I accidentally broke a file

**Symptom:** You edited a file directly in GitHub (not through the CMS) and the site is now broken.

Every change in GitHub is versioned. To restore a previous version of a file:

1. Go to your repo and navigate to the broken file
2. Click **History** (top right of the file view)
3. Find the last good commit — click into it
4. Click the file name to view the old version, then click **Raw**
5. Copy the content
6. Go back to the current file, click the pencil to edit, paste the old content, and commit

The site will rebuild from the restored file.

---

## The site loads but images are broken

**Symptom:** Logo, hero image, or post images show as broken image icons.

- **Wrong baseurl:** If you recently added or removed a custom domain, `baseurl` in `_config.yml` may be wrong. With a custom domain it should be `""` (empty); without one it should be `"/your-repo-name"`.
- **File not committed:** An image was referenced but never uploaded to the repo. Check `assets/images/` to confirm the file is there.
- **Filename mismatch:** File references are case-sensitive on GitHub Pages. `Logo.png` and `logo.png` are different files.

---

## Build stopped working after a GitHub update

**Symptom:** The site was building fine, you didn't change anything, and then builds started failing with errors mentioning Ruby, Bundler, or a specific gem name like `ffi`, `nokogiri`, or `github-pages`.

GitHub periodically updates the Pages build environment. When this happens, the gem versions pinned in your `Gemfile.lock` may no longer be compatible. The live site continues to serve your last successful build, but new changes won't publish until the build is fixed.

**Fix — update your Gemfile.lock:**

*Option A — Copy from the upstream template (no technical skill required)*

Check whether the upstream template's `Gemfile.lock` has been updated recently:
```
https://github.com/LPOregon/lp-affiliate-template/commits/main
```
If it has, copy the new version into your repo:
1. Open `Gemfile.lock` in the upstream repo and click **Raw**
2. Copy all the content
3. Open `Gemfile.lock` in your repo, click the pencil to edit, paste, and commit

The build should succeed on the next run.

*Option B — Regenerate it yourself (requires a computer with Ruby installed)*

If you or someone in your affiliate is comfortable with a command line, run this in a local copy of your repo:
```
bundle update
```
Then commit the updated `Gemfile.lock`. This regenerates the lockfile against current gem versions and usually resolves the conflict.

> **Do not run `bundle update` as routine maintenance.** Only do it when the build is actually broken — unnecessary updates can introduce their own incompatibilities.

---

## Something else

If your issue isn't covered here, the most useful thing you can do is note:

- What you were doing when it broke
- What the site looked like before
- What it looks like now
- Any error message in the Actions build log

With that information, someone with basic GitHub familiarity can usually diagnose the problem quickly.
