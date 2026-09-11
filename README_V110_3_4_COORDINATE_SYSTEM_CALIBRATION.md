# V110.3.4 · SKEL Coordinate-System Calibration

V110.3.4 introduce una etapa discreta previa al ajuste anatómico para separar dos problemas que en versiones anteriores podían confundirse: **convención espacial global incorrecta** y **pose articular incorrecta**.

## Pipeline

`HALPE26/V104/V107 → SKEL neutro → 48 axis/sign/handedness candidates → mejor axis_map → registro rígido/similitud → CMA-ES anatómico reducido → refinamiento → auditoría → PASS/FAIL → temporal → mesh`

## Principio

Una reflexión o intercambio de ejes no debe ser corregido doblando columna, escápulas, caderas o brazos. V110.3.4 busca primero la transformación discreta del marco de coordenadas. El optimizador articular sólo actúa después.

## Criterio práctico

La versión no promete que una de las 48 transformaciones resuelva por sí sola el ajuste. Su función es demostrar si el origen del error estaba en el marco espacial. El Frame 1 seguirá bloqueando la propagación si la auditoría anatómica no es válida o RMSE XY no supera el umbral configurado.

## Exportación

`V110_3_4_SKEL_fit_frame1.json` incorpora:
- `axis_map`
- `coordinate_system_calibration`
- mejores candidatos de convención
- CMA-ES / Top-K
- RMSE XY/Z
- auditoría angular ósea
- parámetros q activos
