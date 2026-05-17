# CLAUDE.md — organigrama

## Flujo de trabajo
- Después de cada cambio funcional, hacé `git add` + `git commit` + `git push origin main` sin pedir confirmación.
- Mensajes de commit en español, una línea corta + cuerpo opcional. No incluir el "Co-Authored-By" salvo que cambie la política.
- No pidas confirmación para operaciones git rutinarias, `gh`, `curl`, `grep`, `sed`, `python3 -m http.server`, ni edits de archivos del repo.
- Sí pedí confirmación antes de: `force-push`, borrar branches, `reset --hard`, modificar `.github/` (workflows de Pages), o tocar `favicon.png`/assets binarios.

## Contexto del proyecto
- Sitio estático de una página: `index.html` + `favicon.png`.
- Desplegado en GitHub Pages desde `main` → https://tomgc.github.io/organigrama/
- Stack: HTML + CSS (vanilla) + un script inline. No usar frameworks ni build steps.
- Tipografía: Nunito (Google Fonts). Paleta en `:root` de `index.html`.

## Estructura editorial
- Subdirecciones: 5 columnas, cada una `<div class="subdir-col c-{color}">`.
- Áreas: dentro de `<div class="area-list">`, una `<div class="area-card">` por área.
- Descripciones (opcionales): cada subdirección y cada área tiene un `<p class="subdir-desc"></p>` o `<p class="area-desc"></p>` vacío. Llenarlos los activa; vacíos se ocultan con `:empty`.

## Preview local
- `python3 -m http.server` en la raíz del repo, o usar el preset `organigrama` de `~/.claude/launch.json` (puerto 4321).
