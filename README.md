# Cheeky Drums

A single-file React drum machine. No build step, no `node_modules` — everything ships in `index.html`.

## Stack

- **React 18** + **ReactDOM** (CDN, UMD builds)
- **Babel Standalone** (CDN) for in-browser JSX
- **Tailwind CSS** (CDN, JIT)
- **Three.js r128** (CDN)
- **Web Audio API** for the drum sampler DSP

## Local usage

Just open `index.html` in a browser. That's it.

```bash
# Optional: serve over HTTP if the browser blocks local file CORS for any reason
python3 -m http.server 8080
# then visit http://localhost:8080
```

## Deploy to Cloudflare Pages

This is a static site — no build step required.

**Via the dashboard (recommended):**

1. Push this repo to GitHub.
2. Cloudflare dashboard → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
3. Pick the repo. When asked for build settings, use:

   | Setting | Value |
   | --- | --- |
   | Framework preset | **None** |
   | Build command | *(leave empty)* |
   | Build output directory | `/` (project root) |
   | Root directory | `/` |

   > ⚠️ **Do not include a `wrangler.toml` in the repo.** Cloudflare Pages auto-detects this as a static site and serves files as-is. A `wrangler.toml` makes it think you want a Workers/Pages CLI build, which breaks things.

4. Save and deploy. Every push to `main` auto-deploys; every PR gets a preview URL.

**Via the CLI:**

```bash
npm install -g wrangler
wrangler pages deploy . --project-name=cheeky-drums
```

## Project layout

```
.
├── index.html            # The entire app
├── _headers              # Cloudflare Pages response headers
├── _redirects            # SPA fallback
├── .nojekyll             # Disables GitHub Pages Jekyll processing
├── .gitignore
└── README.md
```

## License

MIT
