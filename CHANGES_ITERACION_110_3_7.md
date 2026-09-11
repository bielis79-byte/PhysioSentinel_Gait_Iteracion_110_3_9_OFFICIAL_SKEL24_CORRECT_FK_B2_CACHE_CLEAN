# V110.3.7 · Kinematic-Tree Aware DoF Calibration + Hierarchical IK

- Sustituye el criterio de localidad de V110.3.5/3.6 por un criterio basado en descendientes permitidos de la cadena cinemática.
- Un DoF proximal ya no se penaliza por mover rodilla/tobillo o codo/muñeca de su propia cadena.
- Se penaliza únicamente la fuga energética hacia cadenas anatómicas incompatibles.
- Añade calibración central ±Δ de 46 q con `allowed_descendant_energy`, `forbidden_cross_chain_energy` y `kinematic_tree_score`.
- Añade semilla IK jerárquica proximal→distal: tronco → cabeza → pierna D → pierna I → brazo D → brazo I.
- El marco unificado SKEL→V104 de V110.3.6 permanece congelado durante toda la IK y CMA-ES.
- CMA-ES parte de la pose obtenida por IK jerárquica, no de q=0.
- Mantiene HALPE26 Persistent Bridge, Atlas, vídeo 3D simplificado y Backblaze B2 privado.
