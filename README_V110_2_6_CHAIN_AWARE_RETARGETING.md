# PhysioSentinel Gait V110.2.6 — Chain-Aware Empirical Retargeting

- Conserva la calibración automática q0…q45 y el Jacobiano real de SKEL.
- Sustituye la selección global por rango por una selección localizada en cinco cadenas observables: axial, pierna derecha, pierna izquierda, brazo derecho y brazo izquierdo.
- Penaliza los q con efecto importante fuera de su cadena y exige independencia lineal dentro de cada cadena.
- Mantiene q0–q2 fuera del retargeting para no duplicar la rotación global.
- Mantiene DOF no seleccionados exactamente neutros, regularización temporal, Side-by-Side y Mesh Walker.
- El botón de calibración se renombra como auditoría avanzada opcional; el Jacobiano necesario se calcula automáticamente.
