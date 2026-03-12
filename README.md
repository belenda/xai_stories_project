# XAI Stories — Curso 2025/26

Libro colaborativo de casos de estudio en Inteligencia Artificial Explicable (XAI), creado por estudiantes de la asignatura de XAI.

📖 **Libro online:** https://TU-USUARIO.github.io/xai-stories/

---

## Instrucciones para el profesor

### Requisitos previos

1. **Quarto** (>= 1.4): https://quarto.org/docs/get-started/
2. **Python** (>= 3.9) con Jupyter
3. **Git** y cuenta de GitHub

### Configuración inicial (una sola vez)

```bash
# 1. Crear el repositorio en GitHub (puede ser público desde el inicio)
#    Nombre sugerido: xai-stories

# 2. Clonar este proyecto
git clone https://github.com/TU-USUARIO/xai-stories.git
cd xai-stories

# 3. Instalar dependencias Python
pip install -r requirements.txt

# 4. Crear la imagen de portada
#    Poner tu imagen de portada en images/cover.png
#    (Se incluye un placeholder, sustitúyelo por una portada real)

# 5. Editar _quarto.yml
#    - Cambiar repo-url por la URL de tu repositorio
#    - Cambiar author por tu nombre / nombre de la asignatura

# 6. Editar index.qmd, foreword.qmd y acknowledgements.qmd
#    - Personalizar con los datos de tu asignatura

# 7. Compilar localmente para verificar
quarto preview

# 8. Subir a GitHub
git add .
git commit -m "Configuración inicial del libro XAI Stories"
git push origin main
```

### Activar GitHub Pages

1. Ir a **Settings > Pages** en el repositorio de GitHub.
2. En **Source**, seleccionar **GitHub Actions**.
3. El workflow se ejecutará automáticamente con cada push a `main`.

### Añadir capítulos de estudiantes

Cuando recibas los capítulos de los estudiantes:

```bash
# 1. Copiar el archivo .qmd (o .ipynb) del equipo a chapters/
cp entrega_equipo/capitulo.qmd chapters/02-nombre-descriptivo.qmd

# 2. Copiar las imágenes del equipo
cp -r entrega_equipo/figuras/ images/02-nombre-descriptivo/

# 3. Si el equipo entrega un .ipynb, Quarto lo renderiza directamente:
cp entrega_equipo/notebook.ipynb chapters/03-otro-capitulo.ipynb

# 4. Añadir el capítulo a _quarto.yml en la sección chapters:
#    chapters:
#      - chapters/02-nombre-descriptivo.qmd

# 5. Añadir las referencias del equipo al archivo references.bib

# 6. Si el equipo tiene dependencias Python adicionales, añadirlas a requirements.txt

# 7. Compilar y verificar
quarto preview

# 8. Subir
git add .
git commit -m "Añadir capítulo: Nombre del capítulo"
git push origin main
```

### Estructura del proyecto

```
xai-stories/
├── _quarto.yml              # Configuración del libro (EDITAR)
├── index.qmd                # Portada y prefacio (EDITAR)
├── foreword.qmd             # Prólogo (EDITAR)
├── acknowledgements.qmd     # Agradecimientos (EDITAR)
├── references.qmd           # Página de referencias (no tocar)
├── references.bib           # Bibliografía (AÑADIR entradas de cada equipo)
├── styles.css               # Estilos personalizados
├── requirements.txt         # Dependencias Python
├── chapters/                # Capítulos de los estudiantes
│   ├── 01-ejemplo.qmd       # Ejemplo/plantilla (sustituir por capítulos reales)
│   ├── 02-capitulo.qmd      # ...
│   └── 03-capitulo.ipynb    # (también acepta notebooks directamente)
├── images/                  # Imágenes
│   └── cover.png            # Portada del libro
├── docs/                    # Output generado (NO EDITAR, se genera solo)
└── .github/workflows/
    └── publish.yml          # CI/CD para GitHub Pages
```

### Tips

- **Notebooks `.ipynb`**: Quarto los renderiza directamente. Los estudiantes pueden entregar notebooks con narrativa integrada y no necesitan crear un `.qmd` aparte.
- **`code-fold: true`**: El código aparece colapsado por defecto en el libro, permitiendo una lectura más fluida. Los lectores pueden expandirlo si quieren ver el código.
- **`freeze: auto`**: Quarto cachea los resultados de ejecución. Solo re-ejecuta los capítulos que han cambiado. Esto acelera mucho la compilación.
- **Para no ejecutar código** de un capítulo (por ejemplo, si requiere GPU o datos grandes), añadir en la cabecera del archivo:
  ```yaml
  execute:
    eval: false
  ```
  y asegurarse de que las imágenes de output estén incluidas como archivos estáticos.

---

## Licencia

Este libro está licenciado bajo [CC BY-NC-SA 4.0](http://creativecommons.org/licenses/by-nc-sa/4.0/).
