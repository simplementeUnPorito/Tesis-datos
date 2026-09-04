# `data/lab` — datos de banco, NO son datos de campo

Todo lo que hay acá se generó probando el pipeline sobre la mesa, con un solo
nodo y el geófono quieto. **No sirve para ningún análisis geofísico** y no tiene
que mezclarse con `data/raw`, que son 29 GB de campañas reales.

## Cómo se mantiene separado

Con una sola variable de entorno. El servidor la respeta para las tres raíces:

```powershell
Set-Location C:\Github\Tesis\src\interfaces\python
$env:TESIS_DATA_ROOT = 'C:\Github\Tesis\data\lab'
& $py -m server --port 8011
```

Eso manda `raw`, `processed` y `server` adentro de `data/lab`. No hizo falta
tocar código, y se puede confirmar en `/api/meta`, que informa las tres raíces
activas.

## Qué hay adentro

Capturas del nodo 2 (geófono) tomadas por el maestro y subidas por `/ingest`
con el mismo contrato que exporta la página (`geophone_scope_web_zip_v4`):

- `raw/<id>/` — una carpeta por ingesta, con `metadata.json`, `maestro/` y
  `captures/`.
- `server/zips/` — el ZIP original de cada ingesta, tal como llegó.

Todas son de **reposo**: el geófono no fue golpeado, así que los pocos
milivoltios de excursión son ruido y microvibración ambiente. Y quedan como
`estado: "Sin martillo"` en el catálogo, que es correcto: hay un solo esclavo
conectado, así que no hay canal de martillo y no habilitan picking ni MASW.

## Se puede borrar entera

No hay nada acá que haga falta conservar. Si molesta, se borra `data/lab`
completa y no se pierde nada.
