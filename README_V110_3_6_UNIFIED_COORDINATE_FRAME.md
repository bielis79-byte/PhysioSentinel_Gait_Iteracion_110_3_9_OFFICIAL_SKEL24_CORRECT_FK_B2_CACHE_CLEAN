# PhysioSentinel Gait V110.3.6

## Objetivo
Eliminar cualquier deriva de convención espacial entre la calibración inicial de SKEL y los módulos posteriores.

## Regla principal
Tras resolver las 48 convenciones de ejes/signos se crea una transformación inmutable `T_SKEL→V104`. Local DoF Calibration, semilla Jacobiana, CMA-ES, refinamiento y render de malla deben usar esa misma convención.

## Circuit breaker
Antes de calibrar los DoF se calcula el RMSE XY sobre las mismas 15 correspondencias desde dos rutas independientes. La diferencia debe ser ≤ `1e-5`; de lo contrario el ajuste se bloquea.

## Optimización
CMA-ES y Adam sólo pueden modificar los q anatómicos. La rotación global, escala y traslación obtenidas en el registro inicial quedan congeladas durante el frame semilla.
