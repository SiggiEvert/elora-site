# elora.is

Static marketing site for ELORA — configuration and compliance evidence for airline engineering and CAMO teams.

Replaces the previous Gamma-hosted site (Rev 1, Electrical Load Analysis positioning). This is Rev 2.

## Stack

None. One hand-written `index.html` with inline CSS and ~20 lines of vanilla JS. Fonts load from Google Fonts. No build step, no dependencies, no package manager.

Open `index.html` in a browser to preview, or:

```bash
python3 -m http.server 8000
# http://localhost:8000
```

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire site |
| `favicon.svg` | Change-bar mark |
| `robots.txt` | Allows indexing, points to sitemap |
| `sitemap.xml` | Single URL — update `lastmod` on content changes |
| `_headers` | Security headers (read by Cloudflare Pages and Netlify) |

## Deploy

Cloudflare Pages or Netlify, connected to this repo.

- Build command: **none**
- Output directory: **/** (repo root)
- Branch: `main`

Every push to `main` publishes.

## DNS cutover (ISNIC)

1. Add `elora.is` and `www.elora.is` as custom domains in the host.
2. Point the A / CNAME records at the host's targets.
3. **Do not modify MX or TXT records.** They carry `info@elora.is` and any SPF/DKIM. Gamma did not host mail.
4. Verify: `curl -sI https://elora.is | grep -i -E 'server|location'` and confirm no `noindex` in the source.
5. Submit to Google Search Console. The Gamma site was served `noindex, nofollow`, so the domain has never been indexed.

Rollback is a DNS revert.

## Content rules

Two constraints, both deliberate:

- **No interviewee or airline is named.** The discovery interviews were research, not endorsements, and one carrier is the founders' employer. Findings stay anonymised to role and region.
- **No prices.** The pilot and subscription figures in the pitch deck are untested hypotheses. They do not go on a public page before a budget holder has reacted to them.

## Open

- `og.png` (1200×630) — meta tags are stubbed out in `<head>` until it exists
- Legal entity details for the footer once the ehf. is registered
- Interview count in the Evidence section says "six across four airlines and a lessor" — reconcile against the actual file set
