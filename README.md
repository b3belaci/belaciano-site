# Belaciano.com

A simple, static family-domain homepage. The site has **no database, no tracking, no web server to maintain, and no build step**. It uses HTML + CSS, plus a tiny SVG favicon.

## Status

- [x] Starter site committed to `main`
- [ ] Enable GitHub Pages
- [ ] Confirm the temporary GitHub Pages URL works
- [ ] Configure custom domain on GitHub
- [ ] Update **website-only** DNS
- [ ] Verify HTTPS and Google Workspace email
- [ ] Back up and retire the unused GoDaddy hosting

## Enable GitHub Pages

1. Open [repository Settings → Pages](https://github.com/b3belaci/belaciano-site/settings/pages).
2. Under **Build and deployment**, select **Deploy from a branch**.
3. Set branch to `main` and folder to `/ (root)`, then Save.
4. Verify the site at https://b3belaci.github.io/belaciano-site/

## Later: connect belaciano.com (not yet)

1. In **Settings → Pages**, set **Custom domain** to `www.belaciano.com`. Wait for GitHub to register the hostname before changing DNS.
2. Snapshot/export the *entire* current DNS zone and nameservers. Preserve **MX, SPF, DKIM, DMARC, Google verification**, other email records, and any non-website records.
3. Verify family mail is routed to Google independently of the old website IP.
4. At the authoritative DNS provider, make `www` a CNAME to `b3belaci.github.io`; replace only the old website A records for apex `@` with GitHub Pages' official four IPv4 records:
   - `185.199.108.153`
   - `185.199.109.153`
   - `185.199.110.153`
   - `185.199.111.153`
5. Remove any old website AAAA records that still point to the previous host, if present. Preserve all mail and unrelated service records. Do not change nameservers casually.
6. Verify HTTPS on both `belaciano.com` and `www.belaciano.com` and check Google Workspace send/receive.
7. **Before canceling Web Hosting Deluxe and PHP Extended Support**, export the GoDaddy hosting files, Joomla database, DNS, and check for other hosting-based workloads. **Keep the domain registration active.**

Always verify current instructions at [GitHub Pages custom domain docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site).

## Editing the website

Edit `index.html` for wording and `styles.css` for layout and colors. Commit the changes to `main`; Pages republishes automatically.

Everything in this repository is public. **Never commit family records, photos without consent, addresses, keys, credentials, or private documents.** The future private family portal should be hosted separately with proper authentication.

No Rust is needed yet. If the site grows into a content-heavy project, consider **Zola**, a Rust-based static site generator, without changing GitHub Pages hosting.
