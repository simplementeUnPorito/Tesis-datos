# Datos experimentales de Tesis

Este repositorio versiona el índice de las mediciones del sistema MASW mediante Git LFS. GitHub conserva punteros pequeños; los objetos, que ocupan cerca de 30 GB, viven en el folderstore privado sincronizado por OneDrive.

## Estructura local

```text
Tesis-datos/
├── raw/        # capturas originales, inmutables; contenido LFS
├── processed/  # resultados y exportaciones; contenido LFS
├── scripts/    # configuración e hidratación del folderstore
└── CATALOGO.md # inventario de conjuntos de datos
```

La aplicación Python descubre este repositorio automáticamente cuando está montado como `data/` dentro del superproyecto. En un clon independiente puede definir `TESIS_DATA_ROOT` con la ruta absoluta del repositorio.

## Configuración del folderstore

El almacén actual está en `C:/Users/elias/OneDrive/Github-LFS/repositories/Tesis-datos`. Para que la configuración siga funcionando después de mover OneDrive, Google Drive o el disco, defina primero la raíz:

```powershell
$env:GITHUB_LFS_ROOT = 'C:\Users\elias\OneDrive\Github-LFS'
.\scripts\configure-lfs-folderstore.ps1
```

El script configura tanto el adaptador `lfs-folderstore` como `lfs.storage`. Los objetos no se duplican dentro de `.git/lfs`; la copia de OneDrive actúa como almacén y caché local.

Para clonar sin intentar descargar inmediatamente los 30 GB:

```powershell
$env:GIT_LFS_SKIP_SMUDGE = '1'
git clone https://github.com/simplementeUnPorito/Tesis-datos.git
Remove-Item Env:GIT_LFS_SKIP_SMUDGE
Set-Location Tesis-datos
.\scripts\configure-lfs-folderstore.ps1
```

Los archivos quedan como punteros hasta hidratar el conjunto requerido:

```powershell
.\scripts\hydrate-lfs.ps1 -Include 'raw/Canchita/**'
# o, deliberadamente, todo el almacén:
.\scripts\hydrate-lfs.ps1 -All
```

## Reglas

1. No modificar capturas dentro de `raw/`.
2. Guardar todo resultado reproducible en `processed/`.
3. Documentar cada nuevo conjunto en `CATALOGO.md`.
4. Ejecutar el configurador antes de agregar datos para que los bytes entren directamente en OneDrive.
5. No ejecutar `git lfs prune`: `lfs.storage` apunta al folderstore compartido y esa operación podría borrar el almacén remoto.
6. Actualizar el manifiesto central de `Github-LFS` después de agregar o retirar objetos.
