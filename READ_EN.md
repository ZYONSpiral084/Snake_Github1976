# 🐍 GitHub Contribution Snake — Auto-generate & Publish

Generates an animated SVG from your GitHub contributions graph and publishes it to the `output` branch. Use GitHub Pages or raw.githubusercontent to show it on your profile.

**How it works**
- Action `Platane/snk` generates `github-contribution-grid-snake.svg` and `github-contribution-grid-snake-dark.svg`.
- A small `index.html` is created into `dist/` to allow `prefers-color-scheme` switching when served via Pages.
- `dist/` is pushed to the `output` branch, ready to be served.

**Workflow file**
Place `.github/workflows/generate-snake.yml` (see the project root).

**Embed**
- Pages (recommended): `https://<your_user>.github.io/<your_repo>/index.html`
- Raw (simple): `https://raw.githubusercontent.com/<your_user>/<your_repo>/output/github-contribution-grid-snake.svg`
