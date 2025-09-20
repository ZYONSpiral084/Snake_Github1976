# 🐍 GitHub 贡献蛇 — 自动生成与发布

从 GitHub 贡献图生成动画 SVG 并发布到 `output` 分支。可通过 GitHub Pages 或 raw.githubusercontent 在个人主页显示。

**工作原理**
- 使用 `Platane/snk` 生成 `github-contribution-grid-snake.svg` 与 `github-contribution-grid-snake-dark.svg`。
- 在 `dist/` 中创建 `index.html`，在通过 Pages 提供时支持 `prefers-color-scheme` 自动切换。
- 将 `dist/` 推送到 `output` 分支，准备发布。

**嵌入**
- Pages（推荐）：`https://<你的用户名>.github.io/<你的仓库>/index.html`
- Raw（简单）：`https://raw.githubusercontent.com/<你的用户名>/<你的仓库>/output/github-contribution-grid-snake.svg`
