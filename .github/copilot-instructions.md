## Quick repository orientation

This is a tiny static Banner Creator. Primary entry: `index.html` (root). There is no Node/npm or build system in the repo — HTML, CSS and JS are inline in `index.html` and edits take effect immediately when served or opened in a browser.

## Big-picture structure

- `index.html` — single-file app: Google font (Instrument Serif), inline styles, a 1920x1080 `<canvas id="bannerCanvas">`, a small UI (template thumbnails, text field, font size, position), and client-side image loading.
- Image templates referenced as `<img class="template-img" src="img1.jpeg">` (expected in repo root or `img/`).

Why this matters: changes should avoid splitting behavior across files unless you update `index.html` references. Keep canvas-related logic inside the `draw()` function to preserve existing behavior.

## Project-specific conventions & patterns for AI edits


```js
ctx.fillStyle = "#fff";
```
- Responsive canvas: `#bannerCanvas` width is 1920px with a media rule to use 90% width below 1000px. If you change canvas sizing, update both the `<canvas>` width/height attributes and the responsive CSS block.
  - JS: in `draw()` — set the fill style to white:

```js
ctx.fillStyle = "#fff";
```
## Developer workflows (concrete commands)

- Quick preview (no build): serve the folder and open http://localhost:8000

```bash
# from repo root
python3 -m http.server 8000
```

- Alternatively, open `index.html` directly in a browser for simple edits.

## Small examples to reference when making changes

- Enforce white text (do not remove):
  - JS: in `draw()` — `ctx.fillStyle = "#fff";`

- Theme switching pattern:
  - CSS variables in `:root` and `body.dark` (e.g. `--bg-color`, `--text-color`).
  - JS toggles `body.classList.toggle('dark')` and updates `themeToggle.textContent`.

## Integration points & expectations

- Images: templates should be added beside `index.html` or in an `img/` subfolder; update `src` attributes accordingly.
- No server-side code, no CI config discovered — don't add CI assumptions to instructions without asking.

## What an AI agent should do first

1. Open `index.html` and run the page locally (see preview command) to observe runtime behavior.
2. When changing visual behavior, run the page in the browser to validate canvas drawing and theme toggles.
3. When adding templates, include sample images and update the template markup.

## When to ask the human

- If you plan to introduce a build step (npm, bundler) or move JS/CSS into files, ask before restructuring — this repo is intentionally single-file.
- Ask when adding external dependencies (fonts or libraries) that require adding a manifest or external network access.

---
If you'd like, I can expand this to include a brief CONTRIBUTING snippet or small automated preview script (serve + open browser) — tell me which you prefer.
