# Portafolio — Tailwind CSS + GitHub Pages

Sitio **estático** que usa **Tailwind (CLI)** y se publica en **GitHub Pages** mediante **GitHub Actions**.

## Requisitos
- Node.js ≥ 18 y npm ≥ 8

## Instalación
```bash
npm install
```

## Desarrollo
```bash
npm run dev                 # compila Tailwind en watch → ./src/main.css
npx http-server ./src -p 5173 -c-1   # (opcional) sirve http://localhost:5173
```
En `src/index.html` (dev):  
```html
<link rel="stylesheet" href="./main.css" />
```

## Build y vista previa
```bash
npm run build
npx http-server ./dist -p 4173 -c-1  # sirve http://localhost:4173
```
El build genera `dist/` con `assets/main.css`, `.nojekyll` y `404.html`.  
En producción (`dist/index.html`):  
```html
<link rel="stylesheet" href="./assets/main.css" />
```

## Scripts
- **dev**: Tailwind → `./src/main.css` (watch)
- **build**: limpia `dist`, compila a `dist/assets/main.css`, copia `src/*`, crea `.nojekyll` y `404.html`

## Estructura sugerida
```
src/
  index.html
  styles.css     # entrada Tailwind (@tailwind base/components/utilities)
  main.css       # salida dev (generada)
  assets/        # imágenes, fuentes, etc.
dist/            # salida de producción (generada)
```

## Tailwind (opcional)
`tailwind.config.js`
```js
module.exports = { content: ["./src/**/*.{html,js,ts,jsx,tsx}"], theme:{ extend:{} }, plugins:[] };
```

## Despliegue
En push a la rama configurada, el workflow construye y publica `dist/`. Usa rutas relativas (`./assets/...`).

> Nota Windows: si fallan comandos de shell, usar `shx` para un build cross‑platform.
