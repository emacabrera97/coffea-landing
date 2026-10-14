# Coffea — Landing page (HTML + CSS)

Landing page estática de una sola página para **Coffea**, cafetería ficticia de Buenos Aires.
Hecha solo con HTML5 semántico y CSS3: sin JavaScript, frameworks ni preprocesadores.

## Estructura

```
coffea-landing/
├── index.html
├── 404.html
├── netlify.toml
├── css/
│   ├── main.css          # declara el orden de las capas e importa el resto
│   ├── tokens.css        # variables: colores, tipografías, espaciado, radios
│   ├── base.css          # reset, tipografía base, foco, íconos
│   ├── layout.css        # .container, franjas, títulos de sección
│   ├── utilities.css     # .visually-hidden, .skip-link
│   └── components/       # header, hero, categories, product-card, carousel,
│                         # promo, testimonial-card, newsletter, footer
└── assets/
    ├── img/              # fotos en WebP
    └── icons/            # sprite.svg (todos los íconos) y favicon.svg
```

## Convenciones

- **Capas** (`@layer`): `tokens → base → layout → components → utilities`.
- **Tokens:** todo color, fuente, radio y espaciado sale de `tokens.css`.
- **BEM:** `.product-card`, `.product-card__title`, `.testimonial-card--featured`.
- **Mobile-first:** estilos base para 360 px y `@media (min-width: …)` hacia arriba.
  Breakpoints: `md` 48em (768 px), `lg` 64em (1024 px), `xl` 90em (1440 px).
- **Íconos:** un solo `sprite.svg`; se usan con `<svg class="icon"><use href="assets/icons/sprite.svg#nombre"></use></svg>`.

## Interacciones sin JavaScript

| Interacción | Cómo se resuelve |
|---|---|
| Carrusel de productos | `overflow-x: auto` + `scroll-snap` (swipe, trackpad y teclado) |
| Flechas del carrusel | Anclas a la primera / última card (desde 1024 px) |
| Menú móvil | `<details>` / `<summary>` |
| Favorito | `<input type="checkbox">` + `<label>` + `:checked` |
| Newsletter | Validación nativa + `:user-invalid` |
| Movimiento | Se respeta `prefers-reduced-motion` |

## Cómo verlo en tu computadora

Abrí la carpeta en VS Code y usá la extensión **Live Server** (clic derecho en `index.html` → *Open with Live Server*).
Hace falta un servidor local: abrir el archivo con doble clic (`file://`) no carga el sprite de íconos.

## Despliegue (Netlify)

Sitio estático con deploy continuo desde `main`. Configuración: *Build command* vacío y *Publish directory* `.`.
`netlify.toml` define los headers de seguridad y la caché larga de `css/` y `assets/`.
**Importante:** con caché `immutable`, si cambiás un archivo de `css/` o `assets/` renombralo con versión
(por ejemplo `main.v2.css`) y actualizá el enlace en el HTML.

## Decisiones respecto del diseño original

- Idioma `es-AR` y precios en pesos argentinos; todo el copy es de ejemplo.
- 6 cards por carrusel (el PRD muestra 4) para que las flechas tengan algo que desplazar.
- Imágenes solo en WebP (todos los navegadores del PRD lo soportan).
- Hero de 1000 px fijos desde 1024 px de ancho.
- El borde de 1,5 px de las cards se dibuja con `box-shadow: inset`, para que la imagen mida exactamente 334 px.
- Typos del diseño original corregidos y marca unificada como "Coffea".

## Créditos de imágenes

Fotos de [Unsplash](https://unsplash.com) (Unsplash License: uso libre).
