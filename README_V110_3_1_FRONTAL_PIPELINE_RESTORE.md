# V110.3.1 · Frontal pipeline restore

Pipeline esperado con una cámara frontal/posterior:

`HALPE26 2D → V83 monocular 3D estimado/no métrico → V89 visualización/vídeo → V104 → V107 (75F) → SKEL Direct Anatomical Pose Mapping`

La pestaña 9 publica además la cinemática 2D frontal directamente desde el tracking ya calculado, sin depender de un perfil biplanar V48.

El modo frontal/posterior sigue siendo monocular: la profundidad Z es inferida y el atlas/3D no debe interpretarse como reconstrucción métrica calibrada.
