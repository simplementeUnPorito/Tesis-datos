# Datos experimentales de Tesis

Este repositorio define la estructura y el catálogo del almacén de mediciones del sistema MASW. Los datos binarios no se publican en GitHub: actualmente ocupan cerca de 30 GB y deben permanecer en almacenamiento local o en un servicio de datos apropiado.

## Estructura local

```text
data/
├── raw/        # capturas originales, inmutables
├── processed/  # anotaciones, filtros, alineación y exportaciones
└── CATALOGO.md # inventario de conjuntos de datos
```

`raw/` y `processed/` están ignorados por Git. La aplicación Python los descubre automáticamente cuando este repositorio está montado como `data/` dentro del superproyecto. En un clon independiente puede definir la variable `TESIS_DATA_ROOT` con la ruta absoluta de este repositorio.

## Reglas

1. No modificar capturas dentro de `raw/`.
2. Guardar todo resultado reproducible en `processed/`.
3. Documentar cada nuevo conjunto en `CATALOGO.md`.
4. No usar `git add -f` para subir mediciones; GitHub no es el almacén de estos binarios.
