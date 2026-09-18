# Peekashade — website

Sitio estático para Peekashade, servido por GitHub Pages desde `main`.
Sin build, sin npm. <https://xavierbasc.github.io/peekashade-website/>

| Fichero | Qué es | Quién lo escribe |
|---|---|---|
| `index.html` | Landing page | **a mano** — ver abajo |
| `privacy.html` | Política de privacidad (URL que exigen App Store y Google Play) | generado |
| `support.html` | Soporte (la otra URL obligatoria) | generado |
| `img/` | Icono, capturas y el vídeo de 20 s | generado |

## `index.html` ya NO se genera

Hasta el 2026-09-18 la página entera salía de
`peekashade/tools/make_website.py` a partir de `tools/website.json`, igual que
las de Honk & Moo y Paint Plop. La portada se rehízo a mano con un diseño propio
—teatro de sombras: proscenio, telones y candilejas— que la plantilla común no
sabe producir, así que **se desacopla del generador**.

> **Cuidado:** `python3 tools/make_website.py ../peekashade-website` sobrescribe
> `index.html` y devuelve la portada vieja. Si hay que regenerar las otras
> páginas o las imágenes, guarda `index.html` antes y vuelve a ponerlo.

Las otras tres piezas (`privacy.html`, `support.html`, `img/`) **sí** se siguen
generando, y ahí el generador manda: no se editan a mano.

## Qué lleva la portada

- HTML5 + **Tailwind** por su CDN de ejecución (sin build, como el resto de la
  casa) y JavaScript de toda la vida para el acordeón del FAQ.
- Tipografías **Fredoka** (titulares, redondeada) e **Inter** (cuerpo), de
  Google Fonts.
- Paleta: noche `#131a35`, crema `#fdf4e6`, telón `#e8386f` y candilejas
  `#ffc24a` — los dos últimos son los acentos reales del juego.
- Las bases (fondo, tipografías, colores) van en un `<style>` en línea para que
  la primera pintada sea correcta antes de que llegue el CDN de Tailwind.
- El vídeo (8 MB) va con `preload="metadata"`: no se descarga hasta que alguien
  lo pide.
- Respeta `prefers-reduced-motion` y el acordeón funciona también en navegadores
  sin `<details name>`.

## Cambiar los textos

Están en el propio `index.html`. Los de la **ficha de tienda** siguen viviendo
en `peekashade/tools/appstore.json`, que es de donde los leen App Store y Google
Play — no se duplican aquí a propósito.
