# ferguson.se

Personal one-pager for Ralph Black Ferguson. Plain HTML + CSS, one self-hosted
variable font (Fraunces), zero JavaScript, no build step, no dependencies.

```
index.html    the page
style.css     the stylesheet
fonts/        Fraunces variable (roman + italic, latin subset, ~150 KB total) + OFL license
```

## Preview locally

Open `index.html` directly in a browser, or serve it (needed for the font
preload to behave exactly like production):

```sh
python3 -m http.server 8080
# → http://localhost:8080
```

## Deploying

**The site is live at https://ferguson.se**, hosted on Netlify. The GitHub
repo is connected for auto-deploy:

> **Pushing to `main` publishes to production** (live within ~30 s). Treat a
> push as a deploy — verify locally first.

No build command, publish directory `/`. The local `.netlify/` folder is CLI
link state (gitignored); `netlify status` shows the project, and
`netlify deploy --prod --dir .` works as a manual fallback.

### DNS (GoDaddy)

Apex `A @ → 75.2.60.5` (Netlify), `CNAME www → ferguson-se.netlify.app`;
TLS via Netlify/Let's Encrypt covers apex + www, http→https redirects.
Gotcha from setup: GoDaddy re-adds a "Parked" A record when URL forwarding is
removed — if the site ever mysteriously breaks, check for that record first.

## Content rules

Copy is sourced from Ralph's real career facts only. Business metrics on this
public page are deliberately qualitative ("roughly tripled", "majority of
revenue") — exact internal figures are reserved for private applications and
interviews. Keep it that way when editing.
