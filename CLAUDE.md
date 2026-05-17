# CLAUDE.md — organigrama

## Flujo de trabajo
- Después de cada cambio funcional, ejecuta `git add` + `git commit` + `git push origin main` sin pedir confirmación.
- Mensajes de commit en español, una línea corta + cuerpo opcional. No incluyas "Co-Authored-By" salvo que cambie la política.
- No pidas confirmación para operaciones git rutinarias, `gh`, `curl`, `grep`, `sed`, `python3 -m http.server`, ni para editar archivos del repo.
- Sí pide confirmación antes de: `force-push`, borrar branches, `reset --hard`, modificar `.github/` (workflows de Pages), o tocar `favicon.png` u otros assets binarios.

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

## Excepciones declaradas a los Principios de Desarrollo

Per regla A del documento de Principios — la invocación silenciosa de la excepción es peor que la omisión declarada. Aquí van las que aplican a este proyecto:

- **D General — Estructura de directorios estándar:** se omite. Es un sitio de un solo archivo HTML; aplica la excepción para proyectos triviales (línea 261 del documento de Principios).
- **D Web — Sin dependencias externas:** se mantiene una sola excepción — Google Fonts (Nunito) — porque es la tipografía institucional declarada del SLEP. El resto (CSS, JS, SVG) es inline o local.
- **D Web — Datos en JSON:** se omite. Las 5 subdirecciones y 17 áreas viven hardcodeadas en `index.html` porque son contenido estable y de bajo volumen. Si el listado crece o muta con frecuencia, considerar mover a `data.json` con render por template.
- **C.1–C.6, C.8–C.9, C.12–C.13:** no aplican. No hay pipeline de datos, ni APIs, ni gestión de paquetes — el proyecto no procesa datos.
- **B.4 Verificación con criterios formales:** los cambios de UI se verifican manualmente en el preview local antes del push (no hay test suite ni golden file).
