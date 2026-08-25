# AISHA — AI Safety in Humanitarian Assistance

A single-page site for AISHA: humanitarian practitioners and AI engineers working together on hands-on guardrails for AI use in humanitarian programming.

**Live file:** `aisha.html` — this is the entire site. One self-contained HTML file: no build step, no package manager, no framework, no dependencies to install.

## Deploy it

### Option A — Netlify Drop (fastest, no account needed to try it)
1. Go to [netlify.com/drop](https://netlify.com/drop)
2. Drag `aisha.html` onto the page
3. You get a live HTTPS URL immediately

### Option B — GitHub + Netlify (recommended if you'll keep editing)
1. Create a new GitHub repo and add `aisha.html` to it
   - Rename it to `index.html` if you want it to serve at your site's root (`yoursite.netlify.app`) instead of `yoursite.netlify.app/aisha.html`
2. In Netlify: **Add new site → Import an existing project → GitHub** → pick the repo
3. Leave the build command empty and set the publish directory to `/` (the repo root) — there's nothing to build
4. Deploy. Every push to the connected branch will auto-redeploy from then on

### Option C — Any static host
The file has zero server-side requirements. It will work unmodified on GitHub Pages, Vercel, Cloudflare Pages, S3 + CloudFront, or literally any web server that can serve a static file.

## What's in the file

- **HTML + CSS + a small amount of vanilla JS**, all in one file
- **Fonts** load from Google Fonts CDN (Archivo, Source Serif 4, IBM Plex Mono) — the only external request the page makes
- **No JavaScript frameworks, no build tooling** — open it directly in a browser and it works
- **Works with JavaScript disabled.** Content, the 100-dot field (5 flagged), the fabricated-document example, and the risk matrix's default state are all present in the raw HTML. JavaScript adds animation, the dot reshuffle, scroll-based reveals, and matrix cell interactivity — none of it is required to read the page

## Structure

Single scrolling page, in-page anchors only (`#what`, `#risks`, `#principles`, `#team`, `#contact`):

1. Hero — headline, the 100-dot uncertainty visualization
2. What we do — humanitarian/AI bridge diagram
3. Why it matters — a fabricated (clearly labelled) example of unverified AI output
4. Where it breaks — failure modes (collapsible: 4 shown, 4 more behind "See more")
5. Accountability
6. Risk profile — interactive matrix, click a cell for what it requires
7. Principles (collapsible: 5 commitments behind "Read all 5 principles")
8. Who we are
9. How we work
10. Use cases (collapsible: 3 shown, 3 more behind "See more")
11. Contact / CTA

## Customizing

Everything visual is driven by CSS custom properties at the top of the `<style>` block:

```css
:root{
  color-scheme:light only;
  --paper:#FFFFFF;      /* page background */
  --paper-2:#F4F4F3;    /* secondary surface */
  --ink:#333537;        /* body text */
  --mute:#75777A;       /* secondary text */
  --red:#8A1F1F;        /* the only accent color — danger/flagged content */
  ...
}
```

The risk matrix's content lives in one JS array (`const MX = [...]`, near the bottom of the file) — edit the `tag`, `title`, and `items` for each of the 9 cells there. The same content also has a static HTML fallback just above it (`id="mx-panel"`) that should be kept in sync if you change the default-selected cell.

`color-scheme: light only` is set deliberately (meta tag and CSS) to stop browsers/OS from auto-inverting the page into dark mode.

## Other files in this folder

- `aisha-static.html`, `principles.html`, `team.html`, `roster.html` — earlier multi-page drafts, kept for reference. **`aisha.html` is the current, complete, single-file version of the site** and is the one to deploy.
