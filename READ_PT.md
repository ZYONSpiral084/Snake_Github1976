# 🐍 Cobra de Contribuições — Gerar & Publicar Automaticamente

Gera uma animação SVG a partir do gráfico de contribuições do GitHub e publica na branch `output`. Use GitHub Pages ou raw.githubusercontent para exibir no perfil.

**Como funciona**
- A action `Platane/snk` gera `github-contribution-grid-snake.svg` e `github-contribution-grid-snake-dark.svg`.
- Um `index.html` simples é criado em `dist/` para permitir troca automática com `prefers-color-scheme` quando servido via Pages.
- `dist/` é enviado para a branch `output`, pronto para servir.

**Embed**
- Pages (recomendado): `https://<seu_usuario>.github.io/<seu_repositorio>/index.html`
- Raw (simples): `https://raw.githubusercontent.com/<seu_usuario>/<seu_repositorio>/output/github-contribution-grid-snake.svg`
