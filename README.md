# Sitio de StickCode

## Cómo publicarlo en GitHub Pages

1. Crea un repositorio nuevo en GitHub, por ejemplo `stickcode-site` (o `tuusuario.github.io` si quieres que sea tu dominio raíz de GitHub Pages).
2. Sube estos archivos a la raíz del repositorio (`index.html`, `apps.html`, `contacto.html`, `privacidad.html`, `style.css`, y la carpeta `assets/`).
3. En el repositorio: **Settings → Pages → Source**, elige la rama `main` y la carpeta `/ (root)`. Guarda.
4. En un par de minutos tu sitio queda disponible en `https://tuusuario.github.io/stickcode-site/` (o en tu dominio raíz si usaste el nombre especial).

## Agregar tu foto al fondo del Inicio

1. Guarda tu foto (blanco y negro, con la iluminación dramática) como `hero-photo.jpg`.
2. Colócala dentro de la carpeta `assets/`.
3. Ya está conectada — `index.html` la busca automáticamente en `assets/hero-photo.jpg`. Si el nombre del archivo es distinto, edita esta línea en `index.html`:
   ```html
   <section class="hero" style="background-image: url('assets/hero-photo.jpg');">
   ```

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

## Configurar tu email de contacto

Reemplaza `contacto@stickcode.dev` por tu correo real en `contacto.html` y `privacidad.html` (aparece varias veces).
