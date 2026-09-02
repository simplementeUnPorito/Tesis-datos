# Snapshot de datos del servidor de campo

Esta carpeta contiene evidencia generada por el servidor Python durante las
pruebas del 24 y 27 de julio de 2026. No contiene el servidor ejecutable; el
código activo vive en `src/interfaces/python/server`.

## Estructura

| Ruta | Contenido |
|---|---|
| `raw/` | dos campañas recibidas, con metadatos, señales por nodo y CSV combinados |
| `zips/` | paquetes originales correspondientes a esas dos campañas |
| `analysis-results/` | índice JSON de una ejecución de análisis |
| `artifacts/` | curva, inversión y perfil exportados por esa ejecución |
| `analysis_jobs.json` | estado de la cola de análisis |
| `campaigns.json` | índice de campañas |
| `jobs.json` | estado de trabajos de ingreso/procesamiento |

Los JSON de estado son snapshots históricos y no deben reutilizarse como cola
activa al arrancar otra instancia. Para una prueba nueva, configure la raíz de
datos del servidor y deje que la aplicación cree su propio estado.

Al publicar resultados derivados hay que conservar el identificador de campaña
y documentarlos en `data/CATALOGO.md`; no se deben modificar las señales dentro
de `server/raw/`.
