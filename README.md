# ferguson.se

Personal one-pager for Ralph Black Ferguson. Plain HTML + CSS, one self-hosted
variable font (Fraunces), zero JavaScript, no build step, no dependencies.

```
index.html    the page
style.css     the stylesheet
fonts/        Fraunces variable (roman + italic, latin subset, ~150 KB total)
```

## Preview locally

Open `index.html` directly in a browser, or serve it (needed for the font
preload to behave exactly like production):

```sh
python3 -m http.server 8080
# → http://localhost:8080
```

## Deploying

Everything is static, so any static host works. In rough order of least effort:

- **Cloudflare Pages** — connect the repo, no build command, output dir `/`.
  Free, fast global CDN, easy apex-domain support.
- **GitHub Pages** — push to GitHub, enable Pages on the `main` branch root.
- **Netlify / Vercel** — drag-and-drop or connect the repo; set no build
  command and publish directory `/`.

### Pointing ferguson.se at it

**Note: ferguson.se currently redirects to LinkedIn.** That redirect lives
wherever the domain's DNS/forwarding is configured today (registrar-level URL
forwarding or an existing DNS record) and must be removed as part of this.

1. Deploy the site and verify it on the host's preview URL.
2. At the DNS provider, delete the record/forwarding rule that powers the
   LinkedIn redirect.
3. Add the host's records for the apex domain (`ferguson.se`) — an A/ALIAS/
   CNAME per the host's instructions — plus `www` if wanted (redirect `www`
   to the apex).
4. Let the host issue TLS, then confirm `https://ferguson.se` serves the page
   and the old redirect is gone (check in a private window; the 301 may be
   cached in your regular browser).

## Content rules

Copy is sourced from Ralph's real career facts only. Business metrics on this
public page are deliberately qualitative ("roughly tripled", "majority of
revenue") — exact internal figures are reserved for private applications and
interviews. Keep it that way when editing.
