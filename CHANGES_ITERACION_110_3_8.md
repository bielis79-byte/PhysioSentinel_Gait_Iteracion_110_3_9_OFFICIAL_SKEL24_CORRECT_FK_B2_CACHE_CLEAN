# PhysioSentinel Gait V110.3.8

## SKEL Forward-Kinematics Ground Truth + Dependency Graph + Monotonic Hierarchical IK

- Mantiene congelado el Unified Coordinate Frame `T_SKEL→V104` validado en V110.3.6/3.7.
- Calibra los 46 q mediante perturbación central `+Δ/-Δ` ejecutando el `forward()` real de SKEL.
- Construye un grafo empírico `q → joints afectados` a partir del desplazamiento real de los 24 joints; no usa el nombre del parámetro como verdad cinemática.
- Asigna cada q al grupo anatómico donde concentra la mayor energía empírica observada.
- La semilla IK es proximal→distal y **monótona**: cada etapa sólo se confirma si reduce/no empeora el RMSE XY global y no deteriora las cadenas previamente congeladas. Si falla, hace rollback automático.
- CMA-ES queda como rescate residual posterior a una semilla cinemática empírica, con transformación global congelada.
- La puerta anatómica de Frame 1 permanece activa antes de propagar 75 frames.

## Backblaze B2 / SKEL Model Cache

- Directorio de caché runtime estable e independiente del número de versión: `/tmp/physiosentinel_skel_b2_cache_v1_1`.
- Si el ZIP privado ya existe y supera SHA/CRC + comprobación de ambos PKL, **no se llama a Backblaze B2**.
- El origen visible informa `cache runtime HIT` o `MISS → guardado`.
- Los PKL extraídos también se reutilizan desde `/tmp/physiosentinel_skel_models_cache_v1_1`.
- Backblaze sólo se consulta cuando no existe una copia válida en la instancia activa.
- La caché es de runtime; un contenedor completamente nuevo puede requerir una descarga inicial.
