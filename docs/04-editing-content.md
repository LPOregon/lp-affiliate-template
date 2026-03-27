# 04 — Editing Content

Once you're logged into the CMS at `/admin/`, you can update all of your affiliate's content without touching any code. This guide walks through each section.

---

## How the CMS Works

The CMS saves your changes as files in your GitHub repository. After you click **Save**, the site rebuilds automatically — this takes about 60 seconds. Refresh your live site after that wait to see your changes.

**Publish vs. Save:** When editing a News post, you'll see a "Publish" button. For Site Settings, Officers, Meetup, and Resources, use the **Save** button — there's no draft/publish distinction for those.

---

## Logging In

1. Go to `https://your-site-url/admin/` (include the trailing slash)
2. Click **Login with GitHub**
3. Authorize if prompted
4. You'll arrive at the CMS dashboard showing your content collections

---

## Site Settings

**In the CMS sidebar, click "Site Settings"** — this is where you configure everything about your affiliate's identity, appearance, and links.

Work through the groups in order:

### Identity
- **Affiliate name** — Your full affiliate name, e.g. "Podunk Libertarians"
- **Tagline** — Shown in the hero and footer, e.g. "All Your Freedoms. All the Time."
- **LP affiliation label** — e.g. "An LP [State] Affiliate"
- **Geography line** — Shown in the hero eyebrow, e.g. "Serving Jerkwater and Unincorporated Podunk"
- **Contact email** — Used in the footer and About section
- **Paid-for-by line** — Legal disclaimer shown in the footer, e.g. "Paid for by the Podunk Libertarians PAC"

### Hero
- **Headline line 1** — First line of the large hero text
- **Headline line 2** — Second line (italic by default)
- **Subheadline** — Paragraph beneath the headline
- **CTA button 1 label and URL** — Primary call to action (typically your mailing list signup)
- **CTA button 2 label and URL** — Secondary call to action (typically your donate link)

### Branding
- **Logo** — Upload your logo image. PNG with transparent background works best. Displays in the navigation bar.
- **Hero background image** — Upload a photo or image for the hero section background. Landscape orientation, at least 1200px wide.

### Social
- **Twitter/X URL** — Full URL, e.g. `https://twitter.com/PodunkLiberty`
- **Facebook URL** — Your affiliate's Facebook page URL
- **Instagram URL** — Your affiliate's Instagram profile URL
- **Facebook Group URL** — If you have a separate Facebook group for members/events

Leave any social fields blank if you don't use that platform — the icon will not appear in the footer.

### Donation
- **Donate URL** — Your Anedot or other donation processor URL
- **Donate button label** — e.g. "Donate" or "Donate Now"
- **Tax credit note** — Optional. Some states have political contribution tax credits. If yours does, enter the note text here (e.g. "Oregon residents may qualify for a political tax credit."). Leave blank if not applicable.

### Mailing List
- **Mailing list URL** — The URL of your signup form (Google Form, Mailchimp, etc.)
- **Mailing list button label** — e.g. "Join Our List" or "Get Updates"

### Events
- **Events URL** — Your Eventbrite or Luma event page URL. This is used for the "RSVP" button on the meetup card.

  > **Eventbrite or Luma?** Both work. When someone RSVPs on either platform, they receive an email confirmation with a calendar (.ics) attachment — so attendees get calendar integration automatically without any embed on your site.

### Party Links
- **State party name** — e.g. "LP Oregon" or "LP Texas"
- **State party URL** — Your state LP's website URL
- **National party URL** — Defaults to `https://lp.org` — change only if needed

---

## Officers

**In the CMS sidebar, click "Officers."**

Each entry has:
- **Name** — Officer's full name
- **Role** — Their title, e.g. "Chair", "Treasurer", "Secretary"

To add an officer: click **New Officers**
To remove an officer: open their entry and click **Delete**
To reorder: drag the entries using the handle on the left

---

## Meetup Details

**In the CMS sidebar, click "Meetup."**

- **Location name** — Venue name, e.g. "Jerkwater Brewing Co."
- **Address** — Full street address
- **Time** — e.g. "6:00 PM"
- **Schedule** — e.g. "First Thursday of every month"
- **Notes** — Any additional information for attendees, e.g. "All peaceful people welcome — you do not need to be a registered Libertarian to attend."

---

## Resources

**In the CMS sidebar, click "Resources."**

The Resources section is an external links grid on the homepage. Each entry has:
- **Name** — Display name for the link
- **URL** — Full URL
- **Description** — One or two sentence description shown below the name

To add a resource: click **New Resources**
To remove one: open it and click **Delete**

Suggested resources to include: LP national, your state LP, LP Wiki, Cato Institute, Reason Magazine, Foundation for Economic Education (FEE), Mises Institute.

---

## News Posts

**In the CMS sidebar, click "Posts."**

### Writing a new post
1. Click **New Posts**
2. Enter a **Title**
3. Set the **Date** (defaults to today)
4. Write your content in the body area — use the formatting toolbar for headers, bold, links, and lists
5. Click **Publish** when ready

The post will appear on the homepage (most recent posts shown) and on the `/news` archive page.

### Editing or deleting a post
1. Click **Posts** in the sidebar
2. Click the post you want to edit
3. Make changes and click **Save**, or click **Delete** to remove it

### A note on post dates
Posts are sorted by date, newest first. If you need to re-sort posts, you can change the date field. Future-dated posts will not appear until that date.

### Example post topics
- Candidate announcements — "Meet Our 2024 Candidates" with a section per candidate, bio, and campaign link
- Event recaps
- Endorsements or policy statements
- Officer election results

---

## After Saving

After clicking Save or Publish:

1. The CMS commits your changes to your GitHub repository
2. GitHub Actions automatically rebuilds your site (~60 seconds)
3. Refresh your live site to see the update

You can watch the rebuild status at:
```
https://github.com/your-org/your-repo/actions
```
A green checkmark means the build succeeded. A red X means something went wrong — click into the failed run to see the error.

---

**Next:** [05 — Troubleshooting](05-troubleshooting.md) (optional)
