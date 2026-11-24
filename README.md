# Catálogo de películas · Team Challenge

**Equipo:** Javier, Lorena, Judith

Catálogo de películas enriquecido a partir del dataset MovieLens: análisis con Pandas, sinopsis y web oficial desde la API de TMDB, y sinopsis en español generadas con Gemini.

## Reparto de funciones

| Persona | Rol | Notebook / tarea                                                                  |
|---------|-----|-----------------------------------------------------------------------------------|
| Javier  |  A  | 01_ingesta_limpieza, repositorio y ramas, README, PR final desde "develop" a main |
| Lorena  |  B  | 02_analisis (3, 4 y 5), calidad de datos y prueba de reproducibilidad             |
| Judith  |  C  | 03_tmdb y 04_gemini, APIs e IA Generativa                                         |

## Instalación

Requisitos: Python 3.10 o superior y Git.

**Windows (PowerShell):**

```powershell
git clone https://github.com/JaviRoma1984/tc-catalogo-peliculas.git
cd tc-catalogo-peliculas
python -m venv venv
venv\Scripts\Activate.ps1
pip install -r requirements.txt
Copy-Item .env.example .env
```

Si PowerShell bloquea la activación, ejecuta antes `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass` (solo afecta a esa terminal).

**macOS / Linux:**

```bash
git clone https://github.com/JaviRoma1984/tc-catalogo-peliculas.git
cd tc-catalogo-peliculas
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
```

Después abre el fichero `.env` y rellena las claves (ver la sección siguiente).

## Claves necesarias

| Variable                                                | Dónde se obtiene                                                    |
|---------------------------------------------------------|---------------------------------------------------------------------|
| `TMDB_READ_ACCESS_TOKEN` (recomendada) o `TMDB_API_KEY` | [themoviedb.org](https://www.themoviedb.org/) → Settings → API      |
| `GEMINI_API_KEY`                                        | [aistudio.google.com](https://aistudio.google.com/) → Claves de API |

- El fichero `.env` está en `.gitignore`: **nunca se sube al repositorio**. El repositorio solo incluye `.env.example`, sin valores.
- El notebook 04 no necesita la clave de TMDB, porque `data/processed/movies10.csv` ya viene en el repositorio.

## Ejecución

Abre la **carpeta del repositorio** en VS Code (los notebooks leen `data/` con rutas relativas), selecciona el kernel del entorno `venv` y ejecuta los notebooks **en este orden** con *Restart → Run All*. Cada uno genera un CSV en `data/processed/` que usa el siguiente:

1. `01_ingesta_limpieza.ipynb` → `movies_clean.csv`
2. `02_analisis.ipynb`
3. `03_tmdb.ipynb` → `movies10.csv`
4. `04_gemini.ipynb` → `movies10_es.csv`

## Resultados principales

- Existen 9742 películas, 100836 valoraciones de 610 usuarios y 3683 tags.
- 13 películas carecen de año en el título y 18 no tienen ninguna valoración.
- 306 películas son simultáneamente de ciencia ficción y de aventuras.
- La tag más repetida ha sido "In Netflix queue"