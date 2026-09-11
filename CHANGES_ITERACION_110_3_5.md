# PhysioSentinel Gait · V110.3.5

## SKEL Local Joint-Axis Calibration

- Se mantiene la calibración espacial exhaustiva de V110.3.4.
- Antes de CMA-ES se perturba automáticamente cada uno de los 46 q de SKEL con diferencia central ±0.08 rad alrededor de la pose neutra registrada.
- Para cada DoF se mide: sensibilidad XY, sensibilidad Z, joints más afectados, especificidad de la cadena anatómica esperada y eje angular efectivo aproximado.
- Los DoF con respuesta local incoherente quedan fuera del ajuste cuando existe cobertura suficiente.
- Se construye una semilla lineal XY a partir del Jacobiano local medido y CMA-ES parte de esa pose, no de q=0.
- El refinamiento por gradiente sigue siendo residual y se conserva la puerta anatómica del Frame 1.
- Se añade auditoría visible de los 46 DoF y exportación JSON de la calibración.
- Backblaze B2, HALPE26 Persistent Bridge, vídeos simplificados y pipeline clínico permanecen sin cambios.
