# V110.3.6 · SKEL Local Joint-Axis Calibration

Objetivo: dejar de asumir que la etiqueta semántica de un q basta para conocer su efecto geométrico en el modelo privado SKEL. La versión mide empíricamente la respuesta local de cada DoF sobre la pose neutra ya registrada en el sistema V104/V107.

Pipeline Frame 1:

1. HALPE26/V104/V107 y registro de coordenadas.
2. Pose SKEL neutra.
3. Perturbación central +Δ/-Δ de q0..q45.
4. Jacobiano articular medido, cadena dominante y eje angular efectivo.
5. Filtro de DoF anatómicamente coherentes.
6. Semilla lineal XY acotada.
7. CMA-ES reducido desde esa semilla.
8. Refinamiento gradiente residual.
9. Auditoría anatómica y circuit breaker antes de 75 frames.

La malla no se usa durante la calibración; sólo joints, reduciendo coste de CPU. La malla SKEL se genera únicamente tras superar la puerta anatómica.
