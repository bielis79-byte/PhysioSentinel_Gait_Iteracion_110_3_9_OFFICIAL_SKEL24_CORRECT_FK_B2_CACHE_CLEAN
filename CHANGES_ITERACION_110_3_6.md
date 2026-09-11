# V110.3.6 · Unified Coordinate Frame

- Congela una única transformación `T_SKEL→V104 = axis_map + R + scale + translation` tras la calibración espacial del frame semilla.
- Todas las perturbaciones `+Δ/-Δ` de los 46 DoF se evalúan después de aplicar exactamente la misma transformación.
- Añade test de invariancia obligatorio entre Coordinate Calibration y Local DoF Calibration sobre las mismas 15 correspondencias.
- Si `ΔRMSE > 1e-5` o las coordenadas reconstruidas difieren más de `1e-5`, el pipeline se detiene antes de Jacobiano/CMA-ES.
- CMA-ES ya no puede modificar rotación global, escala ni traslación: sólo optimiza q anatómicos.
- El refinamiento Adam y la propagación temporal mantienen congelado el marco global.
- Corrige la comparación anterior entre RMSE calculados sobre subconjuntos distintos de landmarks: el panel muestra ahora RMSE neutral sobre las 15 correspondencias.
- Mantiene Backblaze B2 privado, HALPE26 Persistent Bridge, vídeos simplificados y Atlas/SKEL.
