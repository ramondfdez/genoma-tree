# genoma.tree

Árbol familiar interactivo construido con HTML, CSS y JavaScript vanilla. La aplicación carga la información genealógica desde `familia.json`, representa las relaciones en un lienzo navegable y permite explorar cada persona desde su tarjeta.

La versión pública usa datos ficticios y está marcada como ejemplo.

## Características

- Visualización jerárquica de antepasados y descendientes.
- Tarjetas con nombre, apellidos, fechas y rol familiar.
- Conexiones SVG entre generaciones.
- Arrastre para explorar y controles de zoom.
- Panel de detalle al seleccionar una persona.
- Exportación del árbol a PNG.
- Recarga automática de `familia.json` durante el desarrollo.
- Publicación automática en GitHub Pages.

## Ejecutar en local

Requisitos: Python 3 y un navegador moderno.

```bash
./start-server
```

El script inicia un servidor HTTP local en `http://127.0.0.1:8000/` y abre la aplicación en el navegador. Para detenerlo, pulsa `Ctrl+C` en la terminal.

También se puede iniciar manualmente:

```bash
python3 -m http.server 8000 --bind 127.0.0.1
```

La aplicación necesita servirse por HTTP porque carga `familia.json` mediante `fetch`.

## Editar la familia

La información se encuentra en [`familia.json`](familia.json):

El archivo versionado contiene únicamente datos ficticios. Para trabajar con tu árbol privado en local, conserva tus datos en `familia.local.json`; ese archivo está ignorado por Git y la aplicación lo carga automáticamente antes de usar el ejemplo público como fallback.

- `personas`: nodos individuales del árbol.
- `familias`: relación entre padres e hijos.

Los identificadores representan la posición jerárquica dentro del árbol. Después de guardar cambios, la aplicación los detecta automáticamente mientras está abierta.

No subas nunca `familia.local.json` ni datos personales a un repositorio público.

## Publicar en GitHub Pages

El workflow [`deploy-pages.yml`](.github/workflows/deploy-pages.yml) se ejecuta en cada push a `main` y también se puede lanzar manualmente desde la pestaña **Actions**.

Para activarlo:

1. Sube el repositorio a GitHub.
2. En **Settings > Pages**, selecciona **GitHub Actions** como fuente de despliegue.
3. Haz push a `main`.
4. GitHub mostrará la URL publicada en la ejecución del workflow y en **Settings > Pages**.

El sitio no requiere compilación: Pages publica directamente `index.html`, `app.js`, `styles.css`, `familia.json`, `public/` y el resto de archivos estáticos.

## Estructura

```text
.
├── app.js
├── familia.json
├── index.html
├── public/
├── start-server
├── styles.css
└── .github/workflows/deploy-pages.yml
```

## Licencia

El repositorio público contiene solo datos de ejemplo. Los datos familiares privados deben permanecer en `familia.local.json` y fuera de GitHub.
