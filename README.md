# Instrument Serif Banner Creator

A tiny static banner creator implemented as a single HTML file. It's intended for quick visual mockups and small banner exports (PNG) using a 1920×1080 canvas.


Key points
- Single-file app: see `index.html` at the repo root — HTML, CSS and JavaScript are inline.
- Always-white canvas text: the canvas drawing code enforces white text (`ctx.fillStyle = "#fff"`) to preserve contrast over template images.
- Dark mode: controlled by toggling `body.dark` (CSS variables in `:root` and `body.dark`) and the JS theme toggle.

Live demo link: https://instrument-serif-banner.netlify.app/

Files of interest
- `index.html` — the whole app: UI, canvas, and client-side logic (template selection, text input, font size, position, save PNG).
- `img1.jpeg`, `img2.jpeg`, `img3.jpeg`, `img4.jpeg` — example template images referenced by the page.

Adding templates
- Add image files next to `index.html` (or in an `img/` subfolder) and include an `<img class="template-img" src="...">` element in the `.templates` container.
- Template selection uses an `img.onload` handler to set the image used by the canvas and then calls the `draw()` function.

Contributing
- This repo intentionally avoids a build step. If you plan to split files or add a build system (npm, bundler), please open an issue or ask the maintainer first so the repo structure can be discussed.

License & maintainer
- Owner: amanspector
- If you want me to add a license file or a contributing guide, tell me which license and I will add it.
