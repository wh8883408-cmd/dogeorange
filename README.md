# Doge & Orange — Brand Site

Static landing page + Privacy Policy + Terms of Service for the **Doge & Orange** brand, operated by **Best Bangkok Trading Co., Ltd.**

Built specifically so that **TikTok for Business Marketing API** (and similar platform reviewers) can verify our company has a publicly accessible website with legal pages.

## What's in here

| File | Purpose |
|---|---|
| `index.html` | Brand landing page (About / Products / Where to Buy / Contact) |
| `privacy.html` | Privacy Policy (PDPA-compliant + TikTok API data disclosure) |
| `terms.html` | Terms of Service (jurisdiction: Thailand) |
| `style.css` | Single shared stylesheet (brand color tokens) |
| `README.md` | This file |

Pure static HTML + 1 CSS file. No build step.

## Deploy to Cloudflare Pages (free)

The whole point: get a publicly reachable URL like `https://dogeorange.pages.dev/` that TikTok reviewers can hit.

### Step 1 — Push to GitHub

```bash
cd /Users/saranya/Desktop/my-project/doge-and-orange-site
git init
git add .
git commit -m "Initial brand site"
# Create a new public GitHub repo named 'dogeorange' (or anything),
# then:
git remote add origin git@github.com:wh8883408-cmd/dogeorange.git
git branch -M main
git push -u origin main
```

### Step 2 — Connect Cloudflare Pages

1. Go to <https://dash.cloudflare.com/> → **Workers & Pages** → **Create application** → **Pages** → **Connect to Git**
2. Authorize Cloudflare to access your GitHub
3. Select the `dogeorange` repo
4. **Build settings**:
   - Framework preset: **None**
   - Build command: *(leave empty)*
   - Build output directory: `/`
5. Click **Save and Deploy**

Within ~30 seconds you'll have:

```
https://dogeorange.pages.dev/
https://dogeorange.pages.dev/privacy.html
https://dogeorange.pages.dev/terms.html
```

(If the `dogeorange` subdomain is taken, Cloudflare will append a hash — that's fine, it's still globally reachable.)

### Step 3 — Verify reachability before re-submitting TikTok

From any browser, open all three URLs and confirm they render correctly. **Also test from an incognito window** to make sure no login is required.

```bash
# Optional: command-line check
curl -sI https://dogeorange.pages.dev/ | head -1          # → HTTP/2 200
curl -sI https://dogeorange.pages.dev/privacy.html | head -1
curl -sI https://dogeorange.pages.dev/terms.html | head -1
```

### Step 4 — Re-submit TikTok for Business application

Use these URLs in the TikTok for Business developer profile form:

| Field | URL |
|---|---|
| Company website | `https://dogeorange.pages.dev/` |
| Privacy Policy URL | `https://dogeorange.pages.dev/privacy.html` |
| Terms of Service URL | `https://dogeorange.pages.dev/terms.html` |

## After approval — keep it real

After the TikTok reviewer approves, **do not take the site offline**. TikTok reviews periodically and may revoke access if the registered website becomes unreachable.

If/when you buy a real `.com` domain for Doge & Orange in the future, the migration path is:

1. Add the custom domain in Cloudflare Pages (Settings → Custom domains)
2. Update your DNS to point at Cloudflare
3. Update the URLs in your TikTok developer profile

The site itself doesn't have to change.

## Maintenance

- **Content updates**: edit the HTML files, `git commit && git push`, Cloudflare auto-redeploys
- **Privacy Policy material changes**: bump the "Last updated" date at the top + post a notice on `index.html` for 30 days (the policy itself promises this)
- **Brand color updates**: change the `:root` variables in `style.css`

## Verify locally before pushing

```bash
cd /Users/saranya/Desktop/my-project/doge-and-orange-site
python3 -m http.server 8080
# open http://localhost:8080/
```
