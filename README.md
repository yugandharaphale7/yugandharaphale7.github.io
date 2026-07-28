# Portfolio — deployment & customization

Single file: `index.html`. No build step, no dependencies except two Google
Fonts (JetBrains Mono, Inter) loaded via CDN.

## Deploy to GitHub Pages (2 minutes)

**Option A — project page**
1. Create a new repo, e.g. `portfolio`.
2. Add this `index.html` to the repo root, commit, push.
3. Repo → **Settings → Pages** → Source: `Deploy from a branch` → Branch:
   `main` / `(root)` → Save.
4. Your site is live at `https://<your-username>.github.io/portfolio/`.

**Option B — root/profile page**
1. Create a repo named exactly `<your-username>.github.io`.
2. Add `index.html` to the root, commit, push.
3. Pages is enabled automatically. Live at `https://<your-username>.github.io/`.

## Customize

Everything content-related lives directly in `index.html`, in plain HTML —
search for the section you want to change (`id="projects"`,
`id="experience"`, etc.) and edit the text in place.

A few things are centralized for convenience — find the `CONFIG` object near
the bottom of the file (inside the `<script>` tag) and fill in:

```js
var CONFIG = {
  name: "Yugandhar Aphale",
  email: "you@example.com",       // → powers the Contact panel + mailto link
  github: "yourusername",         // → powers Contact link + the live Activity heatmap
  linkedin: "yourusername",       // → powers Contact link
  resumeUrl: "#",                 // → link to a hosted resume PDF
  docsUrl: "#"
};
```

Set `github` to your real username to turn on the live activity panel (it
calls the public GitHub events API client-side — no key needed).

### Things left as placeholders on purpose
- Project repository / demo / documentation links (marked "— add link")
- Backtest performance figures for the two trading-system projects (marked
  "pending final computation") — fill these in once you have real numbers,
  don't leave placeholder stats that look computed
- Publication link once the paper has a hosted PDF/DOI
- Resume PDF URL

## Hidden details already built in
- Terminal command bar — press `/` anywhere, or `T` to toggle. Try `help`,
  `about`, `projects`, `resume`, and `sudo hire yugandhar`.
- Live IST + UTC clock in the nav.
- Scroll-triggered panel reveals, respecting `prefers-reduced-motion`.
- GitHub activity heatmap (once `CONFIG.github` is set).

## Performance
No JS frameworks, no animation libraries, no images to optimize. Should sit
comfortably in the high-90s on Lighthouse across the board once fonts are
cached.
