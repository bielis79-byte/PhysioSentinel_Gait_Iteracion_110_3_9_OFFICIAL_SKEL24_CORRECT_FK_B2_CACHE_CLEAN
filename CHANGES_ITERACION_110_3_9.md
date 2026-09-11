# V110.3.9 · Official SKEL24 Joint Map + Correct FK Retargeting

## Causa raíz corregida
`SKEL.forward(...).joints` devuelve 24 articulaciones del árbol cinemático interno. El PKL privado expone `joints_name` con 22 nombres de otra capa semántica, por lo que usar esa lista para indexar directamente el tensor de 24 joints desplazaba las etiquetas anatómicas y provocaba falsas dependencias izquierda/derecha, `IndexError` y retargeting incoherente.

## Cambios
- Mapa oficial fijo de 24 joints del forward SKEL:
  `pelvis, femur_r, tibia_r, talus_r, calcn_r, toes_r, femur_l, tibia_l, talus_l, calcn_l, toes_l, lumbar_body, thorax, head, scapula_r, humerus_r, ulna_r, radius_r, hand_r, scapula_l, humerus_l, ulna_l, radius_l, hand_l`.
- Correspondencia HALPE/V104→SKEL24 explícita y por índice real del forward.
- FK Ground Truth recalculado sobre SKEL24, sin `model.joints_name` para indexar forward joints.
- Dependency Graph y Monotonic Hierarchical IK usan la lateralidad oficial de SKEL24.
- Test de sanity previo a la optimización: cadera/hombro/codo derechos no pueden quedar asignados al lado izquierdo, y viceversa.
- Visualizadores y exportaciones usan el mismo orden SKEL24.
- Se mantiene el Unified Coordinate Frame.
- Se mantiene SKEL Model Cache + Backblaze B2 Auto-Loader.
- Se bloquea el retargeting si falla la validación SKEL24.
