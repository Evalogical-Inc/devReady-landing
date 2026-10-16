# DevReady landing page

Static site (no build step): `index.html`, `og.png`, `favicon.svg`, `robots.txt`, `sitemap.xml`, `_headers`.
Lives outside the `devready` repo on purpose.

## 1. Deploy (pick one, all free)

**Cloudflare Pages (recommended)**: fast global CDN, free custom domain + HTTPS, honors `_headers`.
1. Push this folder to its own GitHub repo (e.g. `devready-site`).
2. Cloudflare dashboard > Workers & Pages > Create > Pages > Connect to Git.
3. Build command: *(empty)*. Output directory: `/`. Deploy. You get `https://<name>.pages.dev`.

**Netlify Drop (fastest, no account setup beyond sign-in)**: drag this folder onto https://app.netlify.com/drop. Honors `_headers`.

**GitHub Pages**: push to its own repo > Settings > Pages > Deploy from branch `main` / root. URL: `https://<user>.github.io/<repo>/`. Note: project-site URLs live under a sub-path, so use a custom domain or a `<user>.github.io` repo or the absolute `/favicon.svg`, `/og.png` paths break.

## 2. Set your real URL (important for SEO)

The page uses `https://YOUR-SITE.example` for canonical, Open Graph, JSON-LD, robots and sitemap. After you know the URL, replace it everywhere:

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

- Submit the sitemap in Google Search Console and Bing Webmaster Tools.
- Check the share card: paste the URL into https://cards-dev.twitter.com/validator alternatives, or LinkedIn Post Inspector.
- Add the URL as the repo "Website" on GitHub and in the PyPI project links (`[project.urls] Homepage`).
- Test with Lighthouse (Chrome DevTools) - target 95+ on SEO and Accessibility.

## Notes

- Google Fonts (Bricolage Grotesque, JetBrains Mono) load from Google; swap to self-hosted files if you want zero third-party requests.
- The hero terminal is a labelled simulation; the real tool is `devready-cli` on PyPI.
- Keep the version (`softwareVersion` in the JSON-LD) in step with PyPI releases.
