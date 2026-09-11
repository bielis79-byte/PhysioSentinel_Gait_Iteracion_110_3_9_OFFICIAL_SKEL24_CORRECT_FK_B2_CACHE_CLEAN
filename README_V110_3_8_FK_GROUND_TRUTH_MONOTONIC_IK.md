# V110.3.8 · FK Ground Truth + Dependency Graph + Monotonic IK

Objetivo: dejar de inferir la cinemática local de SKEL a partir del nombre de cada q. V110.3.8 mide directamente el efecto de cada DoF mediante el `forward()` real, construye un grafo q→joint y utiliza esas dependencias para resolver Frame 1 por cadenas con commit/rollback.

Pipeline:

`HALPE26/V104 → Unified Coordinate Frame → SKEL neutral → 46×(+Δ/-Δ) forward → Dependency Graph → linear seed → Monotonic Hierarchical IK → CMA-ES residual → gradient refine → anatomical gate → temporal propagation`

La capa de caché B2 reutiliza un ZIP válido ya presente en la instancia y evita descargar ~174 MB en cada rerun/version cuando el runtime conserva `/tmp`.
