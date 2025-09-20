# 🐍 GitHub Contribution Snake — Auto-generate & Publish | # 🐍 Cobra de Contribuições — Gerar & Publicar Automaticamente | # 🐍 GitHub 贡献蛇 — 自动生成与发布

| 🇺🇸 English | 🇧🇷 Português | 🇨🇳 中文 (简体) |
|---|---|---|
| **What this does**<br>Generates an animated SVG “snake” from your GitHub contributions graph and publishes the output to a branch (`output`). You can then embed that SVG in your profile README or serve it via GitHub Pages so the animation is visible on your GitHub profile. | **O que isso faz**<br>Gera uma animação SVG (a “cobra”) a partir do gráfico de contribuições do seu GitHub e publica o resultado em uma branch (`output`). Em seguida você pode embutir esse SVG no README do perfil ou servi-lo via GitHub Pages para que a animação apareça no seu perfil do GitHub. | **作用说明**<br>从你的 GitHub 贡献图生成一个动画 SVG “蛇” 并将输出发布到 `output` 分支。随后你可以把该 SVG 嵌入个人资料的 README，或通过 GitHub Pages 提供，以便在你的 GitHub 个人主页显示动画。 |

---

## ⚙️ Workflow (what runs) / Workflow (o que roda) / 工作流（运行内容）

| 🇺🇸 Summary | 🇧🇷 Resumo | 🇨🇳 概要 |
|---|---|---|
| Uses `Platane/snk/svg-only@v3` to generate two SVGs (regular + dark) and pushes `dist/` to branch `output` using `crazy-max/ghaction-github-pages`. Runs on schedule, on push to `master`, and can be manually triggered. | Usa `Platane/snk/svg-only@v3` para gerar dois SVGs (regular + dark) e envia `dist/` para a branch `output` com `crazy-max/ghaction-github-pages`. Roda por cron, em push na `master` e pode ser executado manualmente. | 使用 `Platane/snk/svg-only@v3` 生成两个 SVG（普通 + 暗色），并使用 `crazy-max/ghaction-github-pages` 将 `dist/` 推送至 `output` 分支。支持定时、`master` 分支 push 与手动触发。 |

---

## 🧾 Workflow file (paste into `.github/workflows/main.yml`)  
## 🧾 Arquivo do workflow (cole em `.github/workflows/main.yml`)  
## 🧾 工作流文件（粘贴到 `.github/workflows/main.yml`）

```yaml
name: generate animation

on:
  # run automatically every 24 hours
  schedule:
    - cron: "0 */24 * * *"
  # allows to manually run the job at any time
  workflow_dispatch:
  # run on every push on the master branch (change to `main` if needed)
  push:
    branches:
      - master

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
