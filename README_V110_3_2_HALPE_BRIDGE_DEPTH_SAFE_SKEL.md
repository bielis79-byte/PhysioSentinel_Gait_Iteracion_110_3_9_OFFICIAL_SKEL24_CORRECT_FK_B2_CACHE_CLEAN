# V110.3.2 · HALPE26 persistent bridge + depth-safe SKEL

Objetivo: corregir la regresión detectada en V110.3.1 donde el análisis frontal generaba métricas y gráficas pero el atlas informaba que no existía una secuencia HALPE26 válida después de limpiar `analysis_df`.

La V110.3.2 conserva únicamente el segmento numérico de landmarks y FPS en memoria de sesión, sin conservar vídeo ni archivos Pose2Sim. Ese snapshot alimenta V83 → V104/V107 → vídeo simplificado → atlas → SKEL.

Para vídeo frontal/posterior monocular, la profundidad Z es estimada. SKEL reduce su peso para impedir que una profundidad no observada fuerce torsiones de tronco/brazos. Backblaze B2 permanece como cargador privado automático del ZIP oficial SKEL.
