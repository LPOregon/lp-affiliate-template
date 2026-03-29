# 04 — Editing Content

Once you're logged into the CMS at `/admin/`, you can update your affiliate's content without touching any code. This guide covers what you can edit through the CMS and what requires a direct edit on GitHub.

---

## How the CMS Works

The CMS saves your changes as files in your GitHub repository. After you click **Save**, the site rebuilds automatically — this takes about 60 seconds. Refresh your live site after that wait to see your changes.

**Publish vs. Save:** When editing a News post, you'll see a **Publish** button. For Site Settings, Officers, Meeting, and Resources, use the **Save** button — there's no draft/publish distinction for those.

---

## Logging In

1. Go to `https://your-site-url/admin/` (include the trailing slash)
2. Click the small arrow (▾) next to "Sign in with GitHub"
3. Select **Sign in with personal access token**
4. Paste your token and click Sign In

---

## What You Can Edit in the CMS

The CMS handles content that changes regularly: the hero subheadline, officers, meeting details, resources, and news posts.

### Hero Subheadline

**In the CMS sidebar, click "Site Settings."**

- **Hero subheadline** — The line of text shown below the main headline in the hero section, and again in the footer. e.g. "A Libertarian Party of Oregon Affiliate"

---

### Officers

**In the CMS sidebar, click "Site Settings," then scroll to Officers.**

Each entry has:
- **Name** — Officer's full name
- **Role** — Their title, e.g. "Chair", "Treasurer", "Secretary"

To add an officer: click **Add Officers**
To remove an officer: open their entry and click the delete (trash) icon
To reorder: drag the entries using the handle on the left

---

### Meeting Details

**In the CMS sidebar, click "Site Settings," then scroll to Meeting.**

- **Location name** — Venue name, e.g. "Jerkwater Brewing Co."
- **Address** — Full street address
- **Time** — e.g. "6:00 PM"
- **Schedule** — e.g. "First Thursday of every month"
- **Notes** — Any additional information for attendees

---

### Resources

**In the CMS sidebar, click "Site Settings," then scroll to Resources.**

The Resources section is an external links grid on the homepage. Each entry has:
- **Name** — Display name for the link
- **URL** — Full URL
- **Description** — One or two sentence description shown below the name

To add a resource: click **Add Resources**
To remove one: click the delete icon on the entry

Suggested resources to include: Mises Institute, LP Wiki, Institute for Justice, Reason Magazine, Foundation for Economic Education (FEE).

---

### News Posts

**In the CMS sidebar, click "Posts."**

#### Writing a new post
1. Click **New Posts**
2. Enter a **Title**
3. Set the **Date** (defaults to today)
4. Write your content in the body area — use the formatting toolbar for headers, bold, links, and lists
5. Click **Publish** when ready

The post will appear on the homepage (three most recent shown) and on the `/news` archive page.

#### Editing or deleting a post
1. Click **Posts** in the sidebar
2. Click the post you want to edit
3. Make changes and click **Save**, or click **Delete** to remove it

#### A note on post dates
Posts are sorted by date, newest first. If you need to re-sort posts, you can change the date field. Future-dated posts will not appear until that date.

#### Example post topics
- Candidate announcements
- Event recaps
- Endorsements or policy statements
- Officer election results

---

## What Requires a Direct GitHub Edit

The following settings are in `_config.yml` and are not exposed in the CMS. You'll set most of these once when you first set up the site and rarely need to change them afterward.

To edit `_config.yml`:
1. Go to your repo on GitHub
2. Click on `_config.yml`
3. Click the pencil icon to edit
4. Make your changes and commit

### Identity
- `title` — Your affiliate name, e.g. "Podunk Libertarians"
- `description` — A short description for search engines, e.g. "The Libertarian Party affiliate serving Jerkwater and Unincorporated Podunk"
- `email` — Your affiliate's contact email
- `geography` — Shown in the hero eyebrow, e.g. "Serving Jerkwater and Unincorporated Podunk"
- `lp_affiliation_label` — Shown in the footer, e.g. "A Libertarian Party of Oregon Affiliate"
- `paid_for_by` — Legal disclaimer shown in the footer, e.g. "Paid for by the Podunk Libertarians PAC"

### URLs
- `url` — Your GitHub Pages URL or custom domain, e.g. `https://your-org.github.io`
- `baseurl` — Your repo name, e.g. `/your-repo-name` (use `""` if you have a custom domain)

### Social Links
- `twitter` — Full URL to your Twitter/X profile
- `facebook` — Full URL to your Facebook page
- `instagram` — Full URL to your Instagram profile
- `facebook_group` — Full URL to your Facebook group (if applicable)

### Party Links
- `lp_national` — LP national URL (default: `https://www.lp.org`)
- `lp_state` — Your state LP's URL
- `state_party_name` — Your state LP's name, e.g. "LP Oregon"

### Donation & Mailing List
- `anedot_url` — Your Anedot or other donation processor URL
- `rsvp_url` — Your Eventbrite, Luma, or other RSVP page URL

**Mailing list — choose one approach, leave the other blank:**
- `brevo_embed_url` — Paste your Brevo iframe `src` URL here to embed a signup form directly on the page. To get this URL: in your Brevo account go to Contacts → Forms → your form → Share → copy the Iframe code → paste only the URL from the `src="..."` attribute.
- `mailing_list_url` — A link to an external signup form (Google Form, Mailchimp, etc.). Used when `brevo_embed_url` is blank — shows a "Get Involved" button in the hero that opens the form in a new tab.

If both are blank, the Get Involved button does not appear.

### Analytics (optional)
- `goatcounter_code` — Your GoatCounter site code for privacy-friendly visitor analytics. GoatCounter is free, requires no cookies, and needs no consent banner. Sign up at [goatcounter.com](https://www.goatcounter.com), then enter your site code here — that's the subdomain portion of your GoatCounter URL (e.g. `podunklp` if your URL is `podunklp.goatcounter.com`). Leave blank to disable analytics entirely.

If your site is already proxied through Cloudflare, you can use Cloudflare Analytics instead — it requires no changes to the template, as tracking is handled at the DNS layer.

### Images
Logo and hero background image are not managed through the CMS. To replace them:
1. Prepare your files:
   - Logo: save as `logo.png`. PNG format with transparent background is required. The site is designed around the standard LP torch eagle proportions (approximately 200×170px) — images significantly outside these proportions may affect the hero layout.
   - Hero image: save as `skyline.jpg` (landscape, at least 1200px wide)
2. In your repo, navigate to `assets/images/`
3. Click **Add file → Upload files**
4. Upload your images — GitHub will replace the existing files if the names match
5. Commit the changes

---

## After Saving

After clicking Save or Publish in the CMS, or committing a change directly on GitHub:

1. GitHub Actions automatically rebuilds your site (~60 seconds)
2. Refresh your live site to see the update

You can watch the rebuild status at:
```
https://github.com/your-org/your-repo/actions
```
A green checkmark means the build succeeded. A red X means something went wrong — click into the failed run to see the error.

---

**Next:** [05 — Troubleshooting](05-troubleshooting.md)
