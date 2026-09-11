# PhysioSentinel Gait V110.3.3 · SKELAnatomicalAutomata

## Objetivo
Romper el ciclo de ajustes manuales del Frame 1 monocular incorporando un motor estocástico de rescate antes de la propagación temporal SKEL.

## Cambios principales
- Nuevo `SKELAnatomicalAutomata` en el Frame 1.
- Búsqueda CMA-ES interna, sin dependencia externa adicional.
- Espacio monocular reducido a 16 DoF anatómicos observables/seguros: caderas, rodillas, flexión/inclinación de tronco, hombros y codos.
- Las rotaciones axiales, escápulas y demás DoF mal observables desde frontal permanecen neutros durante la búsqueda monocular.
- Optimización global de rotación corporal y escala; la traslación se resuelve analíticamente para cada candidato.
- Función de energía `XY-first`: error coronal prioritario, Z protegida, dirección y longitud ósea, prior neutro y penalización por proximidad a límites.
- Evaluación SKEL vectorizada por población con `skelmesh=False` para evitar generar malla durante la búsqueda.
- Top-K de candidatos anatómicos y refinamiento final corto con Adam únicamente dentro de la cuenca encontrada por CMA-ES.
- Nueva métrica `RMSE XY` separada de `RMSE Z`.
- Circuit breaker del Frame 1: auditoría anatómica OK + RMSE XY < 0.38 antes de permitir la secuencia completa.
- La propagación temporal monocular conserva el mismo subespacio seguro de DoF.

## Infraestructura conservada
- HALPE26 Persistent Bridge de V110.3.2.
- Reconstrucción frontal/posterior → V83/V104/V107.
- Vídeo 3D simplificado y Atlas/SKEL.
- Backblaze B2 privado → `/tmp` → validación ZIP/PKL → fallback manual.
- NumPy 2.x y runtime SKEL CPU aislado.
