# ferguson.se

Personal one-pager for Ralph Black Ferguson. Plain HTML + CSS, one self-hosted
variable font (Fraunces), zero JavaScript, no build step, no dependencies.

```
index.html    the page
style.css     the stylesheet
fonts/        Fraunces variable (roman + italic, latin subset, ~150 KB total) + OFL license
```

## How the page is put together

One `<header class="hero">` and four `<section>`s, in the order a hiring reader
needs them: hero (positioning) → what I bring → experience → how I work →
contact. A standalone `<aside class="pull">` carries the "one loop" line between
value and evidence.

Layout conventions, all in `style.css`:

- Section headings (`h2`) are small uppercase eyebrow labels, not titles. Above
  `56rem` each section becomes a two-column grid — label left, content right —
  using `--label-col` and `--gutter`. `.pull` opts into the same grid so the
  quote aligns with the content column.
- `--measure` (37rem) is the content column width; `--band` is the vertical
  padding every section and the pull quote share. Change the rhythm there, not
  per-section.
- Component classes are one per section: `.bring`, `.roles`, `.questions`,
  `.cta`. `.mail` is the contact CTA.
- Below `30rem` two things change deliberately: a role title stacks under the
  company with no leading em dash (it would otherwise wrap onto its own line
  alone), and the numbered questions get a narrower gutter.
- The only motion is the hero's staggered fade-in, behind
  `prefers-reduced-motion: no-preference`. The delays are `nth-child`-based, so
  adding or reordering hero elements means updating them.

Check both widths before pushing. Headless Chrome enforces a minimum window
width, so a `--window-size=390,…` screenshot silently renders wider than 390px
and looks clipped; load the page in a 390px-wide `<iframe>` on a wrapper page
and screenshot that instead.

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
public page are deliberately qualitative ("around ten percent", "one person to a
team of eight") — exact internal figures are reserved for private applications
and interviews. Keep it that way when editing.

The page is structured for a hiring reader scanning for 30–60 seconds:
hero (positioning) → what I bring → experience → how I work → contact. Keep that
rhythm; the page should still make sense when only headings and bold text are
read. Resist growing it back into a full CV or an essay.
