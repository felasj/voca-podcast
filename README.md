# Voca Podcast — sitio web

Sitio estático de 4 páginas (Inicio, Episodios, Sobre Voca y Contacto) hecho con HTML, CSS y JavaScript, sin frameworks ni proceso de build. Está pensado para publicarse gratis en GitHub Pages.

## Ver el sitio en local

```bash
cd ~/portfolio
python3 -m http.server 8000
```

Abrí <http://localhost:8000> en el navegador. Para detenerlo, `Ctrl + C`.

## Estructura

```
portfolio/
├── index.html          Inicio
├── episodios.html      Los 6 episodios destacados
├── sobre.html          Sobre Voca
├── contacto.html       Formulario y redes
├── assets/
│   ├── css/styles.css  Todos los estilos
│   ├── js/main.js      Menú móvil, animaciones y formulario
│   └── img/            Logo, iconos y miniaturas de episodios
└── README.md
```

## Editar contenido

### Agregar o cambiar un episodio

Las tarjetas están duplicadas en `index.html` (las 3 más recientes) y en `episodios.html` (las 6). Para agregar una:

1. Guardá la miniatura en `assets/img/` (por ejemplo `ep-07.jpg`, 16:9).
2. Copiá un bloque `<article class="episode-card reveal">...</article>` completo.
3. Cambiá imagen, nombre del invitado, título, descripción, duración, fecha y el enlace de YouTube (aparece dos veces: en el título y en "Ver en YouTube").

No hace falta tocar el CSS.

### Cambiar textos generales

- Frase de presentación: buscarla en `index.html`, `sobre.html` y el footer.
- Datos de contacto: `contacto.html` y el footer.
- Enlaces a YouTube, Spotify e Instagram: están en todas las páginas.

## Conectar el formulario (Formspree)

El formulario usa Formspree. El plan gratis permite unas 50 consultas por mes.

1. Creá una cuenta en <https://formspree.io> con `maximosarmiento2004@gmail.com`.
2. Creá un formulario nuevo (nombre: "Voca Podcast").
3. Copiá el endpoint, con la forma `https://formspree.io/f/xxxxxxxx`.
4. En `contacto.html`, reemplazá `https://formspree.io/f/TU_ID` por ese endpoint.
5. Enviá una prueba desde el sitio publicado.

Mientras el endpoint siga siendo `TU_ID`, el sitio muestra un aviso con el email de contacto en lugar de enviar.

## Publicar en GitHub Pages

1. Creá una cuenta en <https://github.com> (si todavía no tenés).
2. Creá un repositorio **público** llamado, por ejemplo, `voca-podcast`.
3. Desde la carpeta del sitio:

```bash
cd ~/portfolio
git init
git add .
git commit -m "Sitio de Voca Podcast"
git branch -M main
git remote add origin https://github.com/USUARIO/voca-podcast.git
git push -u origin main
```

4. En el repositorio: **Settings → Pages → Build and deployment**.
5. En **Source**, elegí **Deploy from a branch**.
6. En **Branch**, elegí `main` y la carpeta `/ (root)`. Guardá.
7. Esperá uno o dos minutos. La URL queda así:
   - `https://USUARIO.github.io/voca-podcast/` si el repo se llama `voca-podcast`.
   - `https://USUARIO.github.io/` si el repo se llama `USUARIO.github.io`.

Todos los enlaces internos son relativos, así que funcionan en cualquiera de las dos URLs.

## Dominio propio (más adelante)

En **Settings → Pages → Custom domain** se agrega el dominio y GitHub indica los registros DNS. Después conviene actualizar las etiquetas `og:image` de los cuatro HTML con la URL absoluta final.

## Notas

- Las miniaturas de los episodios se descargaron del canal de YouTube y se optimizaron a 800 × 450 px.
- Las tipografías (Instrument Serif e Inter) se cargan desde Google Fonts.
- No hay analytics ni cookies de seguimiento.
- El logo original está en `/home/felipe/Facultad/Narrativas Transmedia/logo voca podcast.jpg`. Los archivos `mark-navy.png` y `mark-white.png` se derivaron de ahí.
