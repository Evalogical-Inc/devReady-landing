# DevReady landing page

Static site, no build step. Everything deployable is in **`public/`**:
`index.html`, `og.png`, `favicon.svg`, `robots.txt`, `sitemap.xml`, `_headers`.
Lives outside the `devready` repo on purpose. `efernce/` (design reference) is git-ignored and is **not** part of the site: never upload it.

Design: DM Sans, Lucide icons (loaded from unpkg, pinned to 0.469.0), peach-glow light style, scroll and terminal animations (all disabled under `prefers-reduced-motion`). Evalogical CTAs carry UTM tags (`utm_source=devready`) so you can see the traffic in your analytics.

## 1. Deploy (pick one, all free)

**Cloudflare Pages (recommended)**: global CDN, free HTTPS and custom domain, honors `_headers`.
1. Push this folder to its own GitHub repo (e.g. `devready-site`).
2. Cloudflare dashboard > Workers & Pages > Create > Pages > Connect to Git.
3. Build command: *(empty)*. **Build output directory: `public`**. Deploy. URL: `https://<name>.pages.dev`.

**Netlify Drop (fastest)**: drag the **`public`** folder (not the whole project) onto https://app.netlify.com/drop.

**GitHub Pages**: needs a custom domain or a `<user>.github.io` repo, because the page uses root paths (`/og.png`). Publish the contents of `public/`.

## 2. Set your real URL (important for SEO)

The page uses `https://YOUR-SITE.example` for canonical, Open Graph, JSON-LD, robots and sitemap. Once you know the URL, from inside `public/`:

```bash
# bash / Git Bash
grep -rl "YOUR-SITE.example" . | xargs sed -i 's#https://YOUR-SITE.example#https://devready.pages.dev#g'
```
```powershell
# PowerShell
Get-ChildItem -Recurse -Include *.html,*.txt,*.xml | ForEach-Object { (Get-Content $_ -Raw) -replace 'https://YOUR-SITE.example','https://devready.pages.dev' | Set-Content $_ -NoNewline }
```
Then redeploy.

## 3. After it is live

- Submit `sitemap.xml` in Google Search Console and Bing Webmaster Tools.
- Check the share card with LinkedIn Post Inspector or by pasting the URL into a chat/social composer.
- Add the URL as the repo "Website" on GitHub and as `Homepage` in the PyPI project links.
- Run Lighthouse in Chrome DevTools (aim for 95+ on SEO and Accessibility).
- Link to the page from evalogical.com (a backlink helps both sites).

## Notes

- Fonts come from Google Fonts and icons from unpkg. Self-host both if you want zero third-party requests.
- The hero terminal is a labelled simulation; the real tool is `devready-cli` on PyPI.
- Keep `softwareVersion` in the JSON-LD in step with PyPI releases.
