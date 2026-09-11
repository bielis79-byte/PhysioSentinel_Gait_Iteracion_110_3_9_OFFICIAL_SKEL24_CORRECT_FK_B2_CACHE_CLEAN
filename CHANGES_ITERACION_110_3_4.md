# PhysioSentinel Gait V110.3.4 · SKEL Coordinate-System Calibration

## Cambio principal
Antes de permitir que SKELAnatomicalAutomata modifique los parámetros articulares, V110.3.4 calibra explícitamente la convención espacial entre la salida V104/V107/HALPE26 y el modelo SKEL neutro.

- Evalúa exhaustivamente 48 combinaciones de permutación de ejes y signos (incluidas transformaciones con cambio de handedness).
- Para cada convención calcula una similitud propia: rotación residual det=+1, escala y traslación.
- La selección se realiza con prioridad XY, Z protegida y penalización a rotaciones residuales grandes.
- La matriz seleccionada (`axis_map`) se conserva en Frame 1, propagación temporal y Mesh Walker.
- CMA-ES trabaja ya sobre las coordenadas registradas, evitando que q anatómicos compensen una inversión/reflexión global.

## Diagnóstico visible
La pestaña SKEL muestra:
- 48/48 convenciones probadas.
- determinante de la transformación elegida;
- permutación y signos;
- rotación residual;
- RMSE XY de la pose neutra registrada;
- tabla con las mejores convenciones candidatas.

## Correcciones adicionales
- Corregido `TypeError: Object of type ndarray is not JSON serializable` mediante serialización recursiva de NumPy a tipos Python.
- El JSON del Frame 1 exporta `axis_map` y `coordinate_system_calibration` completos.
- La misma transformación se aplica a los `skin_verts` de Mesh Walker para que joints y malla compartan exactamente el mismo sistema espacial.
- Aislamiento de `session_state` bajo claves V110.3.4 para evitar reutilizar secuencias/mallas de una versión anterior.

## Se mantiene
- HALPE26 Persistent Bridge.
- profundidad Z monocular protegida;
- SKELAnatomicalAutomata / CMA-ES reducido;
- puerta anatómica antes de 75 frames;
- Backblaze B2 privado → `/tmp` → validación ZIP → PKL → fallback manual;
- NumPy 2.x / Pose2Sim / OpenSim intactos.
