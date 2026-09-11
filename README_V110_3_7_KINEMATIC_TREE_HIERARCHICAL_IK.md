# V110.3.7 · Kinematic-Tree Aware DoF Calibration + Hierarchical IK

Objetivo: corregir el falso descarte de DoF proximales observado en V110.3.5/3.6. En una cadena cinemática real, flexionar una cadera desplaza rodilla y tobillo; mover un hombro desplaza codo y muñeca. Esa propagación distal es válida y no debe tratarse como contaminación.

## Flujo
1. HALPE26/V104-V107.
2. Unified Coordinate Frame congelado.
3. Perturbación ±Δ de q0…q45.
4. Clasificación por subárbol cinemático permitido y fuga cross-chain.
5. Semilla Jacobiana XY.
6. IK jerárquica proximal→distal por cadenas.
7. CMA-ES de rescate alrededor de la semilla jerárquica.
8. Refinamiento por gradiente y auditoría anatómica.
9. Sólo si PASS, propagación temporal.

La similitud global no puede ser recolocada por las extremidades. El modo monocular sigue usando profundidad Z protegida y no convierte el 3D estimado en medición métrica.
