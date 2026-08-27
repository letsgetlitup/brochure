# Trippy Wire™ microsite

Static one-page site for Inner Child Apparel LLC. No build step, no dependencies,
no framework. It is one HTML file plus a folder of images.

```
index.html      the whole site — markup, CSS, and JS in one file
assets/         photos, GIFs, logo, bunny ears
vercel.json     caching headers (assets cached forever, HTML always fresh)
```

## Deploy to Vercel

1. Push this folder to a GitHub repo (see below).
2. In Vercel: **Add New → Project → Import** the repo.
3. Framework Preset: **Other**. Leave Build Command and Output Directory **empty**.
4. Deploy.

That's it. Vercel serves `index.html` at the root automatically.

## Push to GitHub

From inside this folder:

```bash
git init
git add .
git commit -m "Trippy Wire microsite"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git
git push -u origin main
```

If you already created the repo on GitHub with a README, run
`git pull --rebase origin main` before pushing.

## Custom domain

In Vercel: **Project → Settings → Domains → Add**. Vercel gives you the DNS
records. Add them at your registrar, then wait for propagation (usually minutes,
occasionally a few hours). HTTPS is issued automatically — nothing to configure.

## Editing

Open `index.html` in any text editor.

- **Copy** lives in the markup, in plain sentences. Search for the text you want
  to change.
- **Colors and type** are CSS custom properties at the very top, under
  `:root`, `html[data-lights="off"]`, and `html[data-lights="on"]`.
- **Images** — drop a new file in `assets/` and change the `src`. Keep photos
  under ~1400px wide.
- **Video** — clips are `<video>`, not GIFs: muted, looping, and lazy-loaded, so
  a clip only downloads once you scroll near it and pauses when it leaves the
  screen. Each has a `-poster.jpg` shown before it loads. The two motion-smear
  clips carry audio and have a speaker button; browsers block autoplaying sound,
  so the visitor has to press it. Only one clip can be unmuted at a time.
  To swap a clip, encode H.264 MP4 (and optionally VP9 WebM), drop both in
  `assets/`, and update `data-src` / `data-src-fallback` / `poster`.
- **The lights switch, the wire frame, the splat shapes behind images, and the
  bunny ears** are all in the `<script>` block at the bottom. The frame and the
  splats are generated at runtime and regenerate on resize, so they fit any
  screen without any fixed dimensions.

## Notes

- Fonts load from Google Fonts. Offline, the page falls back to system fonts and
  still looks fine.
- Images below the fold are lazy-loaded, so the initial load is roughly 1.5MB
  even though the full page is about 7MB.
- No cookies, no analytics, no trackers. Add them yourself if you want them.
