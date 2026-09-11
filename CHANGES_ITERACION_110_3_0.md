# PhysioSentinel Gait · Iteración 110.3.0

## SKEL Direct Anatomical Pose Mapping

- Se abandona la selección empírica/ranking global de q0…q45 como mecanismo principal de retargeting.
- Se usa la semántica anatómica oficial de los 46 parámetros SKEL: pelvis, caderas, rodillas, tobillos, columna, cabeza, escápulas, hombros, codos, pronosupinación y muñecas.
- El registro rígido global se resuelve con pelvis–caderas–cuello; q0–q2 quedan neutros para no duplicar esa rotación global.
- Las cadenas observables usan únicamente q anatómicos preasignados: tronco, cabeza, pierna derecha, pierna izquierda, brazo derecho y brazo izquierdo.
- El coste combina posición XYZ, dirección de vectores óseos y regularización fuerte a neutro/pose temporal previa.
- Se añaden límites conservadores por articulación para evitar que un descenso de RMSE se consiga mediante torsión de tronco o brazos.
- El frame semilla incorpora una puerta anatómica: la secuencia 1→75 queda bloqueada si RMSE >= 0.50 o la auditoría angular ósea detecta alertas.
- Se mantienen Side-by-Side XYZ | SKEL joints | SKEL mesh, vídeo 3D simplificado V104/V107, Mesh Walker y exportaciones JSON/NPZ.

## Verificación del PKL privado

Antes de usar el modelo se verifica la presencia de las estructuras anatómicas privadas:
`joints_name`, `pose_params_name`, `parameter_mapping`, `per_joint_rot` y `osim_kintree_table`.
La app muestra versión del modelo y dimensiones de las estructuras, sin exportar ni redistribuir el PKL.

## Backblaze B2 Auto-Loader

Secrets esperados:

```toml
B2_KEY_ID = "..."
B2_APPLICATION_KEY = "..."
B2_BUCKET = "physiosentinel-skel-assets"
B2_FILE = "skel_models_v1.1(1).zip"
```

Flujo: `b2_authorize_account v4` → descarga privada por nombre → `/tmp` → verificación SHA-1 B2 + ZIP CRC + presencia de ambos PKL → extracción temporal → carga SKEL.
Si B2 no está disponible, sigue apareciendo el uploader manual.
Supabase no almacena el bundle SKEL.
