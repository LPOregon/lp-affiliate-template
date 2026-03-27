# CMS Authentication Setup

Sveltia CMS authenticates with GitHub using a **personal access token (PAT)**. This is much simpler than the OAuth setup required by older CMS tools — no third-party services, no callback URLs, no client secrets.

You generate a token on GitHub, and paste it into the CMS login screen. Your browser remembers the token, so you only need to do this once per device.

## Step 1: Generate a personal access token

1. Go to [github.com/settings/tokens](https://github.com/settings/tokens?type=beta)
2. Click **Generate new token** → **Fine-grained token**
3. Fill in:
   - **Token name:** something like `Sveltia CMS - Podunk LP site`
   - **Expiration:** see the note below on expiration options
   - **Resource owner:** select your **organization** (not your personal account)
   - **Repository access:** select **Only select repositories**, then pick your website repo
4. Under **Repository permissions**, set:
   - **Contents:** Read and write
   - **Metadata:** Read-only (this is required and may already be selected)
5. Click **Generate token**
6. **Copy the token immediately** — you won't be able to see it again

Store the token in a password manager (1Password, Bitwarden, etc.). If you lose it, you'll need to generate a new one.

## Step 2: Log into the CMS

1. Go to `https://your-site-url/admin/`
2. On the login screen, click the small arrow (▾) next to "Sign in with GitHub"
3. Select **Sign in with personal access token**
4. Paste your token and click Sign In

You're in. Your browser will remember the token for future sessions on this device.

## Token expiration options

**Fine-grained tokens** are the recommended type. They can be scoped to a single repo with minimal permissions, which is more secure.

- **For personal accounts:** you can set tokens to never expire
- **For organizations:** GitHub defaults to a 366-day maximum lifetime. Your org admin can change this under Settings → Personal access tokens → Fine-grained tokens → "Set maximum lifetimes"

If your org enforces a maximum lifetime, you'll need to regenerate the token before it expires. Set a calendar reminder.

**Classic tokens** are an alternative if your org's token lifetime policy is too restrictive. They have no expiration requirement, but they grant broader access. If you use a classic token:

1. Go to [github.com/settings/tokens](https://github.com/settings/tokens) → **Generate new token (classic)**
2. Select the `repo` scope
3. Set expiration to "No expiration" (or your preference)
4. Generate and copy the token

Classic tokens work the same way in the CMS login screen.

## Multiple editors

Each person who needs CMS access should:

1. Have their own GitHub account
2. Be added as a collaborator on the repo (Settings → Collaborators)
3. Generate their own personal access token
4. Log in at `/admin` with their own token

Tokens are personal — never share them. If someone leaves the team, remove their collaborator access on the repo. Their token will stop working automatically.

## Troubleshooting

**"Not Found" or "Bad credentials" error on login:**
- Make sure the `repo` field in `admin/config.yml` exactly matches your fork (e.g. `YourOrg/your-repo-name`)
- Make sure your token has Contents: Read and write permission on the correct repository
- If using a fine-grained token with an org as resource owner, check that the org hasn't blocked fine-grained tokens (Settings → Personal access tokens)

**Token expired:**
- Generate a new token following the steps above, then paste it in on the next login

**CMS loads but shows no content:**
- Check that `admin/config.yml` points to the right branch (should be `main`)
- Verify the repo isn't private (GitHub Pages requires public repos on the free plan, or a Pro/Team plan for private repos)

## Next step

→ [Editing Content](04-editing-content.md)
