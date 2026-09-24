# Sitio de StickCode

## Cómo publicarlo en GitHub Pages

1. Crea un repositorio nuevo en GitHub, por ejemplo `stickcode-site` (o `tuusuario.github.io` si quieres que sea tu dominio raíz de GitHub Pages).
2. Sube estos archivos a la raíz del repositorio (`index.html`, `apps.html`, `contacto.html`, `privacidad.html`, `style.css`, y la carpeta `assets/`).
3. En el repositorio: **Settings → Pages → Source**, elige la rama `main` y la carpeta `/ (root)`. Guarda.
4. En un par de minutos tu sitio queda disponible en `https://tuusuario.github.io/stickcode-site/` (o en tu dominio raíz si usaste el nombre especial).

## Agregar tu foto al fondo del Inicio

1. Guarda tu foto en blanco y negro como `hero-photo.jpg` y tu foto a color (la misma toma, o una parecida) como `hero-photo1.jpg`.
2. Coloca ambas dentro de la carpeta `assets/`.
3. Ya están conectadas — `index.html` las busca automáticamente en `assets/hero-photo.jpg` y `assets/hero-photo1.jpg`. Si los nombres son distintos, edita estas líneas en `index.html`:
   ```html
   <div class="hero-bg hero-bg-a" style="background-image: url('assets/hero-photo.jpg');"></div>
   <div class="hero-bg hero-bg-b" style="background-image: url('assets/hero-photo1.jpg');"></div>
   ```

### Efecto glitch entre las dos fotos

Cada 9 segundos, el fondo del Inicio hace un pequeño "glitch" (cortes y parpadeo) y alterna entre la foto en blanco y negro y la de color. Esto se controla en el `<script>` al final de `index.html`:

```js
setInterval(function () { ... }, 9000);   // cada cuánto cambia (en milisegundos)
setTimeout(function () { ... }, 500);      // duración del glitch antes de mostrar la otra foto
```

Para que el cambio sea más o menos frecuente, ajusta el `9000` (9 segundos). Para que el glitch dure más o menos, ajusta el `500` — y el mismo número en `style.css` dentro de `.hero.glitch-active .hero-bg { animation: heroGlitch 0.5s steps(8, end); }` (deben coincidir).

## Galería y video dentro del modal (Ver más)

**Galería en carrusel:** las capturas del modal de una app ahora se muestran de a 2, con flechas (‹ ›) para pasar de par en par. Para agregar o quitar capturas, edita las `<img>` dentro de `.modal-gallery` en el `apps.html` — no hay que tocar nada más, el carrusel se ajusta solo. El mismo bloque (`gallery-carousel` + `modal-gallery` + botones `gallery-prev`/`gallery-next`) lo puedes copiar a cualquier otro modal que quieras que tenga galería.

**Video vertical:** el reproductor ya no fuerza el video a 16:9 — se adapta a la proporción real del archivo (vertical, horizontal, cuadrado, lo que sea), con un alto máximo de 65% de la pantalla (`.modal-video` / `.modal-video video` en `style.css`, la propiedad `max-height: 65vh`). Si algún día usas un video horizontal, se va a ver igual de bien, sin necesidad de cambiar nada.

En escritorio (900px de ancho o más), la foto ya no ocupa todo el ancho de la pantalla — vive en un panel a la derecha (el resto queda oscuro), para que no se vea con tanto zoom/recortada. Puedes ajustar qué tan ancho es ese panel y qué parte de la foto se ve en `style.css`:
```css
@media (min-width: 900px) {
  .hero-bg {
    left: 38%;              /* más alto = panel más angosto (foto más chica) */
    background-position: center 15%;  /* qué parte de la foto se ve — sube o baja el % */
  }
}
```
En móvil la foto sigue a pantalla completa como antes, porque ahí el recorte no se ve exagerado.

## Agregar el link real de descarga de MyNomiApp

En `apps.html`, busca:
```html
<a href="#" class="app-link">Descargar →</a>
```
y reemplaza el `#` por el link real de Play Store cuando publiques la app.

## Agregar una app nueva al portafolio y a Privacidad

**En `apps.html`**: copia un bloque `.app-row` y cambia nombre, estado, descripción y link.

**En `privacidad.html`**: copia el bloque `<article class="privacy-app" id="mynomiapp">...</article>` completo, cámbiale el `id` (ej: `id="calculadora-ramos"`) y ajusta el contenido a esa app. Luego agrega el link correspondiente en `.privacy-nav`:
```html
<a href="#calculadora-ramos">Calculadora de Ramos</a>
```
Así cada app tiene su propia URL directa para poner en la Play Store: `stickcode.dev/privacidad.html#calculadora-ramos`.

## Modal de detalle de MyNomiApp (video + capturas)

En `apps.html`, el botón "Ver más →" de MyNomiApp abre una ventana flotante (`#modal-mynomiapp`) con párrafos de explicación, un video y una galería de capturas. Para activarla del todo, agrega estos archivos a la carpeta `assets/`:

- `assets/mynomiapp-demo.mp4` — el video de demostración (recomendado: menos de 20-30 MB para que cargue rápido).
- `assets/mynomiapp-video-poster.jpg` — una imagen fija que se muestra antes de darle play al video.
- `assets/mynomiapp-screenshot-1.jpg`, `-2.jpg`, `-3.jpg`, `-4.jpg` — tus capturas de pantalla (puedes agregar o quitar imágenes; solo copia o borra el `<img>` correspondiente dentro de `.modal-gallery`).

También reemplaza el `#` del botón "Descargar en Google Play →" dentro del modal por el link real cuando publiques la app.

### Agregar el mismo tipo de modal a otra app

Copia el bloque completo `<div class="modal-overlay" id="modal-mynomiapp">...</div>`, cámbiale el `id` (ej: `id="modal-arat-kz"`) y ajusta el contenido. Luego, en el botón de esa app, cambia `onclick="openAppModal('mynomiapp')"` por `onclick="openAppModal('arat-kz')"` (el nombre debe coincidir con lo que pusiste después de `modal-` en el `id`).

## Arat-Kz (juego)

Ya hay una sección "Juegos" en `apps.html` con la ficha de Arat-Kz. Para completarla:

1. Agrega `assets/arat-kz.png` con el logo o arte del juego.
2. Cuando tengas más material (capturas, trailer), sigue el mismo patrón del modal de MyNomiApp para darle su propia ventana de detalle.

## Configurar tu email de contacto

## Instagram en el encabezado y en Contacto

El link de Instagram (`@stickcodeofficial`) ya está puesto en el menú de las 4 páginas y en la sección de contacto. Si cambias de usuario, actualiza la URL `https://www.instagram.com/stickcodeofficial` donde aparezca.

## Contador de visitas global

El punto verde + número que aparece junto a "Instagram" en el menú es un contador de visitas que suma sin importar desde qué página o dispositivo entre la gente — usa el mismo contador en las 4 páginas.

Funciona con un servicio externo gratuito y sin necesidad de cuenta: [countapi.mileshilliard.com](https://countapi.mileshilliard.com) (sucesor del extinto countapi.xyz). Cada vez que alguien carga cualquier página, se hace una petición a:

```
https://countapi.mileshilliard.com/api/v1/hit/stickcode-dev-site-visits
```

y el número que devuelve es el total acumulado. Si algún día ese servicio deja de funcionar (como le pasó al original countapi.xyz), solo tienes que cambiar esa URL por la de otro servicio equivalente en el bloque `<script>` que dice `data-site-counter` — está repetido igual en `index.html`, `apps.html`, `contacto.html` y `privacidad.html`.

Como es un servicio externo, **el contador no es 100% infalible** (rate limits, caídas ocasionales); si falla, simplemente se muestra un guion (—) en vez de romper la página.

Reemplaza `contacto@stickcode.dev` por tu correo real en `contacto.html` y `privacidad.html` (aparece varias veces).
