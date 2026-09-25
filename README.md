# Consultorios Ambrosetti — sitio web

Landing page de una sola página, en HTML/CSS/JS vanilla (sin frameworks). Liviana, responsive y con animaciones al hacer scroll.

## Estructura

```
index.html          → contenido y estructura del sitio
css/style.css        → todos los estilos (colores, tipografía, layout, animaciones)
js/script.js          → menú móvil, scrollspy y animaciones de scroll
assets/favicon.svg    → ícono de la pestaña del navegador
assets/img/           → fotos del consultorio
robots.txt             → permite indexación por buscadores
```

## Ver el sitio en tu computadora

No hace falta instalar nada. Dos opciones:

1. **Más simple:** doble clic en `index.html` y se abre en el navegador.
2. **Recomendado** (para que el mapa y las rutas de imágenes funcionen igual que en un hosting real): abrí una terminal en esta carpeta y corré:
   ```
   python3 -m http.server 8000
   ```
   y entrá a `http://localhost:8000` en el navegador.

## Reemplazar fotos

Todas las fotos están en `assets/img/`. Para cambiar una, subí tu archivo nuevo **con el mismo nombre** (pisando el que está) — no hace falta tocar el código:

| Archivo | Dónde aparece |
|---|---|
| `hero-consultorio.jpg` | Foto grande de portada (todavía no la subiste — hoy se ve un cartel decorativo en su lugar) |
| `nelida-foto.jpg` | Foto de Nélida, sección "Conocé a quien te va a atender" |
| `galeria-1.jpg`, `galeria-2.jpg`, `galeria-3.jpg` | Las 3 fotos de la galería del consultorio |

Sugerencia de tamaño: fotos de hasta ~1400px de ancho ya se ven perfectas y cargan rápido; no hace falta subir archivos de varios MB.

## Editar textos, teléfono, dirección u horarios

Todo el contenido visible está en `index.html`, en español y fácil de ubicar con `Ctrl+F`:

- **Teléfono / WhatsApp:** buscá `5491158145692` (aparece varias veces — botón del hero, contacto y botón flotante). Es el formato que necesita WhatsApp: `54` (Argentina) + `9` + `11` (código de área) + el número, todo junto y sin el 0 ni el 15.
- **Dirección:** buscá `Av. Rivadavia 5012`.
- **Horario:** buscá `Miércoles de 14 a 20`.
- **Mapa:** en la sección `<!-- UBICACIÓN -->` hay un `<iframe>` de Google Maps. Si cambian de dirección, reemplazá el texto después de `q=` en su `src` por la nueva dirección.

## Publicar el sitio (hosting)

Es un sitio 100% estático, así que cualquiera de estas opciones funciona (todas tienen plan gratuito):

- **GitHub Pages:** en la configuración del repositorio, activar Pages apuntando a la rama y carpeta raíz.
- **Netlify / Vercel:** arrastrar la carpeta del proyecto a netlify.com/drop, o conectar el repositorio.
- Cualquier hosting tradicional: subir estos archivos tal cual por FTP a la carpeta pública (`public_html`, `www`, etc.).

Una vez que el sitio tenga un dominio propio, actualizá en `index.html` la línea `<meta property="og:image" ...>` con la URL completa (`https://tu-dominio/...`) para que se vea bien la miniatura al compartir el link en WhatsApp o redes.

## Notas técnicas

- Las animaciones de scroll usan `animation-timeline` de CSS (nativo del navegador) cuando está disponible, y si no, un `IntersectionObserver` en JS hace lo mismo — no depende de ninguna librería externa.
- El sitio respeta `prefers-reduced-motion`: si el visitante tiene desactivadas las animaciones del sistema, el sitio no anima nada.
- No usa ningún framework ni build step: se edita directamente y se sube tal cual.
