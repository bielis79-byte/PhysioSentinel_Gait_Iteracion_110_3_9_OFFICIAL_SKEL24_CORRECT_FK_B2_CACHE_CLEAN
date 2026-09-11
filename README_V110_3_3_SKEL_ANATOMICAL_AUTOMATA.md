# V110.3.3 · SKELAnatomicalAutomata

Flujo del Frame 1:

`HALPE26/V104 → registro neutro → CMA-ES reducido → Top-K → refinamiento gradiente → auditoría anatómica → PASS/FAIL`

La búsqueda estocástica no intenta resolver los 46 q de SKEL. En monocular frontal/posterior utiliza un subespacio de 16 DoF con información razonablemente observable en X/Y y mantiene cerca de neutro los DoF axiales/escapulares que pueden utilizar la profundidad inferida para producir torsiones artificiales.

La malla corporal no participa en CMA-ES. Cada generación evalúa únicamente `joints` (`skelmesh=False`) y la malla se habilita después de superar la puerta anatómica.

### Criterio de seguridad
La secuencia temporal queda bloqueada si el Frame 1 no supera simultáneamente la auditoría ósea y un RMSE XY < 0.38. El objetivo es evitar invertir tiempo en 75 frames cuando la pose semilla ya es anatómicamente incorrecta.

### Backblaze B2
Se mantiene la carga automática privada configurada mediante Streamlit Secrets. Los modelos SKEL no se almacenan en GitHub, Supabase ni en las exportaciones clínicas.
