# Portafolio — Esteban Vizcaíno

Sitio personal bilingüe (inglés / español), estático y sin dependencias.
Publicado con **GitHub Pages** en <https://estebanvizca.github.io>.

## Estructura

```
.
├── index.html              # Versión en inglés (raíz)
├── es/index.html           # Versión en español
├── assets/
│   ├── styles.css          # Todo el diseño (claro y oscuro automáticos)
│   ├── script.js           # Menú móvil y año del pie de página
│   └── Esteban_Vizcaino_CV.pdf
└── .nojekyll               # Evita el procesamiento de Jekyll en Pages
```

No hay build, ni Node, ni dependencias: lo que hay en el repo es lo que se publica.

## Publicar por primera vez

1. Crea un repositorio **público** llamado exactamente `estebanvizca.github.io`
   en <https://github.com/new>.
2. Desde esta carpeta:

   ```bash
   git init -b main
   git add .
   git commit -m "Portafolio bilingüe"
   git remote add origin https://github.com/estebanvizca/estebanvizca.github.io.git
   git push -u origin main
   ```

3. En GitHub: **Settings → Pages → Build and deployment**.
   Source: *Deploy from a branch* · Branch: `main` · Folder: `/ (root)` · **Save**.
4. Espera uno o dos minutos y abre <https://estebanvizca.github.io>.

### Autenticación

GitHub ya no acepta contraseña por HTTPS. Al hacer `git push` te pedirá
usuario y contraseña: usa un **token personal** (Settings → Developer settings →
Personal access tokens → Fine-grained tokens, permiso *Contents: read and write*)
como contraseña. La otra opción es registrar tu clave SSH en GitHub:

```bash
cat ~/.ssh/id_ed25519.pub
# Copiar la salida en https://github.com/settings/keys
git remote set-url origin git@github.com:estebanvizca/estebanvizca.github.io.git
```

## Editar contenido

- Cada idioma es un archivo independiente. Al cambiar un texto en `index.html`,
  replica el cambio en `es/index.html`.
- Para sustituir el CV, reemplaza `assets/Esteban_Vizcaino_CV.pdf` manteniendo el nombre.
- Para añadir un proyecto, copia un bloque `<article class="project">` completo y
  actualiza el índice, las etiquetas, las métricas y el enlace.
- El diseño está en `assets/styles.css`. Los colores son variables al inicio del
  archivo y el modo oscuro se activa solo con la preferencia del sistema.

## Comprobar en local

```bash
python3 -m http.server 8000
# http://localhost:8000        (inglés)
# http://localhost:8000/es/    (español)
```

## Dominio propio (opcional)

Si compras un dominio, añade un archivo `CNAME` en la raíz con el dominio
(`estebanvizcaino.com`) y configura en tu proveedor un registro `CNAME` hacia
`estebanvizca.github.io`. Después actualiza las etiquetas `canonical` y
`hreflang` de ambos archivos.
