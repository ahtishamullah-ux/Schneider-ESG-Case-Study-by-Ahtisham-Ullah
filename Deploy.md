# Publishing this case study & getting it into Google

Follow these in order. Total hands-on time: ~20 minutes.
Google indexing itself takes **3 days to 2 weeks** — that part is waiting, not work.

---

## Step 1 · Put the files on GitHub

Your repo root must contain:

```
index.html          ← the case study (required, must be named exactly this)
404.html            ← styled not-found page
robots.txt          ← crawler rules
sitemap.xml         ← URL list for search engines
DEPLOY.md           ← this file
.github/workflows/deploy.yml
images/author.jpg   ← optional: your portrait appears automatically
```

If you don't have the repo yet:

```bash
git init
git add .
git commit -m "Schneider Electric ESG case study"
git branch -M main
git remote add origin https://github.com/USERNAME/REPOSITORY.git
git push -u origin main
```

---

## Step 2 · Turn on GitHub Pages

Repo → **Settings** → **Pages** → *Build and deployment* → **Source: GitHub Actions**.

The included workflow deploys automatically on every push to `main`.
Watch it run under the **Actions** tab. When the green tick appears, your URL is:

```
https://USERNAME.github.io/REPOSITORY/
```

> **Tip — the cleanest option.** Name the repo exactly `USERNAME.github.io`.
> You then get `https://USERNAME.github.io/` (a *user site*), which is the root of
> the domain. This matters, because **`robots.txt` is only honoured at the domain
> root**. On a project site (`/REPOSITORY/`) Google reads
> `USERNAME.github.io/robots.txt` and ignores yours.

---

## Step 3 · Replace the placeholder URL ⚠️ REQUIRED

Find-and-replace `https://USERNAME.github.io/REPOSITORY` with your real URL in:

| File | What to change |
|---|---|
| `index.html` | `<link rel="canonical">`, `og:url`, JSON-LD `"url"` |
| `robots.txt` | the `Sitemap:` line at the bottom |
| `sitemap.xml` | every `<loc>` |

Also set the real date in `sitemap.xml` (`<lastmod>`) and `index.html`
(`"datePublished"`), format `YYYY-MM-DD`.

One-liner on macOS/Linux:

```bash
grep -rl 'USERNAME.github.io/REPOSITORY' . \
  | xargs sed -i '' 's#https://USERNAME.github.io/REPOSITORY#https://YOURNAME.github.io/YOURREPO#g'
```

*(On Linux drop the `''` after `-i`.)*

Then `git add . && git commit -m "Set live URL" && git push`.

> A small script in `index.html` auto-corrects the canonical tag at runtime if you
> forget — but hard-coding it is strictly better for SEO. Do the replace.

---

## Step 4 · Verify ownership in Google Search Console

1. Go to **https://search.google.com/search-console** and sign in.
2. **Add property** → choose **URL prefix** → paste your full URL *with trailing slash*.
3. Choose the **HTML tag** method. Copy the `content="..."` value.
4. In `index.html`, find this near the top and **uncomment it**, pasting your code:

   ```html
   <meta name="google-site-verification" content="PASTE_YOUR_CODE_HERE">
   ```
5. Commit, push, wait ~1 minute for Pages to rebuild, then click **Verify**.

---

## Step 5 · Submit the sitemap

In Search Console → **Sitemaps** (left sidebar) → enter:

```
sitemap.xml
```

→ **Submit**. Status should become *Success* within a day.

Repeat at **Bing Webmaster Tools** (https://www.bing.com/webmasters) — you can
import directly from Google Search Console in two clicks, and it feeds DuckDuckGo
and ChatGPT search too.

---

## Step 6 · Force the first crawl

Don't wait passively. In Search Console:

**URL Inspection** (top search bar) → paste your homepage URL →
**Request Indexing**.

This usually gets you crawled within 24–72 hours instead of weeks.

---

## Step 7 · Confirm you're live

After a few days, search Google for:

```
site:USERNAME.github.io/REPOSITORY
```

If results appear, you are indexed. If not, check
Search Console → **Pages** for the reason (most common: *Discovered – currently
not indexed*, which just means "wait longer").

---

## Ranking realistically

A brand-new page with zero backlinks will **not** rank for "Schneider Electric ESG".
It *can* rank quickly for long-tail queries like:

> *"Ahtisham Ullah Schneider Electric case study"*
> *"EcoStruxure ESG flywheel research workflow"*

To speed it up, create real inbound links — the single biggest factor:

- Add the URL to your **LinkedIn** profile (Featured section + a post). The
  `LinkedInBot` is already allowed in `robots.txt`, so the preview card will render.
- Upload the paper to **ResearchGate**, **Academia.edu**, **SSRN** or **Zenodo**
  (Zenodo also gives you a citable **DOI**) and link back to the live site.
- Add it to your **university profile page** — `.edu`/`.it` academic domains carry
  strong authority.
- Put the link in your **GitHub profile README** and the repo's *About* → Website field.

---

## Optional · Custom domain

1. Buy a domain (e.g. `ahtishamullah.com`).
2. At your registrar add DNS records:
   - Four `A` records → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - One `CNAME` for `www` → `USERNAME.github.io`
3. Repo → Settings → Pages → **Custom domain** → enter it → tick **Enforce HTTPS**.
4. Re-run Step 3 with the new domain, and add it as a **new property** in Search Console.

A custom domain also means `robots.txt` sits at the true root and is fully honoured.

---

## Troubleshooting

| Symptom | Fix |
|---|---|
| 404 at the Pages URL | File must be `index.html`, lowercase, in the repo root. |
| Site loads but unstyled | Tailwind loads from a CDN — check you're online / not blocked. |
| Portrait not showing | Add `images/author.jpg`; otherwise the "AU" monogram shows by design. |
| Sitemap "Couldn't fetch" | You forgot Step 3 — the `<loc>` URLs must match the live domain exactly. |
| Not indexed after 3 weeks | Check `robots.txt` isn't blocking, re-request indexing, and build backlinks. |
| Social preview blank | Use https://www.linkedin.com/post-inspector/ to flush LinkedIn's cache. |
