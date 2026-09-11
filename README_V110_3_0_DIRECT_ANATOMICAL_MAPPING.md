# V110.3.0 · SKEL Direct Anatomical Pose Mapping

Esta versión cambia el principio del retargeting: los parámetros q ya no se seleccionan por sensibilidad global. El solver trabaja con una asignación anatómica fija basada en la semántica oficial de SKEL y limita cada cadena a sus propias articulaciones.

La validación empieza en un solo frame. Deben cumplirse simultáneamente el control angular óseo y RMSE < 0.50 para habilitar la propagación temporal. Esto evita invertir tiempo en 75 frames cuando el tronco o los brazos ya son incorrectos en la pose semilla.

La versión conserva NumPy 2.x, Pose2Sim/OpenSim y el runtime SKEL CPU aislado. No instala `moderngl-window`.
