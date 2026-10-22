# Belaciano.com — a family home that can grow

This is the **public** family website for Belaciano. It uses HTML/CSS, is hosted (when enabled) on GitHub Pages, and requires no PHP, database, server, frontend framework, or Rust toolchain.

## Site architecture (October 2026)

```text
belaciano.com                     Public family landing page (this repo)
├── /people/                      Directory of seven reserved spaces
│   ├── /parent-1/                Parent 1 placeholder
│   ├── /parent-2/                Parent 2 placeholder
│   ├── /member-1/                Family member placeholder (1 of 5)
│   ├── /member-2/
│   ├── /member-3/
│   ├── /member-4/
│   └── /member-5/
└── /business/                    An independent-style business design PREVIEW

Future: business.belaciano.com    Separate GitHub repo when the business is ready
Future: person.belaciano.com      Separate repo when a member needs independent control
Private: Google Workspace        Shared calendars, documents and other restricted content
```

**Important:** personal spaces are currently **public template pages**, not personal logins or password-protected sites. In particular, they contain no identifying information about children. Every family member chooses what (if anything) to publish. Please do not publish addresses, school information, birthdays, children's names and photos without appropriate consent, or private family records.

## Logo and design

- `assets/brand-mark.svg` — scalable green/gold botanical B, adapted from the first Belaciano brand concept
- `favicon.svg` — compact browser/site icon
- `styles.css` — shared family website design system
- `business/styles.css` — a deliberately **separate** independent business theme

The mark is an editable SVG approximation inspired by the logo concept, not a pixel-identical vectorization of the original AI-generated raster image. A finalized brand package can be substituted later.

## Publish on GitHub Pages

1. [Settings → Pages](https://github.com/b3belaci/belaciano-site/settings/pages).
2. **Build and deployment → Deploy from a branch → main → /(root) → Save**.
3. Test `https://b3belaci.github.io/belaciano-site/` and all internal links (relative paths work on both the temporary and eventual custom domain).

## Adding each family member's public content

Each member's independent placeholder lives at `people/<slug>/index.html`. Edit that file's headings, text, and safe public links. Shared site styles are in `styles.css`. If a member eventually wants an entirely separate brand, custom domain, independent publishing permissions, or their own tooling, move their content into a new repository and point a named subdomain at it.

Never put private credentials, family documents, or access control in HTML or JavaScript: **GitHub Pages is public**. Hiding a link, or putting a PIN check in browser JavaScript, does not protect information.

## Launching an independent business site

The current `business/` directory is an **illustrative preview only**. It advertises no actual business services and is marked `noindex`. Once the business name and offerings are settled:

1. Create a separate public repo, e.g. `belaciano-business`, controlled by the appropriate owner(s).
2. Move the contents of `business/` into that repo's root, change `../` family links, and replace all preview text and branding. Publish it as a separate GitHub Pages site.
3. Under the business repo's Settings → Pages, configure `business.belaciano.com`.
4. Then add a **CNAME** record for `business` targeting `b3belaci.github.io` at the authoritative DNS provider (not the repository pathname). Verify HTTPS after DNS.
5. Consider a completely different business domain later if professional identity needs separation.
6. Hosting a public static business page is possible on GitHub Pages, but accepting enquiries, bookings, payments, and customer data requires an appropriate third-party service or backend with its own terms, consent, and security.

**Important legacy Google Apps distinction:** The existing family Workspace legacy-free edition is for eligible *personal/non-commercial* use. Do not assume it covers a commercial business or its customer email. Plan independent business email/service licensing without risking the family Workspace account. Merely creating a business subdomain does not change the root domain's Google Mail DNS.

## Private family hub

Keep sensitive material in the currently active Google Workspace tools with real Google account access control, or another authenticated service. Share calendars/docs with selected family members, not with "anyone with the link." Do **not** add a `family.belaciano.com` GitHub Pages site and pretend it is private.

## Safe GoDaddy migration — do not rush this

1. Export the full DNS zone and check who hosts authoritative DNS, plus the nameservers.
2. Back up the **GoDaddy Deluxe** hosting files, legacy Joomla database, and any non-website assets/mailboxes.
3. Confirm Google's existing **MX, SPF, DKIM, DMARC and verification** records. Record any other custom subdomain or TXT records.
4. In this repo's **Settings → Pages**, set the root site custom domain to `www.belaciano.com` (recommended) or `belaciano.com` and follow GitHub's own confirmation instructions.
5. Only then modify website DNS (`www` CNAME and `@` A/AAAA as appropriate). Preserve Google mail and other unrelated records exactly. **Never create a wildcard CNAME** pointing at GitHub Pages; explicitly configure each subdomain to avoid takeover exposure.
6. Verify `https://belaciano.com` and `https://www.belaciano.com`, HTTPS, and family email send and receive.
7. Only after verifying there are no workloads on GoDaddy hosting, cancel Web Hosting Deluxe and PHP Extended Support, but **never cancel domain registration**.
8. Domain registration and Google Workspace remain separate from GitHub Pages web hosting.

GitHub references:
- [Custom domain setup](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
- [Domain verification/security](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages)

## Growing with Rust later

Rust is not useful for this initial, static family site. If it becomes content heavy, **Zola** is a Rust-written static site generator that can keep GitHub Pages as the hosting target; this should be a deliberate migration, not an upfront requirement.
