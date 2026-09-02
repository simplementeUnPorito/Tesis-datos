# Catálogo de datos versionados con LFS

Inventario tomado durante la modularización del 20 de julio de 2026. Los tamaños son aproximados. El contenido se conserva en `Github-LFS/repositories/Tesis-datos/objects` y GitHub guarda los punteros.

| Estado | Conjunto | Archivos | Tamaño aproximado |
|---|---|---:|---:|
| crudo | Canchiga | 9.312 | 12,432 GiB |
| crudo | Canchita | 9.930 | 10,812 GiB |
| crudo | Canchita_2 | 2.472 | 5,016 GiB |
| crudo | Estacionamiento | 12 | 0,003 GiB |
| crudo | Osciloscopio | 90 | 0,005 GiB |
| crudo | Osciloscopio_calibracion_2026-07-21 | 157 | 0,010 GiB |
| crudo | Osciloscopio_descartado_2026-07-20_BP_43k | 156 | 0,018 GiB |
| crudo | Osciloscopio_verificacion_calibracion_2026-07-21 | 182 | 0,011 GiB |
| procesado | Canchiga | 3 | <0,001 GiB |
| procesado | Canchita | 9 | 0,006 GiB |
| procesado | Canchita_2 | 1 | <0,001 GiB |
| procesado | Canchita_grupo1_procesado | 1.501 | 0,415 GiB |
| procesado | Canchita_procesado | 2.014 | 0,530 GiB |
| procesado | raw (auxiliares heredados) | 8 | <0,001 GiB |
| servidor | capturas, índices y un resultado de análisis | 41 | 0,010 GiB |
| modelado | Moldeo Hidro | 3 | <0,001 GiB |

Los conteos corresponden a archivos versionados/materializados al 2026-09-02.
Los ZIP sueltos de intercambio se conservan, pero no se contabilizan como un
conjunto experimental independiente. Consulte `server/README.md` para la
estructura del snapshot del servidor.

Las carpetas `raw/` y `processed/` provienen de los antiguos directorios `Crudos/` y `procesados/`. El manifiesto exhaustivo, con ruta, tamaño y SHA-256 por archivo, está en `Github-LFS/repositories/Tesis-datos/manifests/files.csv`.
